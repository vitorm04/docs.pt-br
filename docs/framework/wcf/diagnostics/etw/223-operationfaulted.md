---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596525"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="f31cd-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="f31cd-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="f31cd-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f31cd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f31cd-104">ID</span><span class="sxs-lookup"><span data-stu-id="f31cd-104">ID</span></span>|<span data-ttu-id="f31cd-105">223</span><span class="sxs-lookup"><span data-stu-id="f31cd-105">223</span></span>|  
|<span data-ttu-id="f31cd-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="f31cd-106">Keywords</span></span>|<span data-ttu-id="f31cd-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f31cd-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f31cd-108">Nível</span><span class="sxs-lookup"><span data-stu-id="f31cd-108">Level</span></span>|<span data-ttu-id="f31cd-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="f31cd-109">Warning</span></span>|  
|<span data-ttu-id="f31cd-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f31cd-110">Channel</span></span>|<span data-ttu-id="f31cd-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="f31cd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f31cd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f31cd-112">Description</span></span>  
 <span data-ttu-id="f31cd-113">Esse evento é emitido quando padrão do modelo de serviço `OperationInvoker` encontrou uma exceção, derivando de `FaultException` ao invocar seu método.</span><span class="sxs-lookup"><span data-stu-id="f31cd-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f31cd-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f31cd-114">Message</span></span>  
 <span data-ttu-id="f31cd-115">O método '%1' gerou uma FaultException quando invocado pelo OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="f31cd-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="f31cd-116">A duração da chamada de método era '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="f31cd-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f31cd-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f31cd-117">Details</span></span>  
  
|<span data-ttu-id="f31cd-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="f31cd-118">Data Item Name</span></span>|<span data-ttu-id="f31cd-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="f31cd-119">Data Item Type</span></span>|<span data-ttu-id="f31cd-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="f31cd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f31cd-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="f31cd-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="f31cd-122">O nome do CLR do método que foi invocado pelo `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="f31cd-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="f31cd-123">Duração</span><span class="sxs-lookup"><span data-stu-id="f31cd-123">Duration</span></span>|`xs:long`|<span data-ttu-id="f31cd-124">O tempo, em milissegundos, que levou o `OperationInvoker` para invocar o método.</span><span class="sxs-lookup"><span data-stu-id="f31cd-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="f31cd-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="f31cd-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="f31cd-126">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="f31cd-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f31cd-127">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f31cd-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f31cd-128">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="f31cd-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f31cd-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f31cd-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f31cd-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f31cd-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
