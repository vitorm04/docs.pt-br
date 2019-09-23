---
title: Combinando contêineres e abordagens sem servidor
description: Combinando contêineres e kubernetes com abordagens sem servidor
ms.date: 06/30/2019
ms.openlocfilehash: 58aff43adbdd2e629370cc685f32c7b61c25f85e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183430"
---
# <a name="combining-containers-and-serverless-approaches"></a>Combinando contêineres e abordagens sem servidor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Frequentemente, aplicativos baseados em microserviços dependem muito de contêineres, orquestração e passagem de mensagens para comunicação entre nós. Esse sistema de mensagens é uma tarefa ideal para Azure Functions, mas com o restante do aplicativo configurado e implantado usando kubernetes e ferramentas relacionadas, seria interessante poder aproveitar Azure Functions dentro desse mesmo conjunto de ferramentas. Felizmente, você pode encapsular Azure Functions em contêineres do Docker e implantá-los usando os mesmos processos e ferramentas que o restante de seu aplicativo baseado em kubernetes.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Quando faz sentido usar contêineres sem servidor?

Por padrão, suas funções sem servidor não têm conhecimento da plataforma na qual elas serão executadas. No entanto, em alguns casos, você pode ter requisitos específicos que o tornam importante para você personalizar a imagem de contêiner na qual seu código será executado. Talvez você queira usar uma imagem personalizada porque sua função depende de uma versão de idioma específica ou tem dependências ou requisitos de configuração que não têm suporte na imagem padrão. Nesses casos, pode fazer sentido personalizar seu próprio contêiner e implantar sua função em um contêiner personalizado do Docker.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Quando você deve evitar o uso de contêineres com Azure Functions?

Se você estiver esperando se beneficiar da cobrança do plano de consumo para sua função, não poderá fazer isso se estiver usando seu próprio contêiner. Além disso, se você terminar de usar apenas um contêiner do Docker e implantar suas funções em seu próprio cluster kubernetes, você não se beneficiará mais do dimensionamento interno fornecido pelo Azure Functions. Você precisará usar os recursos de dimensionamento do kubernetes, descritos abaixo.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Como combinar contêineres sem servidor e Docker

Para encapsular uma função do Azure em um contêiner do Docker, instale o Azure Functions Core Tools e, em seguida, execute o seguinte comando:

```console
func init ProjectName --docker
```

Escolha qual tempo de execução de trabalho você deseja nas seguintes opções:

- `dotnet` (C#)
- `node` (JavaScript)
- `python`

Quando o projeto for criado, ele incluirá um Dockerfile. Agora, você pode criar e testar sua função localmente. Compile e execute-o usando `docker build` os `docker run` comandos e. Para obter etapas detalhadas para começar a criar Azure Functions com o suporte do Docker, consulte o tutorial [criar uma função no Linux usando uma imagem personalizada](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) .

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>Como combinar servidores e kubernetes com KEDA

O Azure Functions é dimensionado automaticamente para atender à demanda com base na taxa de eventos que se destinam a uma determinada função. Além disso, você pode aproveitar o kubernetes para hospedar suas funções e usar o dimensionamento automático controlado por evento baseado em kubernetes ou o KEDA. Quando nenhum evento está ocorrendo, o KEDA pode ser reduzido para 0 instâncias e, em seguida, em resposta a eventos, ele pode escalar verticalmente o número de contêineres para atender à demanda usando o dimensionamento em escala do pod horizontal. [Saiba mais sobre como dimensionar o Azure Functions com o Keda](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).

## <a name="references"></a>Referências

- [Executar Azure Functions em um contêiner do Docker](https://markheath.net/post/azure-functions-docker)
- [Criar uma função no Linux usando uma imagem personalizada](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Azure Functions com dimensionamento automático controlado por evento kubernetes](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)

>[!div class="step-by-step"]
>[Anterior](leverage-serverless-functions.md)
>[Próximo](deploy-containers-azure.md)
