# METRICA SYSTEM

## Documentação funcional e técnica consolidada --- Plataforma de Análise Psicossocial

**Versão:** 2.0\
**Data:** 27/09/2026\
**Status:** Especificação funcional para orientar a implementação

------------------------------------------------------------------------

# 1. Objetivo do projeto

A Metrica System será uma plataforma para administrar avaliações
psicossociais, automatizar a coleta e o mapeamento de respostas,
calcular resultados e organizar relatórios por empresa.

A plataforma será utilizada por profissionais e organizações que
gerenciam avaliações. Os trabalhadores/participantes responderão aos
questionários por meio de links de acesso, sem necessidade de possuir
uma conta administrativa na plataforma, salvo se um fluxo identificado
específico vier a exigir isso.

O sistema deverá permitir diferentes ferramentas de avaliação, cada uma
com suas próprias questões, grupos, fatores, escalas, regras de
pontuação e critérios de interpretação. A metodologia COPSOQ 2 será
contemplada, sem impedir a inclusão de outras metodologias.

# 2. Princípios gerais

-   **Multiempresa:** uma conta de cliente poderá administrar diversas
    empresas.
-   **Isolamento de dados:** cada cliente acessará somente os dados aos
    quais possui autorização.
-   **Acesso contratual:** a utilização da plataforma dependerá de conta
    autorizada e contrato vigente.
-   **Pagamento externo:** o pagamento será realizado fora da plataforma
    e registrado manualmente pela Administração Geral.
-   **Sem cobrança integrada nesta etapa:** não haverá checkout ou
    processamento automático de pagamento como requisito inicial.
-   **Empresas sem limite quantitativo:** não haverá limite de empresas
    por conta nem cobrança adicional por empresa cadastrada, conforme o
    modelo comercial definido.
-   **Participação por link:** os participantes poderão responder por
    link público controlado pela avaliação.
-   **Anonimato configurável:** cada avaliação deverá definir se as
    respostas serão anônimas ou identificadas.
-   **Versionamento:** alterações em ferramentas ou avaliações
    publicadas não deverão modificar os dados históricos.
-   **Personalização individual:** preferências de dashboard e interface
    serão salvas por usuário, sem alterar os dados compartilhados.
-   **Auditoria:** ações administrativas e alterações relevantes deverão
    ser registradas.

# 3. Arquitetura de contas e entidades

A plataforma será organizada em três níveis principais:

1.  **Administração Geral da Plataforma**
2.  **Conta do Cliente**
3.  **Empresas Avaliadas**

## 3.1 Administração Geral

A Administração Geral controla o cadastro dos clientes, contratos,
pagamentos registrados e autorização de acesso à plataforma.

## 3.2 Conta do Cliente

Cada cliente terá uma conta própria vinculada a um ou mais contratos ao
longo do tempo. A conta poderá ter vários usuários, com diferentes
perfis e permissões.

A conta do cliente poderá: - Gerenciar usuários autorizados. - Cadastrar
e administrar empresas sem limite de quantidade. - Criar e acompanhar
avaliações. - Gerenciar questionários, links, respostas e comentários,
conforme as permissões. - Consultar resultados por empresa, avaliação,
grupo e fator. - Gerar relatórios e planos de ação. - Consultar o
histórico de avaliações.

## 3.3 Empresas avaliadas

Cada empresa deverá estar vinculada a uma Conta do Cliente. Seus dados
incluem: - Dados cadastrais. - Setores, departamentos e turnos, quando
aplicáveis. - Avaliações. - Links e configurações de aplicação. -
Respostas e comentários. - Resultados. - Relatórios. - Planos de ação. -
Histórico.

# 4. Administração Geral: clientes, contratos e liberação de acesso

## 4.1 Responsabilidades

