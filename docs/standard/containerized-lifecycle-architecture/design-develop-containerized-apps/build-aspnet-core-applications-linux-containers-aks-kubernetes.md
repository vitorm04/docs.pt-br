---
title: Criar aplicativos ASP.NET Core 2.2 implantados como contêineres do Linux nos clusters do AKS/Kubernetes
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
ms.date: 02/25/2019
ms.openlocfilehash: 89843e0041c12f001f974360da2e5903499155d1
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644790"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Criar aplicativos ASP.NET Core 2.2 implantados como contêineres do Linux em um orquestrador do AKS/Kubernetes

O AKS (Serviço de Kubernetes do Azure) é um serviço de orquestração do Kubernetes gerenciado pelo Azure que simplifica o gerenciamento e a implantação de contêiner.

Os principais recursos do AKS são:

- Um plano de controle hospedado no Azure
- Atualizações automatizadas
- Autorrecuperação
- Escala configurável pelo usuário
- Uma experiência de usuário mais simples para desenvolvedores e operadores de cluster.

Os exemplos a seguir exploram a criação de um aplicativo ASP.NET Core 2.2 que é executado no Linux e implanta um cluster do AKS no Azure, enquanto o desenvolvimento é feito usando o Visual Studio 2017.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Como criar o projeto do ASP.NET Core 2.2 usando o Visual Studio 2017

O ASP.NET Core é uma plataforma de desenvolvimento de uso geral mantida pela Microsoft e pela comunidade .NET no GitHub. Ele é multiplataforma e dá suporte ao Windows, macOS e Linux, bem como pode ser usado em dispositivos, na nuvem e em cenários inseridos/de IoT.

Este exemplo usa um projeto simples com base em um modelo de API Web do Visual Studio, que não precisa de conhecimento adicional para criar o exemplo. Você só precisará criar o projeto usando um modelo padrão que inclua todos os elementos para executar um pequeno projeto com uma API REST, usando a tecnologia ASP.NET Core 2.2.

![Adicione uma nova janela de projeto no Visual Studio selecionando o aplicativo Web ASP.NET Core.](media/create-aspnet-core-application.png)

**Figura 4-36**. Como criar um aplicativo ASP.NET Core

Para criar o projeto de exemplo no Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**, selecione os tipos de projeto **Web** no painel esquerdo, seguido por **Aplicativo Web ASP.NET Core**.

O Visual Studio lista modelos para projetos Web. Para nosso exemplo, selecione **API** para criar um aplicativo ASP.NET Web API.

Verifique se você selecionou o ASP.NET Core 2.2 como a estrutura. O .NET Core 2.2 é incluído na última versão do Visual Studio 2017 e é automaticamente instalado e configurado quando você instala o Visual Studio 2017.

![Caixa de diálogo do Visual Studio para selecionar o tipo de um aplicativo Web do ASP.NET Core com a opção de API selecionada.](media/create-web-api-application.png)

**Figura 4-37**. Como selecionar o tipo de projeto do ASP.NET CORE 2.2 e de API Web

Se você tiver uma versão anterior do .NET Core, poderá baixar e instalar a versão 2.2 do <https://www.microsoft.com/net/download/core#/sdk>.

Você pode adicionar suporte ao Docker ao criar o projeto ou posteriormente, portanto, você pode converter seu projeto para Docker a qualquer momento. Para adicionar suporte ao Docker após a criação do projeto, clique com o botão direito do mouse no nó do projeto no Gerenciador de Soluções e selecione **Adicionar** > **Suporte ao Docker** no menu de contexto.

![Opção do menu de contexto para adicionar suporte ao Docker a um projeto existente: Clique com o botão direito do mouse (no projeto) > Adicionar > Suporte do Docker.](media/add-docker-support-to-project.png)

**Figura 4-38**. Como adicionar suporte ao Docker ao projeto existente

Para concluir a adição de suporte ao Docker, você pode escolher Windows ou Linux. Nesse caso, selecione **Linux**, porque o AKS não é compatível com contêineres do Windows (como o de 2018).

![Caixa de diálogo de opção para selecionar o sistema operacional de destino para o Dockerfile.](media/select-linux-docker-support.png)

**Figura 4-39**. Como selecionar contêineres do Linux.

Com estas etapas simples, você tem seu aplicativo ASP.NET Core 2.2 em execução em um contêiner do Linux.

Como é possível ver, a integração entre o Visual Studio 2017 e o Docker é totalmente orientada à produtividade do desenvolvedor.

Agora você pode executar seu aplicativo com a tecla **F5** ou usando o botão **Executar**.

Depois de executar o projeto, você pode listar as imagens usando o comando `docker images`. Você deve ver a imagem `mssampleapplication` criada pela implantação automática do nosso projeto com o Visual Studio 2017.

```console
docker images
```

![A saída de console do comando de imagens do Docker mostra uma lista com: Repositório, Marca, ID da imagem, Criado (data) e Tamanho.](media/docker-images-command.png)

**Figura 4-40**. Exibição de imagens do Docker

