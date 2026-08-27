# IberCup Australia · Quadro da Equipa

Quadro de tarefas partilhado pela equipa da **IberCup Australia**, sincronizado em tempo real. Uma única página (`index.html`), pensada para **GitHub Pages**.

## Como está organizado

O quadro tem três vistas, e a escolha fica guardada no browser:

- **👤 Pessoas** (predefinida) — uma coluna por membro da equipa, mais uma coluna **Por atribuir** para o que ainda não tem dono. Cada cabeçalho mostra o avatar, o cargo, o contador `feitas/total` e uma barra de progresso.
- **🗂 Áreas** — uma coluna por área de trabalho.
- **☰ Lista** — tudo numa lista única.

Arrastar um cartão pela pega `⠿` muda o que a vista representa: na vista Pessoas muda o **responsável**, na vista Áreas muda a **área**. Funciona com rato e com dedo.

## Equipa

Os responsáveis são os três emails com login, definidos na constante `MEMBERS` no topo do `<script>` e espelhados em `firestore.rules`:

| Pessoa | Cargo | Email |
|---|---|---|
| Jonas Rodrigues | Program Director | `jonas@ibercup.com.au` |
| Luccas Pereira | Football Director | `luccas@ibercup.com.au` |
| João Leonardo | Operations Coordinator | `admin@ibercup.com.au` |

Para adicionar ou trocar alguém é preciso mexer nos dois sítios: `MEMBERS` em `index.html` e a lista de emails em `firestore.rules`.

## Áreas de trabalho

Definidas na constante `AREAS`: Inscrições & Trials · Logística · Pagamentos · Documentação · Equipamento · Famílias & Comunicação · Marketing & Clubes.

Tarefas criadas antes desta versão têm categorias antigas (`geral`, `viagem`, ...). Na vista Áreas aparecem numa coluna **Por classificar**, que só existe enquanto houver alguma — arrastá-las para uma área real guarda o valor novo e a coluna acaba por desaparecer sozinha.

## Funcionalidades

- 🔐 Login com Google (Firebase Auth), restrito à equipa pelas regras do Firestore
- 🔄 Sincronização em tempo real (Firestore) — todos veem as alterações ao instante
- 👤 Responsável escolhido num dropdown das contas com login + filtro "Minhas"
- 📅 Prazos com urgência (atrasada há N dias / hoje / amanhã) e ordenação por prazo
- ✎ Editar tarefas, comentários, "limpar concluídas"
- 📊 Barra de progresso da equipa e por coluna

## Stack

HTML/CSS/JS puro + Firebase (Auth + Firestore), SDK compat v10.8.1. Sem build.

O visual segue os tokens de marca do site novo (`ibercup/site/src/styles/global.css`): paleta navy/gold/cream, Archivo para títulos e Plus Jakarta Sans para corpo.

## Configuração

1. **Firestore:** aplicar as regras de `firestore.rules` no painel do Firebase (Firestore → Rules → Publish).
2. **Domínio autorizado:** em Firebase → Authentication → Settings → Authorized domains, adicionar o domínio do GitHub Pages (ex.: `<user>.github.io`), senão o login falha.

## Desenvolvimento local

O login por popup do Google não funciona em `file://`. Servir a pasta por HTTP:

```bash
npx serve .
```

`localhost` já é domínio autorizado por defeito no Firebase Auth.