O Administrador Geral poderá: - Cadastrar, consultar, editar, ativar,
suspender e bloquear contas de clientes. - Cadastrar e editar dados
comerciais e contratuais. - Registrar valor contratado e condições
acordadas. - Registrar pagamento realizado fora da plataforma. -
Informar data, valor, situação e referência/comprovante do pagamento,
quando aplicável. - Definir início e término da vigência. - Liberar,
suspender ou bloquear o acesso. - Renovar ou registrar novo contrato,
preservando o histórico. - Consultar empresas cadastradas e indicadores
de utilização. - Consultar o histórico de ações administrativas.

## 4.2 Fluxo de autorização

1.  A Administração Geral cadastra a conta do cliente.
2.  O pagamento é realizado externamente, conforme o acordo comercial.
3.  O Administrador Geral confirma e registra o pagamento no sistema.
4.  O Administrador Geral registra o contrato e o período de vigência.
5.  O sistema libera o acesso quando a conta estiver ativa e a vigência
    tiver começado.
6.  O cliente passa a utilizar as funcionalidades disponíveis durante o
    período contratado.
7.  Ao final da vigência, o acesso é bloqueado, salvo renovação ou novo
    contrato válido.

O registro de pagamento não deve, isoladamente, liberar o acesso antes
da data de início contratual.

## 4.3 Modelo comercial

-   Pagamento único vinculado a contrato.
-   Sem cobrança recorrente obrigatória dentro da plataforma.
-   Sem planos comerciais com diferentes conjuntos de funcionalidades
    nesta versão.
-   Todas as contas ativas e com contrato vigente terão acesso ao
    conjunto de funcionalidades disponibilizadas.
-   Cadastro ilimitado de empresas, sem cobrança adicional por empresa.
-   O acesso não será considerado vitalício: sua validade dependerá da
    vigência contratual.

## 4.4 Status separados

### Status do pagamento

-   Pendente
-   Pago
-   Estornado
-   Cancelado

### Status do contrato

-   Aguardando início
-   Vigente
-   Expirado
-   Encerrado

### Status da conta

-   Ativa
-   Suspensa
-   Bloqueada

### Regra de acesso

  -----------------------------------------------------------------------
  Situação                            Resultado
  ----------------------------------- -----------------------------------
  Conta ativa + contrato vigente +    Acesso liberado
  data de início alcançada            

  Pagamento registrado, mas contrato  Acesso aguarda a data de início
  ainda não iniciado                  

  Contrato expirado, sem renovação    Acesso administrativo bloqueado

  Conta suspensa ou bloqueada         Acesso administrativo bloqueado

  Contrato renovado                   Acesso conforme a nova vigência
  -----------------------------------------------------------------------

A suspensão ou expiração não deverá apagar automaticamente os dados. A
política de retenção, exportação e eventual exclusão deverá ser definida
conforme contrato e obrigações aplicáveis.

## 4.5 Dados do contrato e pagamento

Campos sugeridos: - Identificador do contrato. - Conta do cliente. -
Número ou referência contratual. - Valor contratado. - Forma/condição de
pagamento. - Data do pagamento. - Status do pagamento. - Referência ou
arquivo de comprovante, se utilizado. - Usuário administrador que
registrou/confirmou o pagamento. - Data e hora do registro. - Data de
início da vigência. - Data de término da vigência. - Status do
contrato. - Observações administrativas. - Histórico de alterações.

## 4.6 Links de avaliações após vencimento ou suspensão

O comportamento dos links públicos deverá ser uma regra explícita.
Recomenda-se que o sistema permita configurar e aplicar uma política
clara para impedir novas respostas quando a avaliação estiver encerrada
ou quando a conta estiver suspensa/sem vigência. A política não deverá
apagar respostas já recebidas.

# 5. Usuários, contas pessoais e permissões

## 5.1 Separação entre usuário da plataforma e participante

**Usuário da plataforma:** pessoa que possui credenciais, entra na área
administrativa, acessa a dashboard e trabalha com empresas, avaliações e
resultados conforme suas permissões.

**Participante da avaliação:** pessoa que responde ao questionário por
um link. Não precisa necessariamente possuir login na plataforma. A
identificação dependerá da configuração da avaliação.

Esses dois registros e fluxos devem ser separados no modelo de dados.

