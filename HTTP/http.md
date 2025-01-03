# Guia estelar de HTTP

    HyperText Transfer Protocol - HTTP

## Visão Geral

Primeiro vamos entender qual o significado da sigla HTTP, que é Hypertext Transfer Protocol, em português Protocolo de Transferência de Hipertexto que é o conjunto de regras para a comunicação por meio de Hipertexto, um tipo de texto que pode carregar diferentes dados. O protocolo HTTP é usado todos os dias para acessar sites pela internet, pois é ele que permite a troca de dados na web, entre esses dados estão códigos HTML e CSS, Scripts. imagens e vídeos, entre muitos outros, e para cada um desses recursos executa uma chamada.

- Permite troca de informações e dados na internet
- Uma troca de mensagens
- HTML, CSS, Scripts, Imagens, Vídeo
- Uma chamada para cada um desses recursos

## Visualizando a comunicação

No protocolo HTTP tudo funciona com pedidos e respostas, que são chamados em inglês como Request e Response, mandando mensagens nos dois casos. No caso das mensagens de pedidos, você precisa de um verbo HTTP, que chamamos de método, que vai definiir o tipo de pedido que está sendo feito, por exemplo o método GET, vindo do inglês para "pegar", pega um recurso, como um URL para algum local da internet, ou o método POST, que serve para criar um recurso. Depois do pedido, a resposta traz um Status Code do servidor, que é um código sobre o estado do seu pedido, entre esses códigos:

    Estão
        200, onde tudo deu certo e sua página foi enviada,
        404, onde o servidor não conseguiu encontrar o pedido,
        301, que é um redirecionamento para outro local,

Entre outros além do Status Code, o servidor pode mandar um header e um body. Existem coisas que podem estar tanto na Request quanto na Response, que são o header e o body, os Headers são campos informativos, e o body contém conteúdo, podendo ser em forma de HTML ou JSON.

## Visualizando com DevTools

Nesta aula vamos aprender um pouco mais sobre HTTP usando a ferramenta DevTools, mais especificamente a aba "Network", inglês para "Rede". Com a aba aberta, podemos entrar em um site, por exemplo o Google, e iremos ver diversas informações aparecendo, se clicarmos na primeira dessas informações podemos ver algumas das informações sobre o pedido e a resposta. Também pode-se ver, que o navegador faz um pedido para cada link, midia, entre outros, e cada pedido tem sua resposta.

## Visualizando com cURL

Por mais que já possamos visualizar algumas informações com o DevTools, precisamos de alguns detalhes a mais para trabalhar, então usaremos uma ferramenta extra chamada cURL, que já vem instalada em sistemas baseados em UNIX, e no Windows nós aconselhamos a usar a ferramenta Git Bash, que também vem com ela. Usando o cURL podemos entender alguns conceitos, primeiramente temos que saber que o cURL está fazendo o papel do cliente, ao invés do navegador, com a ferramenta, também conseguimos ver o corpo da resposta, o que não era possível com o DevTools, e para também pegar os headers com o cURL, podemos adicionar -i ao comando antes do link, com o parâmetro -v podemos ver todos os headers, tanto os de saída quanto de chegada.

    Exemplo:

        curl -i https://google.com
        
        HTTP/2 301 
        location: https://www.google.com/
        content-type: text/html; charset=UTF-8
        content-security-policy-report-only: object-src 'none';base-uri 'self';script-src 'nonce-3KtRoW9eUjCdd4zGRX-shw' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
        date: Mon, 10 Jul 2023 21:24:43 GMT
        expires: Wed, 09 Aug 2023 21:24:43 GMT
        cache-control: public, max-age=2592000
        server: gws
        content-length: 220
        x-xss-protection: 0
        x-frame-options: SAMEORIGIN
        alt-svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000

        <HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
        <TITLE>301 Moved</TITLE></HEAD><BODY>
        <H1>301 Moved</H1>
        The document has moved
        <A HREF="https://www.google.com/">here</A>.
        </BODY></HTML>

## Conceitos

