---
title: Criar aplicativos ASP.NET Core 2.1 implantados como contêineres do Linux em clusters AKS/Kubernetes
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/25/2019
ms.openlocfilehash: c6d778d345466b1b852d06bc01ce40ccfdebf964
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052737"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Criar aplicativos ASP.NET Core 2.1 implantados como contêineres do Linux em um orquestrador AKS/Kubernetes

Serviços de Kubernetes do Azure (AKS) é gerenciado Kubernetes orquestrações os serviços do Azure que simplificam o gerenciamento e implantação de contêiner.

Principais recursos do AKS são:

- Um plano de controle hospedado no Azure
- Atualizações automatizadas
- Autorrecuperação
- Dimensionamento configuráveis do usuário
- Uma experiência de usuário mais simples para desenvolvedores e operadores do cluster.

Os exemplos a seguir explorar a criação de um aplicativo ASP.NET Core 2.1 é executado no Linux e implanta um Cluster AKS no Azure, enquanto o desenvolvimento é feito usando o Visual Studio 2017.

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a>Criando o projeto do ASP.NET Core 2.1 usando o Visual Studio 2017

ASP.NET Core é uma plataforma de desenvolvimento de uso geral mantida pela Microsoft e pela comunidade .NET no GitHub. Ele é multiplataforma, que dão suporte a Windows, macOS e Linux e pode ser usado em cenários inseridos/IoT, nuvem e dispositivo.

Este exemplo usa um projeto simples com base em um modelo de API de Web do Visual Studio, que exige qualquer conhecimento adicional para criar o exemplo. Você só precisará criar o projeto usando um modelo padrão que inclui todos os elementos para executar um pequeno projeto com uma API REST, usando a tecnologia ASP.NET Core 2.1.

![Adicione janela novo projeto no Visual Studio, selecionando o aplicativo Web ASP.NET Core.](media/create-aspnet-core-application.png)

**Figura 4 a 36**. Criando um aplicativo ASP.NET Core

Para criar o projeto de exemplo no Visual Studio, selecione **arquivo** > **New** > **projeto**, selecione o **Web**tipos de projeto no painel esquerdo, seguido por **aplicativo Web ASP.NET Core**.

Visual Studio contém modelos para projetos web. Para nosso exemplo, selecione **API** para criar um aplicativo de API Web ASP.NET.

Verifique se que você tenha selecionado o ASP.NET Core 2.1 como a estrutura. .NET core 2.1 está incluído na última versão do Visual Studio 2017 e é automaticamente instalado e configurado para você quando você instala o Visual Studio 2017.

![Visual Studio caixa de diálogo para selecionar o tipo de um aplicativo Web do ASP.NET Core com a opção de API selecionada.](media/create-web-api-application.png)

**Figura 4-37**. Tipo de projeto do ASP.NET CORE 2.1 selecionando e API da Web

Se você tiver qualquer versão anterior do .NET Core, você pode baixar e instalar a versão 2.1 do <https://www.microsoft.com/net/download/core#/sdk>.

Você pode adicionar suporte ao Docker ao criar o projeto ou posteriormente, portanto, você pode "colocar no Docker" seu projeto a qualquer momento. Para adicionar suporte ao Docker após a criação do projeto, clique com botão direito no nó do projeto no Gerenciador de soluções e selecione **Add** > **suporte ao Docker** no menu de contexto.

![Opção de menu de contexto para adicionar suporte ao Docker a um projeto existente: Clique com botão direito (no projeto) > Adicionar > suporte do Docker.](media/add-docker-support-to-project.png)

**Figura 4-38**. Adicionando suporte ao Docker ao projeto existente

Para concluir a adição de suporte ao Docker, você pode escolher Windows ou Linux. Nesse caso, selecione **Linux**, porque o AKS não dá suporte a contêineres do Windows (como o final de 2018).

![Caixa de diálogo de opção para selecionar o sistema operacional de destino para o Dockerfile.](media/select-linux-docker-support.png)

**Figura 4-39**. Selecionando os contêineres do Linux.

Com estas etapas simples, você precisa de seu aplicativo ASP.NET Core 2.1 em execução em um contêiner do Linux.

Como você pode ver, a integração entre o Visual Studio 2017 e o Docker é totalmente orientada à produtividade do desenvolvedor.

Agora você pode executar seu aplicativo com o **F5** da chave ou usando o **reproduzir** botão.

Depois de executar o projeto, você pode listar as imagens usando o `docker images` comando. Você deve ver o `mssampleapplication` imagem criada pela implantação automática do nosso projeto no Visual Studio 2017.

```console
docker images
```

![Console de saída do comando de imagens do docker, mostra uma lista com: Repositório, marca, ID da imagem, criado (Data) e tamanho.](media/docker-images-command.png)

**Figura 4-40**. Modo de exibição de imagens do Docker

