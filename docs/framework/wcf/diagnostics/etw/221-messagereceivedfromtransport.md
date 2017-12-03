---
title: 221 - MessageReceivedFromTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0b286264cee3d9a0c2ef1df1c6f215240148f98
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="49eba-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="49eba-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="49eba-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="49eba-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49eba-104">ID</span><span class="sxs-lookup"><span data-stu-id="49eba-104">ID</span></span>|<span data-ttu-id="49eba-105">221</span><span class="sxs-lookup"><span data-stu-id="49eba-105">221</span></span>|  
|<span data-ttu-id="49eba-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="49eba-106">Keywords</span></span>|<span data-ttu-id="49eba-107">EndToEndMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="49eba-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="49eba-108">Nível</span><span class="sxs-lookup"><span data-stu-id="49eba-108">Level</span></span>|<span data-ttu-id="49eba-109">Informações</span><span class="sxs-lookup"><span data-stu-id="49eba-109">Information</span></span>|  
|<span data-ttu-id="49eba-110">Canal</span><span class="sxs-lookup"><span data-stu-id="49eba-110">Channel</span></span>|<span data-ttu-id="49eba-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="49eba-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="49eba-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="49eba-112">Description</span></span>  
 <span data-ttu-id="49eba-113">Esse evento é emitido quando o modelo de serviço recebe uma mensagem do transporte.</span><span class="sxs-lookup"><span data-stu-id="49eba-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="49eba-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="49eba-114">Message</span></span>  
 <span data-ttu-id="49eba-115">O Dispatcher recebeu uma mensagem do transporte.</span><span class="sxs-lookup"><span data-stu-id="49eba-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="49eba-116">ID de correlação = = '%1'.</span><span class="sxs-lookup"><span data-stu-id="49eba-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="49eba-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="49eba-117">Details</span></span>  
  
|<span data-ttu-id="49eba-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="49eba-118">Data Item Name</span></span>|<span data-ttu-id="49eba-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="49eba-119">Data Item Type</span></span>|<span data-ttu-id="49eba-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="49eba-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="49eba-121">ID de correlação</span><span class="sxs-lookup"><span data-stu-id="49eba-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="49eba-122">A atividade de ID usada para correlacionar uma `MessageSentToTransport` evento em um serviço ou cliente correspondente `MessageReceivedFromTransport` na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="49eba-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="49eba-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="49eba-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="49eba-124">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="49eba-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="49eba-125">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="49eba-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="49eba-126">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="49eba-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="49eba-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="49eba-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="49eba-128">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="49eba-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
