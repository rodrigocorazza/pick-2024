FROM ubuntu:20.04
ENV REDIS_HOST=localhost
RUN apt-get update && apt-get install -y \
    pip \
    git  -y 

ADD git clone https://github.com/badtuxx/giropops-senhas.git /app/
WORKDIR /app/giropops-senhas/
RUN echo "Werkzeug==2.2.2" >> requirements.txt && pip install --no-cache-dir -r requirements.txt
CMD ["flask", "run", "--host=0.0.0.0"]
