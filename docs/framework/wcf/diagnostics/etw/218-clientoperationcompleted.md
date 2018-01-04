---
title: 218 - ClientOperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 974fde79d8b24c17928fa4ff38bb9d35d6b5a815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="8fe52-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="8fe52-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="8fe52-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8fe52-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8fe52-104">ID</span><span class="sxs-lookup"><span data-stu-id="8fe52-104">ID</span></span>|<span data-ttu-id="8fe52-105">218</span><span class="sxs-lookup"><span data-stu-id="8fe52-105">218</span></span>|  
|<span data-ttu-id="8fe52-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="8fe52-106">Keywords</span></span>|<span data-ttu-id="8fe52-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8fe52-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8fe52-108">Nível</span><span class="sxs-lookup"><span data-stu-id="8fe52-108">Level</span></span>|<span data-ttu-id="8fe52-109">Informações</span><span class="sxs-lookup"><span data-stu-id="8fe52-109">Information</span></span>|  
|<span data-ttu-id="8fe52-110">Canal</span><span class="sxs-lookup"><span data-stu-id="8fe52-110">Channel</span></span>|<span data-ttu-id="8fe52-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="8fe52-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8fe52-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8fe52-112">Description</span></span>  
 <span data-ttu-id="8fe52-113">Esse evento é emitido por clientes depois que uma operação é concluída.</span><span class="sxs-lookup"><span data-stu-id="8fe52-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="8fe52-114">Para operações unidirecionais, isso é apenas depois que a mensagem é enviada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8fe52-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="8fe52-115">Para operações de solicitação-resposta, isso é após o recebimento da resposta.</span><span class="sxs-lookup"><span data-stu-id="8fe52-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8fe52-116">Mensagem</span><span class="sxs-lookup"><span data-stu-id="8fe52-116">Message</span></span>  
 <span data-ttu-id="8fe52-117">O cliente concluiu a execução da ação '%1' associada ao contrato '%2'.</span><span class="sxs-lookup"><span data-stu-id="8fe52-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="8fe52-118">A mensagem foi enviada para '%3'.</span><span class="sxs-lookup"><span data-stu-id="8fe52-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8fe52-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8fe52-119">Details</span></span>  
  
|<span data-ttu-id="8fe52-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="8fe52-120">Data Item Name</span></span>|<span data-ttu-id="8fe52-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="8fe52-121">Data Item Type</span></span>|<span data-ttu-id="8fe52-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8fe52-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8fe52-123">Ação</span><span class="sxs-lookup"><span data-stu-id="8fe52-123">Action</span></span>|<span data-ttu-id="8fe52-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8fe52-124">xs:string</span></span>|<span data-ttu-id="8fe52-125">O cabeçalho de ação SOAP da mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="8fe52-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="8fe52-126">Nome do contrato</span><span class="sxs-lookup"><span data-stu-id="8fe52-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="8fe52-127">O nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="8fe52-127">The name of the contract.</span></span> <span data-ttu-id="8fe52-128">Exemplo: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="8fe52-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="8fe52-129">Destino</span><span class="sxs-lookup"><span data-stu-id="8fe52-129">Destination</span></span>|`xs:string`|<span data-ttu-id="8fe52-130">O endereço do ponto de extremidade de serviço que a mensagem foi enviada ao.</span><span class="sxs-lookup"><span data-stu-id="8fe52-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="8fe52-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="8fe52-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="8fe52-132">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="8fe52-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8fe52-133">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="8fe52-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8fe52-134">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="8fe52-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8fe52-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8fe52-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8fe52-136">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8fe52-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
