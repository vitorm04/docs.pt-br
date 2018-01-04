---
title: 209 - MessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9083a6dc9849fcd177b1e6a38ca7bb72e7799dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="1efe7-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="1efe7-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="1efe7-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1efe7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1efe7-104">ID</span><span class="sxs-lookup"><span data-stu-id="1efe7-104">ID</span></span>|<span data-ttu-id="1efe7-105">209</span><span class="sxs-lookup"><span data-stu-id="1efe7-105">209</span></span>|  
|<span data-ttu-id="1efe7-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="1efe7-106">Keywords</span></span>|<span data-ttu-id="1efe7-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1efe7-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1efe7-108">Nível</span><span class="sxs-lookup"><span data-stu-id="1efe7-108">Level</span></span>|<span data-ttu-id="1efe7-109">Informações</span><span class="sxs-lookup"><span data-stu-id="1efe7-109">Information</span></span>|  
|<span data-ttu-id="1efe7-110">Canal</span><span class="sxs-lookup"><span data-stu-id="1efe7-110">Channel</span></span>|<span data-ttu-id="1efe7-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="1efe7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1efe7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1efe7-112">Description</span></span>  
 <span data-ttu-id="1efe7-113">Esse evento é emitido após o modelo de serviço foi invocado o `BeforeSend` método em um Inspetor de mensagem.</span><span class="sxs-lookup"><span data-stu-id="1efe7-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1efe7-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="1efe7-114">Message</span></span>  
 <span data-ttu-id="1efe7-115">O Dispatcher invocou 'BeforeSendRequest' em um MessageInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="1efe7-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1efe7-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1efe7-116">Details</span></span>  
  
|<span data-ttu-id="1efe7-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="1efe7-117">Data Item Name</span></span>|<span data-ttu-id="1efe7-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="1efe7-118">Data Item Type</span></span>|<span data-ttu-id="1efe7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="1efe7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1efe7-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="1efe7-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="1efe7-121">O FullName do CLR do tipo de chamada `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="1efe7-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="1efe7-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="1efe7-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="1efe7-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="1efe7-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1efe7-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="1efe7-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1efe7-125">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="1efe7-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1efe7-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1efe7-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1efe7-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1efe7-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
