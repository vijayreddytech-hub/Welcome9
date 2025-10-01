# 📦 Bibliotecas e Dependências

Este documento descreve todas as bibliotecas, dependências e tecnologias utilizadas no projeto **Quasar ApexCharts V2**.

## 📋 Índice

- [Visão Geral](#-visão-geral)
- [Dependências Principais](#-dependências-principais)
- [Dependências de Desenvolvimento](#-dependências-de-desenvolvimento)
- [Configurações](#-configurações)
- [Versões e Compatibilidade](#-versões-e-compatibilidade)
- [Alternativas](#-alternativas)

## 🎯 Visão Geral

O projeto utiliza um stack moderno de tecnologias web, focando em performance, manutenibilidade e experiência do desenvolvedor. Todas as dependências foram cuidadosamente selecionadas para trabalhar em harmonia.

### Stack Principal

- **Vue 3** - Framework JavaScript progressivo
- **Quasar Framework** - Framework Vue para aplicações multiplataforma
- **ApexCharts** - Biblioteca de visualização de dados
- **Vue Router** - Roteamento oficial do Vue
- **Vue I18n** - Internacionalização

## 🚀 Dependências Principais

### Vue 3 (^3.0.0)

**Propósito**: Framework JavaScript progressivo para construção de interfaces de usuário.

**Características**:
- Composition API
- Reactividade otimizada
- Tree-shaking
- TypeScript nativo
- Performance melhorada

**Uso no Projeto**:
```javascript
import { defineComponent, ref, computed } from 'vue'

export default defineComponent({
  setup() {
    const data = ref([])
    const computedValue = computed(() => data.value.length)
    return { data, computedValue }
  }
})
```

**Documentação**: [Vue 3 Guide](https://vuejs.org/guide/)

### Quasar Framework (^2.18.5)

**Propósito**: Framework Vue para desenvolvimento de aplicações multiplataforma.

**Características**:
- Componentes UI prontos
- Suporte a SPA, SSR, PWA, Mobile, Desktop
- Sistema de grid responsivo
- Tema customizável
- CLI poderoso

**Uso no Projeto**:
```vue
<template>
  <q-page padding>
    <q-card>
      <q-card-section>
        <div class="text-h6">Título</div>
      </q-card-section>
    </q-card>
  </q-page>
</template>
```

**Configuração**:
```javascript
// quasar.conf.js
framework: {
  config: {
    brand: {
      primary: '#051124',
      secondary: '#0a3273',
      accent: '#9C27B0'
    }
  }
}
```

**Documentação**: [Quasar Framework](https://quasar.dev/)

### ApexCharts (^3.50.0)

**Propósito**: Biblioteca moderna de visualização de dados.

**Características**:
- 12+ tipos de gráficos
- Responsivo
- Interativo
- Animações suaves
- Temas customizáveis

**Uso no Projeto**:
```vue
<template>
  <apexchart
    height="300"
    type="area"
    :options="options"
    :series="series"
  />
</template>
```

**Integração com Vue**:
```javascript
// src/boot/apexcharts.js
import VueApexCharts from 'vue3-apexcharts'
import { boot } from 'quasar/wrappers'

export default boot(({ app }) => {
  app.use(VueApexCharts)
})
```

**Documentação**: [ApexCharts](https://apexcharts.com/)

### Vue Router (^4.0.0)

**Propósito**: Roteamento oficial do Vue.js.

**Características**:
- Roteamento declarativo
- Lazy loading
- Guards de navegação
- Histórico HTML5
- Roteamento aninhado

**Uso no Projeto**:
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
      }
    ]
  }
]
```

**Documentação**: [Vue Router](https://router.vuejs.org/)

### Vue I18n (^9.3.0-beta.6)

**Propósito**: Internacionalização para aplicações Vue.js.

**Características**:
- Suporte a múltiplos idiomas
- Interpolação de mensagens
- Pluralização
- Formatação de números e datas
- Lazy loading de traduções

**Uso no Projeto**:
```javascript
// src/i18n/pt-BR/index.js
export default {
  charts: {
    area: {
      title: 'Gráfico de Área'
    }
  }
}
```

**Configuração**:
```javascript
// src/boot/i18n.js
import { createI18n } from 'vue-i18n'
import ptBR from 'src/i18n/pt-BR'
import enUS from 'src/i18n/en-US'

const i18n = createI18n({
  locale: 'pt-BR',
  fallbackLocale: 'en-US',
  messages: {
    'pt-BR': ptBR,
    'en-US': enUS
  }
})

export default boot(({ app }) => {
  app.use(i18n)
})
```

**Documentação**: [Vue I18n](https://vue-i18n.intlify.dev/)

### Axios (^1.7.2)

**Propósito**: Cliente HTTP baseado em Promises.

**Características**:
- Requisições HTTP/HTTPS
- Interceptors
- Transformação de dados
- Cancelamento de requisições
- Suporte a async/await

**Uso no Projeto**:
```javascript
// src/boot/axios.js
import axios from 'axios'
import { boot } from 'quasar/wrappers'

export default boot(({ app }) => {
  app.config.globalProperties.$axios = axios
})
```

**Documentação**: [Axios](https://axios-http.com/)

### Driver.js (^1.3.1)

**Propósito**: Biblioteca para criar tours guiados na interface.

**Características**:
- Tours interativos
- Highlighting de elementos
- Animações suaves
- Responsivo
- Customizável

**Uso no Projeto**:
```javascript
// src/composables/UseDriveJs.js
import { driver } from 'driver.js'

export default function useDriver() {
  const initDriver = () => {
    driver.highlight({
      element: '#chart-container',
      popover: {
        title: 'Gráfico Interativo',
        description: 'Este é um exemplo de gráfico ApexCharts'
      }
    })
  }

  return { initDriver }
}
```

**Documentação**: [Driver.js](https://driverjs.com/)

## 🛠️ Dependências de Desenvolvimento

### Quasar CLI (@quasar/app-webpack ^3.15.1)

**Propósito**: CLI oficial do Quasar para build e desenvolvimento.

**Características**:
- Hot reload
- Build otimizado
- Suporte a TypeScript
- Análise de bundle
- Múltiplos modos de build

**Scripts**:
```json
{
  "scripts": {
    "dev": "quasar dev",
    "build": "quasar build",
    "build:pwa": "quasar build -m pwa"
  }
}
```

### ESLint (^7.14.0)

**Propósito**: Linter para JavaScript e Vue.

**Configuração**:
```javascript
// .eslintrc.js
module.exports = {
  extends: [
    'standard',
    'plugin:vue/vue3-essential'
  ],
  rules: {
    'vue/multi-word-component-names': 'off'
  }
}
```

**Plugins**:
- `eslint-config-standard`
- `eslint-plugin-import`
- `eslint-plugin-node`
- `eslint-plugin-promise`
- `eslint-plugin-vue`

### Babel (@babel/eslint-parser ^7.13.14)

**Propósito**: Parser ESLint para JavaScript moderno.

**Configuração**:
```javascript
// babel.config.js
module.exports = {
  presets: [
    '@quasar/babel-preset-app'
  ]
}
```

## ⚙️ Configurações

### Quasar Configuration

```javascript
// quasar.conf.js
module.exports = configure(function (ctx) {
  return {
    supportTS: false,
    boot: ['axios', 'apexcharts', 'i18n'],
    css: ['app.css'],
    extras: ['roboto-font', 'material-icons'],
    build: {
      vueRouterMode: 'hash',
      chainWebpack (chain) {
        chain.plugin('eslint-webpack-plugin')
          .use(ESLintPlugin, [{ extensions: ['js', 'vue'] }])
      }
    },
    framework: {
      config: {
        brand: {
          primary: '#051124',
          secondary: '#0a3273',
          accent: '#9C27B0'
        }
      }
    }
  }
})
```

### JavaScript Configuration

```json
// jsconfig.json
{
  "compilerOptions": {
    "target": "es2017",
    "lib": ["es2017", "dom"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": false,
    "forceConsistentCasingInFileNames": true,
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "preserve"
  },
  "include": [
    "src/**/*"
  ],
  "exclude": [
    "node_modules"
  ]
}
```

## 📊 Versões e Compatibilidade

### Matriz de Compatibilidade

| Biblioteca | Versão | Node.js | Navegadores |
|------------|--------|---------|-------------|
| Vue 3 | ^3.0.0 | >= 12.22.1 | Chrome 60+, Firefox 60+, Safari 12+ |
| Quasar | ^2.18.5 | >= 12.22.1 | Chrome 60+, Firefox 60+, Safari 12+ |
| ApexCharts | ^3.50.0 | >= 12.22.1 | Chrome 60+, Firefox 60+, Safari 12+ |
| Vue Router | ^4.0.0 | >= 12.22.1 | Chrome 60+, Firefox 60+, Safari 12+ |
| Vue I18n | ^9.3.0-beta.6 | >= 12.22.1 | Chrome 60+, Firefox 60+, Safari 12+ |

### Browserslist

```json
// package.json
"browserslist": [
  "last 10 Chrome versions",
  "last 10 Firefox versions",
  "last 4 Edge versions",
  "last 7 Safari versions",
  "last 8 Android versions",
  "last 8 ChromeAndroid versions",
  "last 8 FirefoxAndroid versions",
  "last 10 iOS versions",
  "last 5 Opera versions"
]
```

### Engines

```json
// package.json
"engines": {
  "node": ">= 12.22.1",
  "npm": ">= 6.13.4",
  "yarn": ">= 1.21.1"
}
```

## 🔄 Alternativas

### ApexCharts

**Alternativas**:
- **Chart.js**: Mais leve, menos funcionalidades
- **D3.js**: Mais flexível, curva de aprendizado maior
- **Highcharts**: Mais recursos, licença paga para comercial
- **ECharts**: Boa performance, menos documentação em português

**Por que ApexCharts?**:
- Excelente documentação
- Performance otimizada
- Integração nativa com Vue
- Licença MIT
- Comunidade ativa

### Quasar Framework

**Alternativas**:
- **Vuetify**: Mais componentes, menos multiplataforma
- **Element Plus**: Foco em desktop
- **Ant Design Vue**: Design system robusto
- **Bootstrap Vue**: Baseado em Bootstrap

**Por que Quasar?**:
- Suporte multiplataforma
- CLI poderoso
- Performance otimizada
- Comunidade ativa
- Documentação excelente

### Vue Router

**Alternativas**:
- **Vue Router 3**: Versão anterior
- **Page.js**: Mais leve
- **Director**: Roteamento simples

**Por que Vue Router 4?**:
- Oficial do Vue
- TypeScript nativo
- Performance otimizada
- Recursos avançados

## 📈 Performance

### Bundle Size

```bash
# Análise do bundle
quasar build --analyze
```

**Tamanhos aproximados**:
- Vue 3: ~34KB (gzipped)
- Quasar: ~200KB (gzipped)
- ApexCharts: ~150KB (gzipped)
- Vue Router: ~15KB (gzipped)
- Vue I18n: ~25KB (gzipped)

### Otimizações

1. **Tree Shaking**: Apenas código necessário incluído
2. **Lazy Loading**: Componentes carregados sob demanda
3. **Code Splitting**: Divisão em chunks menores
4. **Minificação**: Código minificado para produção
5. **Gzip**: Compressão gzip habilitada

## 🔧 Manutenção

### Atualizações

```bash
# Verificar atualizações
yarn outdated

# Atualizar dependências
yarn upgrade

# Atualizar dependências específicas
yarn upgrade vue@latest
```

### Auditoria de Segurança

```bash
# Verificar vulnerabilidades
yarn audit

# Corrigir vulnerabilidades
yarn audit --fix
```

### Limpeza

```bash
# Limpar cache
yarn cache clean

# Remover node_modules
rm -rf node_modules
yarn install
```

## 📚 Recursos Adicionais

### Documentação Oficial

- [Vue 3](https://vuejs.org/guide/)
- [Quasar Framework](https://quasar.dev/)
- [ApexCharts](https://apexcharts.com/docs/)
- [Vue Router](https://router.vuejs.org/)
- [Vue I18n](https://vue-i18n.intlify.dev/)

### Comunidade

- [Vue Discord](https://chat.vuejs.org/)
- [Quasar Discord](https://chat.quasar.dev/)
- [GitHub Issues](https://github.com/patrickmonteiro/quasar-apexcharts/issues)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/vue.js)

### Ferramentas

- [Vue DevTools](https://devtools.vuejs.org/)
- [Quasar DevTools](https://quasar.dev/quasar-cli/developing-ssr/handling-ssr#quasar-dev-tools)
- [ApexCharts Playground](https://apexcharts.com/playground/)

---

Esta documentação fornece uma visão completa das bibliotecas e dependências utilizadas no projeto. Para dúvidas específicas sobre alguma biblioteca, consulte sua documentação oficial.
