# 01. Analisando mudanças  

## Introdução à Documentação  
Este documento faz parte da série **"Git e GitHub: dominando controle de versão de código"** e aborda ferramentas essenciais para análise de mudanças em projetos versionados com Git. Os tópicos incluem:  
- Visualização de histórico de commits.  
- Detalhamento de alterações específicas.  
- Comparação entre estados do repositório.  
- Status atual do código e diferenças não registradas.  

O objetivo é auxiliar desenvolvedores a entender e aplicar comandos como `git log`, `git show`, `git status` e `git diff` para gerenciar projetos de forma eficiente.  

---

## Histórico de Commits com `git log`  

### Exibição Básica  
O comando `git log` exibe o histórico de commits, incluindo:  
- **Hash do commit** (identificador único).  
- **Autor** e **data** do commit.  
- **Mensagem** descritiva.  

### Variações Úteis  
- **`git log --oneline`**:  
  Mostra uma lista compacta com hash reduzido e mensagem.  
  Exemplo de saída:  
  ```bash
  abc1234 Removendo foto
  def5678 Atualizando README
  ```

- **`git log -p`**:  
  Exibe detalhes completos de cada commit, incluindo diffs (diferenças nos arquivos).  

- **`git log --graph`**:  
  Apresenta uma visualização gráfica do histórico, útil para entender merges e branches.  

- **`git log --pretty` ou `git log --format`**:  
  Permite personalizar a exibição. Exemplo:  
  ```bash
  git log --pretty=format:"%h - %an: %s"
  ```

### Acesso à Ajuda  
Para explorar opções adicionais:  
```bash
git log --help
```

---

## Detalhamento de Commits com `git show`  

### Visualização de Alterações Específicas  
- **Com hash do commit**:  
  ```bash
  git show abc1234  # Substitua pelo hash desejado
  ```  
  Exibe autor, data, mensagem e alterações realizadas (diff).  

- **Sem hash (último commit)**:  
  ```bash
  git show  # Assume automaticamente o HEAD (último commit)
  ```

### Conceito de `HEAD`  
- **`HEAD`** é um ponteiro que indica o último commit na branch atual.  
- Representa o estado mais recente do repositório local.  

### Acesso à Ajuda  
```bash
git show --help
```

---

## Status do Repositório com `git status`  

### Informações Exibidas  
- Branch atual.  
- Alterações não adicionadas ao stage (`Changes not staged for commit`).  
- Arquivos novos ou modificados.  

### Exemplo de Saída  
```bash
On branch main  
Changes not staged for commit:  
  (use "git add <file>..." to update what will be committed)  
  modified:   app.js
```

---

## Comparação de Diferenças com `git diff`  

### Comparação Básica  
- **Alterações não adicionadas**:  
  ```bash
  git diff
  ```  
  Exibe diferenças entre o estado atual e o último commit.  

- **Entre dois commits**:  
  ```bash
  git diff abc1234..def5678  # Substitua pelos hashes desejados
  ```  

### Após `git add`  
- Após usar `git add`, o `git diff` não mostrará diferenças até o próximo commit.  

---

## Conclusão  
Comandos como `git log`, `git show`, `git status` e `git diff` são fundamentais para analisar mudanças, comparar estados do código e garantir um controle de versão eficiente. Este documento serve como referência para compreender e aplicar essas ferramentas em projetos colaborativos.  

Para mais detalhes sobre comandos específicos, utilize a ajuda integrada do Git (`git <comando> --help`).
