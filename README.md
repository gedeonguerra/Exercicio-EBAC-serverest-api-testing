# Testes de API — ServeRest (Usuários, Login, Produtos e Carrinhos)

Testes automatizados de API REST para os recursos **Usuários**, **Login**, **Produtos** e **Carrinhos** do [ServeRest](https://serverest.dev/), API pública que simula um e-commerce, usada como referência de prática em automação de testes.

Projeto desenvolvido como exercício do módulo de testes de API da formação EBAC.

---

## Cobertura de testes

**Usuários**
- Positivos: listar todos, cadastrar (dados aleatórios), buscar por ID, atualizar (dados aleatórios), deletar
- Negativos: email duplicado, dados inválidos (campo obrigatório faltando), ID inexistente

**Login**
- Positivo: autenticação com credenciais válidas
- Negativo: autenticação com credenciais inválidas

**Produtos**
- Positivos: cadastrar (dados aleatórios), listar, buscar por ID, atualizar, deletar
- Negativos: nome duplicado, cadastro sem token de autenticação

**Carrinhos**
- Positivos: fluxo completo de compra — cadastro de usuário comprador, login, cadastro de produto, criação de carrinho, listagem, busca por ID e conclusão de compra
- Negativos: produto inexistente, carrinho duplicado (limite de 1 por usuário), cancelamento de compra, criação sem token

**Validações aplicadas em cada request:** status code, corpo da resposta, tipos de dados, mensagens de erro e tempo de resposta (< 300ms).

> Escopo: cobertura completa do CRUD dos recursos `/usuarios`, `/login`, `/produtos` e `/carrinhos` do ServeRest, incluindo o fluxo de ponta a ponta de compra (cadastro → login → carrinho → conclusão/cancelamento).

---

## Stack técnica

- **Postman** — criação e organização da collection
- **Newman** — execução via linha de comando e geração de relatório
- **newman-reporter-htmlextra** — relatório HTML navegável
- **ServeRest** — API alvo, rodando localmente via `npx serverest`

---

## Estrutura do projeto

```
├── collections/
│   └── Exercicio EBAC teste de API.postman_collection.json
├── environments/
│   └── Exercicio EBAC.postman_environment.json
├── reports/                 # Relatório HTML gerado pelo Newman (git-ignored)
└── package.json
```

---

## Como executar

Pré-requisito: Node.js 18+

```bash
# 1. Instalar dependências (Newman, reporter e ServeRest)
npm install

# 2. Rodar tudo com um único comando:
# sobe o ServeRest local, espera a API responder, executa a collection via Newman
# e encerra o servidor ao final
npm test
```

O relatório HTML é gerado em `reports/report.html` — abra o arquivo no navegador para ver o resultado detalhado de cada request e asserção.

**Resultado da execução:**

![Relatório de execução via Newman](./docs/report-screenshot.png)

### Rodando manualmente (opcional)

Se preferir subir o servidor e rodar a collection em terminais separados:

```bash
# Terminal 1 — sobe o ServeRest local em http://localhost:3000
npm run serverest

# Terminal 2 — executa a collection via Newman
npm run newman
```

### Rodando pelo Postman (interface gráfica)

1. Importe `collections/Exercicio EBAC teste de API.postman_collection.json`
2. Importe `environments/Exercicio EBAC.postman_environment.json`
3. Selecione o environment **"Exercicio EBAC"**
4. Suba o ServeRest local (`npx serverest`) e rode a collection pelo **Collection Runner**

---

## Autor

**Gedeon Guerra** — QA Engineer  
[GitHub](https://github.com/gedeonguerra)