---
title: 215 - MessageReceivedByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acc39fea579a66479de6686cba928915a437f864
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="7104d-102">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="7104d-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="7104d-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7104d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7104d-104">ID</span><span class="sxs-lookup"><span data-stu-id="7104d-104">ID</span></span>|<span data-ttu-id="7104d-105">215</span><span class="sxs-lookup"><span data-stu-id="7104d-105">215</span></span>|  
|<span data-ttu-id="7104d-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="7104d-106">Keywords</span></span>|<span data-ttu-id="7104d-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7104d-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7104d-108">Nível</span><span class="sxs-lookup"><span data-stu-id="7104d-108">Level</span></span>|<span data-ttu-id="7104d-109">Informações</span><span class="sxs-lookup"><span data-stu-id="7104d-109">Information</span></span>|  
|<span data-ttu-id="7104d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="7104d-110">Channel</span></span>|<span data-ttu-id="7104d-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="7104d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7104d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7104d-112">Description</span></span>  
 <span data-ttu-id="7104d-113">Esse evento ocorre quando um transporte baseado em TCP recebe uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="7104d-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="7104d-114">Observe que, no nível de transporte, várias mensagens podem ser trocadas entre clientes e serviços para uma única operação.</span><span class="sxs-lookup"><span data-stu-id="7104d-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="7104d-115">Isso pode ser devido ao comportamento de infraestrutura, a segurança é um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="7104d-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="7104d-116">Portanto, o número de `MessageReceivedByTransport` eventos que são emitidos variam com base na associação do serviço e sua configuração.</span><span class="sxs-lookup"><span data-stu-id="7104d-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7104d-117">Esse evento não é emitido para transportes unidirecionais.</span><span class="sxs-lookup"><span data-stu-id="7104d-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7104d-118">Mensagem</span><span class="sxs-lookup"><span data-stu-id="7104d-118">Message</span></span>  
 <span data-ttu-id="7104d-119">O transporte recebeu uma mensagem de '%1'.</span><span class="sxs-lookup"><span data-stu-id="7104d-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7104d-120">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7104d-120">Details</span></span>  
  
|<span data-ttu-id="7104d-121">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="7104d-121">Data Item Name</span></span>|<span data-ttu-id="7104d-122">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="7104d-122">Data Item Type</span></span>|<span data-ttu-id="7104d-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="7104d-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7104d-124">Endereço de escuta</span><span class="sxs-lookup"><span data-stu-id="7104d-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="7104d-125">O endereço que recebeu a mensagem.</span><span class="sxs-lookup"><span data-stu-id="7104d-125">The address that received the message.</span></span>|  
|<span data-ttu-id="7104d-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="7104d-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="7104d-127">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="7104d-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7104d-128">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="7104d-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7104d-129">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="7104d-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7104d-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7104d-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7104d-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7104d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
