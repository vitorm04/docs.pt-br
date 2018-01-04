---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a25315a6008be69aeb534b8bf26c0e813c00c01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="79678-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="79678-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="79678-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="79678-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79678-104">ID</span><span class="sxs-lookup"><span data-stu-id="79678-104">ID</span></span>|<span data-ttu-id="79678-105">204</span><span class="sxs-lookup"><span data-stu-id="79678-105">204</span></span>|  
|<span data-ttu-id="79678-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="79678-106">Keywords</span></span>|<span data-ttu-id="79678-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="79678-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="79678-108">Nível</span><span class="sxs-lookup"><span data-stu-id="79678-108">Level</span></span>|<span data-ttu-id="79678-109">Informações</span><span class="sxs-lookup"><span data-stu-id="79678-109">Information</span></span>|  
|<span data-ttu-id="79678-110">Canal</span><span class="sxs-lookup"><span data-stu-id="79678-110">Channel</span></span>|<span data-ttu-id="79678-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="79678-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="79678-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="79678-112">Description</span></span>  
 <span data-ttu-id="79678-113">Esse evento é emitido após o modelo de serviço foi invocado o `BeforeCall` método em um Inspetor de parâmetro do cliente.</span><span class="sxs-lookup"><span data-stu-id="79678-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="79678-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="79678-114">Message</span></span>  
 <span data-ttu-id="79678-115">O Dispatcher invocou 'BeforeCall' em um ClientParameterInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="79678-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="79678-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="79678-116">Details</span></span>  
  
|<span data-ttu-id="79678-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="79678-117">Data Item Name</span></span>|<span data-ttu-id="79678-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="79678-118">Data Item Type</span></span>|<span data-ttu-id="79678-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="79678-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="79678-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="79678-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="79678-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="79678-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="79678-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="79678-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="79678-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="79678-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="79678-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="79678-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="79678-125">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="79678-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="79678-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="79678-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="79678-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="79678-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
