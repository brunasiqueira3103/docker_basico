<h1> Gerar imagem própria e um container a partir dela <h1/>
 <br/>
<h3>

|---> Para esse exemplo vamos precisar da imagem: ubuntu e tabém de um documento python que será usado como aplicação <br/>
# docker pull ubuntu <br/>
|---> Arquivo python: <br/>
# nano app.py <br/> <br/>

	nome = input("Qual é o seu nome? ") <br/>
	print (nome) <br/> <br/> <br/>



--------- Criando a Imagem <br/> <br/>


|---> nome da minha imagem será: meuprimeirocontainer <br/>
# docker run -dti --name meuprimeirocontainer ubuntu <br/>
|---> acessar o bash do container que será imagem, instalar o que será necessário para rodar a aplicação <br/>
# docker exec -ti meuprimeirocontainer bash <br/>
|---> instalar o pytoh3 && nano <br/>
# apt install python3 nano <br/>
|---> limpar arquivos após a instalação <br/>
# apt clean <br/>
|---> criar o dockerfile <br/>
# nano dockerfile <br/>
|---> inserir no dockerfile os comandos que o container irá executar <br/> <br/>
 
	FROM ubuntu <br/>
	RUN apt update && apt install -y python3 && apt clean  <br/>
	COPY app.py /opt/app.py <br/>
	CMD python3 /opt/app.py <br/> <br/>

|---> Buildar, para de fato gerar a imagem:  <br/>  <br/>
# docker build . -t meuprimeirocontainer  <br/>
|---> Verificar a criação da imagem com: <br/>
# docker images  <br/>
|---> Gerar container a parti da imagem criada:  <br/>
# docker run -dti --name meu-app meuprimeirocontainer

|---> 
<h3/>
 <br/>