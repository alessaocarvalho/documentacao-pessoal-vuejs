# Instalação e configuração do Dotenv

Neste tópico destacaremos a instalação e configuração do módulo Dotenv para injeção de variáveis de ambiente.

## Instalação

Pode ser instalado com o seguinte comando:

```bash
npm install dotenv
```

## Configuração

Após a instalação das dependências do Dotenv, é necessário fazer a configuração no `vite.config.ts` ou `vite.config.js` para que o módulo leia as variáveis de ambiente que forem criadas para aplicação:

```typescript
import { config } from "dotenv"; // Importa o dotenv para carregar variáveis de ambiente

config({ path: `.env.${process.env.ENV_FILE}` }); // Carrega as variáveis de ambiente do arquivo .env no caminho informado
```

## Criação do arquivo .env

Crie um arquivo `.env` na raiz do projeto para definir suas variáveis de ambiente:

```bash
# .env
VITE_API_URL=http://localhost:3000
VITE_APP_TITLE=Minha Aplicação Vue.js
VITE_DEBUG=true
```

**Importante:** No Vite, as variáveis de ambiente devem ter o prefixo `VITE_` para serem expostas no cliente.

## Uso das variáveis no código

Para usar as variáveis de ambiente no seu código Vue.js:

```ts
// Acessando variáveis de ambiente
const apiUrl = import.meta.env.VITE_API_URL;
const appTitle = import.meta.env.VITE_APP_TITLE;
const isDebug = import.meta.env.VITE_DEBUG === "true";
```

## Configuração para diferentes ambientes

Você pode criar diferentes arquivos de ambiente:

- `.env` - padrão para todos os ambientes
- `.env.local` - carregado em todos os ambientes, ignorado pelo git
- `.env.development` - carregado apenas no ambiente de desenvolvimento
- `.env.production` - carregado apenas no ambiente de produção

## Exemplo no .gitignore

Adicione os arquivos de ambiente ao `.gitignore` para não versionar informações sensíveis:

```bash
# Arquivos de ambiente
.env
.env.local
.env.*.local
```

## [⬅ Voltar](../instalando-e-configurando-bibliotecas.md)
