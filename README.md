# Food delivery MVP

`Serviço de Entrega de Comida` é uma aplicação de Produto Mínimo Viável (MVP) de uma plataforma online de pedidos e entrega de comida baseada no iFood.</br>

## Resumo
- [1. Requisitos](#1-requisitos)
- [2. Instalação](#2-instalação)
    - [2.1. Backend](#21-backend)
    - [2.2. Frontend](#22-frontend)
- [3. Rotas](#3-rotas)
- [4. Filtros](#4-filtros)
- [5. Como contribuir para este projeto?](#5-como-contribuir-para-este-projeto)
- [6. Como relatar um bug ou solicitar um recurso?](#6-como-relatar-um-bug-ou-solicitar-um-recurso)
## 1. Requisitos:
* Backend
    * Ruby 2.7.3
    * Rails 6.1.3
    * SQLite
* Frontend
    * React
    * TypeScript
    * Vite
    * Yarn

## 2. Instalação:
Clone o repositório

### 2.1. Backend

Instale as dependências usando Yarn ou NPM:

```bash
cd backend && bundle install

rails db:create

rails db:migrate

rails s
```

### 2.2. Frontend

```bash

cd frontend && yarn install

yarn dev
```

### 3. Rotas da API
**OBS.:** Todas as informações de rota foram documentadas com Swagger UI e podem ser encontradas na rota `/api-docs`

| Prefixo            | Verbo | Padrão da URI                          | Controlador#Ação                  |
|--------------------|-------|---------------------------------------|----------------------------------|
| categorias         | GET   | `/api/categorias(.:formato)`         | categorias#index {:formato=>:json} |
| restaurantes       | GET   | `/api/restaurantes(:formato)`         | restaurantes#index {:formato=>:json} |
| restaurante        | GET   | `/api/restaurantes/:id(.:formato)`    | restaurantes#show {:formato=>:json} |
| pedidos            | POST  | `/api/pedidos(.:formato)`             | pedidos#criar {:formato=>:json} |
| pedido             | GET   | `/api/pedidos/:id(.:formato)`         | pedidos#show {:formato=>:json} |
| cidades_disponiveis| GET   | `/api/cidades_disponiveis(.:formato)` | cidades_disponiveis#index {:formato=>:json} |

**POST -> Pedidos**

```json
{
    "pedido":{
        "nome": "São José Alves",
        "telefone": "22912345678",
        "id_do_restaurante": 1,
        "cidade": "Pará",
        "rua": "São João",
        "bairro": "Pitanguia",
        "número": "133",
        "complemento": "casa 4",
        "atributos_de_produtos_do_pedido": [
            { "quantidade": 1, "id_do_produto": 1 },
            { "quantidade": 9, "id_do_produto": 2 }
        ]
    }
}
```

### 4. Filtros

Para aplicar filtros às consultas, você pode usar o seguinte comando no terminal:

```bash
curl http://localhost:3000/api/restaurantes?
    q=bravo             # filtrar por consulta
    &cidade=Para        # filtrar por cidade
    &categoria=mexicana  # filtrar por categoria
```
