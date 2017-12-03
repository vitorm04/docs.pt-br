---
title: 217 - ClientOperationPrepared
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea5526c39d8947a578174dd4d58685249b4952e1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="730ef-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="730ef-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="730ef-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="730ef-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="730ef-104">ID</span><span class="sxs-lookup"><span data-stu-id="730ef-104">ID</span></span>|<span data-ttu-id="730ef-105">217</span><span class="sxs-lookup"><span data-stu-id="730ef-105">217</span></span>|  
|<span data-ttu-id="730ef-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="730ef-106">Keywords</span></span>|<span data-ttu-id="730ef-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="730ef-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="730ef-108">Nível</span><span class="sxs-lookup"><span data-stu-id="730ef-108">Level</span></span>|<span data-ttu-id="730ef-109">Informações</span><span class="sxs-lookup"><span data-stu-id="730ef-109">Information</span></span>|  
|<span data-ttu-id="730ef-110">Canal</span><span class="sxs-lookup"><span data-stu-id="730ef-110">Channel</span></span>|<span data-ttu-id="730ef-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="730ef-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="730ef-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="730ef-112">Description</span></span>  
 <span data-ttu-id="730ef-113">Esse evento é emitido por clientes antes de uma operação é enviada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="730ef-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="730ef-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="730ef-114">Message</span></span>  
 <span data-ttu-id="730ef-115">O cliente está executando a ação '%1' associada ao contrato '%2'.</span><span class="sxs-lookup"><span data-stu-id="730ef-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="730ef-116">A mensagem será enviada para '%3'.</span><span class="sxs-lookup"><span data-stu-id="730ef-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="730ef-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="730ef-117">Details</span></span>  
  
|<span data-ttu-id="730ef-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="730ef-118">Data Item Name</span></span>|<span data-ttu-id="730ef-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="730ef-119">Data Item Type</span></span>|<span data-ttu-id="730ef-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="730ef-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="730ef-121">Ação</span><span class="sxs-lookup"><span data-stu-id="730ef-121">Action</span></span>|`xs:string`|<span data-ttu-id="730ef-122">O cabeçalho de ação SOAP da mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="730ef-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="730ef-123">Nome do contrato</span><span class="sxs-lookup"><span data-stu-id="730ef-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="730ef-124">O nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="730ef-124">The name of the contract.</span></span> <span data-ttu-id="730ef-125">Exemplo: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="730ef-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="730ef-126">Destino</span><span class="sxs-lookup"><span data-stu-id="730ef-126">Destination</span></span>|`xs:string`|<span data-ttu-id="730ef-127">O endereço do ponto de extremidade de serviço que a mensagem é enviada ao.</span><span class="sxs-lookup"><span data-stu-id="730ef-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="730ef-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="730ef-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="730ef-129">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="730ef-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="730ef-130">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="730ef-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="730ef-131">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="730ef-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="730ef-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="730ef-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="730ef-133">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="730ef-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
