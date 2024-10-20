# FlaskPixShop

Este código implementa uma aplicação web usando Flask, que permite gerenciar produtos e realizar pagamentos através do Mercado Pago usando o método de pagamento PIX. Abaixo está uma descrição detalhada das funcionalidades:

### Descrição do Projeto

Este projeto é uma aplicação web em Python usando Flask que permite a criação e gestão de uma lista de produtos, além de realizar pagamentos via PIX utilizando a API do Mercado Pago. A aplicação inclui as seguintes funcionalidades:

- **Adicionar produtos**: Na página principal, o usuário pode adicionar produtos informando o nome, a quantidade e o preço. Os produtos são armazenados em um dicionário em memória.
- **Incrementar e decrementar quantidade**: A aplicação permite aumentar ou diminuir a quantidade de cada produto de forma individual.
- **Deletar produtos**: Os produtos também podem ser removidos da lista.
- **Realizar pagamento**: Através da página de compra, o usuário pode selecionar um produto e realizar o pagamento via PIX.
- **Geração de QR Code**: Quando um pagamento é iniciado, um QR Code é gerado para que o usuário possa realizar o pagamento via PIX.
- **Validação do pagamento**: A aplicação verifica o status do pagamento através da API do Mercado Pago e, se aprovado, desconta a quantidade do produto correspondente.
- **Interface de usuário**: A aplicação utiliza templates HTML para renderizar as páginas e exibir os produtos e os QR Codes de pagamento.

### Tecnologias e Bibliotecas

- **Flask**: Framework web utilizado para criar as rotas e renderizar os templates.
- **Mercado Pago SDK**: Utilizado para integração com a API do Mercado Pago e realizar pagamentos.
- **qrcode**: Biblioteca para gerar o QR Code do pagamento via PIX.
- **Requests**: Utilizado para realizar requisições HTTP e validar o status dos pagamentos.
- **Random e Secrets**: Usados para gerar IDs de pagamento aleatórios para idempotência.

### Estrutura do Código

- **Rota `/`**: Página inicial onde os produtos podem ser adicionados. Exibe a lista de produtos cadastrados.
- **Rota `/increment/<id>`**: Incrementa a quantidade do produto especificado.
- **Rota `/desincrement/<id>`**: Decrementa a quantidade do produto especificado.
- **Rota `/deletar/<id>`**: Remove um produto da lista.
- **Rota `/comprar`**: Exibe a lista de produtos disponíveis para compra.
- **Rota `/comprar/pagamento/<id>`**: Inicia o processo de pagamento para um produto específico. Gera um QR Code para o pagamento via PIX e exibe na tela.
- **Rota `/comprar/validarpagamento/<id>`**: Valida o status do pagamento utilizando a API do Mercado Pago e atualiza a quantidade do produto caso o pagamento seja aprovado.

### Requisitos

- Python 3.x
- Flask
- Mercado Pago SDK
- qrcode
- Requests

### Como Executar

1. Clone este repositório.
2. Instale as dependências usando `pip install -r requirements.txt`.
3. Defina as variáveis `token_mp` e `email_payer` no arquivo `config.py` para a integração com o Mercado Pago.
4. Execute o servidor com o comando:
   ```bash
   python app.py
   ```
5. Acesse `http://127.0.0.1:5000` no seu navegador para usar a aplicação.

### Observações

- O valor dos produtos e suas quantidades são armazenados em um dicionário em memória, sendo resetados a cada reinício do servidor.
- Certifique-se de que os detalhes de autenticação para a API do Mercado Pago estão corretos para evitar problemas na validação dos pagamentos.
- Os QR Codes gerados são salvos na pasta `static` para serem exibidos no frontend durante o processo de pagamento.
