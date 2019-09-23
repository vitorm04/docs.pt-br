---
title: Implantando contêineres no Azure
description: Implantando contêineres no Azure com o registro de contêiner do Azure, serviço kubernetes do Azure e Azure Dev Spaces.
ms.date: 06/30/2019
ms.openlocfilehash: 6d95db26b6a45dd6825c88693308ffe90d1ed071
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183262"
---
# <a name="deploying-containers-in-azure"></a>Implantando contêineres no Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Os contêineres fornecem muitos benefícios, um dos quais é a portabilidade. Você pode facilmente pegar o mesmo contêiner que você desenvolveu e testou localmente e implantá-lo no Azure, em que ele pode executar seu aplicativo em ambientes de preparo e produção. O Azure fornece várias opções para hospedagem de aplicativos baseados em contêiner e, da mesma forma, dá suporte a vários meios diferentes de implantação. A abordagem mais comum e mais flexível é implantar seus contêineres no ACR (registro de contêiner do Azure), onde eles podem ser acessados por quaisquer serviços que você queira usar para hospedá-los. O Azure Aplicativo Web para Contêineres, os serviços Kubernetess do Azure (AKS) e a instância de contêiner do Azure (ACI) podem acessar imagens de contêiner que foram enviadas por push ao ACR.

## <a name="azure-container-registry"></a>Registro de Contêiner do Azure

O ACR (registro de contêiner do Azure) permite que você crie, armazene e gerencie imagens para todas as implantações de contêiner. Há outros registros de contêiner, públicos e privados, nos quais você pode implantar contêineres. O benefício do ACR em relação a outras opções é que você pode manter suas imagens próximas ao seu ambiente de produção, melhorando os tempos de compilação e implantação. Você também pode protegê-los usando os mesmos procedimentos de segurança usados para o restante dos recursos do Azure, melhorando a segurança e reduzindo o esforço de gerenciamento de ativos.

Você [cria um registro de contêiner usando o portal do Azure](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal) ou [usando as ferramentas CLI do Azure](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli) ou [PowerShell](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell). A criação de um novo registro de contêiner requer apenas uma assinatura do Azure, um grupo de recursos e um nome exclusivo. A Figura 3-11 mostra as opções básicas para criar um registro, que será hospedado em *registryname*. azurecr.IO.

![Crie o registro](./media/create-container-registry.png)
de contêiner**Figura 3-11**. Criar registro de contêiner

Depois de criar um registro, você precisará autenticar com ele antes de poder usá-lo. Normalmente, você fará logon no registro usando o comando CLI do Azure:

```azurecli
az acr login --name *registryname*
```

Depois de criar um registro no registro de contêiner do Azure, você pode usar comandos do Docker para enviar imagens de contêiner para ele. No entanto, antes de fazer isso, você deve primeiro marcar sua imagem com o nome totalmente qualificado (URL) do seu servidor de logon do ACR. Isso terá o formato *registryname*. azurecr.IO.

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

Depois de ter marcado a imagem, use o `docker push` comando para enviar a imagem por push para a instância do ACR.

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

Depois de enviar uma imagem por push para o registro, é uma boa ideia remover a imagem do ambiente do Docker local, usando este comando:

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

Os desenvolvedores raramente devem enviar por push diretamente de seus computadores para um registro de contêiner. Em vez disso, um pipeline de compilação definido em uma ferramenta como o Azure DevOps deve ser responsável por esse processo. Saiba mais no [capítulo DevOps de nuvem nativa](devops.md).

## <a name="azure-kubernetes-service"></a>Serviço de Kubernetes do Azure

