---
title: 214 - OperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 823207f4225252d94bd8fba450eb63edd00068ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="214---operationcompleted"></a><span data-ttu-id="90c6c-102">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="90c6c-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="90c6c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="90c6c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90c6c-104">ID</span><span class="sxs-lookup"><span data-stu-id="90c6c-104">ID</span></span>|<span data-ttu-id="90c6c-105">214</span><span class="sxs-lookup"><span data-stu-id="90c6c-105">214</span></span>|  
|<span data-ttu-id="90c6c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="90c6c-106">Keywords</span></span>|<span data-ttu-id="90c6c-107">HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="90c6c-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="90c6c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="90c6c-108">Level</span></span>|<span data-ttu-id="90c6c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="90c6c-109">Information</span></span>|  
|<span data-ttu-id="90c6c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="90c6c-110">Channel</span></span>|<span data-ttu-id="90c6c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="90c6c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="90c6c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="90c6c-112">Description</span></span>  
 <span data-ttu-id="90c6c-113">Esse evento é emitido ao padrão do modelo de serviço `OperationInvoker` concluiu uma chamada para um método sem esse método lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="90c6c-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="90c6c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="90c6c-114">Message</span></span>  
 <span data-ttu-id="90c6c-115">Um OperationInvoker concluiu a chamada ao método '%1'.</span><span class="sxs-lookup"><span data-stu-id="90c6c-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="90c6c-116">A duração da chamada de método foi '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="90c6c-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="90c6c-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="90c6c-117">Details</span></span>  
  
|<span data-ttu-id="90c6c-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="90c6c-118">Data Item Name</span></span>|<span data-ttu-id="90c6c-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="90c6c-119">Data Item Type</span></span>|<span data-ttu-id="90c6c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="90c6c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="90c6c-121">Nome do método</span><span class="sxs-lookup"><span data-stu-id="90c6c-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="90c6c-122">O nome CLR do método que foi invocado pelo `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="90c6c-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="90c6c-123">Duração</span><span class="sxs-lookup"><span data-stu-id="90c6c-123">Duration</span></span>|`xs:long`|<span data-ttu-id="90c6c-124">O tempo, em milissegundos, que levou o `OperationInvoker` para invocar o método.</span><span class="sxs-lookup"><span data-stu-id="90c6c-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="90c6c-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="90c6c-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="90c6c-126">Para serviços hospedados na web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="90c6c-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="90c6c-127">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="90c6c-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="90c6c-128">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="90c6c-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="90c6c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="90c6c-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="90c6c-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="90c6c-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
