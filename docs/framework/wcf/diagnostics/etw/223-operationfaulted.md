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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a04ed11db97d02a90e016ee1825b303375a23412
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="c61fc-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="c61fc-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="c61fc-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c61fc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c61fc-104">ID</span><span class="sxs-lookup"><span data-stu-id="c61fc-104">ID</span></span>|<span data-ttu-id="c61fc-105">223</span><span class="sxs-lookup"><span data-stu-id="c61fc-105">223</span></span>|  
|<span data-ttu-id="c61fc-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c61fc-106">Keywords</span></span>|<span data-ttu-id="c61fc-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c61fc-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c61fc-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c61fc-108">Level</span></span>|<span data-ttu-id="c61fc-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="c61fc-109">Warning</span></span>|  
|<span data-ttu-id="c61fc-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c61fc-110">Channel</span></span>|<span data-ttu-id="c61fc-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="c61fc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c61fc-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c61fc-112">Description</span></span>  
 <span data-ttu-id="c61fc-113">Esse evento é emitido ao padrão do modelo de serviço `OperationInvoker` encontrou uma exceção derivando de `FaultException` ao invocar o método.</span><span class="sxs-lookup"><span data-stu-id="c61fc-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c61fc-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c61fc-114">Message</span></span>  
 <span data-ttu-id="c61fc-115">O método '%1' gerou uma FaultException quando invocado pelo OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="c61fc-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="c61fc-116">A duração da chamada de método foi '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="c61fc-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c61fc-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c61fc-117">Details</span></span>  
  
|<span data-ttu-id="c61fc-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c61fc-118">Data Item Name</span></span>|<span data-ttu-id="c61fc-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c61fc-119">Data Item Type</span></span>|<span data-ttu-id="c61fc-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c61fc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c61fc-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="c61fc-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="c61fc-122">O nome CLR do método que foi invocado pelo `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="c61fc-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="c61fc-123">Duração</span><span class="sxs-lookup"><span data-stu-id="c61fc-123">Duration</span></span>|`xs:long`|<span data-ttu-id="c61fc-124">O tempo, em milissegundos, que levou o `OperationInvoker` para invocar o método.</span><span class="sxs-lookup"><span data-stu-id="c61fc-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="c61fc-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="c61fc-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="c61fc-126">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="c61fc-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c61fc-127">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="c61fc-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c61fc-128">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="c61fc-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c61fc-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c61fc-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c61fc-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c61fc-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
