---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461059"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="dba64-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="dba64-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="dba64-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="dba64-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dba64-104">ID</span><span class="sxs-lookup"><span data-stu-id="dba64-104">ID</span></span>|<span data-ttu-id="dba64-105">217</span><span class="sxs-lookup"><span data-stu-id="dba64-105">217</span></span>|  
|<span data-ttu-id="dba64-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="dba64-106">Keywords</span></span>|<span data-ttu-id="dba64-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dba64-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="dba64-108">Nível</span><span class="sxs-lookup"><span data-stu-id="dba64-108">Level</span></span>|<span data-ttu-id="dba64-109">Informações</span><span class="sxs-lookup"><span data-stu-id="dba64-109">Information</span></span>|  
|<span data-ttu-id="dba64-110">Canal</span><span class="sxs-lookup"><span data-stu-id="dba64-110">Channel</span></span>|<span data-ttu-id="dba64-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="dba64-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dba64-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="dba64-112">Description</span></span>  
 <span data-ttu-id="dba64-113">Esse evento é emitido por clientes antes de uma operação é enviada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="dba64-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dba64-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="dba64-114">Message</span></span>  
 <span data-ttu-id="dba64-115">O cliente está executando a ação '%1' associada ao contrato '%2'.</span><span class="sxs-lookup"><span data-stu-id="dba64-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="dba64-116">A mensagem será enviada para '%3'.</span><span class="sxs-lookup"><span data-stu-id="dba64-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dba64-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="dba64-117">Details</span></span>  
  
|<span data-ttu-id="dba64-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="dba64-118">Data Item Name</span></span>|<span data-ttu-id="dba64-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="dba64-119">Data Item Type</span></span>|<span data-ttu-id="dba64-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="dba64-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dba64-121">Ação</span><span class="sxs-lookup"><span data-stu-id="dba64-121">Action</span></span>|`xs:string`|<span data-ttu-id="dba64-122">O cabeçalho de ação SOAP da mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="dba64-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="dba64-123">Nome do contrato</span><span class="sxs-lookup"><span data-stu-id="dba64-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="dba64-124">O nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="dba64-124">The name of the contract.</span></span> <span data-ttu-id="dba64-125">Exemplo: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="dba64-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="dba64-126">Destino</span><span class="sxs-lookup"><span data-stu-id="dba64-126">Destination</span></span>|`xs:string`|<span data-ttu-id="dba64-127">O endereço do ponto de extremidade de serviço que a mensagem é enviada ao.</span><span class="sxs-lookup"><span data-stu-id="dba64-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="dba64-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="dba64-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="dba64-129">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="dba64-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="dba64-130">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="dba64-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="dba64-131">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="dba64-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="dba64-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dba64-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dba64-133">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dba64-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