## <a name="register-the-solution-in-the-azure-container-registry"></a>Registre-se a solução no registro de contêiner do Azure

Carregar a imagem em qualquer registro do Docker, como [registro de contêiner do Azure (ACR)](https://azure.microsoft.com/services/container-registry/) ou Hub do Docker, portanto, as imagens podem ser implantadas no cluster AKS de que o registro. Nesse caso, estamos está carregando a imagem no registro de contêiner do Azure.

### <a name="create-the-image-in-release-mode"></a>Criar a imagem no modo de versão

Agora, vamos criar a imagem no **Release** modo (pronto para produção), alterando para **versão**, conforme mostrado na Figura 4-41 e a execução do aplicativo, como fizemos antes.

![Opção de barra de ferramentas no VS para compilar no modo de versão.](media/select-release-mode.png)

**Figura 4-41**. Selecionar modo de versão

Se você executar o `docker image` comando, você verá as duas imagens criadas, um para `debug` e o outro para `release` modo.

### <a name="create-a-new-tag-for-the-image"></a>Criar uma nova marca para a imagem

Cada imagem de contêiner precisa ser marcada com o `loginServer` nome do registro. Essa marca é usada para roteamento ao enviar imagens de contêiner para um registro de imagem.

Você pode exibir o `loginServer` nome do portal do Azure, levando as informações do registro de contêiner do Azure

![Exibição de navegador do nome do registro de contêiner do Azure, no canto superior direito.](media/loginServer-name.png)

**Figura 4-42**. Modo de exibição do nome do registro

Ou executando o seguinte comando:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Console de saída do comando acima.](media/az-cli-loginServer-name.png)

**Figura 4-43**. Obter o nome do registro usando o PowerShell

Em ambos os casos, você obterá o nome. Em nosso exemplo, `mssampleacr.azurecr.io`.

Agora você pode marcar a imagem, levando a imagem mais recente (a imagem de versão), com o comando:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Depois de executar o `docker tag` de comando, liste as imagens com o `docker images` comando e você deverá ver a imagem com a nova marca.

![Console de saída do comando de imagens do docker.](media/tagged-docker-images-list.png)

**Figura 4-44**. Modo de exibição de imagens marcadas

### <a name="push-the-image-into-the-azure-acr"></a>A imagem por push o ACR do Azure

Envie a imagem no ACR do Azure, usando o seguinte comando:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Esse comando leva algum tempo, mas fornece comentários no processo de carregamento das imagens.

![Saída do comando docker por push do console: mostra uma barra de progresso com base em caracteres para cada camada.](media/uploading-image-to-acr.png)

**Figura 4-45**. Carregando a imagem no ACR

Você pode ver abaixo o resultado que deve ser obter quando o processo for concluído:

![O comando de envio por push do docker, concluído, mostrando todas as camadas ou nós de saída de console.](media/uploading-docker-images-complete.png)

**Figura 4-46**. Exibição de nós

A próxima etapa é implantar seu contêiner em seu cluster AKS Kubernetes. Para fazer isso, você precisa de um arquivo (**implantar o arquivo. yml**) que contém o seguinte:

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - mane: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> Para obter mais informações sobre a implantação com Kubernetes, consulte: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Agora você está quase pronto para implantar usando **Kubectl**, mas primeiro você deve obter as credenciais para o Cluster do AKS com este comando:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Console de saída do comando acima: Mesclado "MSSampleK8Cluster como o contexto atual no /root/.kube/config](media/getting-aks-credentials.png)

**Figura 4-47**. obtenção de credenciais

Em seguida, use o `kubectl create` comando para iniciar a implantação.

```console
kubectl create -f mssample-deploy.yml
```

![Saída do comando acima do console: implantação "mssamplesbook" foi criado. serviço de "mssample-kub-app" criado.](media/kubectl-create-command.png)

**Figura 4-48**. Implantar no Kubernetes

Quando a implantação for concluída, você pode acessar o console do Kubernetes com um proxy local que você pode acessar temporariamente com este comando:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

E acessar a url `http://127.0.0.1:8001`.

![Exibição de navegador do painel do Kubernetes, mostrando os Pods, implantações, conjuntos de réplicas e serviços.](media/kubernetes-cluster-information.png)

**Figura 4-49**. Exibir informações de cluster do Kubernetes

Agora você tem o seu aplicativo estiver implantado no Azure, usando um contêiner do Linux e um Cluster do AKS Kubernetes. Você pode acessar seu aplicativo navegando até o IP público do seu serviço, que pode ser obtido do portal do Azure.

> [!NOTE]
> Você pode ver como criar o Cluster do AKS para este exemplo na seção [ **implantar para o serviço de Kubernetes do Azure (AKS)** ](deploy-azure-kubernetes-service.md) sobre este guia.

>[!div class="step-by-step"]
>[Anterior](set-up-windows-containers-with-powershell.md)
>[Próximo](../docker-devops-workflow/index.md)
