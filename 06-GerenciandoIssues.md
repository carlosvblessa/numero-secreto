# 06. Gerenciando Issues  

## Introdução  
Este documento faz parte da série **"Git e GitHub: dominando controle de versão de código"** e aborda técnicas para gerenciar **issues** (problemas, tarefas ou melhorias) no GitHub. Como o **sexto material da série**, ele complementa os conceitos de colaboração (documentos 02 e 05), focando em como planejar, organizar e resolver demandas de forma integrada ao fluxo de trabalho Git.  

---

## O que são Issues no GitHub?  
- **Issues** são ferramentas do GitHub para registrar problemas, solicitações de recursos, bugs ou qualquer tarefa relacionada ao projeto.  
- Funcionam como um sistema de gerenciamento de tarefas, permitindo discussões, atribuição de responsáveis, priorização e rastreamento de progresso.  

---

## Criar e Gerenciar Issues  

### 1. Onde Criar Issues  
- **Apenas no GitHub**:  
  - As issues são criadas e gerenciadas exclusivamente pela interface do GitHub.  
  - Não há suporte nativo para criar issues via linha de comando com o Git tradicional.  

- **Ferramentas Alternativas via CLI**:  
  - **GitHub CLI (`gh`)**: Permite criar e gerenciar issues pelo terminal.  
    Exemplo para criar uma issue:  
    ```bash  
    gh issue create --title "Erro na validação do formulário" --body "O formulário não valida campos vazios."  
    ```  
  - **API do GitHub**: Para automações avançadas, use scripts com a API REST ou GraphQL do GitHub.  

### 2. Estrutura de uma Issue  
- **Título**: Descrição clara do problema ou tarefa.  
- **Descrição**: Detalhes sobre o contexto, passos para reproduzir (em bugs), requisitos (em funcionalidades), etc.  
- **Labels**: Etiquetas para categorizar (ex.: `bug`, `feature`, `urgente`).  
- **Milestone**: Vincula a issue a um marco do projeto (ex.: versão `v1.0`).  
- **Assignees**: Define colaboradores responsáveis.  
- **Comments**: Discussões e atualizações sobre a issue.  

---

## Vincular Issues a Branches  

### 1. Criar Branch Diretamente de uma Issue (GitHub UI)  
O GitHub permite criar branches diretamente a partir da página de uma issue, facilitando o fluxo de trabalho.  

#### Passos:  
1. **Acesse a issue**:  
   - Navegue até a issue desejada no repositório.  
2. **Na barra lateral direita**, em **Desenvolvimento**, clique em **Create a branch**.

   * Se a issue já tiver uma branch ou pull request vinculada, selecione-a e, em seguida, clique em **Create a branch**.
3. **Defina o nome da branch**:  
   - O GitHub sugere um nome baseado no título da issue (ex.: `issue-7`).  
   - Edite o nome se necessário.  
4. **Crie a branch localmente**:  
   ```bash  
   git switch -c <nome-da-branch>  
   ```  
5. **Faça alterações e commits**:  
   ```bash  
   git add .  
   git commit -m "Implementação para #<número-da-issue>"  
   ```  
6. **Envie a branch para o GitHub**:  
   ```bash  
   git push origin <nome-da-branch>  
   ```  
7. **Abra um Pull Request**:  
   - O GitHub detectará automaticamente a branch e criará um PR vinculado à issue.  

---

### 2. Associar uma Branch Existente a uma Issue  
Se já houver uma branch criada anteriormente, siga estes passos:  

#### Via GitHub UI:  
1. **Acesse a issue**:  
   - Navegue até a issue desejada.  
2. **Vincule o PR à issue**:  
   - Clique em **Linked pull requests** > **Search pull requests**.  
   - Selecione a branch ou PR existente na lista.  

#### Via Commit/Pull Request:  
- Use palavras-chave como `Fixes #123` ou `Closes #123` no commit ou descrição do PR.  
  Exemplo:  
  ```bash  
  git commit -m "Corrigir validação de campos. Fixes #123"  
  ```  
Palavras-chave válidas: `close`, `closes`, `closed`, `fix`, `fixes`, `fixed`, `resolve`, `resolves`, `resolved`.  

---

