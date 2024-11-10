# go-expert-desafio-stress-test

Desafio Pós-graduação Full Cycle Go Expert

## Enunciado do desafio

### Objetivo:

Criar um sistema CLI em Go para realizar testes de carga em um serviço web. O usuário deverá fornecer a URL do serviço, o número total de requests e a quantidade de chamadas simultâneas.
O sistema deverá gerar um relatório com informações específicas após a execução dos testes.

Entrada de Parâmetros via CLI:

- --url: URL do serviço a ser testado
- --requests: Número total de requests
- --concurrency: Número de chamadas simultâneas

#### Execução do Teste:

- Realizar requests HTTP para a URL especificada.
- Distribuir os requests de acordo com o nível de concorrência definido.
- Garantir que o número total de requests seja cumprido.

#### Geração de Relatório:

Apresentar um relatório ao final dos testes contendo:

- Tempo total gasto na execução
- Quantidade total de requests realizados
- Quantidade de requests com status HTTP 200
- Distribuição de outros códigos de status HTTP (como 404, 500, etc.)

#### Execução da aplicação:

Poderemos utilizar essa aplicação fazendo uma chamada via docker. Ex:

`docker run <sua imagem docker> —url=http://google.com —requests=1000 —concurrency=10`

### Instruções de uso

Compilar o container:
`docker build -t marcioaraujo/pos-stress-test:1.0 .`

Para realizar o teste de stress na url http://google.com.br, com um total de 10 requests, sendo 5 requests simultâneas, pode ser usado o comando abaixo:

`docker run marcioaraujo/pos-stress-test:1.0 run -u http://google.com.br -c 5 -r 10`

Exemplo de resposta:

Running stress test for url: http://google.com.br, with 10 total requests and 5 concurrent calls

## Start time: 2024-11-10 02:40:56

Request completed -- 1.087995209s
Request completed -- 1.088168s
Request completed -- 1.099150668s
Request completed -- 1.146157875s
Request completed -- 1.156508292s
Request completed -- 1.193666251s
Request completed -- 1.441676917s
Request completed -- 830.506084ms
Request completed -- 1.067813459s
Request completed -- 842.000959ms

---

End time: 2024-11-10 02:41:02
Total time: 5.328489211s
Total number of requests: 10
Average number of requests per second: 1.88
Number of requests with status 200: 10 (100%)
Distribution of other status codes:
HTTP 200: 10 (100%)
