---
title: 499 - TransferEmitted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1034ae6bd6072a3849d72fafcad55c61e500439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="d75a0-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="d75a0-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="d75a0-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d75a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d75a0-104">ID</span><span class="sxs-lookup"><span data-stu-id="d75a0-104">ID</span></span>|<span data-ttu-id="d75a0-105">499</span><span class="sxs-lookup"><span data-stu-id="d75a0-105">499</span></span>|  
|<span data-ttu-id="d75a0-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d75a0-106">Keywords</span></span>|<span data-ttu-id="d75a0-107">Solução de problemas, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="d75a0-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="d75a0-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d75a0-108">Level</span></span>|<span data-ttu-id="d75a0-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="d75a0-109">LogAlways</span></span>|  
|<span data-ttu-id="d75a0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d75a0-110">Channel</span></span>|<span data-ttu-id="d75a0-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="d75a0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d75a0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d75a0-112">Description</span></span>  
 <span data-ttu-id="d75a0-113">Esse evento é emitido quando ocorre o evento de transferência.</span><span class="sxs-lookup"><span data-stu-id="d75a0-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d75a0-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d75a0-114">Message</span></span>  
 <span data-ttu-id="d75a0-115">Evento de transferência emitido.</span><span class="sxs-lookup"><span data-stu-id="d75a0-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d75a0-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d75a0-116">Details</span></span>  
  
|<span data-ttu-id="d75a0-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d75a0-117">Data Item Name</span></span>|<span data-ttu-id="d75a0-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d75a0-118">Data Item Type</span></span>|<span data-ttu-id="d75a0-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d75a0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d75a0-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="d75a0-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="d75a0-121">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="d75a0-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d75a0-122">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="d75a0-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d75a0-123">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="d75a0-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d75a0-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d75a0-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d75a0-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d75a0-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
