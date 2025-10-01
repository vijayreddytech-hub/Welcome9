# 📊 Quasar ApexCharts V2

[![All Contributors](https://img.shields.io/badge/all_contributors-4-orange.svg?style=flat-square)](#contributors-)
[![Vue 3](https://img.shields.io/badge/Vue-3.x-4FC08D?style=flat-square&logo=vue.js)](https://vuejs.org/)
[![Quasar](https://img.shields.io/badge/Quasar-2.x-1976D2?style=flat-square&logo=quasar)](https://quasar.dev/)
[![ApexCharts](https://img.shields.io/badge/ApexCharts-3.x-FF4560?style=flat-square)](https://apexcharts.com/)

> 🚀 **Demonstração completa** da integração entre **Quasar Framework V2** (Vue 3) e **ApexCharts** - uma biblioteca moderna de visualização de dados.

## 🎯 Sobre o Projeto

Este repositório demonstra como integrar de forma eficiente a biblioteca **ApexCharts** com o **Quasar Framework V2** e **Vue 3**, oferecendo exemplos práticos de diversos tipos de gráficos e visualizações de dados.

### ✨ Características

- 🎨 **12+ Tipos de Gráficos** - Área, Barras, Bolhas, Velas, Colunas, Rosca, Heatmap, Linha, Pizza, Área Polar, Barras Radiais e Dispersão
- 🌐 **Internacionalização** - Suporte completo a PT-BR e EN-US
- 📱 **Responsivo** - Design adaptável para desktop e mobile
- 🎯 **Componentes Reutilizáveis** - Estrutura modular e bem organizada
- 🚀 **Performance** - Carregamento assíncrono de componentes
- 🎨 **Tema Integrado** - Cores do Quasar integradas aos gráficos

### 🖥️ Demo Online

**[Acesse a demonstração ao vivo](https://quasar-apexcharts.netlify.app/#/)**

## 🚀 Início Rápido

### Pré-requisitos

- **Node.js** >= 12.22.1
- **npm** >= 6.13.4 ou **yarn** >= 1.21.1

### Instalação

```bash
# Clone o repositório
git clone https://github.com/patrickmonteiro/quasar-apexcharts.git

# Entre no diretório
cd quasar-apexcharts

# Instale as dependências
yarn install
# ou
npm install
```

### Desenvolvimento

```bash
# Inicie o servidor de desenvolvimento
quasar dev

# A aplicação estará disponível em http://localhost:8080
```

### Build para Produção

```bash
# Gere o build de produção
quasar build

# Os arquivos estarão em dist/spa/
```

### Linting

```bash
# Execute o linter
yarn run lint
```

## 📚 Documentação

- 📖 **[Arquitetura do Projeto](./docs/architecture.md)** - Estrutura e organização do código
- 🛠️ **[Guia de Desenvolvimento](./docs/development.md)** - Padrões e convenções
- 📊 **[Documentação dos Gráficos](./docs/charts.md)** - Tipos de gráficos disponíveis
- 📦 **[Bibliotecas e Dependências](./docs/libraries.md)** - Tecnologias utilizadas
- 🤝 **[Guia de Contribuição](./docs/contributing.md)** - Como contribuir com o projeto

## 🏗️ Arquitetura

```
src/
├── components/          # Componentes reutilizáveis
│   ├── charts/         # Componentes de gráficos
│   │   ├── area/       # Gráficos de área
│   │   ├── bar/        # Gráficos de barras
│   │   ├── bubble/     # Gráficos de bolhas
│   │   └── ...         # Outros tipos
│   ├── Card.vue        # Componente de card
│   └── Navbar.vue      # Navegação
├── pages/              # Páginas da aplicação
│   ├── chartTypes/     # Páginas por tipo de gráfico
│   └── Index.vue       # Página inicial
├── layouts/            # Layouts da aplicação
├── router/             # Configuração de rotas
├── i18n/               # Internacionalização
├── boot/               # Configurações de inicialização
└── composables/        # Composables Vue 3
```

## 🎨 Tipos de Gráficos

| Tipo | Componente | Descrição |
|------|------------|-----------|
| 📈 **Área** | `ApexArea` | Gráficos de área com preenchimento |
| 📊 **Barras** | `ApexBar` | Gráficos de barras horizontais |
| 🫧 **Bolhas** | `ApexBubble` | Gráficos de dispersão 3D |
| 🕯️ **Velas** | `ApexCandlestick` | Gráficos financeiros |
| 📊 **Colunas** | `ApexColumn` | Gráficos de colunas verticais |
| 🍩 **Rosca** | `ApexDonut` | Gráficos de rosca |
| 🔥 **Heatmap** | `ApexHeatmap` | Mapas de calor |
| 📈 **Linha** | `ApexLine` | Gráficos de linha |
| 🥧 **Pizza** | `ApexPie` | Gráficos de pizza |
| 🎯 **Área Polar** | `ApexPolarArea` | Gráficos de área polar |
| ⚡ **Barras Radiais** | `ApexRadialBar` | Gráficos radiais |
| 📊 **Dispersão** | `ApexScatter` | Gráficos de dispersão |

## 🛠️ Tecnologias

- **[Vue 3](https://vuejs.org/)** - Framework JavaScript progressivo
- **[Quasar Framework](https://quasar.dev/)** - Framework Vue para aplicações multiplataforma
- **[ApexCharts](https://apexcharts.com/)** - Biblioteca de visualização de dados
- **[Vue Router](https://router.vuejs.org/)** - Roteamento oficial do Vue
- **[Vue I18n](https://vue-i18n.intlify.dev/)** - Internacionalização
- **[Driver.js](https://driverjs.com/)** - Biblioteca de tour guiado

## 🤝 Contribuindo

Contribuições são sempre bem-vindas! Por favor, leia nosso [Guia de Contribuição](./docs/contributing.md) para detalhes sobre:

- 🐛 Como reportar bugs
- ✨ Como sugerir novas funcionalidades
- 🔧 Como configurar o ambiente de desenvolvimento
- 📝 Padrões de código e commits
- 🧪 Como executar testes

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👥 Contribuidores

<a href="https://github.com/patrickmonteiro/quasar-apexcharts/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=patrickmonteiro/quasar-apexcharts" />
</a>

Feito com ❤️ pela comunidade [contrib.rocks](https://contrib.rocks).

## 🔗 Links Úteis

- [Documentação do Quasar](https://quasar.dev/)
- [Documentação do ApexCharts](https://apexcharts.com/docs/)
- [Documentação do Vue 3](https://vuejs.org/guide/)
- [Quasar Awesome](https://awesome-quasar.dev/)

---

⭐ **Se este projeto foi útil para você, considere dar uma estrela!**
