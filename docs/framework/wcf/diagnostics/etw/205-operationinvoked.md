---
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781973"
---
# <a name="205---operationinvoked"></a><span data-ttu-id="e166e-102">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="e166e-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="e166e-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e166e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e166e-104">ID</span><span class="sxs-lookup"><span data-stu-id="e166e-104">ID</span></span>|<span data-ttu-id="e166e-105">205</span><span class="sxs-lookup"><span data-stu-id="e166e-105">205</span></span>|  
|<span data-ttu-id="e166e-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e166e-106">Keywords</span></span>|<span data-ttu-id="e166e-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e166e-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e166e-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e166e-108">Level</span></span>|<span data-ttu-id="e166e-109">Informações</span><span class="sxs-lookup"><span data-stu-id="e166e-109">Information</span></span>|  
|<span data-ttu-id="e166e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e166e-110">Channel</span></span>|<span data-ttu-id="e166e-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="e166e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e166e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e166e-112">Description</span></span>  
 <span data-ttu-id="e166e-113">Esse evento é emitido antes de padrão do modelo de serviço `OperationInvoker` inicia uma chamada para um método.</span><span class="sxs-lookup"><span data-stu-id="e166e-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e166e-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e166e-114">Message</span></span>  
 <span data-ttu-id="e166e-115">Objekt OperationInvoker chamado o método '%1'.</span><span class="sxs-lookup"><span data-stu-id="e166e-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="e166e-116">Informações do chamador: '%2'.</span><span class="sxs-lookup"><span data-stu-id="e166e-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e166e-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e166e-117">Details</span></span>  
  
|<span data-ttu-id="e166e-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e166e-118">Data Item Name</span></span>|<span data-ttu-id="e166e-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e166e-119">Data Item Type</span></span>|<span data-ttu-id="e166e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e166e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e166e-121">Nome do método</span><span class="sxs-lookup"><span data-stu-id="e166e-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="e166e-122">O nome do CLR do método que foi invocado pelo `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="e166e-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="e166e-123">Informações de chamador</span><span class="sxs-lookup"><span data-stu-id="e166e-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="e166e-124">O endereço IP e porta número do cliente no formato 'IPAddress:PortNumber'.</span><span class="sxs-lookup"><span data-stu-id="e166e-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="e166e-125">Os dois valores são recuperados da propriedade de mensagem 'Remoteendpointmessageproperty' dentro do contexto de operação.</span><span class="sxs-lookup"><span data-stu-id="e166e-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="e166e-126">Observe que para associações não TCP esse valor `null`.</span><span class="sxs-lookup"><span data-stu-id="e166e-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="e166e-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="e166e-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="e166e-128">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="e166e-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e166e-129">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="e166e-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e166e-130">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="e166e-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e166e-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e166e-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e166e-132">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e166e-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
