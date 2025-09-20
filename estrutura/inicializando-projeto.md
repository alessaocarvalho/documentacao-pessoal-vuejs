# Inicializando projeto com Vite

Neste tópico, o destaque estará nos primeiros passos para criar uma aplicação Vue.js e em qual será sua estrutura inicial após a instalação.

## Primeiros passos

Para inicializar a criação de um projeto Vue.js, basta abrir o terminal na pasta desejada e inserir o seguinte comando:

```bash
npm create vue@latest
```

Este comando criará uma aplicação Vue.js na última versão estável disponível. Para criar em uma versão específica, basta substituir `latest` pela versão desejada. Exemplo:

```bash
npm create vue@3.4.0
```

Após a execução do comando, escolhemos o nome do projeto, o nome escolhido também será aplicado ao diretório onde ele será instalado:

```bash
┌  Vue.js - The Progressive JavaScript Framework
│
◆  Project name (target directory):
│  nome-do-projeto
└
```

Escolhido o nome, agora devemos informar as features que deverão ser instaladas junto da aplicação (algumas podem ser instaladas posteriormente mesmo que não marcadas), as que utilizo para meus projetos estão marcadas abaixo:

```bash
◆  Select features to include in your project: (↑/↓ to navigate, space to select, a to toggle all, enter to confirm)
│  ◼ TypeScript
│  ◻ JSX Support
│  ◼ Router (SPA development)
│  ◼ Pinia (state management)
│  ◻ Vitest (unit testing)
│  ◻ End-to-End Testing
│  ◼ ESLint (error prevention)
│  ◼ Prettier (code formatting)
└
```

No próximo passo, devemos informar se queremos utilizar features experimentais para o projeto, não tenho costume de usar essas features, então apenas deixo desmarcado. E então informamos se queremos um projeto em branco ou com a estrutura inicial do Vue.js (componentes Hello World, etc). É interessante termos essa estrutura inicial para entendermos um pouco de como os componentes funcionam, mas se já estiver mais experiente no framework, pode criar em branco:

```bash
◇  Select experimental features to include in your project: (↑/↓ to navigate, space to select, a to toggle all, enter to
confirm)
│  none
│
◆  Skip all example code and start with a blank Vue project?
│  ○ Yes / ● No
└
```

Após este passo a instalação da aplicação será iniciada no diretório informado anteriormente:

```bash
Scaffolding project in C:\Projects\nome-do-projeto...
│
└  Done. Now run:

   cd nome-do-projeto
   npm install
   npm run format
   npm run dev
```

Feito isso, primeiro navegamos até o diretório:

```bash
cd nome-do-projeto
```

Instalamos as dependências:

```bash
npm install
```

Se você marcou a feature `Prettier` anteriormente, pode rodar um comando de formatação de código para torná-lo mais organizado e legível (opcional):

```bash
npm run format
```

E por fim, rodamos o comando para subir o servidor local da aplicação:

```bash
npm run dev
```

Após a execução do comando, o servidor estará acessível por uma URL parecida com a exibida abaixo, e ao acessarmos, podemos visualizar a estrutura inicial da aplicação:

```bash
> nome-do-projeto@0.0.0 dev
> vite


  VITE v7.1.6  ready in 756 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  Vue DevTools: Open http://localhost:5173/__devtools__/ as a separate window
  ➜  Vue DevTools: Press Alt(⌥)+Shift(⇧)+D in App to toggle the Vue DevTools
  ➜  press h + enter to show help
```

### Importante

- Certifique-se de ter uma versão atualizada do Node.js.

## Estrutura inicial

Após a instalação da aplicação, a estrutura inicial deve ser algo parecida com esta, destacarei alguns diretórios importantes:

```text
nome-do-projeto/
├── public/          # Arquivos estáticos (favicon, index.html, etc.)
├── src/
│   ├── assets/      # Imagens, ícones e estilos
│   ├── components/  # Componentes Vue reutilizáveis
│   ├── router/      # Configurações de rotas com Vue Router
│   ├── stores/      # Configurações de gerenciamento de estado com Pinia
│   ├── views/       # Páginas da aplicação
│   ├── App.vue      # Componente raiz
│   └── main.ts      # Ponto de entrada da aplicação (TypeScript)
├── index.html       # HTML principal
├── package.json     # Dependências e scripts
└── vite.config.ts   # Configurações do Vite

```

## Documentação

Para mais detalhes, consulte a documentação oficial do Vue.js:

- [Introdução Rápida | Vue.js](https://pt.vuejs.org/guide/quick-start)

## [⬅ Voltar](../README.md)
