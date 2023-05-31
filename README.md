# RabbitMQ-microservice

- Inspirado em [tutorial-kubernetes-microservices](https://github.com/eduardo-matos/tutorial-kubernetes-microservices.git). Esse [link](https://eduardomatos.dev/deployando-microsservicos-com-rabbitmq-e-mongodb-no-kubernetes/) contém uma descrição detalhada dos processos (não utilizei a parte de MongoDB)

- Imagem utilizada de [bypass](https://github.com/eduardo-matos/bypass)

# Uso

- Instale K3s versão v1.26.4 (8d0255af).

- Instância de RabbitMQ:

```kubectl apply -f rabbitmq.yaml``` 

- Crie 3 queue: queue-1, queue-2, queue-3.

- Instância do microsserviço:

```kubectl apply -f microservice-1.yaml``` 

- Publique um JSON vazio (isto é {}) na queue-1. Esperasse que a mensagem publicada em queue-1 seja replicada na queue-2 pelo microservive-1.

# Comportamento Esperado

- De modo geral, cada microsserviço age como um replicador da mensagem consumida, publicando em outra queue.
