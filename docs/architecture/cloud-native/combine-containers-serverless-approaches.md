---
title: Combinando contêineres e abordagens sem servidor para serviços nativos de nuvem
description: Combinando contêineres e kubernetes com abordagens sem servidor
ms.date: 04/23/2020
ms.openlocfilehash: fe9e9fd5d07132971d64bc6433a762fb7bd22048
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199658"
---
# <a name="combining-containers-and-serverless-approaches"></a>Como combinar contêineres e abordagens sem servidor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplicativos nativos de nuvem normalmente implementam serviços que aproveitam contêineres e orquestração. Muitas vezes, há oportunidades para expor alguns dos serviços do aplicativo como Azure Functions. No entanto, com um aplicativo nativo de nuvem implantado no kubernetes, seria interessante aproveitar Azure Functions dentro desse mesmo conjunto de ferramentas. Felizmente, você pode encapsular Azure Functions dentro de contêineres do Docker e implantá-los usando os mesmos processos e ferramentas que o restante de seu aplicativo baseado em kubernetes.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Quando faz sentido usar contêineres sem servidor?

Sua função do Azure não tem conhecimento da plataforma na qual ela está implantada. Para alguns cenários, você pode ter requisitos específicos e precisa personalizar o ambiente no qual o código de função será executado. Você precisará de uma imagem personalizada que dê suporte a dependências ou a uma configuração não suportada pela imagem padrão. Nesses casos, faz sentido implantar sua função em um contêiner do Docker personalizado.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Quando você deve evitar o uso de contêineres com Azure Functions?

Se você quiser usar a cobrança de consumo, não poderá executar sua função em um contêiner. Além disso, se você implantar sua função em um cluster kubernetes, não se beneficiará mais do dimensionamento interno fornecido pelo Azure Functions. Você precisará usar os recursos de dimensionamento do kubernetes, descritos anteriormente neste capítulo.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Como combinar contêineres sem servidor e Docker

Para encapsular uma função do Azure em um contêiner do Docker, instale o [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) e, em seguida, execute o seguinte comando:

```console
func init ProjectName --worker-runtime dotnet --docker
```

Quando o projeto for criado, ele incluirá um Dockerfile e o tempo de execução de `dotnet`trabalho configurado como. Agora, você pode criar e testar sua função localmente. Compile e execute-o usando `docker build` os `docker run` comandos e. Para obter etapas detalhadas para começar a criar Azure Functions com o suporte do Docker, consulte o tutorial [criar uma função no Linux usando uma imagem personalizada](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) .

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>Como combinar servidores e kubernetes com KEDA

O Azure Functions é dimensionado automaticamente para atender à demanda com base na taxa de eventos que o direcionam. Você sempre pode aproveitar o AKS para hospedar suas funções e usar o dimensionamento automático controlado por evento baseado em kubernetes ou o KEDA. Quando nenhum evento está ocorrendo, KEDA pode reduzir verticalmente até zero instâncias. [Saiba mais sobre como dimensionar o Azure Functions com o Keda](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).

>[!div class="step-by-step"]
>[Anterior](leverage-serverless-functions.md)
>[próximo](deploy-containers-azure.md)
