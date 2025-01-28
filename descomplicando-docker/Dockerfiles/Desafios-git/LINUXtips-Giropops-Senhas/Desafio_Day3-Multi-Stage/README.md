# Desafio Day 3 - LINUXtips-Giropops-Senhas-Multi-Stage
Desafio do dia 3 da LinuxTips Giropops-Senhas dando continuidade na aula sobre Multi-Stage utilizando a imagem da chainguard.

Foi utilizado 2 imagens para reduzir o tamanho da imagem final.

- 1º é a imagem de dev, para instalar todos as bibliotecas necessárias

- 2º para rodar o a aplicação Giropops-Senhas

Foi necessário copiar da imagem de teste o binario do flask para o comando poder funcionar:
```
COPY --from=buildar /home/nonroot/.local/bin/flask /home/nonroot/.local/bin/flask
```
E apontar o binário do flask como variável de ambiente:
```
ENV PATH="/home/nonroot/.local/bin:$PATH"
```
