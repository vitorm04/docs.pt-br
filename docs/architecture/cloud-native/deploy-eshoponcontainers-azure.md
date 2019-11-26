---
title: Como implantar o eShopOnContainers no Azure
description: Implantando o aplicativo eShopOnContainers usando o serviço kubernetes do Azure, o Helm e o DevSpaces.
ms.date: 06/30/2019
ms.openlocfilehash: 21033cc904dc595193c69f3452ce2522740f8ff6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183269"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>Como implantar o eShopOnContainers no Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

A lógica que dá suporte ao aplicativo eShopOnContainers pode ser suportada pelo Azure usando uma variedade de serviços. A abordagem recomendada é aproveitar o kubernetes usando o AKS (serviço kubernetes do Azure). Isso pode ser combinado com a implantação do Helm para garantir uma configuração de infraestrutura facilmente repetida. Opcionalmente, os desenvolvedores podem aproveitar Azure Dev Spaces para kubernetes como parte de seu processo de desenvolvimento. Outra opção é hospedar a funcionalidade do aplicativo usando recursos sem servidor do Azure, como Azure Functions e aplicativos lógicos do Azure.

## <a name="azure-kubernetes-service"></a>Serviço de Kubernetes do Azure

Se você quiser hospedar o aplicativo eShopOnContainers em seu próprio cluster AKS, a primeira etapa será criar o cluster. Você pode fazer isso usando o portal do Azure, que irá orientá-lo pelas etapas necessárias, ou você pode usar o CLI do Azure, tomando cuidado para garantir que você habilite o controle de acesso baseado em função (RBAC) e o roteamento de aplicativos quando fizer isso. A documentação do eShopOnContainers ' descreve as etapas envolvidas na criação de seu próprio cluster AKS. Depois que o cluster é criado, você deve habilitar o acesso ao painel do kubernetes, ponto em que você deve ser capaz de navegar até o painel do kubernetes para gerenciar o cluster.

Depois que o cluster tiver sido criado e configurado, você poderá implantar o aplicativo nele usando o Helm e o gaveta.

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Implantando no serviço kubernetes do Azure usando o Helm

As implantações básicas no AKS podem usar scripts CLI personalizados ou arquivos de implantação simples, mas aplicativos mais complexos devem usar uma ferramenta de gerenciamento de dependência como Helm. O Helm é mantido pela base de computação nativa em nuvem e ajuda você a definir, instalar e atualizar aplicativos kubernetes. O Helm é composto por um cliente de linha de comando, Helm, que usa gráficos do Helm e um componente no cluster, o. Os gráficos Helm usam arquivos padrão formatados por YAML para descrever um conjunto relacionado de recursos do kubernetes e são normalmente com controle de versão junto com o aplicativo que eles descrevem. Os gráficos Helm variam de simples a complexo, dependendo dos requisitos da instalação que descrevem.

Você encontrará os gráficos eShopOnContainers Helm na pasta/K8S/Helm. A Figura 2-6 mostra como os diferentes componentes do aplicativo são organizados em uma estrutura de pastas usada pelo Helm para definir e implantações gerenciadas.

![arquitetura eShopOnContainers](./media/eshoponcontainers-helm-folder.png)
**figura 2-6**. A pasta eShopOnContainers Helm

Cada componente individual é instalado usando um comando `helm install`. Esses comandos são facilmente incluídos no script e o eShopOnContainers fornece um script "implantar tudo" que faz o loop pelos diferentes componentes e os instala usando seus respectivos gráficos do Helm. O resultado é um processo repetível, com versão com o aplicativo no controle do código-fonte, que qualquer pessoa da equipe pode implantar em um cluster AKS com um comando de script de uma linha. Especialmente quando combinado com Azure Dev Spaces, isso torna mais fácil para os desenvolvedores diagnosticar e testar suas alterações individuais em seus aplicativos nativos de nuvem baseados em microserviço.

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Azure Dev Spaces ajuda os desenvolvedores individuais a hospedarem sua própria versão exclusiva dos clusters AKS no Azure durante o desenvolvimento. Isso minimiza os requisitos do computador local e permite que os membros da equipe vejam rapidamente como suas alterações se comportarão em um ambiente AKS real. O Azure Dev Spaces oferece uma CLI para que os desenvolvedores usem para gerenciar seus espaços de desenvolvimento e para implantar em um espaço de desenvolvimento filho específico, conforme necessário. Cada espaço de desenvolvimento filho é referenciado usando um subdomínio de URL exclusivo, permitindo implantações lado a lado de clusters modificados para que os desenvolvedores individuais possam evitar conflitos com o trabalho de cada um deles em andamento. Na Figura 2-7, você pode ver como o desenvolvedor Susana implantou sua própria versão do microserviço bikes em seu espaço de desenvolvimento. Em seguida, ela é capaz de testar suas alterações usando uma URL personalizada que começa com o nome de seu espaço (susie.s.dev.myapp.eus.azds.io).

![arquitetura eShopOnContainers](./media/azure-devspaces-one.png)
**figura 2-7**. O Developer Susana implanta sua própria versão do microserviço Bikes e a testa.

Ao mesmo tempo, o desenvolvedor John está Personalizando o microserviço de reservas e precisa testar suas alterações. Ele é capaz de implantar suas alterações em seu próprio espaço de desenvolvimento sem entrar em conflito com as alterações do Susana, conforme mostrado na Figura 2-8. Ele pode testar suas alterações usando sua própria URL, que é prefixada com o nome de seu espaço (john.s.dev.myapp.eus.azds.io).

![arquitetura eShopOnContainers](./media/azure-devspaces-two.png)
**figura 2-8**. O desenvolvedor John implanta sua própria versão do microserviço de reservas e a testa sem entrar em conflito com outros desenvolvedores.

Usando Azure Dev Spaces, as equipes podem trabalhar diretamente com o AKS enquanto alteram, implantam e testam suas alterações de forma independente. Essa abordagem reduz a necessidade de ambientes hospedados dedicados separados, pois cada desenvolvedor efetivamente tem seu próprio ambiente AKS. Os desenvolvedores podem trabalhar com Azure Dev Spaces usando sua CLI ou iniciar seu aplicativo para Azure Dev Spaces diretamente do Visual Studio. [Saiba mais sobre como Azure Dev Spaces funciona e está configurado.](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions e aplicativos lógicos (sem servidor)

O exemplo de eShopOnContainers inclui suporte para acompanhamento de campanhas de marketing online. Uma função do Azure é usada para receber detalhes da campanha de marketing para uma determinada ID de campanha. Em vez de criar um aplicativo ASP.NET Core completo para essa finalidade, um único ponto de extremidade do Azure function é mais simples e suficiente. Azure Functions ter um modelo de compilação e implantação muito mais simples do que aplicativos ASP.NET Core completos, especialmente quando configurados para serem executados no kubernetes. A implantação da função é inserida em script usando modelos de Azure Resource Manager (ARM) e a CLI do Azure. Este microserviço de detalhes da campanha não é voltado para o cliente e não tem os mesmos requisitos que o armazenamento online, tornando-o um bom candidato para Azure Functions. A função requer que algumas configurações funcionem corretamente, como as configurações de cadeia de caracteres de conexão de banco de dados e URI de base de imagem. Você configura Azure Functions no portal do Azure.

## <a name="references"></a>Referências

- [eShopOnContainers: criar cluster kubernetes no AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers: Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[Anterior](map-eshoponcontainers-azure-services.md)
>[Próximo](centralized-configuration.md)
