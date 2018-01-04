---
title: 223 - OperationFaulted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcaea7b98bc57bcac901ac659786175a10799700
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="40d21-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="40d21-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="40d21-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="40d21-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40d21-104">ID</span><span class="sxs-lookup"><span data-stu-id="40d21-104">ID</span></span>|<span data-ttu-id="40d21-105">223</span><span class="sxs-lookup"><span data-stu-id="40d21-105">223</span></span>|  
|<span data-ttu-id="40d21-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="40d21-106">Keywords</span></span>|<span data-ttu-id="40d21-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="40d21-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="40d21-108">Nível</span><span class="sxs-lookup"><span data-stu-id="40d21-108">Level</span></span>|<span data-ttu-id="40d21-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="40d21-109">Warning</span></span>|  
|<span data-ttu-id="40d21-110">Canal</span><span class="sxs-lookup"><span data-stu-id="40d21-110">Channel</span></span>|<span data-ttu-id="40d21-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="40d21-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="40d21-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="40d21-112">Description</span></span>  
 <span data-ttu-id="40d21-113">Esse evento é emitido ao padrão do modelo de serviço `OperationInvoker` encontrou uma exceção derivando de `FaultException` ao invocar o método.</span><span class="sxs-lookup"><span data-stu-id="40d21-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="40d21-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="40d21-114">Message</span></span>  
 <span data-ttu-id="40d21-115">O método '%1' gerou uma FaultException quando invocado pelo OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="40d21-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="40d21-116">A duração da chamada de método foi '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="40d21-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="40d21-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="40d21-117">Details</span></span>  
  
|<span data-ttu-id="40d21-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="40d21-118">Data Item Name</span></span>|<span data-ttu-id="40d21-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="40d21-119">Data Item Type</span></span>|<span data-ttu-id="40d21-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="40d21-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="40d21-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="40d21-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="40d21-122">O nome CLR do método que foi invocado pelo `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="40d21-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="40d21-123">Duração</span><span class="sxs-lookup"><span data-stu-id="40d21-123">Duration</span></span>|`xs:long`|<span data-ttu-id="40d21-124">O tempo, em milissegundos, que levou o `OperationInvoker` para invocar o método.</span><span class="sxs-lookup"><span data-stu-id="40d21-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="40d21-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="40d21-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="40d21-126">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="40d21-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="40d21-127">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="40d21-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="40d21-128">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="40d21-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="40d21-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="40d21-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="40d21-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="40d21-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
