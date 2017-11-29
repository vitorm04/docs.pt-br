---
title: 205 - OperationInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b0a96f1e3ba72a226d9b1a871382a27db61c57e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="205---operationinvoked"></a><span data-ttu-id="c39eb-102">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="c39eb-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="c39eb-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c39eb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c39eb-104">ID</span><span class="sxs-lookup"><span data-stu-id="c39eb-104">ID</span></span>|<span data-ttu-id="c39eb-105">205</span><span class="sxs-lookup"><span data-stu-id="c39eb-105">205</span></span>|  
|<span data-ttu-id="c39eb-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c39eb-106">Keywords</span></span>|<span data-ttu-id="c39eb-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c39eb-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c39eb-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c39eb-108">Level</span></span>|<span data-ttu-id="c39eb-109">Informações</span><span class="sxs-lookup"><span data-stu-id="c39eb-109">Information</span></span>|  
|<span data-ttu-id="c39eb-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c39eb-110">Channel</span></span>|<span data-ttu-id="c39eb-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="c39eb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c39eb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c39eb-112">Description</span></span>  
 <span data-ttu-id="c39eb-113">Esse evento é emitido antes de padrão do modelo de serviço `OperationInvoker` começa uma chamada para um método.</span><span class="sxs-lookup"><span data-stu-id="c39eb-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c39eb-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c39eb-114">Message</span></span>  
 <span data-ttu-id="c39eb-115">Um OperationInvoker invocou o método '%1'.</span><span class="sxs-lookup"><span data-stu-id="c39eb-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="c39eb-116">Informações do chamador: '%2'.</span><span class="sxs-lookup"><span data-stu-id="c39eb-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c39eb-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c39eb-117">Details</span></span>  
  
|<span data-ttu-id="c39eb-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c39eb-118">Data Item Name</span></span>|<span data-ttu-id="c39eb-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c39eb-119">Data Item Type</span></span>|<span data-ttu-id="c39eb-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c39eb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c39eb-121">Nome do método</span><span class="sxs-lookup"><span data-stu-id="c39eb-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="c39eb-122">O nome CLR do método que foi invocado pelo `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="c39eb-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="c39eb-123">Informações de chamador</span><span class="sxs-lookup"><span data-stu-id="c39eb-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="c39eb-124">O endereço IP e porta número do cliente no formato 'IPAddress:PortNumber'.</span><span class="sxs-lookup"><span data-stu-id="c39eb-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="c39eb-125">Os dois valores são recuperados da propriedade de mensagem 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' dentro do contexto da operação.</span><span class="sxs-lookup"><span data-stu-id="c39eb-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="c39eb-126">Observe que para ligações TCP não esse valor `null`.</span><span class="sxs-lookup"><span data-stu-id="c39eb-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="c39eb-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="c39eb-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="c39eb-128">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="c39eb-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c39eb-129">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="c39eb-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c39eb-130">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="c39eb-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c39eb-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c39eb-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c39eb-132">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c39eb-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
