<h1 align="center"> Fazendo deploy da sua solução GPT na Azure. </h1>
Este repositório tem o objetivo de compartilhar a implementação de uma solução utilizando um modelo de LLM na cloud Azure. Como forma de representação, pode utilizar o link abaixo para acessar o repositório que contém uma solução para realizar os passos a seguir.

[Acesso aqui o repositório 📁](https://github.com/MoisesArruda/GPT_Streamlit_FAISS)

## DockerFile.

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

[Link para download.](https://learn.microsoft.com/pt-br/cli/azure/)https://learn.microsoft.com/pt-br/cli/azure/)
