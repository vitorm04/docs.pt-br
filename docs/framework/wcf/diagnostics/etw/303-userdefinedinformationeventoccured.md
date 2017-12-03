---
title: 303 - UserDefinedInformationEventOccured
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc04837834277dccc9d21d27e89c84f09f36167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="b2d28-102">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="b2d28-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="b2d28-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b2d28-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2d28-104">ID</span><span class="sxs-lookup"><span data-stu-id="b2d28-104">ID</span></span>|<span data-ttu-id="b2d28-105">303</span><span class="sxs-lookup"><span data-stu-id="b2d28-105">303</span></span>|  
|<span data-ttu-id="b2d28-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="b2d28-106">Keywords</span></span>|<span data-ttu-id="b2d28-107">Solução de problemas, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="b2d28-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="b2d28-108">Nível</span><span class="sxs-lookup"><span data-stu-id="b2d28-108">Level</span></span>|<span data-ttu-id="b2d28-109">Informações</span><span class="sxs-lookup"><span data-stu-id="b2d28-109">Information</span></span>|  
|<span data-ttu-id="b2d28-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b2d28-110">Channel</span></span>|<span data-ttu-id="b2d28-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="b2d28-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b2d28-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2d28-112">Description</span></span>  
 <span data-ttu-id="b2d28-113">Esse evento é emitido do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="b2d28-113">This event is emitted from user code.</span></span> <span data-ttu-id="b2d28-114">Os desenvolvedores podem emitir esse evento quando ocorre um evento informativo personalizadas em seu serviço.</span><span class="sxs-lookup"><span data-stu-id="b2d28-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="b2d28-115">Isso pode ser feito usando o <xref:System.Diagnostics.Eventing> APIs.</span><span class="sxs-lookup"><span data-stu-id="b2d28-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="b2d28-116">Além disso, há um exemplo do WCF que encapsula essa API e demonstra como emitir corretamente este evento.</span><span class="sxs-lookup"><span data-stu-id="b2d28-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b2d28-117">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b2d28-117">Message</span></span>  
 <span data-ttu-id="b2d28-118">Nome: '%1', referência: '%2', carga: % 3</span><span class="sxs-lookup"><span data-stu-id="b2d28-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="b2d28-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b2d28-119">Details</span></span>  
  
|<span data-ttu-id="b2d28-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="b2d28-120">Data Item Name</span></span>|<span data-ttu-id="b2d28-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="b2d28-121">Data Item Type</span></span>|<span data-ttu-id="b2d28-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2d28-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b2d28-123">Nome</span><span class="sxs-lookup"><span data-stu-id="b2d28-123">Name</span></span>|`xs:string`|<span data-ttu-id="b2d28-124">O nome do evento definido pelo usuário</span><span class="sxs-lookup"><span data-stu-id="b2d28-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="b2d28-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="b2d28-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="b2d28-126">Os serviços hospedados da Web, este campo identificam exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="b2d28-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b2d28-127">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="b2d28-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b2d28-128">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="b2d28-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b2d28-129">Carga</span><span class="sxs-lookup"><span data-stu-id="b2d28-129">Payload</span></span>|`xs:string`|<span data-ttu-id="b2d28-130">A carga do evento definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b2d28-130">The user-defined payload of the event.</span></span>|