Nessa aula vamos esclarecer alguns conceitos relacionados ao HTTP, que foi feito pra ser um protocolo simples e fácil de entender pra qualquer pessoa. Ele foi baseado na estrutura de cliente/servidor, ou seja, sempre vão ter uma requisição e uma resposta acontecendo, como um exemplo, voce pode pensar na forma de comprar um lanche, você faz um pedido, especificando a comida que você quer, e o estabelecimento te "responde" com a comida. O HTTP foi criado para também ser stateless, traduzindo, não guardar estado, ou seja, ele não vai guardar nenhuma informação, e não existe nenhuma relação entre as conexões. Outra característica do protocolo é ser extensível, podendo fazer diversas trocas de informação entre o cliente e o servidor, conforme a necessidade.

### Cliente

Nessa aula falaremos do Cliente, que na maioria das vezes é o Browser, ou no nosso caso, também pode ser o cURL. O Cliente é a entidade que dá inicio à toda comunicação com um pedido, fora em algumas poucas exceções. Esses pedidos são feitos através de ações, que usam os métodos do HTTP, como:

- GET,
- POST,
- PUT e DELETE

que vamos ver com mais detalhes em uma próxima aula.

### Servidor

Nessa aula nós falaremos do Servidor, que é uma máquina em algum lugar do mundo preparada para lidar com as requisições do cliente e mandar uma reposta. A resposta sempre tem um Status Code, e pode ter headers e body.

### Proxies

Nesta aula vamos falar sobre Proxies, que são coisas que ficam entre o Servidor e o Cliente, como por exemplo o roteador que está servindo internet para você agora. O Proxy pode ter diversas funções, como cache, para armazenar algumas informações e acelerar o uso. filtro, para impedir o acesso de alguns sites para um antivirus ou um controle parental, entre outros.

## URI - Uniform Resource Identifier

### Resource

Para entendermos como como chegar a um endereço, precisamos entender primeiramente como montar um endereço, para isso usamos o URI, sigla para Uniform Resource Identifier, Identificador de Recurso Uniforme em português, que serve para identificar um recurso por seu nome ou sua localização.

### Recurso

Para entendermos o URI precisamos entender o que é o recurso, que é o alvo do pedido feito cliente. Um recurso pode ser qualquer coisa identificável, como uma entidade digital, como um email, uma entidade abstrata, como uma sessão e até uma entidade física, como um produto.

### URL - Uniform Resource Locator

Um recurso pode ser encontrado pelo locator, localizador em português, ou pelo nome, para encontrar com o locator, utilizamos o URL, sigla para Uniform Resource Locator, ou seja, toda URL é um URI, mas o contrário não é verdadeiro. Toda URL obrigatoriamente precisa de 2 componentes, um protocolo, que é por exemplo o "HTTPS" em uma URL, e um domínio, que é por exemplo a parte "rocketseat.com.br" no site da Rocketseat. A URL pode ter alguns outros componentes opcionais, como o subdomínio, como a parte "www." antes de alguns URLs, como o Path, que serve para acessar partes específicas de um site, como os Parâmetros, como a Porta, que é um componente que é adicionado depois do domínio por um carácter :, e também a Âncora, que serve para apontar algum lugar específico de algum documento.

### URN - Uniform Resource Name

Para encontrar um recurso pelo nome, ao invés da URL, utilizamos a URN, Uniform Resource Name. Um exemplo de URN é urn:isbn:0451450523, porém a URL é bem mais usada na web.

### Revisão Resource

Nessa aula nós revisaremos o que aprendemos nesse módulo.

- O URI (Uniform Resource Identifier) é a forma de encontrar um recurso, que se trata de qualquer entidade indentificável, na internet pelo seu nome ou pelo seu local, a forma mais usada é pelo local.

- A URL (Uniform Resource Locator), que possui 2 componentes obrigatórios, o Protocolo e o Domínio, e 5 opcionais, o subdomínio, o Path, os Parâmetros, a Porta e a Âncora.

## Messages

### Mensagens

Para existir a comunicação entre o servidor e o cliente precisamos ter mensagens entre eles, que são denoninadas HTTP Messages, que existem tanto no request quanto na response. Elas existem desde a versão 1.1 do protocolo HTTP, onde eram feitas em formato de textos legíveis, agora na versão 2, para serem melhor otimizadas, serão feitas em uma estrutura binária, mas basicamente estão no mesmo jeito.

