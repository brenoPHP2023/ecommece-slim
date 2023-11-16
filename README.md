# Projeto E-commerce

Template usado no projeto [Almsaeed Studio](https://almsaeedstudio.com)

## Visão Geral

O projeto consiste na implementação de um sistema de administração para uma loja virtual, com foco em funcionalidades essenciais, como autenticação, gerenciamento de produtos, e processo de compra. Embora o projeto seja apresentado como de "alto nível", os alunos são incentivados a aprofundar seus conhecimentos em conceitos-chave, como orientação a objetos e uso do PDO, conforme necessário.

## Descrição do Projeto

O projeto proposto visa criar um sistema de administração para uma loja virtual usando a linguagem de programação PHP. A abordagem é prática, permitindo aos alunos aplicar os conceitos aprendidos durante o curso de maneira concreta. Aqui estão os principais aspectos do projeto:

## Funcionalidades

Autenticação de Login:

Implementação de um sistema seguro de autenticação de login para garantir o acesso restrito apenas a usuários autorizados.
Utilização de boas práticas de segurança para proteger as informações de login.
CRUD de Produtos:

Desenvolvimento de operações CRUD (Create, Read, Update, Delete) para gerenciamento de produtos.
Criação de novos produtos, visualização detalhada, edição de informações existentes e exclusão de produtos do banco de dados.
Sistema de Carrinho de Compras:

Adição de funcionalidades de carrinho de compras para permitir que os clientes selecionem produtos para compra.
Atualização dinâmica do carrinho à medida que os produtos são adicionados ou removidos.
Processo de Compra:

Implementação de um fluxo de compra completo, desde a seleção de produtos até o fechamento do pedido.
Geração de um boleto bancário como método de pagamento.
Segurança e Boas Práticas:

Incorporação de práticas de segurança, como prevenção contra injeção de SQL e manipulação de sessões para garantir uma experiência segura aos usuários.
Utilização de orientação a objetos para organizar e estruturar o código de maneira eficiente e modular.
Flexibilidade para Expansão:

Encorajamento aos alunos para explorar e expandir o projeto além do básico fornecido.
Possibilidade de adicionar novas funcionalidades, criar relatórios ou melhorar a interface administrativa.
Aprendizado Contínuo:

Conscientização de que o projeto não cobrirá todos os detalhes durante a execução, incentivando os alunos a revisitar as seções relevantes do curso conforme necessário.
Atualizações Futuras:

Compromisso de continuar atualizando o curso com novas aulas, dicas e informações para manter os alunos informados sobre as práticas mais recentes em PHP.

## Tecnologias Utilizadas

PHP (Hypertext Preprocessor):

A linguagem de programação principal para o desenvolvimento do back-end.
HTML/CSS:

Para a marcação e estilização das páginas web, respectivamente.
JavaScript:

Pode ser usado para aprimorar a interatividade do lado do cliente, especialmente no contexto de um carrinho de compras dinâmico.
MySQL (ou outro Sistema de Gerenciamento de Banco de Dados):

Banco de dados para armazenar informações relacionadas a produtos, usuários e transações.
PDO (PHP Data Objects):

Para interagir com o banco de dados de maneira segura e eficiente.
Orientação a Objetos em PHP:

Provavelmente será usada extensivamente para organizar o código de maneira modular e reutilizável.
Boas Práticas de Segurança:

Implementação de práticas de segurança, como preparação de consultas SQL para prevenir injeções de SQL e manipulação segura de sessões para autenticação.

## Observação
Sucede que por uma brecha de segurança a função get_magic_quotes_gpc() foi depreciada e desconsiderada logo após sair o php 5.4 e pelo que percebi a razão tinha a ver com  problemas relacionados a sql injection.

Provavelmente se a utilizaram aqui de alguma forma a ignoraram no .htacces ou no php.ini com alguma configuração.

Acho que acabo de resolver também este problema pois percebi que a função em si retorna sempre false, e assim sendo fui à pasta HTTP em vendor/slim, editei o ficheiro Util.php e substitui o código da função pelo que apresento de seguida (em vez de usar a função get_magic_quotes_gpc() como lá estava substituí-a pelo valor lógico false)

 ```bash
public static function stripSlashesIfMagicQuotes($rawData, $overrideStripSlashes = null)
{
    $strip = is_null($overrideStripSlashes) ? false : $overrideStripSlashes;
    if ($strip) {
        return self::_stripSlashes($rawData);
    } else {
        return $rawData;
    }
}
```

## Como Iniciar

Para executar o projeto localmente, siga estas etapas:

1. Clone este repositório.

2. Certifique-se de ter o PHP e/ou o Xampp instalado em sua máquina.

2.1 - Vá em C:\Windows\System32\drivers\etc e modifique o host para o endereço do seu projeto

exemplo:

    ```bash
    127.0.0.1		www.seusite.com.br
    ```

2.2 Vá em C:\xampp74\apache\conf\extra e modifique o apontamento do host no apache do seu Xampp

exemplo:

    ```bash
    <VirtualHost *:80>
    ServerAdmin seuemail@seuemail.com.br
    DocumentRoot "C:\xampp74\htdocs\ecommerce"
    ServerName www.seusite.com.br
    ErrorLog "logs/dummy-host2.example.com-error.log"
    CustomLog "logs/dummy-host2.example.com-access.log" common
	<Directory "C:\xampp74\htdocs\ecommerce">
        Require all granted

        RewriteEngine On

        RewriteCond %{REQUEST_FILENAME} !-d
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^ index.php [QSA,L]
	</Directory>
</VirtualHost>

```

3. Configure a conexão com o banco na classe Sql.

4. Abra o terminal na pasta raiz do projeto e execute o comando:

   ```bash

   composer init
   composer update

   ```

# E-commerce Project

Project developed from scratch in the [PHP 7 Course](https://www.udemy.com/curso-completo-de-php-7/) available on Udemy and on the [HTML5dev.com.br](https://www.html5dev.com.br/curso/curso-completo-de-php-7) website.

Template used in the project: [Almsaeed Studio](https://almsaeedstudio.com)

## Overview

The project involves the implementation of an administration system for an online store, focusing on essential functionalities such as authentication, product management, and the purchasing process. Although presented as "high-level," students are encouraged to deepen their understanding of key concepts such as object-oriented programming and the use of PDO as needed.

## Project Description

The proposed project aims to create an administration system for an online store using the PHP programming language. The approach is practical, allowing students to apply the concepts learned during the course in a tangible way. Here are the key aspects of the project:

## Features

### Authentication:

- Implementation of a secure authentication system to ensure restricted access only to authorized users.
- Utilization of security best practices to protect login information.

### Product CRUD:

- Development of CRUD operations (Create, Read, Update, Delete) for product management.
- Creation of new products, detailed viewing, editing of existing information, and deletion of products from the database.

### Shopping Cart System:

- Addition of shopping cart functionalities to enable customers to select products for purchase.
- Dynamic updating of the cart as products are added or removed.

### Purchase Process:

- Implementation of a complete purchase flow, from selecting products to closing the order.
- Generation of a bank slip as a payment method.

### Security and Best Practices:

- Incorporation of security practices, such as prevention against SQL injection and session handling to ensure a secure user experience.
- Utilization of object-oriented programming to organize and structure code efficiently and modularly.

### Flexibility for Expansion:

- Encouragement for students to explore and expand the project beyond the provided basics.
- Possibility of adding new features, creating reports, or improving the administrative interface.

### Continuous Learning:

- Awareness that the project will not cover all details during execution, encouraging students to revisit relevant sections of the course as needed.

### Future Updates:

- Commitment to continue updating the course with new lessons, tips, and information to keep students informed about the latest PHP practices.

## Technologies Used

- **Programming Language:** PHP
- **Markup/Styling:** HTML/CSS
- **Client-Side Interactivity:** JavaScript
- **Database:** MySQL or another Database Management System
- **Database Interaction:** PDO (PHP Data Objects)
- **Object-Oriented Programming in PHP:** Extensively used
- **Security Best Practices:** Implemented, including prevention against SQL injection.

## Important Note

- Identification of a potential security loophole related to the `get_magic_quotes_gpc()` function, with a suggested solution.

```bash
public static function stripSlashesIfMagicQuotes($rawData, $overrideStripSlashes = null)
{
    $strip = is_null($overrideStripSlashes) ? false : $overrideStripSlashes;
    if ($strip) {
        return self::_stripSlashes($rawData);
    } else {
        return $rawData;
    }
}
```


## Getting Started

To run the project locally, follow these steps:

1. Clone this repository.
2. Ensure you have PHP and/or Xampp installed on your machine.
    example:
    exemplo:

    ```bash
    127.0.0.1		www.seusite.com.br
    ```
     ```bash
    <VirtualHost *:80>
    ServerAdmin seuemail@seuemail.com.br
    DocumentRoot "C:\xampp74\htdocs\ecommerce"
    ServerName www.seusite.com.br
    ErrorLog "logs/dummy-host2.example.com-error.log"
    CustomLog "logs/dummy-host2.example.com-access.log" common
	<Directory "C:\xampp74\htdocs\ecommerce">
        Require all granted

        RewriteEngine On

        RewriteCond %{REQUEST_FILENAME} !-d
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^ index.php [QSA,L]
	</Directory>
</VirtualHost>
```

3. Modify the host settings in the hosts file and Apache configuration file.
4. Configure the database connection in the Sql class.
5. Open the term

```bash
   composer init
   composer update
   ```
