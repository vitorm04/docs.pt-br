---
title: Dimensionamento de aplicativos nativos de nuvem
description: Dimensionamento de aplicativos nativos de nuvem com o serviço kubernetes do Azure e o Azure Functions para atender à demanda do usuário de maneira econômica.
ms.date: 04/13/2020
ms.openlocfilehash: 91d925778e9dfcf8a1ec2486fe8961037409f207
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199931"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="6ebcc-103">Dimensionamento de aplicativos nativos de nuvem</span><span class="sxs-lookup"><span data-stu-id="6ebcc-103">Scaling cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6ebcc-104">Uma das vantagens mais frequentes de mudar para um ambiente de Hospedagem de nuvem é a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="6ebcc-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="6ebcc-105">Escalabilidade ou a capacidade de um aplicativo aceitar a carga adicional do usuário sem comprometer o desempenho de cada usuário.</span><span class="sxs-lookup"><span data-stu-id="6ebcc-105">Scalability, or the ability for an application to accept additional user load without compromising performance for each user.</span></span> <span data-ttu-id="6ebcc-106">Ele é mais frequentemente obtido com a divisão de um aplicativo em pequenas partes que podem receber quaisquer recursos necessários.</span><span class="sxs-lookup"><span data-stu-id="6ebcc-106">It's most often achieved by breaking up an application into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="6ebcc-107">Os fornecedores de nuvem permitem grande escalabilidade a qualquer momento e em qualquer lugar do mundo.</span><span class="sxs-lookup"><span data-stu-id="6ebcc-107">Cloud vendors enable massive scalability anytime and anywhere in the world.</span></span>

 <span data-ttu-id="6ebcc-108">Neste capítulo, discutiremos tecnologias que permitem que aplicativos nativos de nuvem sejam dimensionados para atender à demanda do usuário.</span><span class="sxs-lookup"><span data-stu-id="6ebcc-108">In this chapter, we discuss technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="6ebcc-109">Essas tecnologias incluem:</span><span class="sxs-lookup"><span data-stu-id="6ebcc-109">These technologies include:</span></span>

- <span data-ttu-id="6ebcc-110">Contêineres</span><span class="sxs-lookup"><span data-stu-id="6ebcc-110">Containers</span></span>
- <span data-ttu-id="6ebcc-111">Orquestradores</span><span class="sxs-lookup"><span data-stu-id="6ebcc-111">Orchestrators</span></span>
- <span data-ttu-id="6ebcc-112">Computação sem servidor</span><span class="sxs-lookup"><span data-stu-id="6ebcc-112">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6ebcc-113">[Anterior](centralized-configuration.md)
>[próximo](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="6ebcc-113">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
