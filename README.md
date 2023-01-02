# Sorteio Loteria

Esse projeto nada mais é que uma brincadeira de um grupo de amigos, que ao não terem nada para fazer resolveram montar um sorteio de loteria.
O fluxo da aplicação é extremamente simples, basicamente:
- Um usuário qualquer escolhe 6 números de 1 a 60.
- Clica em sortear.
- Captura os números selecionados e a porcentagem de acertos.

# Desafios

Poxa! Qual é o desafio de gerar números e mostrar para um usuário? Então, ai que a brincadeira começa! Para deixar o desafio mais complexo, definimos algumas coisas.

Divagando muito, decidimos criar um fluxo de desenvolvimento completo do projeto. No qual consiste em ter:
- Um bord configurado para acompanhamento das tasks aqui no Github Projects.
- Não teremos persistência de dados. Para que deveríamos? rsrs... Então pensamos algo diferente, nossa aplicação tem:
    - Uma API Gateway criada com Golang .
    - Uma API que realiza o sorteio dos números feita com Golang e GRPC.
    - Uma API que realiza o cálculo da porcentagem de acertos do usuário com PHP e GRPC.
    - Um APP criado com Flutter para o usuário escolher os números e realizar o sorteio.
    - Uma página WEB criada com Vue.js o usuário escolher os números e realizar o sorteio.
- O projeto inteiro tem cobertura de testes documentadas no Codecov.
- A aplicação toda tem scripts de CI/CD para publicações no fly.io e também para gerar os apps para as lojas.
## Documentação da API

#### Retorna os números sorteados e a porcentagem de acertos

```http
GET /sorteio
```

```json
{
    "numerosSorteados": [1, 7, 45, 23, 8, 59]
    "porcentagemDeAcerto": 13.67
}
```


## Rodando localmente

#### Clone o projeto

```bash
git clone https://github.com/booscaaa/sorteio-loteria
```

#### Entre no diretório do projeto

```bash
cd sorteio-loteria
```

#### Inicialize as APIs

```bash
docker-compose up --build -d
```


## Stack utilizada

**Front-end:** Flutter, Vue, Vuetify, Dayjs

**Back-end:** Golang, PHP, GRPC, REST


## Autores

- [@booscaaa](https://www.github.com/booscaaa)
- [@julioolver](https://www.github.com/julioolver)
- [@kyrllan](https://www.github.com/kyrllan)
- [@sergiotessaro](https://www.github.com/sergiotessaro)
- [@wiliamfrisonribeiro](https://www.github.com/wiliamfrisonribeiro)


