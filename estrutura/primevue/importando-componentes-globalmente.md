# Importando os componentes do PrimeVue globalmente

Neste tópico, o destaque será em como criar um utilitário para importar os componentes do PrimeVue globalmente, evitando assim a necessidade de importá-los individualmente em cada arquivo e melhorando a produtividade no desenvolvimento.

## Criando o utilitário

Podemos criar um arquivo `primeVueComponents.ts` ou `primeVueComponents.js` e colocá-lo em nossa pasta de utilitários, o arquivo deve ser estruturado da seguinte forma:

```ts
import Button from "primevue/button"; // Importa o componente Button do PrimeVue

export default [{ name: "Button", component: Button }]; // Exporta um array com o nome e o componente Button

// Você pode adicionar mais componentes do PrimeVue a este arquivo conforme necessário
```

## Registrando os componentes globalmente

Para registrar globalmente todos os componentes importados no arquivo, fazemos a seguinte configuração no nosso `main.ts` ou `main.js`:

```ts
import primeVueComponents from "./utils/primeVueComponents"; // Importa os componentes do PrimeVue do arquivo primeVueComponents.ts

primeVueComponents.forEach(({ name, component }) => {
  app.component(name, component); // Registra cada componente do PrimeVue globalmente na aplicação
});
```

Agora todos os componentes registrados no nosso utilitário podem ser criados em nossos templates sem necessidade de nova importação.

## [⬅ Voltar](../instalando-e-configurando-bibliotecas.md)
