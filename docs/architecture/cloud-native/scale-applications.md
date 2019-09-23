---
title: Dimensionamento de aplicativos nativos de nuvem
description: Dimensionamento de aplicativos nativos de nuvem com o serviço kubernetes do Azure e o Azure Functions para atender à demanda do usuário de maneira econômica.
ms.date: 09/23/2019
ms.openlocfilehash: 5f4aac5804c5498c331787083c943a6ea1b69748
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184823"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="cfa04-103">Dimensionamento de aplicativos nativos de nuvem</span><span class="sxs-lookup"><span data-stu-id="cfa04-103">Scaling cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="cfa04-104">Uma das vantagens mais frequentes de mudar para um ambiente de Hospedagem de nuvem é a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="cfa04-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="cfa04-105">A escalabilidade ou a capacidade de um aplicativo de aceitar carga de usuário adicional sem indevidamente degradação do desempenho para cada usuário, geralmente é obtida com a divisão de aplicativos em pequenas partes que podem receber quaisquer recursos necessários.</span><span class="sxs-lookup"><span data-stu-id="cfa04-105">Scalability, or the ability for an application to accept additional user load without unduly degrading performance for each user, is most often achieved by breaking up applications into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="cfa04-106">Neste capítulo, apresentamos as tecnologias que permitem que aplicativos nativos de nuvem sejam dimensionados para atender à demanda do usuário.</span><span class="sxs-lookup"><span data-stu-id="cfa04-106">In this chapter, we introduce the technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="cfa04-107">Essas tecnologias incluem:</span><span class="sxs-lookup"><span data-stu-id="cfa04-107">These technologies include:</span></span>

- <span data-ttu-id="cfa04-108">Contêineres</span><span class="sxs-lookup"><span data-stu-id="cfa04-108">Containers</span></span>
- <span data-ttu-id="cfa04-109">Orquestradores</span><span class="sxs-lookup"><span data-stu-id="cfa04-109">Orchestrators</span></span>
- <span data-ttu-id="cfa04-110">Computação sem servidor</span><span class="sxs-lookup"><span data-stu-id="cfa04-110">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cfa04-111">[Anterior](centralized-configuration.md)
>[Próximo](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="cfa04-111">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
