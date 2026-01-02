# Testes de API - ServeRest (Usuários)

## 📋 Sobre
Projeto de testes automatizados de API REST para a funcionalidade de Usuários do ServeRest - Exercício Módulo 13.

## 🛠️ Tecnologias
- Node.js
- Postman
- ServeRest

## 🚀 Como Executar

### 1. Instalar e iniciar o ServeRest
```bash
npm install -g serverest
npx serverest
```

### 2. Importar no Postman
1. Importe `ServeRest_Usuarios.postman_collection.json`
2. Importe `ServeRest_Local.postman_environment.json`
3. Selecione o environment "Exercicio EBAC"

### 3. Executar
- Run Collection 

## 📊 Cenários Cobertos

### Positivos (5)
- Listar todos os usuários
- Cadastrar Usuário usando random
- Buscar Usuário por ID
- Atualizar Usuário usando random
- Deletar usuário

### Negativos (3)
- Email duplicado
- Dados Inválidos (Campo Obrigatório Faltando)
- ID inexistente

## ✅ Validações
- Status codes
- Response body
- Tipos de dados
- Mensagens de erro
- Tempo de resposta

## 👤 Autor
[Gedeon Guerra QA Enginner]