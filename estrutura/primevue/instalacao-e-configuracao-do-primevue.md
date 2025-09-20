# Instalação e configuração do PrimeVue

Neste tópico destacaremos a instalação e configuração inicial da biblioteca de componentes PrimeVue.

## Instalação

Pode ser instalado com o seguinte comando:

```Bash
npm install primevue @primeuix/themes
```

## Configuração

### Importando o PrimeVue na aplicação

Após a instalação das dependências do PrimeVue, é necessário importar as configurações da biblioteca no seu `main.ts` ou `main.js`:

```ts
import "./assets/main.css";

import { createApp } from "vue";
import { createPinia } from "pinia";
import PrimeVue from "primevue/config"; // Importa o PrimeVue

import App from "./App.vue";
import router from "./router";

const app = createApp(App);

app.use(createPinia());
app.use(router);
app.use(PrimeVue); // Inicializa o PrimeVue na aplicação

app.mount("#app");
```

### Configurando o PrimeVue para utilizar um tema

O PrimeVue disponibiliza os _design systems_ Aura, Material, Lara e Nora aplicáveis a seus componentes. Para utilizá-los, devemos configurar a inicialização do PrimeVue no `main.ts` ou `main.js`:

```ts
import "./assets/main.css";

import { createApp } from "vue";
import { createPinia } from "pinia";
import PrimeVue from "primevue/config"; // Importa o PrimeVue
import Aura from "@primeuix/themes/aura"; // Importa o tema Aura do PrimeVue

import App from "./App.vue";
import router from "./router";

const app = createApp(App);

app.use(createPinia());
app.use(router);
app.use(PrimeVue, {
  theme: {
    preset: Aura,
  },
}); // Inicializa o PrimeVue na aplicação com o tema Aura

app.mount("#app");
```

### Importando componentes

Após a configuração, será possível importar os componentes do PrimeVue em nossos templates como no exemplo abaixo:

```html
<template>
  <Button label="Clique aqui" />
  <!-- Exibe o Button do PrimeVue no template -->
</template>

<script setup lang="ts">
  import Button from "primevue/button"; // Importa o componente Button do PrimeVue
</script>
```

**Importante**: a importação do componente sempre deve ser feita no `script setup`, do contrário ele não será exibido.

## Documentação

Para mais detalhes, consulte a documentação oficial do PrimeVue:

- [Install PrimeVue with Vite](https://primevue.org/vite)

## [⬅ Voltar](../instalando-e-configurando-bibliotecas.md)
