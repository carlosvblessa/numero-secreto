
# 04. Gerando Entregas  

## Introdução  
Este documento faz parte da série **"Git e GitHub: dominando controle de versão de código"** e aborda técnicas para criar versões estáveis de projetos utilizando **tags** e **releases** no Git e no GitHub. Como o **quarto material da série**, ele complementa os conceitos de análise de mudanças (documento 01), organização de branches (documento 02) e manipulação de versões (documento 03), focando em como marcar pontos críticos do projeto para facilitar a gestão de entregas.  

---

## Tags no Git  

### O que são Tags?  
- **Tags** são marcadores estáticos que apontam para commits específicos, funcionando como **checkpoints** em um projeto.  
- Úteis para identificar versões do código, como `v1.0.0`, `v2.1.3`, etc.  

### Tipos de Tags  
| **Annotated Tags** | **Unannotated Tags** |  
|---------------------|-----------------------|  
| Contêm metadados (autor, data, mensagem). | São apenas referências simples para commits. |  
| Recomendadas para versões oficiais. | Usadas para marcações temporárias ou internas. |  

### Comandos Básicos  
- **Criar uma tag simples**:  
  ```bash  
  git tag v0.1.0  
  ```  
  Marca o último commit.  

- **Criar uma annotated tag**:  
  ```bash  
  git tag -a v0.2.0 -m "Versão inicial estável"  
  ```  
  O `-a` indica uma tag anotada, e `-m` adiciona uma mensagem.  

- **Listar tags**:  
  ```bash  
  git tag  
  ```  

- **Visualizar detalhes de uma tag**:  
  ```bash  
  git show v0.2.0  
  ```  

- **Apagar uma tag local**:  
  ```bash  
  git tag -d v0.1.0  
  ```  

- **Enviar tags para o GitHub**:  
  - **Tag específica**:  
    ```bash  
    git push origin v0.2.0  
    ```  
  - **Todas as tags**:  
    ```bash  
    git push origin --tags  
    ```  

- **Remover tag do repositório remoto**:  
  ```bash  
  git push origin --delete v0.1.0  
  ```  

---

## Releases no GitHub  

### O que é uma Release?  
- Uma **release** é uma versão oficial de um projeto no GitHub, associada a uma tag.  
- Inclui:  
  - Artefatos (ex.: binários compilados).  
  - Changelogs (lista de alterações).  
  - Notas de lançamento.  

### Como Criar uma Release  
1. **No GitHub**:  
   - Acesse a aba **Releases** do repositório.  
   - Clique em **Draft a new release**.  
   - Selecione a tag criada no Git (ex.: `v0.2.0`).  
   - Adicione título, descrição e arquivos anexos.  
   - Clique em **Publish release**.  

2. **Associar a uma tag existente**:  
   - Se a tag já existe, a release será vinculada automaticamente.  
   - Se não, crie a tag primeiro com `git tag` e envie para o GitHub.  

### Diferenças entre Tags e Releases  
| **Tags** | **Releases** |  
|----------|--------------|  
| Criadas localmente com Git. | Criadas via interface do GitHub. |  
| Podem ser simples ou anotadas. | Incluem metadados e artefatos. |  
| Não exibem changelogs por padrão. | Exibem informações organizadas para usuários finais. |  

---

## Boas Práticas  

1. **Use annotated tags para versões oficiais**:  
   - Documente o propósito da versão com mensagens claras.  

2. **Sincronize tags locais e remotas**:  
   - Sempre envie tags para o GitHub com `git push origin <tag>` ou `git push origin --tags`.  

3. **Crie releases para entregas públicas**:  
   - Inclua changelogs detalhados e links para documentação.  

4. **Mantenha o histórico organizado**:  
   - Remova tags obsoletas localmente e no GitHub.  

5. **Versionamento semântico**:  
   - Siga padrões como `v<major>.<minor>.<patch>` (ex.: `v1.2.3`).  

---

## Conclusão  
O uso de **tags** e **releases** é essencial para gerenciar versões de projetos de forma profissional. Enquanto as tags marcam pontos específicos no histórico do código, as releases no GitHub transformam essas marcações em entregas organizadas para usuários ou equipes. Seguir boas práticas garante transparência, rastreabilidade e facilidade na manutenção do projeto.  