Se seu aplicativo baseado em contêiner envolver vários contêineres, você provavelmente desejará definir e gerenciar as interações entre os contêineres usando um *orquestrador* como o kubernetes. Depois de implantar suas imagens de contêiner no ACR, você pode configurar facilmente os serviços Kubernetess do Azure para implantar automaticamente imagens atualizadas do ACR. Com um pipeline completo de CI/CD em vigor, você pode configurar uma estratégia de [liberação do canário](https://martinfowler.com/bliki/CanaryRelease.html) para minimizar o risco envolvido ao implantar atualizações rapidamente. A nova versão do aplicativo é inicialmente configurada em produção sem tráfego roteado para ele e, em seguida, um pequeno número de usuários é roteado para a versão implantada recentemente do aplicativo. À medida que a equipe ganha confiança na nova versão do software, mais instâncias da nova versão são distribuídas e as instâncias da versão anterior são desativadas. O AKS dá suporte facilmente a esse estilo de implantação.

Assim como acontece com a maioria dos recursos no Azure, você pode criar clusters do Azure kubernetes usando o portal ou ferramentas de linha de comando ou ferramentas de automação de infraestrutura como Helm ou Terraform. Para começar a usar um novo cluster, você precisa fornecer as seguintes informações:

- Assinatura do Azure
- Grupo de recursos
- Nome do cluster kubernetes
- Região
- Versão do kubernetes
- Prefixo do nome DNS
- Tamanho do nó
- Contagem de nós

Essas informações são suficientes para começar. Como parte do processo de criação no portal do Azure, você também pode configurar opções para os seguintes recursos do cluster:

- Dimensionar
- Autenticação
- Rede
- Monitoramento
- Marcas

Este [Guia de início rápido orienta a implantação de um cluster AKs usando o portal do Azure](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Clusters kubernetes complexos podem exigir recursos significativos para hospedar, o que pode dificultar para os desenvolvedores executarem todo o aplicativo em um único computador (especialmente um laptop). O Azure Dev Spaces oferece uma solução para isso, permitindo que os desenvolvedores trabalhem com suas próprias versões dos clusters do Azure kubernetes hospedados no Azure. O Azure Dev Spaces foi projetado para facilitar o desenvolvimento de aplicativos baseados em microserviço usando o AKS.

Para entender o valor de Azure Dev Spaces, deixe-me compartilhar essa citação de Gabe Monroy, PM Lead dos contêineres em Microsoft Azure:

"Imagine que você seja um novo funcionário tentando corrigir um bug em um aplicativo de microserviços complexos que consiste em dezenas de componentes, cada um com sua própria configuração e serviços de apoio. Para começar, você deve configurar seu ambiente de desenvolvimento local para que ele possa imitar a produção, incluindo a configuração de seu IDE, criação de cadeia de ferramentas, dependências de serviço em contêineres, um ambiente kubernetes local, simulações para fazer backup de serviços e muito mais. Com o tempo todo envolvido na configuração de seu ambiente de desenvolvimento, corrigir esse primeiro bug pode levar dias.

> Ou você pode usar espaços de desenvolvimento e AKS. "

O processo para trabalhar com Azure Dev Spaces envolve as seguintes etapas:

1. Crie o espaço de desenvolvimento.
2. Configure o espaço de desenvolvimento raiz.
3. Configure um espaço de desenvolvimento filho (para sua própria versão do sistema).
4. Conecte-se ao espaço de desenvolvimento.

Todas essas etapas podem ser executadas usando o CLI do Azure e as novas `azds` ferramentas de linha de comando. Por exemplo, para criar um novo espaço de desenvolvimento do Azure para um determinado cluster kubernetes, você usaria um comando como este:

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

Em seguida, você pode usar `azds prep` o comando para gerar os ativos necessários do Docker e do gráfico Helm para executar o aplicativo. Em seguida, você executa seu código no `azds up`AKs usando. Na primeira vez que você executar esse comando, o gráfico Helm será instalado e os contêineres serão compilados e implantados de acordo com suas instruções. Isso pode levar alguns minutos na primeira vez em que for executado. No entanto, depois de fazer alterações, você pode se conectar ao seu próprio espaço `azds space select` de desenvolvimento filho usando e, em seguida, implantar e depurar suas atualizações em seu espaço de desenvolvimento filho isolado. Depois que seu espaço de desenvolvimento estiver em funcionamento, você poderá enviar atualizações para ele emitindo novamente o comando ou `azds up` pode usar as ferramentas internas no Visual Studio ou Visual Studio Code. Com VS Code, você usa a paleta de comandos para se conectar ao seu espaço de desenvolvimento. A Figura 3-12 mostra como iniciar seu aplicativo Web usando o Azure Dev Spaces no Visual Studio.

![Conecte-se a Azure dev Spaces no](./media/azure-dev-spaces-visual-studio-launchsettings.png)
Visual Studio**Figura 3-12**. Conectar-se a Azure Dev Spaces no Visual Studio

## <a name="references"></a>Referências

- [Versão canário](https://martinfowler.com/bliki/CanaryRelease.html)
- [Azure Dev Spaces com VS Code](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [Azure Dev Spaces com o Visual Studio](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)

>[!div class="step-by-step"]
>[Anterior](combine-containers-serverless-approaches.md)
>[Próximo](scale-containers-serverless.md)
