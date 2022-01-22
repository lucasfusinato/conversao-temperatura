# Conversão de temperatura

Aplicação web da [Iniciativa Kubernetes](https://iniciativakubernetes.com.br/) para conversão de temperatura entre as medidas Celsius e Farenheit.

```
$ git clone https://github.com/lucasfusinato/conversao-temperatura

$ cd conversao-temperatura
```

## Etapas para execução com Docker

1. Construir a imagem:

```
$ docker build -t lucasfusinato/conversao-temperatura:1.0 -f src/Dockerfile src/
```

2. Executar o contâiner:

```
$ docker run -d -p 30010:8080 lucasfusinato/conversao-temperatura:1.0
```

3. Testar a aplicação:

```
$ curl -X GET "http://localhost:30010/celsius/1/fahrenheit" -H "Accept: application/json"
```

## Etapas para execução com Kubernetes

1. Criar o *deployment*:

```
$ kubectl apply -f k8s/deployment.yaml
```

2. Testar a aplicação:

```
$ KUBERNETES_HOST=localhost

$ curl -X GET "http://$KUBERNETES_HOST:30010/celsius/1/fahrenheit" -H "Accept: application/json"
```
