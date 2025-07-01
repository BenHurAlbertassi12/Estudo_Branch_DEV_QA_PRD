````markdown
# Fluxo de Desenvolvimento

Este repositório segue um fluxo simples e funcional baseado em três ambientes principais:

- `dev` → Desenvolvimento (sandbox)
- `qa` → Testes e validação
- `main` → Produção (PRD)

---

## 🔀 Branches

### `dev`
> Ambiente de desenvolvimento livre.

- Aqui nascem novas features e correções.
- Pode ser usada de forma colaborativa.
- Branches de funcionalidade devem partir daqui.

### `qa`
> Ambiente de testes.

- Recebe código estável da `dev`.
- Todas as funcionalidades devem ser testadas e validadas aqui.
- Não permite push direto — alterações devem vir de pull requests.

### `main`
> Produção. Código oficial.

- Contém apenas código validado e aprovado.
- Qualquer alteração precisa passar por `qa` antes.
- Protegida contra push direto.

---

## 🔁 Fluxo de Trabalho

```mermaid
graph TD
    A[Feature Branch] --> B[dev]
    B --> C[qa]
    C --> D[main]
````

1. Crie uma branch a partir da `dev`:

   ```
   git checkout dev
   git checkout -b feat/nome-da-feature
   ```

2. Ao finalizar, abra um Pull Request para `dev`.

3. Após testes locais, crie um PR de `dev → qa`.

4. Equipe de QA valida, testa e aprova.

5. Se estiver tudo certo, cria-se um PR de `qa → main`.

---

## ✅ Regras de Proteção

### `main` (produção)

* ✅ Pull Request obrigatório
* ✅ Aprovação de reviewer
* ✅ Testes automatizados (CI)
* ❌ Push direto proibido

### `qa` (teste)

* ✅ Pull Request obrigatório
* ✅ Testes automatizados
* ❌ Push direto proibido

### `dev` (desenvolvimento)

* ✅ PRs recomendados
* ✅ Push direto permitido (caso necessário)

---

## 🛠️ Nomenclatura de Branches

* `feat/nome-da-feature` → novas funcionalidades
* `fix/nome-do-bug` → correções de bugs
* `hotfix/nome` → correções urgentes em produção
* `refactor/nome` → melhorias internas sem mudança de comportamento

---

## 📦 Exemplo de Pull Request

* Título: `feat: adicionar botão de login`
* Descrição:

  ```
  - Adiciona botão com redirecionamento
  - Integra com API de autenticação
  - Refatora componente Header
  ```

---

## 📌 Importante

* **Nunca altere diretamente a branch `main`.**
* **Todas as alterações devem passar por `qa`.**
* **Sempre use Pull Requests com revisões.**

