# Backend de comentários no Firebase (multiusuário, tempo real)

A camada de revisão do `obeya-board.html` já está preparada para salvar os comentários
na nuvem via **Firebase Firestore**. Enquanto o config não for preenchido, ela usa
`localStorage` (igual antes). Ao colar o config, passa a **salvar e sincronizar entre
todos os usuários em tempo real**.

## 1. Criar o projeto
1. Acesse <https://console.firebase.google.com> → **Adicionar projeto**.
2. No projeto, **Criar app Web** (ícone `</>`) → copie o objeto `firebaseConfig`.
3. Menu **Build → Firestore Database → Criar banco de dados** → modo **Production** (ou Test) → escolha a região.

## 2. Colar o config no protótipo
No `obeya-board.html`, no bloco `window.RV_CONFIG`, substitua `firebase: null` pelo seu config:

```js
window.RV_CONFIG = {
  key: 'obeya_board_v1',
  title: 'Review — Digital Obeya',
  modalSelector: '.edit-modal, .room-modal',
  firebaseCollection: 'rv_comments',
  firebase: {
    apiKey: 'AIza…',
    authDomain: 'SEU-PROJ.firebaseapp.com',
    projectId: 'SEU-PROJ',
    storageBucket: 'SEU-PROJ.appspot.com',
    messagingSenderId: '0000000000',
    appId: '1:0000:web:abcdef'
  }
};
```

> Dica: a `key` define o "documento" da página. Cada protótipo/página deve ter uma `key`
> única para não misturar comentários.

## 3. Regras de segurança (Firestore Rules)
Para um protótipo interno de revisão (sem login), libere a coleção de comentários:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /rv_comments/{docId} {
      allow read, write: if true;   // protótipo aberto — qualquer um lê/escreve
    }
  }
}
```

⚠️ **Atenção:** essas regras são abertas (qualquer pessoa com a URL e o config pode
ler/escrever). Bom para revisão interna; para algo sensível, restrinja por
**Firebase Authentication** (ex.: `allow read, write: if request.auth != null`) ou por
domínio de e-mail.

## 4. Como funciona (modelo de dados)
- Um documento por página: `rv_comments/<key>` (ex.: `rv_comments/obeya_board_v1`).
- Conteúdo: `{ savedAt, comments: [ {n, view, xPct, yPct, author, text, ts, resolved} ] }`.
- **Tempo real:** a página escuta o documento com `onSnapshot` — quando alguém salva,
  todos os abertos recebem e re-renderizam os pinos/lista.
- **Sem config:** cai no `localStorage` + Exportar/Importar (comportamento offline).

## 5. Observações
- A escrita é do **array inteiro** (last-write-wins por save). Para poucos revisores
  simultâneos é suficiente; se precisar de edição concorrente fina, migrar para
  **um documento por comentário** (`rv_comments/<key>/items/<id>`) com `onSnapshot` na
  subcoleção (evolução futura).
- O campo `view` mantém a separação board × modal (comentário feito num modal só aparece
  naquele modal).
- Continua funcionando o **Exportar/Importar** para snapshots/backup.
