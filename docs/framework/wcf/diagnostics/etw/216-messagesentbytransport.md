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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b35f46ae7a214ab45e4062928de82c4da6541a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="50789-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="50789-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="50789-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="50789-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="50789-104">ID</span><span class="sxs-lookup"><span data-stu-id="50789-104">ID</span></span>|<span data-ttu-id="50789-105">216</span><span class="sxs-lookup"><span data-stu-id="50789-105">216</span></span>|  
|<span data-ttu-id="50789-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="50789-106">Keywords</span></span>|<span data-ttu-id="50789-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="50789-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="50789-108">Nível</span><span class="sxs-lookup"><span data-stu-id="50789-108">Level</span></span>|<span data-ttu-id="50789-109">Informações</span><span class="sxs-lookup"><span data-stu-id="50789-109">Information</span></span>|  
|<span data-ttu-id="50789-110">Canal</span><span class="sxs-lookup"><span data-stu-id="50789-110">Channel</span></span>|<span data-ttu-id="50789-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="50789-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="50789-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="50789-112">Description</span></span>  
 <span data-ttu-id="50789-113">Esse evento ocorre quando um transporte baseado em TCP envia uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="50789-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="50789-114">Observe que no nível do transporte várias mensagens podem ser trocadas entre clientes e serviços para uma única operação.</span><span class="sxs-lookup"><span data-stu-id="50789-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="50789-115">Isso pode ser devido ao comportamento de infraestrutura, sendo um bom exemplo de segurança.</span><span class="sxs-lookup"><span data-stu-id="50789-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="50789-116">Portanto, o número de **MessageSentByTransport** eventos que são emitidos variam com base na associação do serviço e sua configuração.</span><span class="sxs-lookup"><span data-stu-id="50789-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="50789-117">Mensagem</span><span class="sxs-lookup"><span data-stu-id="50789-117">Message</span></span>  
 <span data-ttu-id="50789-118">O transporte enviou uma mensagem para '%1'.</span><span class="sxs-lookup"><span data-stu-id="50789-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="50789-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="50789-119">Details</span></span>  
  
|<span data-ttu-id="50789-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="50789-120">Data Item Name</span></span>|<span data-ttu-id="50789-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="50789-121">Data Item Type</span></span>|<span data-ttu-id="50789-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="50789-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="50789-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="50789-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="50789-124">O endereço que recebeu a mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="50789-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="50789-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="50789-125">HostReference</span></span>|<span data-ttu-id="50789-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="50789-126">xs:string</span></span>|<span data-ttu-id="50789-127">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="50789-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="50789-128">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="50789-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="50789-129">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="50789-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="50789-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="50789-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="50789-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="50789-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
