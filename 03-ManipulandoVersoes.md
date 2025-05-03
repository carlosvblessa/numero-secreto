# ManipulandoVersões

## Introdução  
O Git oferece ferramentas poderosas para manipulação de versões, permitindo que você gerencie alterações temporárias, reverta estados e mantenha o histórico do projeto organizado. Este documento aborda comandos essenciais como `git stash` e `git restore`, além de boas práticas para utilizá-los de forma eficaz.

---

## Git Stash: Armazenamento Temporário de Alterações  

### Contexto de Uso  
- **Problema**: Interrupção de uma tarefa em andamento (ex.: desenvolvimento de uma nova funcionalidade) para resolver um bug urgente, sem poder fazer um commit por conta de código inválido.  
- **Solução**: Usar `git stash` para guardar alterações temporariamente.  

### Comandos Básicos  
- **Guardar alterações**:  
  ```bash  
  git stash  
  ```  
  Ou com uma descrição:  
  ```bash  
  git stash save "Descrição da alteração"  
  ```  

- **Listar stashes armazenadas**:  
  ```bash  
  git stash list  
  ```  

- **Aplicar uma stash**:  
  ```bash  
  git stash apply  # Aplica a última stash sem removê-la  
  git stash apply stash@{1}  # Aplica uma stash específica  
  ```  

- **Aplicar e remover uma stash**:  
  ```bash  
  git stash pop  # Aplica e remove a última stash  
  git stash pop stash@{1}  # Aplica e remove uma stash específica  
  ```  

- **Remover uma stash sem aplicar**:  
  ```bash  
  git stash drop  # Remove a última stash  
  git stash drop stash@{1}  # Remove uma stash específica  
  ```  

- **Limpar todas as stashes**:  
  ```bash  
  git stash clear  
  ```  

### Pilha de Modificações  
- As stashes são armazenadas em uma pilha (stack), onde o último item adicionado é o primeiro a ser recuperado (**LIFO - Last In, First Out**).  

---

## Git Restore: Desfazendo Alterações  

### Restaurar Arquivos para o Estado do Último Commit  
- **Desfazer alterações em um arquivo específico**:  
  ```bash  
  git restore index.html  
  ```  
  Equivalente a:  
  ```bash  
  git restore --source=HEAD index.html  
  ```  

- **Desfazer alterações em todos os arquivos**:  
  ```bash  
  git restore .  
  ```  

### Restaurar para um Estado Específico de um Commit Anterior  
- **Usando o hash de um commit**:  
  ```bash  
  git restore --source=<hash_commit> index.html  
  ```  
  Exemplo:  
  ```bash  
  git restore --source=abc1234 index.html  
  ```  

### Manipular a "Staging Area"  
- **Remover um arquivo da staging area sem perder alterações**:  
  ```bash  
  git restore --staged app.js  
  ```  

### Diferenças entre `git restore` e `git checkout`  
| **git restore** | **git checkout** |  
|------------------|------------------|  
| Focado em restaurar arquivos ou a staging area | Usado para alternar branches e revisar histórico |  
| Mais intuitivo para desfazer alterações | Requer cuidado para não alterar histórico acidentalmente |  

---

## Boas Práticas  

1. **Git Stash**:  
   - Sempre adicione descrições às stashes para facilitar a identificação.  
   - Limpe stashes obsoletas com `git stash clear` para evitar acúmulo.  
   - Use `git stash pop` para aplicar e remover stashes automaticamente.  

2. **Git Restore**:  
   - Confirme o estado atual do repositório com `git status` antes de restaurar arquivos.  
   - Use `git restore --staged` para corrigir erros no `git add`.  
   - Seja cauteloso ao restaurar para commits antigos, garantindo que não haja perda de trabalho importante.  

3. **Gestão de Versões**:  
   - Marque pontos importantes do projeto com commits claros e descritivos.  
   - Mantenha branches organizados e remova branches e stashes desnecessárias.  

---

## Conclusão  
O domínio de comandos como `git stash` e `git restore` é fundamental para manipular versões de forma eficiente. Eles permitem salvar alterações temporárias, reverter estados e manter o repositório organizado. Seguir boas práticas evita erros críticos e garante um fluxo de trabalho mais produtivo e seguro.  