## <a name="register-the-solution-in-the-azure-container-registry"></a>Registrar a solução no Registro de Contêiner do Azure

Carregue a imagem em um registro do Docker, como o [ACR (Registro de Contêiner do Azure)](https://azure.microsoft.com/services/container-registry/), ou Docker Hub, para que as imagens possam ser implantadas no cluster do AKS desse registro. Neste caso, estamos carregando a imagem para um Registro de Contêiner do Azure.

### <a name="create-the-image-in-release-mode"></a>Criar a imagem no modo de versão

Agora vamos criar a imagem no modo de **Versão** (pronto para produção), alterando para **Versão**, conforme mostrado na Figura 4-41, e executando o aplicativo como fizemos antes.

![Opção de barra de ferramentas no VS para build no modo de versão.](media/select-release-mode.png)

**Figura 4-41**. Como selecionar o modo de versão

Se executar o comando `docker image`, você verá as duas imagens criadas, uma para `debug` e a outra para o modo `release`.

### <a name="create-a-new-tag-for-the-image"></a>Criar uma marca para a imagem

Cada imagem de contêiner precisa ser marcada com o nome do `loginServer` do registro. Essa marca é usada para roteamento ao enviar imagens de contêiner por push a um registro da imagem.

Você pode exibir o nome `loginServer` do portal do Azure com as informações do Registro de Contêiner do Azure

![Exibição de navegador do nome do registro de contêiner do Azure, no canto superior direito.](media/loginServer-name.png)

**Figura 4-42**. Exibição do nome do Registro

Ou executando o seguinte comando:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Saída do console do comando acima.](media/az-cli-loginServer-name.png)

**Figura 4-43**. Obtenha o nome do registro usando o PowerShell

Em ambos os casos, você obterá o nome. Em nosso exemplo, `mssampleacr.azurecr.io`.

Agora você pode marcar a imagem, usando a imagem mais recente (a imagem de versão), com o comando:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Depois de executar o comando `docker tag`, liste as imagens com o comando `docker images` e você deverá ver a imagem com a nova marca.

![Saída de console do comando de imagens do Docker.](media/tagged-docker-images-list.png)

**Figura 4-44**. Exibição de imagens marcadas

### <a name="push-the-image-into-the-azure-acr"></a>Efetue push da imagem no ACR do Azure

Faça logon no Registro de Contêiner do Azure

```console
az acr login --name mssampleacr
```

Efetue push da imagem no ACR do Azure usando o seguinte comando:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Esse comando demora um pouco para carregar as imagens, mas fornece comentários sobre o processo.

![Saída de console do comando docker push: mostra uma barra de progresso com base em caracteres para cada camada.](media/uploading-image-to-acr.png)

**Figura 4-45**. Como carregar a imagem no ACR

É possível ver abaixo o resultado que será obtido quando o processo for concluído:

![Saída de console do comando docker push, concluída, mostrando todas as camadas ou nós.](media/uploading-docker-images-complete.png)

**Figura 4-46**. Exibição de nós

A próxima etapa é implantar seu contêiner no cluster de AKS do Kubernetes. Para fazer isso, você precisa de um arquivo (**arquivo de implantação .yml**) que contém o seguinte:

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
        - name: mssample-services-app
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
> Para obter mais informações sobre implantação com o Kubernetes, consulte: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Agora você está quase pronto para implantar usando **Kubectl**, mas primeiro você deve obter as credenciais para o Cluster do AKS com este comando:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Saída de console do comando acima: "MSSampleK8Cluster mesclado como o contexto atual em /root/.kube/config](media/getting-aks-credentials.png)

**Figura 4-47**. Como obter credenciais

Em seguida, use o comando `kubectl create` para iniciar a implantação.

```console
kubectl create -f mssample-deploy.yml
```

![Saída de console do comando acima: implantação "mssamplesbook" criada. serviço "mssample-kub-app" criado.](media/kubectl-create-command.png)

**Figura 4-48**. Implantar para o Kubernetes

Quando a implantação for concluída, você poderá acessar o console do Kubernetes com um proxy local que pode ser acessado temporariamente com este comando:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

E acessar a URL `http://127.0.0.1:8001`.

![Exibição de navegador do painel do Kubernetes mostrando Implantações, Pods, Conjuntos de Réplicas e Serviços.](media/kubernetes-cluster-information.png)

**Figura 4-49**. Exibição de informações de cluster do Kubernetes

Agora você tem seu aplicativo implantado no Azure usando um contêiner do Linux e um Cluster de Kubernetes do AKS. Você pode acessar seu aplicativo navegando até o IP público do seu serviço, que pode ser obtido do portal do Azure.

> [!NOTE]
> Você pode ver como criar o Cluster do AKS para esta amostra na seção [**Implantar no AKS (Serviço de Kubernetes do Azure)** ](deploy-azure-kubernetes-service.md) neste guia.

>[!div class="step-by-step"]
>[Anterior](set-up-windows-containers-with-powershell.md)
>[Próximo](../docker-devops-workflow/index.md)
