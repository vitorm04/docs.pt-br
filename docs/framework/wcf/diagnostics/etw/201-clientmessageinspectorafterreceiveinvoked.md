---
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 213808824051c812717e1e5b1f379be63824e255
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="dea05-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="dea05-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="dea05-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="dea05-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dea05-104">ID</span><span class="sxs-lookup"><span data-stu-id="dea05-104">ID</span></span>|<span data-ttu-id="dea05-105">201</span><span class="sxs-lookup"><span data-stu-id="dea05-105">201</span></span>|  
|<span data-ttu-id="dea05-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="dea05-106">Keywords</span></span>|<span data-ttu-id="dea05-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dea05-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="dea05-108">Nível</span><span class="sxs-lookup"><span data-stu-id="dea05-108">Level</span></span>|<span data-ttu-id="dea05-109">Informações</span><span class="sxs-lookup"><span data-stu-id="dea05-109">Information</span></span>|  
|<span data-ttu-id="dea05-110">Canal</span><span class="sxs-lookup"><span data-stu-id="dea05-110">Channel</span></span>|<span data-ttu-id="dea05-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="dea05-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dea05-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="dea05-112">Description</span></span>  
 <span data-ttu-id="dea05-113">Esse evento é emitido após o modelo de serviço foi invocado o `AfterReceiveReply` método em um Inspetor de mensagem do cliente.</span><span class="sxs-lookup"><span data-stu-id="dea05-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dea05-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="dea05-114">Message</span></span>  
 <span data-ttu-id="dea05-115">O Dispatcher invocou 'AfterReceiveReply' em um ClientMessageInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="dea05-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dea05-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="dea05-116">Details</span></span>  
  
|<span data-ttu-id="dea05-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="dea05-117">Data Item Name</span></span>|<span data-ttu-id="dea05-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="dea05-118">Data Item Type</span></span>|<span data-ttu-id="dea05-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="dea05-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dea05-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="dea05-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="dea05-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="dea05-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="dea05-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="dea05-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="dea05-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="dea05-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="dea05-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="dea05-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="dea05-125">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="dea05-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="dea05-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dea05-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dea05-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dea05-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
