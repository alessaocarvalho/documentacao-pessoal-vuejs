# DatePicker com datas desabilitadas

Neste tópico demonstro como configurar um componente DatePicker do PrimeVue para desabilitar datas específicas, impedindo que o usuário selecione determinados dias no calendário.

## Configuração básica

O DatePicker do PrimeVue oferece a propriedade `disabledDates` que aceita um array de objetos `Date` representando as datas que devem ser desabilitadas na interface do calendário.

```html
<template>
  <!--
    Componente DatePicker com datas desabilitadas
    :disabledDates - propriedade que recebe um array de datas que não podem ser selecionadas
  -->
  <DatePicker :disabledDates="disabledDates" />
</template>

<script setup lang="ts">
  // Importa a função ref do Vue para criar referências reativas
  import { ref } from "vue";

  /**
   * Array de datas desabilitadas no DatePicker
   *
   * Contém as datas que não poderão ser selecionadas pelo usuário:
   * - 01/10/2025 às 10:00
   * - 02/10/2025 às 10:00
   *
   * @type {Ref<Date[]>} Array reativo de objetos Date
   */
  const disabledDates = ref([
    new Date("2025-10-01T10:00:00"), // 1º de outubro de 2025
    new Date("2025-10-02T10:00:00"), // 2º de outubro de 2025
  ]);
</script>
```

## Casos de uso

### Desabilitando fins de semana

```html
<template>
  <DatePicker :disabledDays="[0, 6]" placeholder="Selecione uma data" />
</template>
```

### Desabilitando datas passadas

```html
<template>
  <DatePicker :minDate="new Date()" placeholder="Selecione uma data futura" />
</template>

<script setup lang="ts">
  // A propriedade minDate impede a seleção de datas anteriores à data atual
</script>
```

### Combinando datas específicas com intervalos

```html
<template>
  <DatePicker 
    :disabledDates="disabledDates" 
    :minDate="minDate"
    :maxDate="maxDate"
    placeholder="Selecione uma data disponível"
  />
</template>

<script setup lang="ts">
  import { ref } from "vue";

  const minDate = ref(new Date()); // Data mínima é hoje
  const maxDate = ref(new Date("2025-12-31")); // Data máxima é fim do ano

  const disabledDates = ref([
    new Date("2025-10-01"),
    new Date("2025-10-02"),
    new Date("2025-11-15"), // Feriado específico
  ]);
</script>
```

## Propriedades úteis

| Propriedade | Tipo | Descrição |
|-------------|------|-----------|
| `disabledDates` | `Date[]` | Array de datas específicas a serem desabilitadas |
| `disabledDays` | `number[]` | Array com os dias da semana a serem desabilitados (0=domingo, 6=sábado) |
| `minDate` | `Date` | Data mínima selecionável |
| `maxDate` | `Date` | Data máxima selecionável |

## Documentação

Para mais detalhes, consulte a documentação oficial do PrimeVue:

- [DatePicker - PrimeVue](https://primevue.org/datepicker/)

## [⬅ Voltar](../README.md)
