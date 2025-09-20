# Instalação e configuração do Tailwind CSS + PrimeUI

Neste tópico destacaremos a instalação e configuração inicial do framework de utilitários Tailwind CSS e sua extensão para o PrimeVue, o PrimeUI.

## Tailwind CSS Vite

Como criamos nossa aplicação Vue.js em Vite, devemos instalar o Tailwind CSS com o seguinte comando:

```bash
npm install tailwindcss @tailwindcss/vite
```

### Adicionando na configuração do Vite

Após a instalação, devemos adicionar o Tailwind CSS na configuração do Vite no nosso `vite.config.ts` ou `vite.config.js`:

```ts
import { fileURLToPath, URL } from "node:url";

import { defineConfig } from "vite";
import vue from "@vitejs/plugin-vue";
import vueDevTools from "vite-plugin-vue-devtools";
import tailwindcss from "@tailwindcss/vite"; // Importa o plugin Tailwind CSS

// https://vite.dev/config/
export default defineConfig({
  plugins: [
    vue(),
    vueDevTools(),
    tailwindcss(), // Adiciona o plugin Tailwind CSS na configuração do Vite
  ],
  resolve: {
    alias: {
      "@": fileURLToPath(new URL("./src", import.meta.url)),
    },
  },
});
```

### Importando no CSS principal

Após adicionar ao Vite, fazemos a importação no nosso arquivo CSS principal, que nesse caso é o `main.css`:

```text
├── src/
│   ├── assets/
│       ├── main.css
```

Dentro do arquivo, devemos importar o plugin `tailwindcss` no início do arquivo da seguinte forma:

```css
@import "tailwindcss";
```

### Aplicando estilos Tailwind CSS

Agora vamos aplicar estilos em elementos do nosso template:

```html
<template>
  <div class="flex items-center justify-center border h-100">
    <span class="text-3xl font-bold underline">Teste</span>
  </div>
</template>
```

## PrimeUI

Devemos instalar o PrimeUI com o seguinte comando:

```bash
npm install tailwindcss-primeui
```

### Importação no CSS principal

No mesmo arquivo onde importamos o Tailwind CSS, adicionamos logo após a importação `tailwindcss-primeui` (a ordem importa):

```css
@import "tailwindcss-primeui";
```

### Aplicação nos elementos

Com isso os elementos podem ter classes referenciando estilos e paleta de cores do PrimeVue:

```html
<template>
  <div class="border rounded-border">
    <span class="text-surface-600">Olá</span>
  </div>
</template>
```

## Documentação

Para mais detalhes, consulte a documentação oficial do Tailwind CSS e do PrimeVue:

- [Install Tailwind CSS with Vite - Tailwind CSS](https://tailwindcss.com/docs/installation/using-vite)
- [Tailwind CSS - PrimeVue](https://primevue.org/tailwind/)

## [⬅ Voltar](../instalando-e-configurando-bibliotecas.md)