## 5.2 Minha conta / Meu perfil

Cada usuário poderá administrar suas próprias informações: - Visualizar
e editar nome. - Atualizar telefone e foto, se esses campos forem
disponibilizados. - Alterar e-mail mediante validação/confirmação. -
Alterar senha. - Solicitar recuperação de senha. - Consultar informações
básicas da conta. - Gerenciar sessões ativas, quando suportado.

O usuário não poderá alterar o próprio papel, permissões, vínculos
administrativos ou status privilegiado por meio da edição do perfil.

## 5.3 Segurança da autenticação

-   Utilizar Supabase Auth para autenticação, recuperação e alteração de
    senha.
-   Nunca armazenar senhas em texto puro.
-   Nunca permitir que administradores visualizem a senha de outros
    usuários.
-   Proteger alterações de e-mail e credenciais com os mecanismos de
    confirmação apropriados.
-   Considerar autenticação multifator para contas privilegiadas.
-   Registrar eventos relevantes de segurança.
-   Não expor chaves privilegiadas do Supabase no frontend.

## 5.4 Gestão de usuários

Usuários com permissão administrativa poderão: - Convidar e cadastrar
usuários. - Editar dados administrativos permitidos. - Ativar, suspender
ou desativar contas. - Atribuir perfis e permissões. - Vincular usuários
a uma conta de cliente. - Restringir o acesso a empresas específicas. -
Consultar histórico de convites e alterações.

## 5.5 Papéis sugeridos

-   **Administrador Geral:** administra toda a plataforma, contas de
    clientes, contratos, registros de pagamento e liberação de acesso.
-   **Administrador do Cliente:** gerencia os usuários e dados da
    própria conta, dentro do escopo permitido.
-   **Gestor/Analista:** gerencia empresas e avaliações autorizadas e
    consulta resultados.
-   **Leitor/Consulta:** consulta informações autorizadas, sem poder
    alterá-las.

Os papéis devem ser configuráveis por permissões, e não apenas por
ocultação de itens na interface.

## 5.6 Permissões

As permissões devem considerar módulo, ação e escopo. Exemplos: -
`companies.read`, `companies.create`, `companies.update`,
`companies.archive` - `question_tools.read`, `question_tools.manage` -
`questions.manage` - `scoring_rules.manage` - `assessments.read`,
`assessments.create`, `assessments.publish`, `assessments.close` -
`results.read`, `results.export` - `reports.create`, `reports.update`,
`reports.export` - `users.read`, `users.invite`, `users.manage_roles` -
`action_plans.read`, `action_plans.manage` - `contracts.read` e
permissões administrativas exclusivas para contratos/pagamentos,
restritas à Administração Geral.

## 5.7 Vínculos e escopo

Um usuário poderá estar vinculado à conta de um cliente e, conforme o
modelo de acesso, a todas as empresas daquela conta ou somente a
empresas selecionadas. O backend deverá validar o vínculo em todas as
operações.

# 6. Dashboard personalizada por usuário

A dashboard deverá oferecer uma visão geral do trabalho e permitir
personalização individual.

## 6.1 Indicadores possíveis

-   Empresas vinculadas ao usuário.
-   Avaliações em andamento.
-   Avaliações concluídas.
-   Respostas recebidas.
-   Participação percentual, quando aplicável.
-   Resultados disponíveis.
-   Relatórios recentes.
-   Avaliações próximas do encerramento.
-   Atividades recentes, conforme permissões.

Os indicadores devem refletir dados reais acessíveis ao usuário; não
devem ser números fixos ou simulados em produção.

## 6.2 Personalização

Cada usuário poderá, conforme as opções implementadas: - Escolher os
cartões/indicadores exibidos. - Reordenar cartões e widgets. - Definir
filtros padrão, como cliente ou empresa. - Configurar atalhos para
tarefas frequentes. - Escolher a página inicial. - Definir tema
claro/escuro, se disponibilizado. - Ajustar preferências de
visualização.

As preferências devem ser salvas por usuário. A personalização de um
usuário não poderá alterar a dashboard de outro.

