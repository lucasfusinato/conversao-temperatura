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

Opção A) Execução com Docker:

```
$ docker run -d -p 30010:8080 kubedev/conversao-temperatura:1.0
```

Opção B) Execução com Kubernetes:

Criar um Container Registry local:

```
$ docker run -d -p 5000:5000 --restart=always --name registry registry:2
```

Enviar imagem para o Container Registry local:

```
$ docker tag kubedev/conversao-temperatura:1.0 localhost:5000/kubedev/conversao-temperatura:1.0

$ docker push localhost:5000/kubedev/conversao-temperatura:1.0
```

Criar o Deployment no Kubernetes:

```
$ kubectl apply -f k8s/deployment.yaml
```

4. Testar a aplicação:

```
$ curl -X GET "http://localhost:30010/celsius/1/fahrenheit" -H "Accept: application/json"
```

E pronto! O resultado do último comando deverá apresentar o valor convertido de Celsius para Farenheit. Também deve ser possível testar a aplicação através da [interface web](http://localhost:30010) ou da [página de documentação no swagger](http://localhost:30010/api-docs).