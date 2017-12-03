---
title: 222 - OperationFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d56766dd32acf1ef71f7c06a5c3c94cc7510070
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="222---operationfailed"></a><span data-ttu-id="73985-102">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="73985-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="73985-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="73985-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73985-104">ID</span><span class="sxs-lookup"><span data-stu-id="73985-104">ID</span></span>|<span data-ttu-id="73985-105">222</span><span class="sxs-lookup"><span data-stu-id="73985-105">222</span></span>|  
|<span data-ttu-id="73985-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="73985-106">Keywords</span></span>|<span data-ttu-id="73985-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="73985-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="73985-108">Nível</span><span class="sxs-lookup"><span data-stu-id="73985-108">Level</span></span>|<span data-ttu-id="73985-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="73985-109">Warning</span></span>|  
|<span data-ttu-id="73985-110">Canal</span><span class="sxs-lookup"><span data-stu-id="73985-110">Channel</span></span>|<span data-ttu-id="73985-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="73985-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="73985-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="73985-112">Description</span></span>  
 <span data-ttu-id="73985-113">Esse evento é emitido ao padrão do modelo de serviço `OperationInvoker` encontrou uma exceção ao invocar o método.</span><span class="sxs-lookup"><span data-stu-id="73985-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="73985-114">Observe que exceções que derivam de `FaultException` fazer esse evento não será emitido.</span><span class="sxs-lookup"><span data-stu-id="73985-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="73985-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="73985-115">Message</span></span>  
 <span data-ttu-id="73985-116">O método '%1' gerou uma exceção sem tratamento quando invocado pelo OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="73985-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="73985-117">A duração da chamada de método foi '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="73985-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="73985-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="73985-118">Details</span></span>  
  
|<span data-ttu-id="73985-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="73985-119">Data Item Name</span></span>|<span data-ttu-id="73985-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="73985-120">Data Item Type</span></span>|<span data-ttu-id="73985-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="73985-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="73985-122">Nome do método</span><span class="sxs-lookup"><span data-stu-id="73985-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="73985-123">O nome CLR do método que foi invocado pelo `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="73985-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="73985-124">Duração</span><span class="sxs-lookup"><span data-stu-id="73985-124">Duration</span></span>|`xs:long`|<span data-ttu-id="73985-125">O tempo, em milissegundos, que levou o `OperationInvoker` para invocar o método.</span><span class="sxs-lookup"><span data-stu-id="73985-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="73985-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="73985-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="73985-127">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="73985-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="73985-128">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="73985-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="73985-129">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="73985-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="73985-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="73985-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="73985-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="73985-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