## 6.3 Limites da personalização

A personalização não poderá: - Alterar dados de avaliações. - Modificar
cálculos ou resultados. - Ampliar permissões. - Exibir dados de empresas
não autorizadas. - Alterar configurações compartilhadas do cliente ou da
plataforma.

# 7. Configurações

## 7.1 Preferências pessoais

-   Tema e preferências visuais.
-   Página inicial.
-   Filtros padrão.
-   Organização da dashboard.
-   Preferências de notificações.

## 7.2 Configurações do cliente

-   Dados e preferências da conta, conforme permissões.
-   Parâmetros compartilhados de operação.
-   Preferências de relatórios.
-   Configurações gerais aplicáveis às empresas da conta.

## 7.3 Configurações de avaliação

As configurações próprias de cada avaliação deverão ficar no módulo
Avaliações, incluindo: - Período de aplicação. - Modo anônimo ou
identificado. - Regras de participação. - Configuração de comentários. -
Estado do link. - Publicação, pausa e encerramento.

## 7.4 Configurações da plataforma

Exclusivas à Administração Geral: - Parâmetros globais. - Recursos
habilitados. - Configurações gerais de segurança. - Padrões globais e
configurações operacionais.

## 7.5 Notificações

-   Convites de usuários.
-   Recuperação de acesso.
-   Lembretes de avaliação, quando habilitados.
-   Avisos administrativos e contratuais.
-   Alertas de contratos próximos do vencimento.

## 7.6 Histórico

Alterações relevantes em configurações globais, configurações do cliente
e parâmetros de avaliação deverão ser auditadas. Mudanças futuras não
deverão alterar retroativamente avaliações publicadas ou relatórios
históricos.

# 8. Menu principal sugerido

``` text
01. DASHBOARD
    ├── Visão geral
    └── Personalizar dashboard

02. EMPRESAS
    ├── Todas as empresas
    ├── Cadastrar empresa
    ├── Setores
    ├── Departamentos
    └── Turnos

03. BANCO DE QUESTÕES
    ├── Ferramentas de avaliação
    ├── Questões
    ├── Grupos de avaliação
    ├── Fatores psicossociais
    ├── Escalas de resposta
    └── Regras de pontuação e interpretação

04. AVALIAÇÕES
    ├── Todas as avaliações
    ├── Criar avaliação
    ├── Links e participação
    ├── Acompanhar respostas
    └── Encerradas

05. RESULTADOS
    ├── Resultados por empresa
    ├── Resultados por avaliação
    └── Resultados por fator

06. COMPARATIVOS
    ├── Entre empresas
    ├── Entre avaliações
    └── Entre períodos

07. RELATÓRIOS E PLANOS DE AÇÃO
    ├── Relatórios
    └── Planos de ação

08. USUÁRIOS
    ├── Minha conta / Meu perfil
    ├── Segurança e acesso
    ├── Todos os usuários
    ├── Convidar usuário
    ├── Perfis e permissões
    ├── Vínculos com clientes
    ├── Vínculos com empresas
    └── Histórico de alterações

09. CONFIGURAÇÕES
    ├── Preferências pessoais
    ├── Personalização da dashboard
    ├── Configurações do cliente
    ├── Notificações
    ├── Segurança e privacidade
    ├── Padrões de relatórios
    └── Histórico de alterações

ÁREA EXCLUSIVA — ADMINISTRAÇÃO GERAL
    ├── Visão geral da plataforma
    ├── Contas de clientes
    ├── Cadastro de cliente
    ├── Contratos
    ├── Pagamentos registrados
    ├── Liberação e suspensão de acesso
    ├── Renovações
    ├── Utilização por cliente
    ├── Parâmetros globais
    └── Auditoria administrativa
```

A área de Administração Geral deverá ser protegida por permissões
próprias e não deverá aparecer como acessível a usuários comuns.

# 9. Banco de Questões e ferramentas

