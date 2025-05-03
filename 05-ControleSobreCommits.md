# 05. Controle sobre Commits  

## Introdução  
Este documento faz parte da série **"Git e GitHub: dominando controle de versão de código"** e aborda técnicas avançadas para gerenciar commits entre branches, com foco em comandos como `git cherry-pick` e `git blame`. Como o **quinto material da série**, ele complementa os conceitos de análise de mudanças (documento 01), organização de branches (documento 02) e manipulação de versões (documento 03), destacando como reaproveitar alterações e rastrear responsabilidades no código.  

---

## Reaproveitando Commits com `git cherry-pick`  

### Contexto de Uso  
- **Problema**: Duas equipes trabalham em funcionalidades distintas, mas precisam de uma mesma modificação (ex.: criação de uma tabela no banco de dados).  
- **Solução**: Usar `git cherry-pick` para aplicar um commit específico de uma branch em outra, evitando conflitos e duplicidade de código.  

### Fluxo de Trabalho  
1. **Criar branches**:  
   ```bash  
   git switch -c funcionalidade1  
   git switch -c funcionalidade2  
   ```  

2. **Realizar commits na `funcionalidade2`**:  
   ```bash  
   echo "<h1>Bem-vindo ao Jogo!</h1>" > index.html  
   git add index.html  
   git commit -m "Adicionando título na funcionalidade2"  

   echo "<title>Jogo JS</title>" >> index.html  
   git add index.html  
   git commit -m "Atualizando meta tag na funcionalidade2"  
   ```  

3. **Identificar o hash do commit desejado**:  
   ```bash  
   git log funcionalidade2  
   # Exemplo de saída: abc1234 Adicionando título na funcionalidade2  
   ```  

4. **Aplicar o commit na `funcionalidade1`**:  
   ```bash  
   git switch funcionalidade1  
   git cherry-pick abc1234  
   ```  

5. **Verificar alterações aplicadas**:  
   ```bash  
   git log  
   cat index.html  
   ```  

6. **Mesclar branches na `main`**:  
   ```bash  
   git switch main  
   git merge funcionalidade1  
   git merge funcionalidade2  
   git push origin main  
   ```  

### Vantagens  
- **Reaproveitamento de código**: Evita copiar manualmente alterações.  
- **Histórico claro**: Mantém o rastro do commit original.  

---

## Rastreando Alterações com `git blame`  

### Contexto de Uso  
- **Objetivo**: Identificar quem fez alterações em cada linha de um arquivo, útil para entender o contexto de um código ou esclarecer dúvidas.  

### Comandos Básicos  
- **Visualizar autores por linha**:  
  ```bash  
  git blame script.js  
  ```  
  Exemplo de saída:  
  ```
  abc1234 (João Silva 2023-10-01) console.log("Hello World");
  def5678 (Maria Souza 2023-10-02) // Atualização crítica
  ```  

- **Localizar o commit original de uma linha**:  
  ```bash  
  git blame -L 10,15 index.html  
  # Mostra detalhes da linha 10 à 15  
  ```  

- **Detalhar um commit específico**:  
  ```bash  
  git show abc1234  
  ```  

### Uso em IDEs  
- **Visual Studio Code**:  
  - Extensões como **GitLens** ou **Git Blame** exibem informações diretamente no editor.  
- **Outras IDEs**:  
  - Funcionalidades semelhantes estão disponíveis via plugins ou menus integrados.  

### Boas Práticas  
- **Evite julgamentos**: O nome `blame` pode levar a usos negativos (ex.: culpar alguém por bugs). Use a ferramenta para fins colaborativos.  
- **Combine com `git log`**: Para entender o histórico completo de alterações.  

---

## Boas Práticas  

1. **Use `cherry-pick` com cuidado**:  
   - Apenas para commits independentes. Evite aplicar alterações que dependem de outros commits.  

2. **Documente mudanças críticas**:  
   - Use mensagens claras nos commits para facilitar a leitura com `git blame`.  

3. **Mantenha o histórico linear**:  
   - Prefira `rebase` para branches locais e `merge` para integrações colaborativas.  

4. **Versionamento semântico**:  
   - Siga padrões como `v<major>.<minor>.<patch>` (ex.: `v1.2.3`).  

5. **Revise código antes de mesclar**:  
   - Use `git diff` ou ferramentas visuais para validar alterações.  

---

## Conclusão  
Dominar comandos como `git cherry-pick` e `git blame` é essencial para gerenciar projetos colaborativos de forma eficiente. Enquanto o `cherry-pick` permite reaproveitar alterações entre branches, o `blame` ajuda a rastrear responsabilidades e entender o contexto do código. Seguir boas práticas garante transparência e evita conflitos no desenvolvimento em equipe.  

