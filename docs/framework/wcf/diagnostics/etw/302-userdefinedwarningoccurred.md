---
title: 302 - UserDefinedWarningOccurred
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae455c9eec2335fcf6eb5473932bd8d9e5d2db95
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2018
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="11923-102">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="11923-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="11923-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="11923-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="11923-104">ID</span><span class="sxs-lookup"><span data-stu-id="11923-104">ID</span></span>|<span data-ttu-id="11923-105">302</span><span class="sxs-lookup"><span data-stu-id="11923-105">302</span></span>|  
|<span data-ttu-id="11923-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="11923-106">Keywords</span></span>|<span data-ttu-id="11923-107">Solução de problemas, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="11923-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="11923-108">Nível</span><span class="sxs-lookup"><span data-stu-id="11923-108">Level</span></span>|<span data-ttu-id="11923-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="11923-109">Warning</span></span>|  
|<span data-ttu-id="11923-110">Canal</span><span class="sxs-lookup"><span data-stu-id="11923-110">Channel</span></span>|<span data-ttu-id="11923-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="11923-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="11923-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="11923-112">Description</span></span>  
 <span data-ttu-id="11923-113">Esse evento é emitido do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="11923-113">This event is emitted from user code.</span></span> <span data-ttu-id="11923-114">Os desenvolvedores podem emitir esse evento quando ocorre um evento de aviso personalizadas em seu serviço.</span><span class="sxs-lookup"><span data-stu-id="11923-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="11923-115">Isso pode ser feito usando o <xref:System.Diagnostics.Eventing> APIs.</span><span class="sxs-lookup"><span data-stu-id="11923-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="11923-116">Além disso, há um exemplo do WCF que encapsula essa API e demonstra como emitir corretamente este evento.</span><span class="sxs-lookup"><span data-stu-id="11923-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="11923-117">Mensagem</span><span class="sxs-lookup"><span data-stu-id="11923-117">Message</span></span>  
 <span data-ttu-id="11923-118">Nome: '%1', referência: '%2', carga: % 3</span><span class="sxs-lookup"><span data-stu-id="11923-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="11923-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="11923-119">Details</span></span>  
  
|<span data-ttu-id="11923-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="11923-120">Data Item Name</span></span>|<span data-ttu-id="11923-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="11923-121">Data Item Type</span></span>|<span data-ttu-id="11923-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="11923-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="11923-123">Nome</span><span class="sxs-lookup"><span data-stu-id="11923-123">Name</span></span>|`xs:string`|<span data-ttu-id="11923-124">O nome do evento definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="11923-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="11923-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="11923-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="11923-126">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="11923-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="11923-127">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="11923-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="11923-128">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="11923-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="11923-129">Carga</span><span class="sxs-lookup"><span data-stu-id="11923-129">Payload</span></span>|`xs:string`|<span data-ttu-id="11923-130">A carga do evento definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="11923-130">The user-defined payload of the event.</span></span>|
