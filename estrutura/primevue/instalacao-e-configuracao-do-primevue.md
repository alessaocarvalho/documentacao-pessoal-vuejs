# Instalação e configuração do PrimeVue

Neste tópico destacaremos a instalação e configuração inicial da biblioteca de componentes PrimeVue.

## Instalação

Pode ser instalado com o seguinte comando:

```bash
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
  <Button label="Clique aqui" /> <!-- Exibe o Button do PrimeVue no template -->
</template>

<script setup lang="ts">
  import Button from "primevue/button"; // Importa o componente Button do PrimeVue
</script>
```

**Importante**: a importação do componente sempre deve ser feita no `script setup`, do contrário ele não será exibido.

## Instalando PrimeIcons

PrimeIcons é a biblioteca de ícones padrão do PrimeVue, com mais de 250 ícones de código aberto. A biblioteca PrimeIcons é opcional, pois os componentes do PrimeVue podem usar ícones de qualquer biblioteca

### Comando de instalação

```bash
npm install primeicons
```

### Importando para o arquivo `main.css`

O arquivo CSS da biblioteca de ícones precisa ser importado para o nosso arquivo CSS principal da aplicação, que nesse caso é `main.css`. O caminho padrão é:

```text
├── src/
│   ├── assets/
│       ├── main.css
```

Dentro do arquivo, devemos importar a biblioteca da seguinte forma:

```css
@import 'primeicons/primeicons.css';
```

### Aplicando ícone a um componente

Agora vamos aplicar um ícone no botão que criamos anteriormente:

```html
<Button icon="pi pi-check-circle" label="Clique aqui" />
```

## Documentação

Para mais detalhes, consulte a documentação oficial do PrimeVue:

- [Install PrimeVue with Vite](https://primevue.org/vite)
- [Vue Icon Library - PrimeVue](https://primevue.org/icons/)

## [⬅ Voltar](../instalando-e-configurando-bibliotecas.md)
