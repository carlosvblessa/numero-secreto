
# Organizando o Trabalho

## Introdução  
O Git é uma ferramenta essencial para gestão de projetos colaborativos, permitindo o trabalho em equipe de forma organizada. Este documento aborda conceitos fundamentais sobre branches, mesclagem, rebase e boas práticas para evitar conflitos e otimizar a colaboração.

---

## Colaboração em Equipe e Problemas Comuns  

### 1. Usuário Correto no Git  
- **Importância**: Configurar corretamente o usuário (`git config --global user.name` e `git config --global user.email`) para atribuir commits a quem realizou as alterações.  
- **Problemas ao ignorar**: Commits atribuídos a usuários incorretos podem gerar confusão e dificultar o acompanhamento de responsabilidades.  

### 2. Manter o Repositório Atualizado  
- **Necessidade**: Projetos com múltiplas alterações simultâneas exigem atualizações frequentes do repositório local com o remoto (`git pull`).  
- **Riscos de não atualizar**: Conflitos entre versões locais e remotas, perda de trabalho ou integração inconsistente.  

### 3. Organização em Equipe  
- **Estratégias**:  
  - Dividir tarefas em branches específicos.  
  - Estabelecer padrões de nomenclatura para branches.  
  - Utilizar ferramentas como **Visualizing Git** para compreender o fluxo de commits e branches.  

---

## Branches no Git  

### 1. Criação e Gerenciamento  
- **Criar um branch**:  
  ```bash  
  git branch nova-funcionalidade  
  ```  
- **Renomear um branch**:  
  ```bash  
  git branch -m antigo_nome novo_nome  
  ```  
- **Remover um branch (local)**:  
  ```bash  
  git branch -d nome_branch  
  ```  

### 2. Remover um Branch Remoto  
Para excluir um branch no repositório remoto (como no GitHub), use:  
```bash  
git push origin --delete nome_branch  
```  
**Alternativa (sintaxe antiga)**:  
```bash  
git push origin :nome_branch  
```  
**Importante**:  
- Confirme que o branch foi mesclado antes de deletá-lo.  
- Informe a equipe para evitar perda de trabalho.  

### 3. Alternar entre Branches  
- **Com `git checkout`**:  
  ```bash  
  git checkout nome_branch  
  ```  
- **Com `git switch`** (Git 2.23+):  
  ```bash  
  git switch nome_branch  
  ```  
- **Criar e alternar em um comando**:  
  ```bash  
  git checkout -b nova-funcionalidade  # ou git switch -c nova-funcionalidade  
  ```  

### 4. Fluxo de Trabalho Básico  
1. Verificar status do repositório:  
   ```bash  
   git status  
   ```  
2. Adicionar alterações para commit:  
   ```bash  
   git add nome_arquivo  
   ```  
3. Registrar alterações:  
   ```bash  
   git commit -m "Descrição da alteração"  
   ```  

---

## Mesclagem de Branches (`git merge`)  

### 1. Fast-Forward Merge  
- **Ocorre quando**: A branch principal (`main`) não teve alterações após a criação da branch de funcionalidade.  
- **Resultado**: Histórico linear, sem commit de merge.  
  ```bash  
  git checkout main  
  git merge nova-funcionalidade  
  ```  

### 2. Merge Commit  
- **Ocorre quando**: Ambas as branches têm alterações divergentes.  
- **Resultado**: Cria um commit de merge para unir os históricos.  
  ```bash  
  git checkout main  
  git merge nova-funcionalidade  
  # Resolve conflitos (se necessário) e salva o commit automático  
  ```  

### 3. Limpeza de Branches  
- **Após mesclagem (local e remoto)**:  
  1. Remova o branch local:  
     ```bash  
     git branch -d nova-funcionalidade  
     ```  
  2. Remova o branch remoto (se aplicável):  
     ```bash  
     git push origin --delete nova-funcionalidade  
     ```  

---

## Atualização de Branches com `git rebase`  

### 1. Processo de Rebase  
- **Objetivo**: Integrar atualizações da branch principal (`main`) na branch de desenvolvimento (`nova-funcionalidade`).  
- **Comando**:  
  ```bash  
  git checkout nova-funcionalidade  
  git rebase main  
  ```  
- **Funcionamento**: Reaplica commits da `nova-funcionalidade` após os commits mais recentes da `main`.  

### 2. Rebase vs. Merge  
| **Rebase** | **Merge** |  
|------------|-----------|  
| Histórico linear | Histórico com commit de merge |  
| Reescreve histórico (cuidado com repositórios compartilhados) | Preserva histórico original |  
| Ideal para branches locais | Ideal para integrar branches públicas |  

### 3. Políticas Empresariais  
- Algumas equipes preferem `merge` para preservar o histórico completo, enquanto outras usam `rebase` para manter o histórico limpo.  

---

## Boas Práticas  

1. **Use branches para cada tarefa**: Isola alterações e facilita testes.  
2. **Atualize regularmente**: `git pull` antes de iniciar o trabalho e durante desenvolvimento longo.  
3. **Escolha entre merge e rebase com critério**:  
   - Use `rebase` para branches locais não compartilhadas.  
   - Use `merge` para integrar branches colaborativas.  
4. **Limpe branches obsoletos (locais e remotos)**: Mantém o repositório organizado.  
5. **Configure usuário corretamente**:  
   ```bash  
   git config --global user.name "Seu Nome"  
   git config --global user.email "seu@email.com"  
   ```  

---

## Conclusão  
Dominar o Git é essencial para colaboração eficiente. O uso estratégico de branches, mesclagem e rebase permite integrar alterações sem comprometer o histórico do projeto. Seguir boas práticas evita conflitos, garante transparência no trabalho em equipe e facilita a manutenção do repositório.  

