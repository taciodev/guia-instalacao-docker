# Guia de Instalação do Docker Engine



### Pré-requisitos

1. Inicie a VM01 no seu hipervisor.
2. Acesse o terminal na VM01.

7. Siga as instruções do script para configurar a senha do root e responder às perguntas de segurança.

### Desinstale as versões antigas do Docker

Desinstale quaisquer versões mais antigas antes de tentar instalar uma nova versão, juntamente com as dependências associadas.

```bash
sudo yum remove docker \
    docker-client \
    docker-client-latest \
    docker-common \
    docker-latest \
    docker-latest-logrotate \
    docker-logrotate \
    docker-engine
```

Imagens, contêineres, volumes e redes armazenados /var/lib/docker/não são removidos automaticamente quando você desinstala o Docker.

### Instale usando o repositório rpm

Antes de instalar o Docker Engine pela primeira vez em uma nova máquina host, você precisa configurar o repositório Docker. Depois, você pode instalar e atualizar o Docker a partir do repositório.

#### Configure o repositório

Instale o pacote yum-utils (que fornece o yum-config-manager utilitário) e configure o repositório.

```bash
sudo yum remove docker \
        docker-client \
        docker-client-latest \
        docker-common \
        docker-latest \
        docker-latest-logrotate \
        docker-logrotate \
        docker-engine
```

#### Instale o Docker Engine

1. Instale o Docker Engine, o containerd e o Docker Compose:

```bash
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Se for solicitado a aceitar a chave GPG, verifique se a impressão digital corresponde 060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35e, em caso afirmativo, aceite-a.

Este comando instala o Docker, mas não inicia o Docker. Ele também cria um dockergrupo, mas não adiciona nenhum usuário ao grupo por padrão.

2. Inicie o Docker.

```bash
sudo systemctl start docker
```

3. Verifique se a instalação do Docker Engine foi bem-sucedida executando a imagem hello-world.

```bash
sudo docker run hello-world
```

Este comando baixa uma imagem de teste e a executa em um contêiner. Quando o contêiner é executado, ele imprime uma mensagem de confirmação e sai.

Agora você instalou e iniciou o Docker Engine com sucesso.