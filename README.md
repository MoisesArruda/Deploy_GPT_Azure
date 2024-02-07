<h1 align="center"> Fazendo deploy da sua solução GPT na Azure. </h1>
Este repositório tem o objetivo de compartilhar a implementação de uma solução utilizando um modelo de LLM na cloud Azure.
Como forma de representação, pode utilizar o link abaixo para acessar o repositório que contém uma solução para realizar os passos a seguir.

[Acesso aqui o repositório 📁](https://github.com/MoisesArruda/GPT_Streamlit_FAISS)

## DockerFile

Faça a criação e e configuração do seu Dockerfile para que seja possível criar sua imagem e executar seu container.

![DockerFile](https://github.com/MoisesArruda/Deploy_GPT_Azure/assets/107249412/36d732dc-5ea8-44ef-8a84-d0120001b2f7)

## Criando sua imagem docker.

No terminal de comando faça as seguintes operações para criar sua imagem:

```docker build -t chatbot_gpt```

Para visualizar se sua imagem foi criada corretamente:

```docker images```

![Docker images]()

## Rodando o container docker.

Rode o container para verificar se está como o esperado:

'''docker run -it chatbot_gpt'''

## Instalação do AZURE CLI

Iremos utilizar a interface de linha de comando do Azure para criar e gerenciar recursos do Azure.

[Link para download.](https://learn.microsoft.com/pt-br/cli/azure/)

## Registros de Container no Azure

Faça a criação do seu recurso de Registro de Container na Azure, a configuração não possui nenhum ponto de atenção.

![Container Registry]()

## Registrar sua imagem

Com o recurso já criado e em sua tela inicial, vamos copiar o **servidor de logon** para utilizar futuramente.

![Servidor logon]()

Retorne ao prompt de comando para realizar o login com a azure localmente com a ajuda do Azure CLI instalado anteriormente. Coloque o nome da sua imagem e o Logon server.

'''docker tag *NomeSUAImagem* *LogonServer*/*NomeSUAImagem*:latest'''

Para visualizar a nova imagem criada.

'''docker images''' 

Realizar login na Azure com a ajuda do Azure CLI instalado anteriormente.

'''docker login *LogonServer*'''

Após isso ele vai pedir o usuário e a senha, essas informações podem ser obtidas indo em **Chaves de acesso**.

![Azure logon]()

Enviar sua imagem para a cloud Azure.

'''docker push *NomeNOVAImagem*:latest'''

Procure por **Repositórios** e verifique se sua imagem está lá.

![Repositórios]()


## Aplicativo de Container

As seguintes configurações são necessárias para a criação correta do recurso:

1. Página de **Contêiner**:

- Desmarcar **Usar imagem de início rápido**
- Preencher os seguintes campos de **Detalhes do contêiner**
  
![Container app ]()

2. Página de **Entrada**

- Habilitar **Ingresso**
- Selecionar **Aceitando tráfego de qualquer lugar**
- em **Porta de destino** colocar 8501

![Container app ]()

3. Recurso criado.

![Container app 3]()
