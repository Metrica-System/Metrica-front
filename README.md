# Metrica System - Frontend📊

Plataforma de Análise Psicossocial para administração de avaliações, automação de coleta de dados, cálculo de resultados e geração de relatórios organizacionais.

## 🎯 Objetivo do Projeto

A **Metrica System** é uma solução robusta projetada para profissionais e organizações que gerenciam avaliações psicossociais. O sistema automatiza todo o ciclo de vida de uma avaliação: desde a configuração de questionários e distribuição de links de acesso até o processamento de respostas e a criação de planos de ação baseados em resultados.

A plataforma suporta múltiplas metodologias (incluindo a **COPSOQ 2**) e permite a gestão de diversas empresas sob a mesma conta de cliente, garantindo o isolamento total de dados.

## 🚀 Principais Funcionalidades

- **Gestão Multiempresa:** Administração de múltiplas empresas vinculadas a uma única conta de cliente.
- **Banco de Questões Flexível:** Criação de ferramentas de avaliação com grupos, fatores, escalas e regras de pontuação customizáveis.
- **Avaliações Dinâmicas:** Publicação de avaliações via links controlados, com suporte a modos anônimos ou identificados.
- **Análise de Resultados:** Processamento automatizado de respostas com detalhamento por fator psicossocial e comparativos entre empresas/períodos.
- **Relatórios e Planos de Ação:** Geração de documentos de análise e acompanhamento de melhorias organizacionais.
- **Controle de Acesso Rigoroso:** Sistema de permissões baseado em papéis (RBAC) e gestão de vigência contratual.
- **Dashboard Personalizável:** Visão geral de indicadores chave com interface adaptável por usuário.

## 🏗️ Arquitetura do Sistema

O projeto é dividido em três níveis de governança:
1. **Administração Geral:** Controle de clientes, contratos e liberação de acesso à plataforma.
2. **Conta do Cliente:** Gestão de usuários, empresas avaliadas e coordenação de avaliações.
3. **Empresas Avaliadas:** Escopo onde ocorrem as avaliações, coleta de respostas e geração de resultados.

### Stack Tecnológica (Frontend)
- **Framework:** React
- **Build Tool:** Vite
- **Linguagem:** TypeScript
- **Estilização:** CSS (Custom)
- **Integração:** Supabase (Auth & Database)

## 📁 Estrutura do Repositório

- `metrica/`: Código fonte da aplicação frontend desenvolvida com React e Vite.
  - `src/`: Componentes, hooks, páginas e serviços da interface.
  - `public/`: Ativos estáticos.
- `documentacao_atualizada_metrica_system.md`: Especificação funcional e técnica detalhada do sistema.

## 🛠️ Como Iniciar (Desenvolvimento)

1. **Acesse a pasta do projeto:**
   ```bash
   cd metrica
   ```

2. **Instale as dependências:**
   ```bash
   npm install
   ```

3. **Inicie o servidor de desenvolvimento:**
   ```bash
   npm run dev
   ```

4. **Acesse no navegador:**
   [http://localhost:5173/](http://localhost:5173/)

---
**Versão:** 2.0 | **Data:** 27/09/2026
