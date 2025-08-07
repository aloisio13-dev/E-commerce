# E-commerce
Vendas de produtos 

Repositório desenvolvido para conclusao de exercicio de aulas sobre   Modelagem de DB  utilizando o diagrama para Entidade e Atributos sobre a  Plataforma DRAW.IO , não executado a criação deste db , 
### 🧩 Entidades Principais e Atributos

#### 👤 Cliente
- **ID_Cliente** (PK)
- **Nome**
- **Tipo** (PF ou PJ — restrição: apenas um)
- **CPF/CNPJ**
- **Endereço** (usado para cálculo do frete)

#### 📦 Produto
- **ID_Produto** (PK)
- **Nome**
- **Descrição**
- **Preço**
- **Fornecedor_ID** (FK)
- **Plataforma_ID** (FK)

#### 🧾 Pedido
- **ID_Pedido** (PK)
- **Data_Pedido**
- **Status_Entrega**
- **Endereço_Entrega**
- **Cliente_ID** (FK)
- **Pode_Cancelar** (booleano)
- **Data_Devolucao_Permitida** (prazo para devolução)

#### 💸 Pagamento
- **ID_Pagamento** (PK)
- **Pedido_ID** (FK)
- **Tipo_Pagamento** (ex: cartão, boleto, pix)
- **Status_Pagamento**
- **Valor**

#### 🚚 Entrega
- **ID_Entrega** (PK)
- **Pedido_ID** (FK)
- **Status**
- **Código_Rastreio**

#### 🏪 Fornecedor
- **ID_Fornecedor** (PK)
- **Nome**
- **Contato**

#### 📦 Estoque
- **ID_Estoque** (PK)
- **Produto_ID** (FK)
- **Quantidade_Disponível**

#### 🛍️ Plataforma
- **ID_Plataforma** (PK)
- **Nome**
- **Descrição**

---

### 🔗 Relacionamentos

| Entidade A     | Relacionamento            | Entidade B      | Descrição                                                              |
|----------------|---------------------------|------------------|-------------------------------------------------------------------------|
| Cliente        | 1:N                        | Pedido           | Um cliente pode fazer vários pedidos                                   |
 |Cliente        | 1:N                        | Endereço        | Um cliente pode ter varios endereços
| Pedido         | N:N (via Pedido_Produto)  | Produto          | Um pedido pode ter vários produtos e vice-versa                        |
| Produto        | N:1                        | Fornecedor       | Cada produto possui um fornecedor específico                          |
| Produto        | N:1                        | Plataforma       | Vendido por apenas uma plataforma                                      |
| Pedido         | 1:N                        | Pagamento        | Cada pedido pode ter várias formas de pagamento                        |
| Pedido         | 1:1                        | Entrega          | Cada pedido possui uma entrega associada                               |
| Produto        | 1:N                        | Estoque          | Cada produto possui seu controle de estoque                            |
