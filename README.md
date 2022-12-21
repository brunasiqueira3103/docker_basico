<h1> -- DOCKER -- <h1/>
<h2> Anotações feitas durante o processo de aprendizagem <h2/>

![image](https://user-images.githubusercontent.com/104859742/201178981-ae2db2d8-ed70-46dc-bd99-22a0a0c7b7a9.png)

# O que é Docker
https://www.docker.com/
https://www.redhat.com/pt-br/topics/containers/what-is-docker
https://learn.microsoft.com/pt-br/dotnet/architecture/microservices/container-docker-introduction/docker-defined


# Como instalar no Ubuntu-server
https://www.hostinger.com.br/tutoriais/install-docker-ubuntu

## Para instalar o Docker, você pode seguir os seguintes passos:

- Abra um terminal e atualize o índice de pacotes do gerenciador de pacotes do seu sistema operacional, digitando:
$ sudo apt update

- Instale as dependências necessárias para adicionar um novo repositório do gerenciador de pacotes do sistema operacional:
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common

- Adicione a chave GPG do repositório do Docker com o seguinte comando:
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

- Adicione o repositório do Docker ao seu sistema operacional com o seguinte comando:
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" 

- Atualize novamente o índice de pacotes do gerenciador de pacotes do seu sistema operacional:
$ sudo apt update

- Instale o Docker com o seguinte comando:
$ sudo apt install docker-ce

- Verifique se o Docker foi instalado corretamente executando o seguinte comando:
$ sudo docker run hello-world

- Se tudo estiver funcionando corretamente, você deverá ver uma mensagem de saudação do Docker.

### Observação: os comandos acima foram escritos para o Ubuntu 20.04 (Focal Fossa). Se você estiver usando outra distribuição do Linux, pode ser necessário alterar alguns dos comandos acima para refletir a sintaxe específica da distribuição que você está usando.
