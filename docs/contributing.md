# 🤝 Guia de Contribuição

Obrigado por considerar contribuir com o **Quasar ApexCharts V2**! Este guia fornece todas as informações necessárias para contribuir de forma eficaz com o projeto.

## 📋 Índice

- [Código de Conduta](#-código-de-conduta)
- [Como Contribuir](#-como-contribuir)
- [Configuração do Ambiente](#-configuração-do-ambiente)
- [Padrões de Desenvolvimento](#-padrões-de-desenvolvimento)
- [Processo de Pull Request](#-processo-de-pull-request)
- [Testes](#-testes)
- [Documentação](#-documentação)
- [Reportando Bugs](#-reportando-bugs)
- [Sugerindo Funcionalidades](#-sugerindo-funcionalidades)

## 🤝 Código de Conduta

Este projeto segue o [Código de Conduta do Contributor Covenant](https://www.contributor-covenant.org/version/2/1/code_of_conduct/). Ao participar, você concorda em manter este código.

### Nossos Compromissos

- **Inclusivo**: Bem-vindos todos, independente de identidade ou experiência
- **Respeitoso**: Tratamos todos com dignidade e respeito
- **Construtivo**: Focamos no que é melhor para a comunidade
- **Profissional**: Mantemos um ambiente profissional e acolhedor

## 🚀 Como Contribuir

### Tipos de Contribuição

- 🐛 **Bug Reports**: Reportar problemas encontrados
- ✨ **Feature Requests**: Sugerir novas funcionalidades
- 📝 **Documentação**: Melhorar documentação existente
- 🧪 **Testes**: Adicionar ou melhorar testes
- 🎨 **UI/UX**: Melhorar interface e experiência do usuário
- 🔧 **Refatoração**: Melhorar código existente
- 🌐 **Traduções**: Adicionar novos idiomas

### Antes de Começar

1. **Verifique Issues Existentes**: Procure por issues similares
2. **Discuta Mudanças Grandes**: Abra uma issue para discussão
3. **Fork o Repositório**: Crie seu fork pessoal
4. **Configure o Ambiente**: Siga o guia de configuração

## ⚙️ Configuração do Ambiente

### Pré-requisitos

- **Node.js** >= 12.22.1
- **npm** >= 6.13.4 ou **yarn** >= 1.21.1
- **Git** >= 2.20.0

### Passo a Passo

1. **Fork e Clone**
   ```bash
   # Fork o repositório no GitHub
   # Clone seu fork
   git clone https://github.com/SEU_USUARIO/quasar-apexcharts.git
   cd quasar-apexcharts

   # Adicione o repositório original como upstream
   git remote add upstream https://github.com/patrickmonteiro/quasar-apexcharts.git
   ```

2. **Instale Dependências**
   ```bash
   yarn install
   # ou
   npm install
   ```

3. **Execute a Aplicação**
   ```bash
   quasar dev
   ```

4. **Verifique se Tudo Funciona**
   - Acesse http://localhost:8080
   - Navegue pelos diferentes tipos de gráficos
   - Teste a funcionalidade de troca de idioma

### Estrutura de Branches

```bash
# Branch principal
main

# Branches de feature
feature/nome-da-funcionalidade

# Branches de bugfix
bugfix/descricao-do-bug

# Branches de hotfix
hotfix/descricao-urgente
```

## 📝 Padrões de Desenvolvimento

### Convenções de Código

#### JavaScript/Vue
- **ESLint**: Configuração padrão do projeto
- **Prettier**: Formatação automática
- **Composition API**: Preferir Composition API sobre Options API
- **TypeScript**: Quando possível, usar tipagem

#### Nomenclatura
```javascript
// ✅ Bom
const ApexAreaChart = defineComponent({})
const chartData = ref([])
const handleChartClick = () => {}

// ❌ Evitar
const apexAreaChart = defineComponent({})
const chart_data = ref([])
const handle_chart_click = () => {}
```

#### Estrutura de Componentes
```vue
<template>
  <!-- Template primeiro -->
</template>

<script>
// Script segundo
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'ComponentName',
  // ... resto do componente
})
</script>

<style scoped>
/* Estilos por último */
</style>
```

### Padrões de Commits

Seguimos o padrão [Conventional Commits](https://www.conventionalcommits.org/):

```bash
# Formato
<type>(<scope>): <description>

# Exemplos
feat(charts): add new bubble chart component
fix(ui): resolve responsive layout issue
docs(readme): update installation instructions
test(charts): add unit tests for area chart
refactor(components): improve chart data handling
```

#### Tipos de Commit
- `feat`: Nova funcionalidade
- `fix`: Correção de bug
- `docs`: Mudanças na documentação
- `style`: Formatação, sem mudança de código
- `refactor`: Refatoração de código
- `test`: Adição ou correção de testes
- `chore`: Mudanças em ferramentas ou configurações

### Estrutura de Arquivos

```
src/components/charts/novo-tipo/
├── ApexNovoTipo.vue          # Componente principal
├── ExemploNovoTipo.vue       # Exemplo específico (opcional)
└── README.md                 # Documentação do componente
```

## 🔄 Processo de Pull Request

### 1. Preparação

```bash
# Atualize sua branch com a main
git checkout main
git pull upstream main

# Crie uma nova branch
git checkout -b feature/nova-funcionalidade

# Faça suas mudanças
# ... código ...

# Commit suas mudanças
git add .
git commit -m "feat: add new chart type"
```

### 2. Testes Locais

```bash
# Execute o linter
yarn run lint

# Execute a aplicação
quasar dev

# Teste manualmente
# - Navegue pela aplicação
# - Teste a funcionalidade adicionada
# - Verifique responsividade
# - Teste em diferentes navegadores
```

### 3. Documentação

- [ ] Atualize o README.md se necessário
- [ ] Adicione documentação para novos componentes
- [ ] Atualize a documentação de arquitetura
- [ ] Adicione comentários no código

### 4. Criação do PR

#### Template Obrigatório

```markdown
## 📝 Descrição

Breve descrição das mudanças realizadas.

## 🎯 Tipo de Mudança

- [ ] Bug fix (mudança que corrige um problema)
- [ ] Nova funcionalidade (mudança que adiciona funcionalidade)
- [ ] Breaking change (correção ou funcionalidade que quebra funcionalidade existente)
- [ ] Documentação (mudança apenas na documentação)

## 🧪 Como Testar

1. Passo 1
2. Passo 2
3. Passo 3

## 📸 Screenshots/Vídeos

### Antes
![Antes](url-da-imagem)

### Depois
![Depois](url-da-imagem)

## ✅ Checklist

- [ ] Meu código segue as convenções do projeto
- [ ] Realizei uma auto-revisão do meu código
- [ ] Comentei partes complexas do código
- [ ] Minhas mudanças não geram warnings
- [ ] Adicionei testes que provam que minha correção é eficaz
- [ ] Novos e antigos testes passam localmente
- [ ] Qualquer mudança dependente foi documentada e atualizada

## 🔗 Issues Relacionadas

Fixes #(issue_number)
```

### 5. Revisão

- **Auto-revisão**: Revise seu próprio código
- **Testes**: Certifique-se que tudo funciona
- **Documentação**: Atualize documentação necessária
- **Screenshots**: Adicione imagens das mudanças

## 🧪 Testes

### Testes Obrigatórios

#### 1. Testes Manuais
- [ ] Navegação entre páginas
- [ ] Renderização dos gráficos
- [ ] Responsividade (mobile/desktop)
- [ ] Troca de idioma
- [ ] Performance (carregamento)

#### 2. Testes de Compatibilidade
- [ ] Chrome (últimas 2 versões)
- [ ] Firefox (últimas 2 versões)
- [ ] Safari (última versão)
- [ ] Edge (última versão)

#### 3. Testes de Performance
- [ ] Tempo de carregamento < 3s
- [ ] Bundle size não aumentou significativamente
- [ ] Lazy loading funcionando

### Como Executar Testes

```bash
# Linter
yarn run lint

# Build de produção
quasar build

# Análise de bundle
quasar build --analyze
```

## 📚 Documentação

### Documentação Obrigatória

#### Para Novos Componentes
```markdown
# Nome do Componente

## Descrição
Breve descrição do que o componente faz.

## Props
| Prop | Tipo | Padrão | Descrição |
|------|------|--------|-----------|
| data | Array | [] | Dados do gráfico |

## Exemplo
```vue
<template>
  <ApexNovoTipo :data="chartData" />
</template>
```

#### Para Novas Funcionalidades
- Atualize o README.md
- Adicione exemplos de uso
- Documente APIs públicas
- Atualize a documentação de arquitetura

### Padrões de Documentação

- **Markdown**: Use sintaxe Markdown correta
- **Exemplos**: Sempre inclua exemplos práticos
- **Imagens**: Use screenshots quando necessário
- **Links**: Mantenha links atualizados

## 🐛 Reportando Bugs

### Template de Bug Report

```markdown
## 🐛 Descrição do Bug

Descrição clara e concisa do problema.

## 🔄 Passos para Reproduzir

1. Vá para '...'
2. Clique em '...'
3. Role até '...'
4. Veja o erro

## 🎯 Comportamento Esperado

Descrição do que deveria acontecer.

## 📸 Screenshots

Se aplicável, adicione screenshots.

## 🖥️ Ambiente

- OS: [e.g. macOS, Windows, Linux]
- Navegador: [e.g. Chrome, Firefox, Safari]
- Versão: [e.g. 22]
- Node.js: [e.g. 16.14.0]

## 📋 Informações Adicionais

Qualquer outra informação relevante.
```

### Critérios para Bug Reports

- [ ] Bug é reproduzível
- [ ] Descrição clara do problema
- [ ] Passos para reproduzir
- [ ] Comportamento esperado vs atual
- [ ] Screenshots quando aplicável
- [ ] Informações do ambiente

## ✨ Sugerindo Funcionalidades

### Template de Feature Request

```markdown
## 🚀 Funcionalidade Sugerida

Descrição clara da funcionalidade desejada.

## 🎯 Problema que Resolve

Qual problema esta funcionalidade resolve?

## 💡 Solução Proposta

Descrição detalhada da solução.

## 🔄 Alternativas Consideradas

Outras soluções que você considerou.

## 📋 Informações Adicionais

Qualquer contexto adicional.
```

### Critérios para Feature Requests

- [ ] Funcionalidade é útil para a comunidade
- [ ] Não duplica funcionalidade existente
- [ ] Alinha com os objetivos do projeto
- [ ] Descrição clara e detalhada
- [ ] Considera implementação e manutenção

## 🏷️ Labels e Milestones

### Labels Disponíveis

- `bug`: Algo não está funcionando
- `enhancement`: Nova funcionalidade ou melhoria
- `documentation`: Melhorias na documentação
- `good first issue`: Bom para iniciantes
- `help wanted`: Precisa de ajuda extra
- `question`: Mais informações necessárias
- `wontfix`: Não será corrigido

### Milestones

- `v1.0.0`: Versão inicial
- `v1.1.0`: Próxima versão menor
- `v2.0.0`: Próxima versão maior

## 🎉 Reconhecimento

### All Contributors

Este projeto usa o [All Contributors](https://allcontributors.org/) para reconhecer contribuidores.

Para adicionar um contribuidor:

```bash
yarn all-contributors add username contribution-type
```

### Tipos de Contribuição

- `code`: Código
- `bug`: Bug reports
- `content`: Conteúdo
- `design`: Design
- `doc`: Documentação
- `ideas`: Ideias
- `question`: Perguntas
- `review`: Code review
- `test`: Testes
- `translation`: Traduções

## 📞 Suporte

### Onde Pedir Ajuda

- **GitHub Issues**: Para bugs e funcionalidades
- **GitHub Discussions**: Para perguntas e discussões
- **Discord**: Para conversas informais

### Tempo de Resposta

- **Bugs críticos**: 24-48 horas
- **Feature requests**: 1-2 semanas
- **Perguntas**: 3-5 dias úteis
- **Pull requests**: 1-2 semanas

## 🎯 Roadmap

### Próximas Funcionalidades

- [ ] Testes automatizados
- [ ] Mais tipos de gráficos
- [ ] Temas customizáveis
- [ ] Exportação de gráficos
- [ ] Modo escuro
- [ ] PWA completo

### Contribuindo para o Roadmap

- Vote em issues existentes
- Sugira novas funcionalidades
- Contribua com implementações
- Ajude com documentação

---

**Obrigado por contribuir! 🎉**

Sua contribuição faz a diferença para toda a comunidade. Se tiver dúvidas, não hesite em perguntar!
