# DIO-Bootcamp-AzureAdvantage

Docker
Docker é uma plataforma que permite criar, implementar e executar aplicativos em contêineres. Os contêineres são leves, portáteis e garantem que o software funcione de forma consistente, independentemente do ambiente.

Dockerfile
Um Dockerfile é um script de texto simples que contém instruções sobre como criar uma imagem Docker. Ele especifica tudo o que o contêiner precisa para ser executado, incluindo o sistema operacional, dependências, código-fonte e comandos.

Exemplo de Dockerfile:

# Usar uma imagem base do Python
FROM python:3.8-slim

# Definir o diretório de trabalho
WORKDIR /app

# Copiar os arquivos do projeto para o contêiner
COPY . .

# Instalar as dependências
RUN pip install --no-cache-dir -r requirements.txt

# Comando para executar o aplicativo
CMD ["python", "app.py"]
Docker Compose
Docker Compose é uma ferramenta para definir e executar aplicativos Docker multi-contêiner. Com um arquivo YAML (docker-compose.yml), você pode especificar todos os serviços de contêiner que seu aplicativo precisa.

Exemplo de docker-compose.yml:

version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/app
  redis:
    image: "redis:alpine"
Contêiner
Um contêiner é uma instância em execução de uma imagem Docker. Ele contém tudo o que o aplicativo precisa para funcionar e é isolado do sistema host e de outros contêineres.

Redes
No Docker, redes permitem que os contêineres se comuniquem entre si e com o mundo exterior. O Docker gerencia automaticamente a criação e a configuração das redes.

Cluster Swarm
Docker Swarm é uma ferramenta de orquestração que permite gerenciar um cluster de contêineres Docker. Com Swarm, você pode implantar, gerenciar e escalar seus contêineres em várias máquinas.

Testes de Stress
Testes de stress verificam a estabilidade e a robustez de um sistema sob condições extremas. Para executar testes de stress em contêineres, você pode usar ferramentas como Apache JMeter ou Siege.

Proxy utilizando o NGINX
O NGINX pode ser usado como um proxy reverso para distribuir o tráfego de rede entre vários contêineres.

Exemplo de configuração do NGINX:

server {
    listen 80;

    location / {
        proxy_pass http://app_container:5000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
Escalabilidade dos Contêineres com Gateways e Hubs
Para escalar contêineres, você pode usar ferramentas como Docker Swarm, Kubernetes e serviços de balanceamento de carga (load balancer) para distribuir o tráfego de forma eficiente entre várias instâncias de contêiner.
