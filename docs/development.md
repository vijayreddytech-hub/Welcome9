# 🛠️ Guia de Desenvolvimento

Este documento descreve os padrões, convenções e práticas de desenvolvimento utilizados no projeto **Quasar ApexCharts V2**.

## 📋 Índice

- [Configuração do Ambiente](#-configuração-do-ambiente)
- [Padrões de Código](#-padrões-de-código)
- [Estrutura de Arquivos](#-estrutura-de-arquivos)
- [Convenções de Nomenclatura](#-convenções-de-nomenclatura)
- [Padrões de Componentes](#-padrões-de-componentes)
- [Gerenciamento de Estado](#-gerenciamento-de-estado)
- [Roteamento](#-roteamento)
- [Internacionalização](#-internacionalização)
- [Estilos e CSS](#-estilos-e-css)
- [Testes](#-testes)
- [Performance](#-performance)
- [Debugging](#-debugging)

## ⚙️ Configuração do Ambiente

### Pré-requisitos

- **Node.js**: >= 12.22.1
- **npm**: >= 6.13.4 ou **yarn**: >= 1.21.1
- **Git**: >= 2.20.0
- **VS Code** (recomendado) com extensões:
  - Vetur ou Volar
  - ESLint
  - Prettier
  - Quasar Framework

### Configuração Inicial

```bash
# Clone o repositório
git clone https://github.com/patrickmonteiro/quasar-apexcharts.git
cd quasar-apexcharts

# Instale dependências
yarn install

# Inicie o servidor de desenvolvimento
quasar dev
```

### Configuração do VS Code

Crie `.vscode/settings.json`:

```json
{
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "eslint.validate": ["javascript", "vue"],
  "vetur.format.defaultFormatter.html": "prettier",
  "vetur.format.defaultFormatter.js": "prettier"
}
```

## 📝 Padrões de Código

### JavaScript/Vue

#### ESLint Configuration
O projeto usa ESLint com as seguintes regras:
- `eslint-config-standard`
- `eslint-plugin-vue`
- `eslint-plugin-import`

#### Prettier Configuration
```json
{
  "semi": false,
  "singleQuote": true,
  "trailingComma": "none",
  "printWidth": 80,
  "tabWidth": 2
}
```

### Vue 3 Composition API

#### Preferir Composition API
```vue
<script>
import { defineComponent, ref, computed, onMounted } from 'vue'

export default defineComponent({
  name: 'ComponentName',
  setup() {
    const data = ref([])
    const computedValue = computed(() => data.value.length)

    onMounted(() => {
      // Lógica de inicialização
    })

    return {
      data,
      computedValue
    }
  }
})
</script>
```

#### Composables
```javascript
// src/composables/useChartData.js
import { ref, computed } from 'vue'

export function useChartData() {
  const data = ref([])
  const isLoading = ref(false)

  const chartOptions = computed(() => ({
    // Configurações do gráfico
  }))

  const loadData = async () => {
    isLoading.value = true
    try {
      // Carregar dados
    } finally {
      isLoading.value = false
    }
  }

  return {
    data,
    isLoading,
    chartOptions,
    loadData
  }
}
```

### Estrutura de Arquivos

#### Organização de Componentes
```
src/components/
├── charts/                 # Componentes específicos de gráficos
│   ├── area/
│   │   ├── ApexArea.vue
│   │   └── README.md
│   └── bar/
│       ├── ApexBar.vue
│       └── README.md
├── common/                 # Componentes genéricos
│   ├── Card.vue
│   ├── CardSkeleton.vue
│   └── ExternalLink.vue
└── layout/                 # Componentes de layout
    ├── Navbar.vue
    └── RouterLink.vue
```

#### Organização de Páginas
```
src/pages/
├── chartTypes/             # Páginas por tipo de gráfico
│   ├── AllCharts.vue
│   ├── AreaCharts.vue
│   └── BarCharts.vue
├── Index.vue               # Página inicial
└── Error404.vue            # Página de erro
```

## 🏷️ Convenções de Nomenclatura

### Arquivos e Diretórios

```bash
# Componentes Vue
ApexArea.vue              # PascalCase
apex-area.vue             # kebab-case (alternativo)

# Diretórios
chartTypes/               # camelCase
area-charts/              # kebab-case (alternativo)

# Páginas
AllCharts.vue             # PascalCase
AreaCharts.vue            # PascalCase
```

### Variáveis e Funções

```javascript
// ✅ Bom
const chartData = ref([])
const isLoading = ref(false)
const handleChartClick = () => {}
const generateChartData = () => {}

// ❌ Evitar
const chart_data = ref([])
const is_loading = ref(false)
const handle_chart_click = () => {}
const generate_chart_data = () => {}
```

### Props e Events

```javascript
// Props
props: {
  chartData: {
    type: Array,
    required: true
  },
  isLoading: {
    type: Boolean,
    default: false
  }
}

// Events
const emit = defineEmits(['chart-click', 'data-updated'])
```

### Constantes

```javascript
// Constantes em UPPER_CASE
const CHART_TYPES = {
  AREA: 'area',
  BAR: 'bar',
  LINE: 'line'
}

const API_ENDPOINTS = {
  CHARTS: '/api/charts',
  DATA: '/api/data'
}
```

## 🧩 Padrões de Componentes

### Estrutura Padrão

```vue
<template>
  <!-- Template primeiro -->
  <div class="chart-container">
    <apexchart
      :height="height"
      :type="type"
      :options="chartOptions"
      :series="chartSeries"
    />
  </div>
</template>

<script>
import { defineComponent, computed } from 'vue'
import { getCssVar } from 'quasar'

export default defineComponent({
  name: 'ApexChartName',

  props: {
    data: {
      type: Array,
      required: true
    },
    height: {
      type: [String, Number],
      default: 300
    }
  },

  emits: ['chart-click', 'data-updated'],

  setup(props, { emit }) {
    const chartOptions = computed(() => ({
      title: {
        text: 'Chart Title',
        align: 'left'
      },
      colors: [
        getCssVar('primary'),
        getCssVar('secondary')
      ]
    }))

    const chartSeries = computed(() => props.data)

    const handleChartClick = (event) => {
      emit('chart-click', event)
    }

    return {
      chartOptions,
      chartSeries,
      handleChartClick
    }
  }
})
</script>

<style scoped>
.chart-container {
  width: 100%;
  height: 100%;
}
</style>
```

### Componentes de Gráfico

#### Estrutura Padrão
```vue
<template>
  <apexchart
    :height="height"
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

#### Integração com Tema
```javascript
// Sempre usar getCssVar para cores
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

### Componentes de Página

```vue
<template>
  <q-page padding>
    <div class="row q-col-gutter-sm">
      <div class="col-md-6 col-xs-12">
        <q-card>
          <apex-chart />
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, defineAsyncComponent } from 'vue'

const ApexChart = defineAsyncComponent(() =>
  import('src/components/charts/type/ApexChart.vue')
)

export default defineComponent({
  name: 'ChartTypePage',

  components: {
    ApexChart
  }
})
</script>
```

## 🔄 Gerenciamento de Estado

### Estado Local

```javascript
// Para estado simples
const data = ref([])
const isLoading = ref(false)

// Para estado complexo
const state = reactive({
  data: [],
  isLoading: false,
  error: null
})
```

### Composables para Estado

```javascript
// src/composables/useChartState.js
import { ref, computed } from 'vue'

export function useChartState() {
  const data = ref([])
  const isLoading = ref(false)
  const error = ref(null)

  const hasData = computed(() => data.value.length > 0)
  const isEmpty = computed(() => !isLoading.value && data.value.length === 0)

  const setData = (newData) => {
    data.value = newData
    error.value = null
  }

  const setError = (err) => {
    error.value = err
    data.value = []
  }

  const setLoading = (loading) => {
    isLoading.value = loading
  }

  return {
    data,
    isLoading,
    error,
    hasData,
    isEmpty,
    setData,
    setError,
    setLoading
  }
}
```

## 🛣️ Roteamento

### Estrutura de Rotas

```javascript
// src/router/routes.js
const routes = [
  {
    path: '/',
    component: () => import('layouts/MainLayout.vue'),
    children: [
      {
        path: '',
        name: 'home',
        component: () => import('pages/Index.vue')
      },
      {
        path: '/all-charts',
        name: 'allCharts',
        component: () => import('pages/chartTypes/AllCharts.vue')
      }
    ]
  }
]
```

### Lazy Loading

```javascript
// Sempre usar lazy loading para rotas
const routes = [
  {
    path: '/chart-type',
    component: () => import('pages/chartTypes/ChartType.vue')
  }
]
```

### Navegação Programática

```javascript
// Em componentes
import { useRouter } from 'vue-router'

const router = useRouter()

const navigateToChart = (chartType) => {
  router.push({ name: `${chartType}Charts` })
}
```

## 🌐 Internacionalização

### Estrutura de Traduções

```javascript
// src/i18n/pt-BR/index.js
export default {
  charts: {
    area: {
      title: 'Gráfico de Área',
      description: 'Visualização de dados em formato de área'
    },
    bar: {
      title: 'Gráfico de Barras',
      description: 'Visualização de dados em formato de barras'
    }
  },
  common: {
    loading: 'Carregando...',
    error: 'Erro ao carregar dados',
    noData: 'Nenhum dado disponível'
  }
}
```

### Uso em Componentes

```vue
<template>
  <div>
    <h1>{{ $t('charts.area.title') }}</h1>
    <p>{{ $t('charts.area.description') }}</p>
  </div>
</template>

<script>
import { useI18n } from 'vue-i18n'

export default defineComponent({
  setup() {
    const { t } = useI18n()

    const title = computed(() => t('charts.area.title'))

    return {
      title
    }
  }
})
</script>
```

## 🎨 Estilos e CSS

### Quasar CSS Classes

```vue
<template>
  <div class="row q-col-gutter-md">
    <div class="col-md-6 col-xs-12">
      <q-card class="q-pa-md">
        <q-card-section>
          <div class="text-h6">Título</div>
        </q-card-section>
      </q-card>
    </div>
  </div>
</template>
```

### CSS Custom Properties

```css
/* src/css/app.css */
:root {
  --chart-primary: #{$primary};
  --chart-secondary: #{$secondary};
  --chart-accent: #{$accent};
}

.chart-container {
  --chart-height: 300px;
  --chart-padding: 16px;
}
```

### Scoped Styles

```vue
<style scoped>
.chart-container {
  position: relative;
  width: 100%;
  height: var(--chart-height);
}

.chart-loading {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
```

## 🧪 Testes

### Estrutura de Testes

```
tests/
├── unit/
│   ├── components/
│   │   └── charts/
│   └── composables/
├── integration/
└── e2e/
```

### Testes de Componentes

```javascript
// tests/unit/components/charts/ApexArea.spec.js
import { mount } from '@vue/test-utils'
import ApexArea from 'src/components/charts/area/ApexArea.vue'

describe('ApexArea', () => {
  it('renders chart correctly', () => {
    const wrapper = mount(ApexArea)
    expect(wrapper.find('apexchart').exists()).toBe(true)
  })

  it('applies correct chart type', () => {
    const wrapper = mount(ApexArea)
    expect(wrapper.find('apexchart').attributes('type')).toBe('area')
  })
})
```

### Testes de Composables

```javascript
// tests/unit/composables/useChartData.spec.js
import { useChartData } from 'src/composables/useChartData'

describe('useChartData', () => {
  it('initializes with empty data', () => {
    const { data, isLoading } = useChartData()
    expect(data.value).toEqual([])
    expect(isLoading.value).toBe(false)
  })
})
```

## ⚡ Performance

### Lazy Loading

```javascript
// Componentes
const ApexArea = defineAsyncComponent(() =>
  import('src/components/charts/area/ApexArea.vue')
)

// Páginas
const routes = [
  {
    path: '/area-charts',
    component: () => import('pages/chartTypes/AreaCharts.vue')
  }
]
```

### Otimizações de Dados

```javascript
// Use computed para dados derivados
const chartData = computed(() =>
  rawData.value.map(item => ({
    x: item.date,
    y: item.value
  }))
)

// Use shallowRef para objetos grandes
const largeDataset = shallowRef([])
```

### Bundle Analysis

```bash
# Analise o bundle
quasar build --analyze

# Verifique o tamanho
quasar build --mode production
```

## 🐛 Debugging

### Vue DevTools

```javascript
// Adicione logs para debug
export default defineComponent({
  setup() {
    const data = ref([])

    // Debug no desenvolvimento
    if (process.env.NODE_ENV === 'development') {
      watch(data, (newData) => {
        console.log('Chart data updated:', newData)
      }, { deep: true })
    }

    return { data }
  }
})
```

### Console Logging

```javascript
// Logs estruturados
console.group('Chart Component')
console.log('Props:', props)
console.log('Data:', data.value)
console.log('Options:', options.value)
console.groupEnd()
```

### Error Handling

```javascript
// Error boundaries
export default defineComponent({
  setup() {
    const error = ref(null)

    const handleError = (err) => {
      console.error('Chart error:', err)
      error.value = err
    }

    return {
      error,
      handleError
    }
  }
})
```

## 📦 Build e Deploy

### Scripts Disponíveis

```json
{
  "scripts": {
    "dev": "quasar dev",
    "build": "quasar build",
    "build:pwa": "quasar build -m pwa",
    "build:spa": "quasar build -m spa",
    "lint": "eslint --ext .js,.vue ./",
    "test": "echo \"No test specified\" && exit 0"
  }
}
```

### Variáveis de Ambiente

```javascript
// quasar.conf.js
build: {
  env: {
    API_URL: process.env.API_URL || 'http://localhost:3000',
    NODE_ENV: process.env.NODE_ENV || 'development'
  }
}
```

### Deploy

```bash
# Build para produção
quasar build

# Deploy para Netlify
netlify deploy --prod --dir=dist/spa

# Deploy para Vercel
vercel --prod
```

## 🔧 Ferramentas de Desenvolvimento

### ESLint

```bash
# Executar linter
yarn run lint

# Corrigir automaticamente
yarn run lint --fix
```

### Prettier

```bash
# Formatar código
npx prettier --write "src/**/*.{js,vue}"
```

### Git Hooks

```json
// package.json
{
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{js,vue}": [
      "eslint --fix",
      "prettier --write"
    ]
  }
}
```

---

Este guia cobre os principais padrões e práticas de desenvolvimento do projeto. Para dúvidas específicas, consulte a documentação oficial do [Vue 3](https://vuejs.org/guide/), [Quasar](https://quasar.dev/) e [ApexCharts](https://apexcharts.com/docs/).
