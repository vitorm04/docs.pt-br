---
title: 216 - MessageSentByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b2bf2841c04dcdc74bf64a0169b95caa6c8a36a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="1c98c-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="1c98c-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="1c98c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1c98c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c98c-104">ID</span><span class="sxs-lookup"><span data-stu-id="1c98c-104">ID</span></span>|<span data-ttu-id="1c98c-105">216</span><span class="sxs-lookup"><span data-stu-id="1c98c-105">216</span></span>|  
|<span data-ttu-id="1c98c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="1c98c-106">Keywords</span></span>|<span data-ttu-id="1c98c-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1c98c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1c98c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="1c98c-108">Level</span></span>|<span data-ttu-id="1c98c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="1c98c-109">Information</span></span>|  
|<span data-ttu-id="1c98c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="1c98c-110">Channel</span></span>|<span data-ttu-id="1c98c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="1c98c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c98c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c98c-112">Description</span></span>  
 <span data-ttu-id="1c98c-113">Esse evento ocorre quando um transporte baseado em TCP envia uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="1c98c-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="1c98c-114">Observe que no nível do transporte várias mensagens podem ser trocadas entre clientes e serviços para uma única operação.</span><span class="sxs-lookup"><span data-stu-id="1c98c-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="1c98c-115">Isso pode ser devido ao comportamento de infraestrutura, sendo um bom exemplo de segurança.</span><span class="sxs-lookup"><span data-stu-id="1c98c-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="1c98c-116">Portanto, o número de **MessageSentByTransport** eventos que são emitidos variam com base na associação do serviço e sua configuração.</span><span class="sxs-lookup"><span data-stu-id="1c98c-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1c98c-117">Mensagem</span><span class="sxs-lookup"><span data-stu-id="1c98c-117">Message</span></span>  
 <span data-ttu-id="1c98c-118">O transporte enviou uma mensagem para '%1'.</span><span class="sxs-lookup"><span data-stu-id="1c98c-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1c98c-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1c98c-119">Details</span></span>  
  
|<span data-ttu-id="1c98c-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="1c98c-120">Data Item Name</span></span>|<span data-ttu-id="1c98c-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="1c98c-121">Data Item Type</span></span>|<span data-ttu-id="1c98c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c98c-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1c98c-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="1c98c-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="1c98c-124">O endereço que recebeu a mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="1c98c-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="1c98c-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="1c98c-125">HostReference</span></span>|<span data-ttu-id="1c98c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c98c-126">xs:string</span></span>|<span data-ttu-id="1c98c-127">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="1c98c-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1c98c-128">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="1c98c-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1c98c-129">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="1c98c-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1c98c-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c98c-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1c98c-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1c98c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
