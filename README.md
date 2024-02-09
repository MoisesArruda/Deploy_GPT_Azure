<h1 align="center"> Fazendo deploy da sua solução GPT na Azure. </h1>
Este repositório tem o objetivo de compartilhar a implementação de uma solução utilizando um modelo de LLM na cloud Azure.
Como forma de representação, pode utilizar o link abaixo para acessar o repositório que contém uma solução desenvolvida para realizar os passos seguintes.

[Acesse aqui o repositório. 📁](https://github.com/MoisesArruda/GPT_Streamlit_FAISS)

## DockerFile

Crie e configure o Dockerfile para que seja possível criar a imagem e executar o container.

![DockerFile](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/DockerFile.png)

## Criando sua imagem docker.

No terminal de comando realize as seguintes operações para criar a imagem:

```bash
docker build -t chatbot_gpt .
```
![Build image](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/build%20image.png)


Para visualizar se a imagem foi criada corretamente:

```bash
docker images
```

![Docker images](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/docker%20images.png)

## Rodando o container docker.

Rode o container para verificar se está funcionando como o esperado:

```bash
docker run -d -p 8000:8501 chatbot_gpt 
```

Abra uma aba no seu navegador de prefêrencia, e cole a seguinte URL para acessar a aplicação

```bash
localhost:8000
```

## Instalação do AZURE CLI

Será necessário utilizar a interface de linha de comando do Azure para criar e gerenciar recursos do Azure.

[Link para download.](https://learn.microsoft.com/pt-br/cli/azure/)

## Registros de Container no Azure

Faça a criação do recurso de Registro de Container na Azure, a configuração não possui nenhum detalhe que necessite ser alterado, apenas prossiga.

![Container Registry](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/Container_registry.png)


## Registrar sua imagem

Com o recurso já criado e em sua tela inicial, vamos copiar o **Servidor de logon** para utilizar futuramente.

![Servidor logon](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/servidor_Logon.png)

- Retorne ao prompt de comando para realizar a conexão com a azure com a ajuda do Azure CLI instalado anteriormente. Coloque o nome da imagem e o Logon server.

```bash
docker tag chatbot_gpt LogonServer/chatbot_gpt:latest
```

- Para visualizar a nova imagem criada.

```bash
docker images
``` 

- Realizar login na Azure com a ajuda do Azure CLI instalado anteriormente, apague o **LogonServer** e cole o Logon server novamente.

```bash
docker login LogonServer
```

- Após isso irá solicitar o usuário e a senha, essas informações podem ser obtidas indo em **Chaves de acesso**.

![Azure logon](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/docker%20login.png)

- Enviar a imagem para a cloud Azure.

```bash
docker push NomeNOVAImagem:latest
```

- Procure por **Repositórios** e verifique se sua imagem está lá.

![Repositórios](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/Reposit%C3%B3rios.png)


## Aplicativo de Container.

As seguintes configurações são necessárias para a criação correta do recurso:

1. Página de **Contêiner**:

- Desmarcar **Usar imagem de início rápido**.
- Preencher os seguintes campos de **Detalhes do contêiner**.
  
![Container app ](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/Container_app.png)

2. Página de **Entrada**.

- Habilitar **Ingresso**.
- Selecionar **Aceitando tráfego de qualquer lugar**.
- em **Porta de destino** colocar 8501.

![Container app ](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/Container_app2.png)

3.   Recurso criado.

![Container app 3](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/Container_app3.png)

4. Na página inicial do seu recurso, selecione **URL do aplicativo**.

![Url do app](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/url_app.png)


Aplicação implementada com êxito.

![Chatbot GPT](https://github.com/MoisesArruda/Deploy_GPT_Azure/blob/main/imgs/Gpt_streamlit.png)