O Banco de Questões deverá permitir cadastrar diferentes ferramentas de
avaliação. Cada ferramenta poderá ter: - Nome, sigla, descrição e
versão. - Questões. - Grupos. - Fatores psicossociais. - Escalas e
alternativas. - Pontuação por alternativa. - Regras de cálculo. - Faixas
de classificação. - Interpretações e recomendações. - Status e histórico
de versões.

## 9.1 Campos de questão

-   Pergunta.
-   Grupo.
-   Fator psicossocial.
-   Tipo de avaliação.
-   Escala de resposta.
-   Status.
-   Permitir comentário.
-   Comentário obrigatório ou opcional.
-   Ordem da questão.
-   Ferramenta e versão às quais pertence.

## 9.2 Ações administrativas

-   Adicionar.
-   Editar.
-   Excluir, quando não houver dependências históricas.
-   Duplicar.
-   Ativar e desativar.
-   Reordenar.
-   Versionar.

Questões usadas em avaliações publicadas devem permanecer preservadas na
versão aplicada.

# 10. Avaliações e links de participação

Cada avaliação deverá estar vinculada a uma conta de cliente, empresa e
versão de ferramenta.

Campos e configurações: - Nome da avaliação. - Empresa. - Ferramenta e
versão. - Público participante. - Período de aplicação. - Modo de
identificação. - Permissão para comentários. - Regras de participação. -
Link ou token de acesso. - Status: rascunho, publicada, pausada,
encerrada. - Data de publicação e encerramento.

## 10.1 Modos de participação

-   **Anônima:** não registrar identificação direta do participante no
    conjunto de respostas. A implementação deverá evitar metadados
    desnecessários que permitam reidentificação.
-   **Identificada:** registrar os dados de identificação previstos e
    informados ao participante.

O link poderá ser configurado para uma resposta por participante ou para
permitir múltiplas respostas no contexto de aplicação presencial,
conforme regra definida na avaliação. A prevenção de duplicidade deverá
respeitar o modo escolhido.

# 11. Resultados por empresa

Os resultados deverão ser apresentados por empresa e avaliação, com
detalhamento por grupo e fator psicossocial.

Informações gerais sugeridas: - Total de trabalhadores, quando
informado. - Total de participantes. - Total de respostas. - Percentual
de participação. - Data/período da avaliação. - Resultado geral por
grupo de avaliação. - Score, percentual, condição e interpretação. -
Resultados por fator. - Segmentação por setor, departamento, turno ou
grupo, quando houver dados suficientes e a configuração permitir.

A plataforma deverá automatizar o mapeamento das respostas para as
questões, fatores, grupos e regras de cálculo configuradas. Não deverá
depender de resultados fixos ou simulados.

Os resultados deverão armazenar a versão da ferramenta, das regras de
cálculo e do processamento que os gerou.

# 12. Relatórios e planos de ação

Os relatórios poderão incluir: - Identificação da empresa e avaliação. -
Período e participação. - Resultados gerais e por fator. -
Interpretações configuradas. - Análise técnica e recomendações. -
Gráficos e tabelas. - Histórico/versão do relatório.

Os planos de ação deverão permitir: - Descrição da ação. - Fator
relacionado. - Responsável. - Prazo. - Status. - Evidências ou
observações. - Acompanhamento de eficácia. - Histórico de alterações.

# 13. Arquitetura técnica recomendada

## 13.1 Tecnologias

-   Frontend: Next.js, React e TypeScript.
-   Backend: NestJS e TypeScript.
-   Banco de dados: PostgreSQL via Supabase.
-   Autenticação: Supabase Auth.
-   Validação compartilhada: schemas e contratos tipados.
-   API versionada: `/api/v1`.
-   Monorepo sugerido com pnpm.

Estrutura possível:

``` text
apps/
  web/
  api/
packages/
  contracts/
  schemas/
  config/
  test-utils/
docs/
  architecture/
  database/
  api/
  security/
  business-rules/
  runbooks/
```

A interface atual de protótipo deverá servir como referência visual e
funcional. Regras de negócio, autenticação, autorização, cálculos e
persistência deverão ser implementados de forma real no backend e no
banco.

