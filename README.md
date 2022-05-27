# LocalStack provisionada para testes

Preparação de infra mockada de AWS para testes de arquitetura em nuvem

## Requisitos

1. ```python``` (Python v3.6+)
2. ```pip```(Python package manager)
3. ```Docker```
4. ```Terraform```

## DISCLAIMER!

> Antes de prosseguir, tome ciência que sistemas Windows fora do padrão de unicode UTF-8, podem enfrentar problemas ao usar pacotes Python, devido ao uso de caracteres incompatíveis com CP-1252, portanto prefira trocar o idioma para inglês e adotar o uso do UTF-8 evitando esse e outros tipos de problema no futuro.

Para garantir a funcionalidade em sistemas Windows, serão seguidos os passos abaixo


## Ambiente Virtual python

1. ```python -m venv venv```
2. ```source venv/bin/activate``` | em sistemas Windows: ```source venv/Scripts/activate```
3. ```pip install -r requirements.txt```

## Subir container LocalStack (escolha um)

### 1. Com Docker Compose

1. Montar um arquivo ```docker-compose.yml``` com as configurações da imagem, portas, _var envs_ e ponto de montagem
2. Em um terminal, execute o comando para orquestrar um container de localstack
```
docker-compose up
```

### 2. Ou via pip (Leia o DISCLAIMER)

1. Em um terminal, execute o comando abaixo
```
localstack start
```

## Execução

Em outro terminal execute os comandos ```aws-cli```

Em vez de executar dessa forma:

```
aws --endpoint-url http://localhost:4566 cloudformation list-stacks
```

...simplesmente faça:

```
awslocal cloudformation list-stacks
```

## Subindo uma infra de exemplo como código

```
awslocal cloudformation deploy --stack-name lstack-s3 --template-file infra_cf/s3/sample.yaml
```

## License
This software library is released under the Apache License, Version 2.0 (see LICENSE).