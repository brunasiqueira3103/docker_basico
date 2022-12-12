<div align="justify">
<h1> -- DOCKER -- <h1/>

<h2> Material do Bootcamp da DIO [Jornada DevOps com AWS - Impulso] <h2/>

<h3>>>> Instalando Docker <h3/>
<h4>
Utilizei esse passo a passo (ubuntu-server) <br/>
https://www.hostinger.com.br/tutoriais/install-docker-ubuntu  <br/> <br/>

ou por script:
    
sudo curl -fsSL https://get.docker.com -o get-docker.sh <br/>
comentar a parte do script que tem cdrom: <br/>
sudo nano /etc/apt/sources.list <br/>
>>>>#deb [check-date=no] file:///cdrom jammy main restricted <br/>
    
    
sudo sh get-docker.sh <br/>
   
<h4/>
    
---
<h3>>>> REALIZANDO O DOWNLOAD DE IMAGEM <h3/>
<h4>
Realizar cadastro gratuíto no:  <br/>
https://hub.docker.com/ <br/>
buscar pela imagem: hello-word (mostra a documentação da imagem, e dá o comando de pull) <br/>
docker pull hello-world <br/>
docker images (mostra as imagens baixadas localmente) <br/>
docker run hello-world (executa a imagem) <br/>
docker run ps (mostra se há algum container em execução) <br/>
docker run ps -a (mostra as atividades rescentes) <br/>
<h4/>

<h3>>>> EXECUTANDO UM CONTAINER (IMAGEM UBUNTU) <h3/>
<h4>
docker pull ubuntu (baixa a imagem)  <br/>
docker run ubuntu  (executa imagem) <br/>
docker run ubuntu sleep 1500 (executa o container por 1500 segundos)  <br/>
docker stop [id/name] (para a execução do container verificar id/name com docker ps -a)  <br/>
docker run --help   <br/>
<h4/>
---
<h3>>>> EXECUTANDO APLICAÇÕES NO CONTAINER <h3/>
<h4>
docker run -it ubuntu  (t- terminal / i- interação / acessa como root dentro do container) <br/>
docker run -dti  ubuntu (-d roda em background) <br/>
docker exec -it [id ou nome]  /bin/bash  <br/>
|-->(vamos estar dentro do ubuntu no container/ fazer update/upgrade/criar um arquivo usando nano) <br/>
<h4/>
---
<h3>>>> EXCLUINDO E RENOMEANDO CONTAINERS <h3/>
<h4>
docker stop [id] (para a execução do container) <br/>
docker rm [id]  (remove o container executado) <br/>
docker rmi [imagem]  (remove a imagem do container) <br/>
docker run -dti --name Ubuntu-A ubuntu  <br/>
|--> (remomeando --name [novo-nome] Ubuntu-A [imagem] ubuntu)
---
<h4/>
<h3>>>> COPIANDO ARQUIVOS <h3/>
<h4>
(Do servidor para o container) <br/>
docker exec Ubuntu-A mkdir /destino/ (cria a pasta destino sem precisar "entrar no container") <br/>
docker exec Ubuntu-A mkdir ls -l /  (mostra os diretórios do container Ubunto-A) <br/>
criar arquivos txt para fazer a cópia e depois zipar--->>>> touch arquivo1.txt/touch arquivo2.txt no seu diretório <br/>
docker cp arquivo.txt Ubuntu-A:/destino/  (copia o arquivo que você criou para dentro do container na pasta /destino) <br/>
>>>apt -y install zip  [instalar o zip no seu servidor, criar alguns arquivos txt para zipar  <br/>
>>>zip Meuzip.zip *txt (zipa os arquivos .txt que encontrar) <br/>
docker cp Meuzip.zip  Ubuntu-A:/destino  <br/>
|--->(cp também copia pastas, nesse exemplo uma pasta zipada)  <br/>
(Do container para o servidor) <br/>
docker cp Ubuntu-A:/destino/Meuzip.zip  Zipcopia.zip  <br/>
|----> origem container / para sua pasta, novo nome
<h4/>
---
<h3>>>> CRIANDO UM CONTAINER MYSQL <h3/>
<h4>
docker pull mysql (faz download da imagem) <br/>
docker run -e MYSQL_ROOT_PASSWORD=aa --name mysql-A -d -p 3306:3306 mysq <br/>
|--> MYSQL_ROOT_PASSWORD=aa (cria a senha do banco de dados) <br/>
|--> --name mysql-A (cria o nome mysql-A) <br/>
|--> 3306:3306 (porta de acesso ao banco de dados, porta padrão sql) <br/>
|--> -e(setar as variáveis) -d(executa em background) -p(portas no host) <br/>
docker exec -it mysql-A bash (abre execução do bash no Mysql) <br/>
#######mysql -u root -p --protocol=tcp (faz login como root e passar o protocolo) <br/><br/>

CREATE DATABASE aula; (cria um banco de dados chamado "aula" não esqueça do ";") <br/>
show databases; (mostra os bancos de dados criados) <br/>
<h4>
|--->ip a (verificar a faixa de ip "docker0:") <br/>
docker inspect mysql-A (procurar IPAddress do container, conferir a porta) <br/>
apt -y install mysql-client (instala mysql-client) <br/>
mysql -u root -p --protocol=tcp (FAZ LOGIN ROOT)<br/>

CREATE TABLE alunos (  <br/>
    AlunoID int,  <br/>
    Nome varchar(50),  <br/>
    Sobrenome varchar(50),  <br/>
    Endereco varchar(150),  <br/>
    Cidade varchar(50)  <br/>
);  <br/>  <br/>

INSERT INTO alunos (AlunoID, Nome, Sobrenome, Endereco, Cidade)   <br/>
VALUES (1, 'Bruna', 'Siqueira', 'Onde eu moro', 'Massaranduba'); <br/>
<h4/>
---