## 13.2 Módulos de backend sugeridos (Estrutura NestJS)

Para alinhar com a arquitetura do NestJS, cada módulo deve conter seu próprio controller, service e módulo. A estrutura de pastas no `src` deve seguir este padrão:

-   `auth/` (Autenticação e JWT)
-   `tenants/` (Contas de clientes/Multi-tenancy)
-   `users/` (Gestão de usuários e perfis)
-   `access-control/` (Permissões e Roles)
-   `contracts/` (Contratos e Vigências)
-   `payments/` (Registro de pagamentos externos)
-   `companies/` (Empresas, Setores, Departamentos)
-   `question-tools/` (Ferramentas de avaliação e Versões)
-   `questions/` (Questões, Grupos, Fatores)
-   `assessments/` (Avaliações e Configurações)
-   `participants/` (Gestão de participantes)
-   `responses/` (Coleta de respostas e Comentários)
-   `scoring/` (Regras de pontuação e Cálculo)
-   `results/` (Consolidação de resultados)
-   `comparisons/` (Análises comparativas)
-   `reports/` (Geração de relatórios)
-   `action-plans/` (Planos de ação)
-   `notifications/` (Alertas e Notificações)
-   `audit/` (Logs de auditoria administrativa)
-   `common/` (Interceptors, Filters, Guards e Decorators globais)
-   `config/` (Configurações de ambiente e Supabase)
-   `database/` (Configurações de conexão e Repositórios globais)

## 13.3 Entidades/tabelas sugeridas

-   `tenants` ou `client_accounts`
-   `contracts`
-   `payment_records`
-   `profiles`
-   `tenant_memberships`
-   `company_memberships`
-   `roles`
-   `permissions`
-   `role_permissions`
-   `user_role_assignments`
-   `user_preferences`
-   `dashboard_preferences`
-   `tenant_settings`
-   `platform_settings`
-   `companies`
-   `sectors`
-   `departments`
-   `shifts`
-   `assessment_tools`
-   `assessment_tool_versions`
-   `question_groups`
-   `psychosocial_factors`
-   `questions`
-   `question_versions`
-   `response_scales`
-   `response_options`
-   `scoring_rules`
-   `assessments`
-   `assessment_versions`
-   `assessment_questions`
-   `assessment_links`
-   `participants`
-   `responses`
-   `answers`
-   `answer_comments`
-   `calculation_runs`
-   `results`
-   `reports`
-   `action_plans`
-   `action_plan_items`
-   `audit_events`

Os nomes finais podem ser ajustados durante a modelagem, preservando as
responsabilidades e os relacionamentos.

# 14. Segurança, privacidade e auditoria

-   Aplicar autorização no backend em toda operação protegida.
-   Garantir isolamento entre contas de clientes no backend e no banco.
-   Utilizar políticas RLS do PostgreSQL/Supabase quando adequadas.
-   Não confiar apenas na ocultação de telas ou botões.
-   Não expor segredos administrativos no frontend.
-   Proteger links públicos com tokens não previsíveis e regras de
    validade.
-   Validar entradas, permissões, estado da avaliação e vigência
    contratual.
-   Auditar alterações de contratos, pagamentos, status de conta,
    permissões, publicações, exportações e configurações relevantes.
-   Minimizar dados pessoais coletados.
-   Separar dados de identificação das respostas quando o modo anônimo
    exigir.
-   Definir política de retenção, exportação e exclusão de dados.
-   Não excluir automaticamente dados ao suspender uma conta ou expirar
    um contrato.

# 15. Regras de negócio consolidadas

1.  Uma conta de cliente pode conter vários usuários.
2.  Um usuário só acessa dados autorizados para sua conta e escopo.
3.  O pagamento é realizado fora da plataforma e registrado pela
    Administração Geral.
4.  O acesso depende de conta ativa e contrato vigente, respeitando as
    datas.
5.  A renovação deve preservar o histórico contratual.
6.  Não há cobrança automática recorrente nesta versão.
7.  Não há limite de quantidade de empresas por conta no modelo
    definido.
