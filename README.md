# Conversão de temperatura

Aplicação web da [Iniciativa Kubernetes](https://iniciativakubernetes.com.br/) para conversão de temperatura entre as medidas Celsius e Farenheit.

## Etapas para execução

1. Clonar o repositório:

```
$ git clone https://github.com/lucasfusinato/conversao-temperatura

$ cd conversao-temperatura
```

2. Construir a imagem:

```
$ docker build -t kubedev/conversao-temperatura:1.0 -f src/Dockerfile src/
```

3. Executar o contâiner:

```
$ docker run -d -p 8080:8080 kubedev/conversao-temperatura:1.0
```

4. Testar a aplicação:

```
$ curl -X GET "http://localhost:8080/celsius/1/fahrenheit" -H "Accept: application/json"
```

E pronto! O resultado do último comando deverá apresentar o valor convertido de Celsius para Farenheit. Também deve ser possível testar a aplicação através da [interface web](http://localhost:8080) ou da [página de documentação no swagger](http://localhost:8080/api-docs).