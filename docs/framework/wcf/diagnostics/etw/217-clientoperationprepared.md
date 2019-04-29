---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781752"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="915cb-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="915cb-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="915cb-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="915cb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="915cb-104">ID</span><span class="sxs-lookup"><span data-stu-id="915cb-104">ID</span></span>|<span data-ttu-id="915cb-105">217</span><span class="sxs-lookup"><span data-stu-id="915cb-105">217</span></span>|  
|<span data-ttu-id="915cb-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="915cb-106">Keywords</span></span>|<span data-ttu-id="915cb-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="915cb-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="915cb-108">Nível</span><span class="sxs-lookup"><span data-stu-id="915cb-108">Level</span></span>|<span data-ttu-id="915cb-109">Informações</span><span class="sxs-lookup"><span data-stu-id="915cb-109">Information</span></span>|  
|<span data-ttu-id="915cb-110">Canal</span><span class="sxs-lookup"><span data-stu-id="915cb-110">Channel</span></span>|<span data-ttu-id="915cb-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="915cb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="915cb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="915cb-112">Description</span></span>  
 <span data-ttu-id="915cb-113">Esse evento é emitido por clientes antes de uma operação é enviada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="915cb-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="915cb-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="915cb-114">Message</span></span>  
 <span data-ttu-id="915cb-115">O cliente está executando a ação '%1' associado ao contrato '%2'.</span><span class="sxs-lookup"><span data-stu-id="915cb-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="915cb-116">A mensagem será enviada para '%3'.</span><span class="sxs-lookup"><span data-stu-id="915cb-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="915cb-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="915cb-117">Details</span></span>  
  
|<span data-ttu-id="915cb-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="915cb-118">Data Item Name</span></span>|<span data-ttu-id="915cb-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="915cb-119">Data Item Type</span></span>|<span data-ttu-id="915cb-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="915cb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="915cb-121">Ação</span><span class="sxs-lookup"><span data-stu-id="915cb-121">Action</span></span>|`xs:string`|<span data-ttu-id="915cb-122">O cabeçalho de ação SOAP da mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="915cb-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="915cb-123">Nome do contrato</span><span class="sxs-lookup"><span data-stu-id="915cb-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="915cb-124">O nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="915cb-124">The name of the contract.</span></span> <span data-ttu-id="915cb-125">Exemplo: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="915cb-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="915cb-126">Destino</span><span class="sxs-lookup"><span data-stu-id="915cb-126">Destination</span></span>|`xs:string`|<span data-ttu-id="915cb-127">O endereço do ponto de extremidade de serviço que a mensagem é enviada ao.</span><span class="sxs-lookup"><span data-stu-id="915cb-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="915cb-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="915cb-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="915cb-129">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="915cb-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="915cb-130">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="915cb-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="915cb-131">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="915cb-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="915cb-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="915cb-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="915cb-133">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="915cb-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