8.  O participante pode responder por link sem possuir conta
    administrativa.
9.  O modo anônimo ou identificado é definido por avaliação.
10. A dashboard é personalizável por usuário.
11. Preferências pessoais não alteram dados compartilhados nem
    permissões.
12. Ferramentas e avaliações publicadas devem ser versionadas.
13. Resultados devem ser calculados por regras configuradas e
    rastreáveis.
14. A suspensão ou expiração bloqueia o acesso conforme a regra
    comercial, sem apagar dados.
15. O comportamento dos links após vencimento/suspensão deve ser
    definido explicitamente.
16. Ações administrativas e alterações críticas devem ser auditadas.

# 16. Plano de implementação sugerido

## Fase 1 --- Fundação

-   Organizar o repositório e ambientes.
-   Definir contratos, schemas e padrões.
-   Configurar PostgreSQL/Supabase e migrations.
-   Configurar CI, lint, testes e build.

## Fase 2 --- Autenticação e contas

-   Implementar login, recuperação e alteração de senha.
-   Criar perfis e memberships.
-   Implementar isolamento multi-tenant.
-   Criar Administração Geral protegida.

## Fase 3 --- Contratos e autorização

-   Criar cadastro de clientes e contratos.
-   Implementar registro manual de pagamento externo.
-   Implementar estados de pagamento, contrato e conta.
-   Implementar liberação, suspensão, expiração e renovação.
-   Registrar auditoria das ações administrativas.

## Fase 4 --- Empresas e usuários

-   Implementar cadastro ilimitado de empresas.
-   Implementar convites, perfis, permissões e vínculos.
-   Implementar Meu Perfil e preferências pessoais.

## Fase 5 --- Banco de Questões

-   Implementar ferramentas, versões, questões, grupos, fatores, escalas
    e regras de cálculo.

## Fase 6 --- Avaliações e links

-   Criar avaliação, publicar versão, gerar links e receber respostas.
-   Implementar modos anônimo/identificado e regras de participação.

## Fase 7 --- Resultados

-   Implementar cálculo, validação, consolidação e resultados por
    empresa/fator.
-   Registrar versões do cálculo e garantir reprodutibilidade.

## Fase 8 --- Dashboard e relatórios

-   Implementar indicadores reais e personalização por usuário.
-   Implementar relatórios, exportações e planos de ação.

## Fase 9 --- Produção

-   Testes de segurança, autorização, isolamento e fluxos contratuais.
-   Backups, monitoramento, logs e alertas.
-   Documentação operacional e política de retenção.
-   Revisão de acessibilidade e experiência de uso.

# 17. Critérios de aceite principais

-   O Administrador Geral consegue cadastrar um cliente, registrar
    pagamento externo e definir vigência.
-   O sistema libera o acesso somente quando as condições de conta e
    contrato forem atendidas.
-   O contrato vencido bloqueia o acesso conforme a regra definida, sem
    apagar dados.
-   O cliente consegue cadastrar empresas sem limite quantitativo.
-   Uma conta de cliente pode ter vários usuários com permissões
    diferentes.
-   Um usuário consegue editar seus dados pessoais e alterar/recuperar a
    senha com segurança.
-   Um usuário consegue personalizar sua dashboard sem afetar outros
    usuários.
-   Participantes conseguem responder por link conforme as regras da
    avaliação.
-   Respostas são mapeadas para questões, fatores e resultados por
    regras configuradas.
-   Clientes não conseguem acessar dados de outras contas.
-   Alterações críticas e ações administrativas são auditáveis.
-   Resultados históricos permanecem vinculados às versões de
    ferramenta, avaliação e cálculo utilizadas.

------------------------------------------------------------------------

**Nota de implementação:** esta documentação consolida os requisitos
funcionais e a arquitetura-alvo. Decisões ainda abertas ---
especialmente a política dos links após vencimento/suspensão, os dados
obrigatórios do contrato e a política de retenção --- deverão ser
formalizadas antes da entrada em produção.
