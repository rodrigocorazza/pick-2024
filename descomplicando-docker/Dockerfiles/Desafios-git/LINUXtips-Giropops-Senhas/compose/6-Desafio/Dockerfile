FROM cgr.dev/chainguard/python:latest-dev as buildar
ENV REDIS_HOST=localhost
WORKDIR /app/giropops-senhas/
COPY . .
RUN pip install --no-cache-dir -r requirements.txt --user

FROM cgr.dev/chainguard/python:latest
WORKDIR /app/giropops-senhas/
COPY --from=buildar /home/nonroot/.local/lib/python3.12/site-packages /home/nonroot/.local/lib/python3.12/site-packages
COPY --from=buildar /home/nonroot/.local/bin/flask /home/nonroot/.local/bin/flask
COPY . .
ENV PATH="/home/nonroot/.local/bin:$PATH"
ENTRYPOINT ["flask", "run", "--host=0.0.0.0"]