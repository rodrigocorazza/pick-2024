É hora de instalar o incrível Kind, para que possamos ter o nosso primeiro cluster Kubernetes criado com sucesso!

Para a criação do seu cluster Kubernetes, nós vamos utilizar o Kind! O nosso cluster será composto de um node Control-Plane e 3 nodes Workers.

Você deve criar um arquivo chamado meu-primeiro-cluster.yaml no diretório /root com todas as definições necessárias para o Kind criar o seu cluster.


🚀 Deploy do Nosso Primeiro Pod
Temos um arquivo já criado esperando apenas você realizar o deploy desse nosso primeiro pod!

O manifesto com todas as definições para a criação desse pod está em /root/meu-primeiro-pod.yaml.

Lembre-se, se houver algum erro no momento do deploy, você precisa ajustar o que estiver errado e tentar novamente!

Precisamos ter esse pod em execução!

====================================================================================================

apiVersion: v1
kind: Pod
metadata:
  labels:
    run: nginx-giropops
    app: giropops-strigus
  name: nginx_giropops
spec:
  containers:
  - image: nginx
    name: nginx_giropops
    ports:
    - containerPort: 80
    resources: 
      limits: 
        memory:
        cpu: "0.5"
    requests:
        memory: "4400MB"
        cpu: "0.3"
  dnsPolicy: ClusterFirst
  restartPolicy: Always
