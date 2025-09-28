# DatePicker com datas desabilitadas

Neste tópico, o destaque será na configuração avançada do componente DatePicker do PrimeVue, incluindo como desabilitar datas específicas, dias da semana e aplicar estilos personalizados através de slots.

## Configuração avançada com múltiplas restrições

O DatePicker do PrimeVue oferece diversas propriedades para controlar quais datas podem ser selecionadas. O exemplo abaixo demonstra uma configuração completa combinando datas específicas desabilitadas, dias da semana bloqueados e estilização personalizada.

```html
<template>
  <!--
    Componente DatePicker avançado com múltiplas restrições de data

    Propriedades configuradas:
    :disabledDates - Array de datas específicas desabilitadas
    :disabledDays  - Array de dias da semana desabilitados [0=Domingo, 6=Sábado]
    :minDate       - Data mínima selecionável (hoje)
    showIcon       - Exibe ícone do calendário
  -->
  <DatePicker
    :disabledDates="disabledDates"
    :disabledDays="[0, 6]"
    :minDate="new Date()"
    showIcon
  >
    <!--
      Slot personalizado para renderização das datas no calendário
      Aplica estilo especial (fundo cinza) para datas desabilitadas
    -->
    <template #date="slotProps">
      <strong
        v-if="
          disabledDates.some(
            (date) =>
              date.getDate() === slotProps.date.day &&
              date.getMonth() === slotProps.date.month &&
              date.getFullYear() === slotProps.date.year,
          )
        "
        class="text-white bg-gray-500 p-2 rounded"
        >{{ slotProps.date.day }}</strong
      >
      <template v-else>{{ slotProps.date.day }}</template>
    </template>
  </DatePicker>
</template>

<script setup lang="ts">
  // Importa a função ref do Vue para criar referências reativas
  import { ref } from "vue";

  /**
   * Array de datas específicas desabilitadas no DatePicker
   *
   * Contém as datas que não poderão ser selecionadas pelo usuário:
   * - 01/10/2025 às 10:00 (1º de outubro)
   * - 02/10/2025 às 10:00 (2 de outubro)
   * - 06/10/2025 às 10:00 (6 de outubro)
   * - 15/10/2025 às 10:00 (15 de outubro)
   * - 20/10/2025 às 10:00 (20 de outubro)
   *
   * Estas datas aparecerão com fundo cinza no calendário
   *
   * @type {Ref<Date[]>} Array reativo de objetos Date
   */
  const disabledDates = ref([
    new Date("2025-10-01T10:00:00"), // 1º de outubro de 2025
    new Date("2025-10-02T10:00:00"), // 2 de outubro de 2025
    new Date("2025-10-06T10:00:00"), // 6 de outubro de 2025
    new Date("2025-10-15T10:00:00"), // 15 de outubro de 2025
    new Date("2025-10-20T10:00:00"), // 20 de outubro de 2025
  ]);
</script>
```

## Entendendo o slot personalizado

### Como funciona o slot `#date`

O exemplo principal demonstra o uso do slot `#date` para aplicar estilos personalizados às datas desabilitadas. O slot recebe um objeto `slotProps` contendo informações sobre cada data do calendário:

```javascript
// Estrutura do slotProps
{
  date: {
    day: number,    // Dia do mês (1-31)
    month: number,  // Mês (0-11, onde 0=Janeiro)
    year: number    // Ano completo
  }
}
```

A lógica do template verifica se a data atual do calendário está presente no array `disabledDates` comparando dia, mês e ano. Se encontrada, aplica as classes Tailwind `text-white bg-red-500 p-2 rounded` para destacá-la com fundo cinza e bordas arredondadas.

### Tipos de restrições utilizadas

O exemplo principal demonstra a combinação de três tipos de restrições:

1. **`disabledDates`** - Array de datas específicas que não podem ser selecionadas
2. **`disabledDays`** - Array com dias da semana bloqueados (`[0, 6]` = fins de semana)
3. **`minDate`** - Data mínima selecionável (no exemplo, a data atual)
4. **`showIcon`** - Exibe ícone do calendário no campo de entrada

## Exemplos de configurações específicas

### Desabilitando apenas fins de semana

```html
<template>
  <DatePicker :disabledDays="[0, 6]" placeholder="Selecione uma data" />
</template>
```

### Limitando a um intervalo específico

```html
<template>
  <DatePicker
    :minDate="minDate"
    :maxDate="maxDate"
    placeholder="Selecione uma data no intervalo"
  />
</template>

<script setup lang="ts">
  import { ref } from "vue";

  const minDate = ref(new Date("2025-10-01")); // Data mínima
  const maxDate = ref(new Date("2025-12-31")); // Data máxima
</script>
```

### Destacando feriados com estilo diferenciado

```html
<template>
  <DatePicker :disabledDates="holidays">
    <template #date="slotProps">
      <div
        v-if="isHoliday(slotProps.date)"
        class="bg-yellow-200 text-red-600 font-bold rounded p-1"
      >
        {{ slotProps.date.day }}
      </div>
      <template v-else>{{ slotProps.date.day }}</template>
    </template>
  </DatePicker>
</template>

<script setup lang="ts">
  import { ref } from "vue";

  const holidays = ref([
    new Date("2025-12-25"), // Natal
    new Date("2025-01-01"), // Ano Novo
  ]);

  const isHoliday = (dateObj: { day: number; month: number; year: number }) => {
    return holidays.value.some(
      (holiday) =>
        holiday.getDate() === dateObj.day &&
        holiday.getMonth() === dateObj.month &&
        holiday.getFullYear() === dateObj.year
    );
  };
</script>
```

## Propriedades e slots úteis

### Propriedades

| Propriedade     | Tipo       | Descrição                                                               |
| --------------- | ---------- | ----------------------------------------------------------------------- |
| `disabledDates` | `Date[]`   | Array de datas específicas a serem desabilitadas                        |
| `disabledDays`  | `number[]` | Array com os dias da semana a serem desabilitados (0=domingo, 6=sábado) |
| `minDate`       | `Date`     | Data mínima selecionável                                                |
| `maxDate`       | `Date`     | Data máxima selecionável                                                |
| `showIcon`      | `boolean`  | Exibe ícone do calendário no campo de entrada                           |

### Slots disponíveis

| Slot      | Descrição                                             | Props                            |
| --------- | ----------------------------------------------------- | -------------------------------- |
| `#date`   | Personaliza a renderização de cada data no calendário | `{ date: { day, month, year } }` |
| `#header` | Personaliza o cabeçalho do calendário                 | `{ month, year }`                |
| `#footer` | Personaliza o rodapé do calendário                    | -                                |

## Documentação

Para mais detalhes, consulte a documentação oficial do PrimeVue:

- [DatePicker - PrimeVue](https://primevue.org/datepicker/)

## [⬅ Voltar](../README.md)
