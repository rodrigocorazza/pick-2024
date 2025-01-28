# LINUXtips-Giropops-Senhas
Desafio do dia 2 da LinuxTips Giropops-Senhas utilizando Dockerfile

Criar um Dockerfile utilizando as boas práticas aprendidas durante o curso, no caso utilizei 2 containers para o processo.

- 1 Container para o Redis
- 1 Container para aplicação Giropops-Senhas

## Gerar os builds dos 2 Dockerfile criados:

1º - Build das imagens:
- Redis
```
docker build -f Dockerfile-redis -t rodrigocorazza/linuxtips-redis:1.0 .
```
- Giropops-senhas
```
docker build -f Dockerfile-giropops-senha -t rodrigocorazza/linuxtips-giropops-senhas:1.0 .
```
Após esse proceso as imagens já estarão criadas.

---

2º - Ciar os containers
- Redis
```
docker run -d -p 6379:6379 --name redis rodrigocorazza/linuxtips-redis:1.0
```

- Giropops-senhas
> **Vale lembrar**: Para que a aplicação Giropops-senhas possa funcionar temos que apontar o IP do container do Redis. 
```
docker container inspect ID_CONTAINER_REDIS | grep IPAddress
```
Após ver qual o IP do container do redis, passar ele como variável para rodar o container:
```
docker run -d -p 80:5000 --name giropops-senhas -env=IP_CONTAINER_REDIS rodrigocorazza/linuxtips-giropops-senhas:1.0
```

Acessar o localhost no navegador e já está funcionando.

Há outras maneiras de criar esse projeto, criando uma rede específica para os 2 container se comunicar ou até mesmo usando docker-compose