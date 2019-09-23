---
title: Outras opções de implantação de contêiner
description: Outras opções de implantação de contêiner usando o Azure
ms.date: 06/30/2019
ms.openlocfilehash: 892514417cb8650c28b7491315f767758278ad6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184879"
---
# <a name="other-container-deployment-options"></a>Outras opções de implantação de contêiner

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Além de implantar no AKS, você também pode implantar contêineres no serviço Azure App para contêineres e instâncias de contêiner do Azure.

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>Quando faz sentido implantar no serviço de aplicativo para contêineres?

Aplicativos de produção simples que não exigem orquestração são adequados para Azure App serviço para contêineres.

## <a name="how-to-deploy-to-app-service-for-containers"></a>Como implantar no serviço de aplicativo para contêineres

Para implantar o [serviço de Azure app para contêineres](https://azure.microsoft.com/services/app-service/containers/), você precisa ter configurado um ACR (registro de contêiner do Azure) e credenciais para acessá-lo. Envie por push o contêiner que você pretende hospedar no registro para que ele esteja disponível para efetuar pull em seu serviço de Azure App. Depois de criado, você pode configurar o aplicativo para implantação contínua, que implantará automaticamente atualizações no aplicativo sempre que você atualizar sua imagem correspondente no ACR.

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>Quando faz sentido implantar em instâncias de contêiner do Azure?

As instâncias de contêiner do Azure são mais bem usadas para cenários de teste. Eles fornecem uma maneira rápida e simples de implantar um aplicativo em uma instância de contêiner hospedada na nuvem. Use-os para testar ou demonstrar aplicativos quando você não precisar de recursos de dimensionamento e de orquestração oferecidos pelo serviço kubernetes do Azure.

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>Como implantar um aplicativo em instâncias de contêiner do Azure

Para implantar as [ACI (instâncias de contêiner do Azure)](https://docs.microsoft.com/azure/container-instances/), você precisa ter configurado um ACR (registro de contêiner do Azure) e credenciais para acessá-lo. Você também deve ter enviado anteriormente a imagem de contêiner para o registro, portanto, ele está disponível para efetuar pull no ACI. Você pode trabalhar com ACI usando o CLI do Azure ou por meio do Portal. Os registros de contêiner do Azure facilitam a implantação de instâncias de contêiner individuais para ACI diretamente de dentro do registro, como mostra a Figura 3-14.

![Instância de execução do registro de contêiner do Azure](./media/acr-runinstance-contextmenu.png)

**Figura 3-14**. Instância de execução do registro de contêiner do Azure

A criação de uma instância de contêiner a partir do registro requer apenas que você especifique as configurações usuais do Azure (nome, assinatura, grupo de recursos e local), a quantidade de memória a ser alocada ao contêiner e a qual porta ela deve escutar. Este guia [de início rápido mostra como implantar uma instância de contêiner no ACI usando o portal do Azure](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).

Quando a implantação for concluída, localize o endereço IP do contêiner implantado recentemente e comunique-se com ele pela porta especificada.

As instâncias de contêiner do Azure oferecem a maneira mais rápida e simples de executar um contêiner no Azure. Não há necessidade de configurar um serviço de aplicativo ou um orquestrador ou para lidar com máquinas virtuais. No entanto, devido à sua simplicidade, o ACI deve ser usado principalmente para fins de teste. Se seu aplicativo requer escalabilidade automática, vários contêineres configurados para trabalhar juntos ou quaisquer recursos complexos adicionais, há outros serviços do Azure mais adequados disponíveis para hospedar seu aplicativo.

## <a name="references"></a>Referências

- [Documentos de instâncias de contêiner do Azure](https://docs.microsoft.com/azure/container-instances/)
- [Implantar instância de contêiner do ACR](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[Anterior](scale-containers-serverless.md)
>[Próximo](communication-patterns.md) <!-- Next Chapter -->
