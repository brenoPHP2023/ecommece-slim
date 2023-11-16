# Projeto E-commerce

Projeto desenvolvido do zero no [Curso de PHP 7](https://www.udemy.com/curso-completo-de-php-7/) disponível na plataforma da Udemy e no site do [HTML5dev.com.br](https://www.html5dev.com.br/curso/curso-completo-de-php-7).

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

## Como Iniciar

Para executar o projeto localmente, siga estas etapas:

1. Clone este repositório.

2. Certifique-se de ter o PHP e/ou o Xampp instalado em sua máquina.

2.1 - Vá em C:\Windows\System32\drivers\etc e modifique o host para o endereço do seu projeto

exemplo:
    ```bash
    127.0.0.1		www.seusite.com.br

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

3. Configure a conexão com o banco na classe Sql.

4. Abra o terminal na pasta raiz do projeto e execute o comando:

   ```bash
   composer init
   composer update
