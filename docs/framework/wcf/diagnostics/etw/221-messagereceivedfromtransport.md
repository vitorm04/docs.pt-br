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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f977f938844f48182be6662f489506e8119fe67
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="620a9-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="620a9-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="620a9-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="620a9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="620a9-104">ID</span><span class="sxs-lookup"><span data-stu-id="620a9-104">ID</span></span>|<span data-ttu-id="620a9-105">221</span><span class="sxs-lookup"><span data-stu-id="620a9-105">221</span></span>|  
|<span data-ttu-id="620a9-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="620a9-106">Keywords</span></span>|<span data-ttu-id="620a9-107">EndToEndMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="620a9-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="620a9-108">Nível</span><span class="sxs-lookup"><span data-stu-id="620a9-108">Level</span></span>|<span data-ttu-id="620a9-109">Informações</span><span class="sxs-lookup"><span data-stu-id="620a9-109">Information</span></span>|  
|<span data-ttu-id="620a9-110">Canal</span><span class="sxs-lookup"><span data-stu-id="620a9-110">Channel</span></span>|<span data-ttu-id="620a9-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="620a9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="620a9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="620a9-112">Description</span></span>  
 <span data-ttu-id="620a9-113">Esse evento é emitido quando o modelo de serviço recebe uma mensagem do transporte.</span><span class="sxs-lookup"><span data-stu-id="620a9-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="620a9-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="620a9-114">Message</span></span>  
 <span data-ttu-id="620a9-115">O Dispatcher recebeu uma mensagem do transporte.</span><span class="sxs-lookup"><span data-stu-id="620a9-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="620a9-116">ID de correlação = = '%1'.</span><span class="sxs-lookup"><span data-stu-id="620a9-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="620a9-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="620a9-117">Details</span></span>  
  
|<span data-ttu-id="620a9-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="620a9-118">Data Item Name</span></span>|<span data-ttu-id="620a9-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="620a9-119">Data Item Type</span></span>|<span data-ttu-id="620a9-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="620a9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="620a9-121">ID de correlação</span><span class="sxs-lookup"><span data-stu-id="620a9-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="620a9-122">A atividade de ID usada para correlacionar uma `MessageSentToTransport` evento em um serviço ou cliente correspondente `MessageReceivedFromTransport` na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="620a9-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="620a9-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="620a9-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="620a9-124">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="620a9-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="620a9-125">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="620a9-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="620a9-126">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="620a9-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="620a9-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="620a9-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="620a9-128">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="620a9-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
