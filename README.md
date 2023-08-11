# Desafio LINUXtips PICK

1. Clone esse repositório

    ```bash	
    git clone https://github.com/Rapha-Borges/LINUXtips-Giropops-Senhas.git
    ```

2. Criar o [Dockerfile](https://github.com/Rapha-Borges/LINUXtips-Giropops-Senhas/blob/main/Dockerfile) (no caso do exemplo, o Dockerfile já está no nosso repositório)

3. Subir o Redis

    ```bash	
    sudo docker run -d -p 6379:6379 --name redis cgr.dev/chainguard/redis:latest
    ```

4. Criar a imagem

    ```bash
    sudo docker build -t giropops-senhas:1.0 .
    ```

5. Rodar a imagem

    ```bash
    sudo docker container run -d -p 5000:5000 --env REDIS_HOST={IP do REDIS} --name giropops-senhas giropops-senhas:1.0
    ```

6. Testar a aplicação

    ```bash
    curl http://localhost:5000
    ```

7. Faça a [instalação do Trivy](https://aquasecurity.github.io/trivy/v0.44/getting-started/installation/) e execute a verificação da imagem

    ```bash
    trivy image giropops-senhas:1.0
    ```

8. Instale o Docker Scout e execute a verificação da imagem

    ```bash
    curl -fsSL https://raw.githubusercontent.com/docker/scout-cli/main/install.sh -o install-scout.sh
    sh install-scout.sh
    ```

    ```bash
    docker scout cves giropops-senhas:1.0
    ```
