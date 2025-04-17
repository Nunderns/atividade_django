
# API de Gerenciamento de Produtos e Vendas

API RESTful desenvolvida com Django e Django REST Framework como parte da atividade B1 – CRUD API.

## Tema: E-commerce / Gestão de Estoque

A API gerencia entidades relacionadas a um ambiente de vendas, com controle de produtos, fornecedores, categorias, clientes e pagamentos.

## Tabelas Criadas

| Tabela      | Descrição                               |
|-------------|------------------------------------------|
| Produto     | Informações de produtos com preço, categoria e fornecedor |
| Categoria   | Tipos de produtos (ex: eletrônicos, roupas) |
| Fornecedor  | Dados dos fornecedores responsáveis      |
| Cliente     | Cadastro de clientes                     |
| Pagamento   | Registro de pagamentos com valores e datas |

### Relacionamentos
- Produto tem ForeignKey para Categoria e Fornecedor
- Pagamento tem ForeignKey para Cliente

## Como rodar o projeto

```bash
git clone <repo-url>
cd <pasta-do-projeto>
python -m venv venv
source venv/Scripts/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

## Endpoints Disponíveis

### Produto (/api/produtos/)
| Método | Rota                     | Ação                 |
|--------|--------------------------|----------------------|
| GET    | /api/produtos/           | Lista todos os produtos |
| POST   | /api/produtos/           | Cria um novo produto |
| GET    | /api/produtos/{id}/      | Detalha um produto   |
| PUT    | /api/produtos/{id}/      | Atualiza um produto  |
| DELETE | /api/produtos/{id}/      | Deleta um produto    |

Repete-se a estrutura acima para:
- /api/categorias/
- /api/fornecedores/
- /api/clientes/
- /api/pagamentos/

## Documentação da API

- Swagger UI: http://localhost:8000/swagger/
- Redoc UI: http://localhost:8000/redoc/

## Exemplos de Requisição (Postman)

### Criar Produto

```json
POST /api/produtos/
{
  "nome": "Notebook Dell",
  "preco": 3500.00,
  "categoria": 1,
  "fornecedor": 1
}
```

### Criar Cliente

```json
POST /api/clientes/
{
  "nome": "João Silva",
  "email": "joao@email.com"
}
```

## Validações e Integridade

- Campos obrigatórios validados com required=True
- Chaves estrangeiras validadas com existência (PrimaryKeyRelatedField)
- Emails e nomes únicos (unique=True)
- Preço e valor de pagamento validado para não aceitar negativos