### Request

A mensagem do pedido consiste no método, por exemplo GET, a versão do protocolo e a URI, dependendo do método usado, pode se levar headers e body.

    curl -v https://www.google.com
    **
    > GET / HTTP/2
    > Host: www.google.com
    > user-agent: curl/7.68.0
    > accept: */*
    > 
    **

### Response

A mensagens de resposta tem a versão do protocolo, o status code, os headers e a status message.

    curl -i https://www.google.com
    HTTP/2 200 
    date: Tue, 11 Jul 2023 13:42:42 GMT
    expires: -1
    cache-control: private, max-age=0
    content-type: text/html; charset=ISO-8859-1
    content-security-policy-report-only: object-src 'none';base-uri 'self';script-src 'nonce-Xd10llihZ9uAPQZpOkLP1A' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
    p3p: CP="This is not a P3P policy! See g.co/p3phelp for more info."
    server: gws
    x-xss-protection: 0
    x-frame-options: SAMEORIGIN
    set-cookie: 1P_JAR=2023-07-11-13; expires=Thu, 10-Aug-2023 13:42:42 GMT; path=/; domain=.google.com; Secure
    set-cookie: AEC=Ad49MVHExis2Rn9TMPYDXHH8NDWtqy88HDP1MK-px581GqOmUZ6NJvfwi0E; expires=Sun, 07-Jan-2024 13:42:42 GMT; path=/; domain=.google.com; Secure; HttpOnly; SameSite=lax
    set-cookie: NID=511=hhlwE79fOoUc3Ey_wIfPNxe3Lba6104dLJHo6EbctaiCr0L2eWMn6jL1yr2FJsMAhHEz-f3TZI_RPxkXsaCFEAfundhuPQGkuE_q6-xsRoZntrqpdUS8ZRzWuyh_e8s8UMgqOZ682q2VWDmN0KS7C0Pu2UcLP66YjA8kQwl-xyo; expires=Wed, 10-Jan-2024 13:42:42 GMT; path=/; domain=.google.com; HttpOnly
    alt-svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000
    accept-ranges: none
    vary: Accept-Encoding

## Methods

### Introdução

Existem diversos métodos HTTP, nesse módulo iremos entender os mais usados entre eles.

- OPTIONS
- GET
- HEAD
- POST
- PUT
- PATCH
- DELETE

### Methods+

Nessa aula vamos estudar os Métodos, ou verbos do HTTP que apesar de poderem ser chamados assim não necessáriamente tem formato de verbos. Eles servem para indicar o intuito da operação que o cliente está realizando, e cada um possui seu significado, que vamos estudar nas próximas aulas. Os métodos podem ter 2 características, seguro e idempotente. Métodos seguros não alteram o servidor, são de apenas leitura, então não apresentam carga extra para o servidor e são mantidos seguros por ele, métodos considerados seguros são: GET, HEAD e OPTIONS. Os métodos Idempotentes são os métodos que não mudam de resposta, por isso a parte de "idem" no nome, mas podem ter status codes diferentes os métodos idempotentes são todos os métodos seguros, PUT e DELETE.

### JSON Server

Nesta aula iremos ensinar como instalar a ferramenta JSON Server, que nos permite pegar respostas em formato JSON. Antes de tudo temos que já ter o Node.js instalado na máquina, depois disso podemos executar o comando npm install -g json-server, depois do comando terminar, crie um diretório chamado http-course e entre nele, copie as linhas de código:

    {
        "posts": [
            { "id": 1, "title": "json-server", "author": "typicode" }
        ],
        "comments": [
            { "id": 1, "body": "some comment", "postId": 1 }
        ],
        "profile": { "name": "typicode" }
    }

Agora pra iniciar o servidor, podemos usar o comando json-server --watch db.json e assim podemos acessar esses conteúdos.

### OPTIONS

Nesta aula falaremos sobre o método OPTIONS, que é um verbo HTTP que irá nos dar informações sobre a disponibilidade de métodos da requisição. Ele é um método seguro, pois não faz alteração alguma, e é idempotente, pois sempre retornará a mesma coisa para a mesma requisição, o OPTIONS não manda nem recebe um Body, não é usado em formulários e nem é cacheable.