### Exemplo Prático  
Suponha que você tenha uma issue chamada **"Erro na autenticação" (#7)**.  
1. **Criar branch diretamente da issue**:  
   - No GitHub, clique em **create a branch** e escolha o nome `resolve-auth-error`.  
2. **Trabalhar localmente**:  
   ```bash  
   git switch -c resolve-auth-error  
   # Faça suas alterações...  
   git add .  
   git commit -m "Corrigir erro de autenticação. Closes #7"  
   git push origin resolve-auth-error  
   ```  
3. **Abrir PR**:  
   - O GitHub gerará automaticamente um PR vinculado à issue #7.  
4. **Fechar a issue**:  
   - Ao mesclar o PR, a issue será fechada automaticamente.  

---

## Atribuir e Organizar Issues  

### 1. Atribuir Responsáveis  
- **Atribuir Colaboradores**:  
  - No GitHub, clique em **Assignees** na issue e selecione um ou mais colaboradores.  
- **Atribuição Automática (via GitHub Actions)**:  
  - Use workflows para atribuir automaticamente issues com base em labels ou áreas do código.  

### 2. Priorizar e Classificar  
- **Labels**:  
  - Crie labels personalizadas para categorizar issues (ex.: `alta prioridade`, `documentação`, `dependência`).  
- **Milestones**:  
  - Vincule issues a milestones para organizar por versão, sprint ou objetivo.  
- **Project Boards**:  
  - Use quadros Kanban (To Do, In Progress, Done) para visualizar o progresso das issues.  

---

## Resolver Issues com Branches  

### 1. Fluxo Completo  
1. **Criar Branch**:  
   ```bash  
   git switch -c resolver-issue-123  
   ```  
2. **Implementar Solução**:  
   - Faça alterações e commits relacionados à issue.  
3. **Testar e Validar**:  
   - Garanta que a solução resolve o problema descrito.  
4. **Abrir Pull Request**:  
   - Associe o PR à issue e solicite revisões.  
5. **Mesclar e Fechar**:  
   - Após revisão aprovada, o PR fecha a issue automaticamente (se configurado).  

### 2. Fechar Issues Manualmente  
- Se a issue não for resolvida via código, feche-a manualmente no GitHub clicando em **Close issue**.  

---

## O que são Milestones no GitHub?  

### Definição  
- **Milestones** (marcos) são utilizados para agrupar **issues e Pull Requests (PRs)** em objetivos maiores, como lançamentos de versões, sprints ou eventos específicos.  
- Funcionam como **metas com prazos**, ajudando a organizar o trabalho em etapas mensuráveis.  

### Exemplo Prático  
Imagine que você está desenvolvendo um aplicativo e planeja lançar a versão `v1.0`. Você pode criar um **milestone chamado "v1.0 - Lançamento Inicial"** e vincular todas as issues e PRs relacionadas a essa versão.  

---

## Principais Funcionalidades dos Milestones  

| **Funcionalidade** | **Descrição** |  
|---------------------|---------------|  
| **Agrupamento de Issues/PRs** | Vincule múltiplas tasks a um objetivo comum (ex.: "Versão 2.0", "Sprint 1"). |  
| **Prazo (Due Date)** | Defina datas limite para concluir o milestone. |  
| **Progresso Automático** | O GitHub mostra uma barra de progresso com base nas issues fechadas. |  
| **Integração com Project Boards** | Use quadros Kanban para visualizar o progresso do milestone. |  

---

## Como Criar e Gerenciar Milestones  

### 1. Criar um Milestone  
1. No repositório do GitHub, clique na aba **Issues** ou **Pull Requests**.  
2. No menu lateral, clique em **Milestones** > **Create a milestone**.  
3. Preencha:  
   - **Title**: Nome do milestone (ex.: `v1.0`, `Sprint 3`).  
   - **Description** (opcional): Descrição detalhando o objetivo.  
   - **Due Date**: Data limite para conclusão.  
4. Clique em **Create milestone**.  

### 2. Vincular Issues/PRs a um Milestone  
- **Ao criar uma issue/PR**:  
  - No formulário, selecione o milestone desejado no campo **Milestone**.  
- **Editar uma issue/PR existente**:  
  - Na sidebar da issue/PR, clique em **Edit** e selecione o milestone.  

### 3. Visualizar e Acompanhar  
- Acesse **Milestones** no repositório para ver:  
  - Quantas issues/PRs estão abertas e fechadas.  
  - A barra de progresso.  
  - A data limite.  

---

## Exemplo de Uso de Milestones  

### Cenário: Lançamento da Versão `v1.0`  
1. **Criar o milestone**:  
   - Título: `v1.0 - Lançamento Inicial`  
   - Prazo: `30/11/2023`  
2. **Vincular issues/PRs**:  
   - Issue #123: "Criar tela de login"  
   - Issue #124: "Implementar autenticação"  
   - PR #125: "Corrigir validação de formulário"  
3. **Acompanhar**:  
   - A barra de progresso mostrará quantas tasks foram concluídas.  
   - Se a data limite se aproximar, a equipe pode priorizar as tasks restantes.  

---

## Boas Práticas para Usar Milestones  

1. **Use para Objetivos Claros**:  
   - Ex.: Versões (`v1.0`, `v2.1`), eventos (`Hackathon 2023`), ou sprints (`Sprint 1`).  
2. **Defina Prazos Realistas**:  
   - Evite prazos muito curtos que possam sobrecarregar a equipe.  
3. **Atualize Regularmente**:  
   - Adicione ou remova issues/PRs conforme o escopo mudar.  
4. **Combine com Labels**:  
   - Use labels como `urgente` ou `documentação` para categorizar issues dentro do milestone.  
5. **Feche Milestones Concluídos**:  
   - Após finalizar todas as tasks, marque o milestone como **Closed**.  

---

## Vantagens de Usar Milestones  

- **Organização**: Agrupa tasks em objetivos maiores, facilitando o planejamento.  
- **Transparência**: Mostra claramente o que foi concluído e o que falta.  
- **Motivação**: A barra de progresso ajuda a equipe a visualizar o avanço.  
- **Priorização**: Permite focar em tasks essenciais para atingir o objetivo.  

---

## Boas Práticas  

1. **Issue Pequena e Focada**:  
   - Evite issues genéricas (ex.: "Melhorar performance"). Divida em tarefas específicas.  
2. **Descrição Clara**:  
   - Explique o problema, inclua passos para reproduzir (em bugs) e links relevantes.  
3. **Use Labels e Milestones**:  
   - Facilita filtrar e organizar issues.  
4. **Atualize Regularmente**:  
   - Comente sobre o progresso ou bloqueios.  
5. **Automatize Processos**:  
   - Use GitHub Actions para atribuir labels, responsáveis ou atualizar quadros automaticamente.  

---

## Conclusão  
O uso eficaz de **issues** e **milestones** no GitHub é essencial para planejar, rastrear e resolver demandas em projetos colaborativos. Ao vincular issues a branches, PRs e milestones, é possível garantir transparência e alinhar desenvolvimento com as necessidades do projeto. Seguir boas práticas ajuda a manter o repositório organizado e facilita a colaboração em equipe.  


