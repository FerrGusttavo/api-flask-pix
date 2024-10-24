
# API PIX com Flask

Esta API foi desenvolvida utilizando Flask para facilitar a criação e gerenciamento de pagamentos via PIX. Ela permite criar novos pagamentos, confirmar transações e gerar QRCodes para realização de pagamentos. A API também oferece endpoints para consulta de detalhes de pagamentos e recuperação de QRCodes em formato de imagem.

## Rodando localmente

Clone o projeto

```bash
  git clone https://github.com/FerrGusttavo/api-flask-pix.git
```

Entre no diretório do projeto

```bash
  cd api-flask-pix
```

Instale as dependências

```bash
  pip install -r requirements.txt
```

Criando o banco de dados local

```bash
  flask shell
```
```bash
  db.create_all()
```
```bash
  exit()
```

Inicie o servidor

```bash
  python app.py
```


## Documentação da API

#### Criar um novo pagamento

```http
  POST /payments/pix
```

- Cria um novo pagamento no banco de dados.

| Parâmetro (Body)   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `value`      | `float` | **Obrigatório**. Valor do pagamento a ser criado.|

#### Confirmar pagamento


```http
  POST /payments/pix/confirmation
```

- Confirma um pagamento baseado no id do banco e no valor.

| Parâmetro (Body)   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `bank_payment_id`      | `string` | **Obrigatório**. id do pagamento a ser confirmado.|
| `value`      | `float` | **Obrigatório**. Valor do pagamento a ser confirmado.|


#### Retornar página do pagamento em PIX. 

```http
  GET /payments/pix/<payment_id>
```

- Retorna uma página detalhes do pagamento e QRCODE.

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `payment_id`      | `int` | **Obrigatório**. O ID do pagamento. |

#### Retornar imagem QRCODE do pagamento

```http
  GET /payments/pix/qr_code/<qr_code_id>
```

- Retorna a imagem QRCODE de um pagamento específico.

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `qr_code_id`      | `string` | **Obrigatório**. ID do QRCODE gerado a partir da criação do pagamento. |

## Rodando os testes

Para rodar os testes, rode os seguintes comandos

```bash
  cd /tests
```
```bash
  pytest tests.py -v
```
