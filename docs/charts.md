# 📊 Documentação dos Gráficos

Este documento descreve todos os tipos de gráficos disponíveis no projeto **Quasar ApexCharts V2**, suas características, casos de uso e exemplos de implementação.

## 📋 Índice

- [Visão Geral](#-visão-geral)
- [Tipos de Gráficos](#-tipos-de-gráficos)
- [Padrões de Implementação](#-padrões-de-implementação)
- [Customização](#-customização)
- [Exemplos Práticos](#-exemplos-práticos)
- [Boas Práticas](#-boas-práticas)

## 🎯 Visão Geral

O projeto implementa **12 tipos diferentes de gráficos** utilizando a biblioteca **ApexCharts**, cada um otimizado para diferentes cenários de visualização de dados. Todos os componentes seguem padrões consistentes e integram-se perfeitamente com o tema do Quasar Framework.

### Características Comuns

- 🎨 **Integração com Tema**: Cores do Quasar aplicadas automaticamente
- 📱 **Responsividade**: Adaptação automática a diferentes tamanhos de tela
- ⚡ **Performance**: Carregamento assíncrono e otimizações
- 🔧 **Customizável**: Fácil personalização de opções e estilos
- 🌐 **Internacionalização**: Suporte a múltiplos idiomas

## 📈 Tipos de Gráficos

### 1. 📊 Gráficos de Área (Area Charts)

**Componente**: `ApexArea.vue`
**Tipo ApexCharts**: `area`
**Página**: `/area-charts`

#### Características
- Preenchimento colorido abaixo da linha
- Ideal para mostrar tendências ao longo do tempo
- Suporte a múltiplas séries
- Marcadores interativos

#### Casos de Uso
- Vendas mensais
- Crescimento de usuários
- Métricas de performance
- Análise temporal

#### Exemplo de Implementação
```vue
<template>
  <apexchart height="300" type="area" :options="options" :series="series" />
</template>

<script>
import { defineComponent } from 'vue'
import { getCssVar } from 'quasar'

export default defineComponent({
  name: 'ApexArea',
  data() {
    return {
      options: {
        title: { text: 'ApexArea', align: 'left' },
        colors: [getCssVar('primary'), getCssVar('secondary')],
        markers: { size: 4, hover: { sizeOffset: 6 } },
        xaxis: { categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998] }
      },
      series: [{
        name: 'series1',
        data: [31, 40, 28, 51, 42, 109, 100]
      }]
    }
  }
})
</script>
```

### 2. 📊 Gráficos de Barras (Bar Charts)

**Componente**: `ApexBar.vue`
**Tipo ApexCharts**: `bar`
**Página**: `/bar-charts`

#### Características
- Barras horizontais
- Formato arredondado
- Largura customizável
- Animações suaves

#### Casos de Uso
- Comparação de categorias
- Rankings
- Métricas de performance
- Análise comparativa

#### Configurações Especiais
```javascript
plotOptions: {
  bar: {
    horizontal: true,
    columnWidth: '55%',
    endingShape: 'rounded'
  }
}
```

### 3. 🫧 Gráficos de Bolhas (Bubble Charts)

**Componente**: `ApexBubble.vue`
**Tipo ApexCharts**: `bubble`
**Página**: `/bubble-charts`

#### Características
- Visualização 3D com bolhas
- Tamanho da bolha representa valor
- Cores diferentes por categoria
- Interação hover avançada

#### Casos de Uso
- Análise de correlação
- Dados com 3 dimensões
- Análise de mercado
- Estudos estatísticos

### 4. 🕯️ Gráficos de Velas (Candlestick Charts)

**Componente**: `ApexCandlestick.vue`
**Tipo ApexCharts**: `candlestick`
**Página**: `/candlestick-charts`

#### Características
- Representação OHLC (Open, High, Low, Close)
- Cores para alta/baixa
- Ideal para dados financeiros
- Animações realistas

#### Casos de Uso
- Análise de ações
- Criptomoedas
- Mercado de commodities
- Trading técnico

### 5. 📊 Gráficos de Colunas (Column Charts)

**Componente**: `ApexColumn.vue`
**Tipo ApexCharts**: `column`
**Página**: `/column-charts`

#### Características
- Barras verticais
- Agrupamento de séries
- Empilhamento opcional
- Animações de entrada

#### Casos de Uso
- Comparação de valores
- Análise temporal
- Métricas por categoria
- Relatórios executivos

### 6. 🍩 Gráficos de Rosca (Donut Charts)

**Componente**: `ApexDonut.vue`
**Tipo ApexCharts**: `donut`
**Página**: `/donut-charts`

#### Características
- Centro vazio
- Legenda integrada
- Animações de rotação
- Interação por fatia

#### Casos de Uso
- Distribuição percentual
- Análise de market share
- Métricas de uso
- Relatórios de status

### 7. 🔥 Mapas de Calor (Heatmap Charts)

**Componente**: `ApexHeatmap.vue`
**Tipo ApexCharts**: `heatmap`
**Página**: `/heatmap-charts`

#### Características
- Grade de cores
- Intensidade por cor
- Tooltips informativos
- Dados bidimensionais

#### Casos de Uso
- Análise de correlação
- Dados de temperatura
- Atividade de usuários
- Métricas de performance

#### Exemplo de Dados
```javascript
series: [{
  name: 'Metric1',
  data: generateData(18, { min: 0, max: 90 })
}]
```

### 8. 📈 Gráficos de Linha (Line Charts)

**Componente**: `ApexLine.vue`
**Tipo ApexCharts**: `line`
**Página**: `/line-charts`

#### Características
- Linhas conectadas
- Marcadores opcionais
- Múltiplas séries
- Animações suaves

#### Casos de Uso
- Tendências temporais
- Análise de performance
- Métricas contínuas
- Relatórios de progresso

### 9. 🥧 Gráficos de Pizza (Pie Charts)

**Componente**: `PopulationByContinent.vue`
**Tipo ApexCharts**: `pie`
**Página**: `/pie-charts`

#### Características
- Formato circular
- Fatias proporcionais
- Cores distintas
- Legenda automática

#### Casos de Uso
- Distribuição de dados
- Análise de composição
- Relatórios de participação
- Métricas de mercado

#### Exemplo com Dados Reais
```javascript
series: [
  4694576167, // Asia
  1393676444, // Africa
  745173774,  // Europe
  595783465,  // North America
  434254119,  // South America
  44491724    // Oceania
]
```

### 10. 🎯 Gráficos de Área Polar (Polar Area Charts)

**Componente**: `ApexPolarArea.vue`
**Tipo ApexCharts**: `polarArea`
**Página**: `/polar-area-charts`

#### Características
- Formato circular
- Áreas radiais
- Cores graduais
- Animações rotativas

#### Casos de Uso
- Análise de direção
- Dados cíclicos
- Métricas radiais
- Visualizações especiais

### 11. ⚡ Gráficos de Barras Radiais (Radial Bar Charts)

**Componente**: `ApexRadialBar.vue`
**Tipo ApexCharts**: `radialBar`
**Página**: `/radial-bar-charts`

#### Características
- Formato circular
- Barras radiais
- Gradientes
- Valores centrais

#### Casos de Uso
- KPIs principais
- Métricas de progresso
- Dashboards executivos
- Indicadores de status

#### Configuração Avançada
```javascript
plotOptions: {
  radialBar: {
    startAngle: -90,
    endAngle: 90,
    track: {
      background: '#e7e7e7',
      strokeWidth: '97%',
      dropShadow: { enabled: true }
    },
    dataLabels: {
      value: { offsetY: -2, fontSize: '30px' }
    }
  }
}
```

### 12. 📊 Gráficos de Dispersão (Scatter Charts)

**Componente**: `ApexScatter.vue`
**Tipo ApexCharts**: `scatter`
**Página**: `/scatter-charts`

#### Características
- Pontos de dados
- Correlação visual
- Múltiplas séries
- Interação hover

#### Casos de Uso
- Análise de correlação
- Dados experimentais
- Estudos estatísticos
- Análise de dispersão

## 🏗️ Padrões de Implementação

### Estrutura Padrão de Componente

```vue
<template>
  <apexchart
    height="300"
    :type="chartType"
    :options="options"
    :series="series"
  />
</template>

<script>
import { defineComponent } from 'vue'
import { getCssVar } from 'quasar'

export default defineComponent({
  name: 'ApexChartName',
  data() {
    return {
      options: {
        // Configurações do gráfico
      },
      series: [
        // Dados do gráfico
      ]
    }
  }
})
</script>
```

### Padrões de Nomenclatura

- **Componentes**: `Apex[NomeDoTipo].vue`
- **Páginas**: `[Tipo]Charts.vue`
- **Rotas**: `/[tipo]-charts`
- **IDs**: `apex-[tipo]`

### Integração com Tema Quasar

```javascript
// Cores do tema
colors: [
  getCssVar('primary'),
  getCssVar('secondary'),
  getCssVar('accent'),
  getCssVar('positive'),
  getCssVar('negative'),
  getCssVar('info'),
  getCssVar('warning')
]
```

## 🎨 Customização

### Opções Comuns

#### Título
```javascript
title: {
  text: 'Título do Gráfico',
  align: 'left',
  offsetY: 20
}
```

#### Cores
```javascript
colors: [
  getCssVar('primary'),
  getCssVar('secondary')
]
```

#### Marcadores
```javascript
markers: {
  size: 4,
  hover: {
    sizeOffset: 6
  }
}
```

#### Eixo X
```javascript
xaxis: {
  categories: ['Jan', 'Fev', 'Mar', 'Abr', 'Mai', 'Jun']
}
```

#### Responsividade
```javascript
responsive: [{
  breakpoint: 480,
  options: {
    chart: { width: 200 },
    legend: { position: 'bottom' }
  }
}]
```

### Configurações Avançadas

#### Animações
```javascript
chart: {
  animations: {
    enabled: true,
    easing: 'easeinout',
    speed: 800
  }
}
```

#### Tooltips
```javascript
tooltip: {
  enabled: true,
  shared: true,
  followCursor: true
}
```

#### Legenda
```javascript
legend: {
  position: 'bottom',
  horizontalAlign: 'center',
  floating: false,
  offsetY: 0,
  offsetX: 0
}
```

## 📱 Responsividade

### Breakpoints do Quasar

```vue
<template>
  <div class="row q-col-gutter-sm">
    <div class="col-md-6 col-xs-12">
      <q-card>
        <apex-chart />
      </q-card>
    </div>
  </div>
</template>
```

### Configuração Responsiva

```javascript
responsive: [{
  breakpoint: 1024,
  options: {
    chart: { width: 400 }
  }
}, {
  breakpoint: 600,
  options: {
    chart: { width: 300 },
    legend: { position: 'bottom' }
  }
}]
```

## 🌐 Internacionalização

### Títulos Traduzidos

```javascript
// Em pt-BR
title: {
  text: this.$t('charts.area.title')
}

// Em en-US
title: {
  text: this.$t('charts.area.title')
}
```

### Configuração de i18n

```javascript
// src/i18n/pt-BR/index.js
charts: {
  area: {
    title: 'Gráfico de Área'
  }
}
```

## 🧪 Testes

### Testes Manuais

1. **Renderização**: Verificar se o gráfico aparece
2. **Interação**: Testar hover e cliques
3. **Responsividade**: Testar em diferentes tamanhos
4. **Performance**: Verificar tempo de carregamento

### Testes Automatizados

```javascript
// Exemplo de teste
describe('ApexArea', () => {
  it('renders chart correctly', () => {
    const wrapper = mount(ApexArea)
    expect(wrapper.find('apexchart').exists()).toBe(true)
  })
})
```

## 📊 Exemplos Práticos

### Dashboard Executivo

```vue
<template>
  <div class="row q-col-gutter-md">
    <div class="col-md-6">
      <q-card>
        <apex-radial-bar />
      </q-card>
    </div>
    <div class="col-md-6">
      <q-card>
        <apex-line />
      </q-card>
    </div>
  </div>
</template>
```

### Relatório de Vendas

```vue
<template>
  <div class="row q-col-gutter-md">
    <div class="col-md-8">
      <q-card>
        <apex-column />
      </q-card>
    </div>
    <div class="col-md-4">
      <q-card>
        <apex-pie />
      </q-card>
    </div>
  </div>
</template>
```

## ✅ Boas Práticas

### 1. Performance

- Use `defineAsyncComponent` para carregamento assíncrono
- Evite re-renderizações desnecessárias
- Otimize dados grandes com paginação

### 2. Acessibilidade

- Adicione `aria-label` nos gráficos
- Forneça alternativas textuais
- Use cores com bom contraste

### 3. UX

- Adicione loading states
- Implemente error handling
- Forneça feedback visual

### 4. Manutenibilidade

- Mantenha componentes pequenos
- Use props para configuração
- Documente APIs públicas

### 5. Dados

- Valide dados antes de renderizar
- Trate casos de dados vazios
- Use formatação consistente

## 🔧 Troubleshooting

### Problemas Comuns

#### Gráfico não renderiza
- Verifique se os dados estão no formato correto
- Confirme se o tipo do gráfico está correto
- Verifique erros no console

#### Cores não aplicadas
- Confirme se `getCssVar` está sendo usado
- Verifique se o tema do Quasar está carregado
- Teste com cores hardcoded

#### Performance lenta
- Use `defineAsyncComponent`
- Implemente paginação para dados grandes
- Otimize configurações do ApexCharts

### Debug

```javascript
// Adicione logs para debug
console.log('Chart options:', this.options)
console.log('Chart series:', this.series)
```

---

Esta documentação cobre todos os aspectos dos gráficos implementados no projeto. Para mais informações específicas, consulte a [documentação oficial do ApexCharts](https://apexcharts.com/docs/).
