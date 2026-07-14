# Select Australia · To-Do da Equipa

Plataforma de lista de tarefas partilhada pela equipa **Select Australia** (IberCup), sincronizada em tempo real. Uma única página (`index.html`), pensada para **GitHub Pages**.

## Funcionalidades

- 🔐 Login com Google (Firebase Auth)
- 🔄 Sincronização em tempo real (Firestore) — todos veem as alterações ao instante
- 📅 Prazos com urgência (atrasada / hoje / amanhã)
- 👤 Responsável por missão + filtro "Minhas"
- 🏷️ Categorias com cor (Viagem · Pagamentos · Equipamento · Documentos)
- ✎ Editar tarefas, comentários, "limpar concluídas"
- 🗓️ Countdown para o torneio + ordenação por prazo
- 📊 Barra de progresso da equipa

## Stack

HTML/CSS/JS puro + Firebase (Auth + Firestore), SDK compat v10.8.1. Sem build.

## Configuração

1. **Firestore:** aplicar as regras de `firestore.rules` no painel do Firebase (Firestore → Rules → Publish).
2. **Domínio autorizado:** em Firebase → Authentication → Settings → Authorized domains, adicionar o domínio do GitHub Pages (ex.: `<user>.github.io`), senão o login falha.
3. **Countdown:** editar a constante `EVENT_DATE` no topo do `<script>` em `index.html`.
