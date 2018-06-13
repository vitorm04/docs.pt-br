---
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457968"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="eefdf-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="eefdf-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="eefdf-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="eefdf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eefdf-104">ID</span><span class="sxs-lookup"><span data-stu-id="eefdf-104">ID</span></span>|<span data-ttu-id="eefdf-105">218</span><span class="sxs-lookup"><span data-stu-id="eefdf-105">218</span></span>|  
|<span data-ttu-id="eefdf-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="eefdf-106">Keywords</span></span>|<span data-ttu-id="eefdf-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="eefdf-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="eefdf-108">Nível</span><span class="sxs-lookup"><span data-stu-id="eefdf-108">Level</span></span>|<span data-ttu-id="eefdf-109">Informações</span><span class="sxs-lookup"><span data-stu-id="eefdf-109">Information</span></span>|  
|<span data-ttu-id="eefdf-110">Canal</span><span class="sxs-lookup"><span data-stu-id="eefdf-110">Channel</span></span>|<span data-ttu-id="eefdf-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="eefdf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eefdf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="eefdf-112">Description</span></span>  
 <span data-ttu-id="eefdf-113">Esse evento é emitido por clientes depois que uma operação é concluída.</span><span class="sxs-lookup"><span data-stu-id="eefdf-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="eefdf-114">Para operações unidirecionais, isso é apenas depois que a mensagem é enviada com êxito.</span><span class="sxs-lookup"><span data-stu-id="eefdf-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="eefdf-115">Para operações de solicitação-resposta, isso é após o recebimento da resposta.</span><span class="sxs-lookup"><span data-stu-id="eefdf-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eefdf-116">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eefdf-116">Message</span></span>  
 <span data-ttu-id="eefdf-117">O cliente concluiu a execução da ação '%1' associada ao contrato '%2'.</span><span class="sxs-lookup"><span data-stu-id="eefdf-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="eefdf-118">A mensagem foi enviada para '%3'.</span><span class="sxs-lookup"><span data-stu-id="eefdf-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eefdf-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="eefdf-119">Details</span></span>  
  
|<span data-ttu-id="eefdf-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="eefdf-120">Data Item Name</span></span>|<span data-ttu-id="eefdf-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="eefdf-121">Data Item Type</span></span>|<span data-ttu-id="eefdf-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="eefdf-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eefdf-123">Ação</span><span class="sxs-lookup"><span data-stu-id="eefdf-123">Action</span></span>|<span data-ttu-id="eefdf-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="eefdf-124">xs:string</span></span>|<span data-ttu-id="eefdf-125">O cabeçalho de ação SOAP da mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="eefdf-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="eefdf-126">Nome do contrato</span><span class="sxs-lookup"><span data-stu-id="eefdf-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="eefdf-127">O nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="eefdf-127">The name of the contract.</span></span> <span data-ttu-id="eefdf-128">Exemplo: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="eefdf-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="eefdf-129">Destino</span><span class="sxs-lookup"><span data-stu-id="eefdf-129">Destination</span></span>|`xs:string`|<span data-ttu-id="eefdf-130">O endereço do ponto de extremidade de serviço que a mensagem foi enviada ao.</span><span class="sxs-lookup"><span data-stu-id="eefdf-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="eefdf-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="eefdf-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="eefdf-132">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="eefdf-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="eefdf-133">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="eefdf-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="eefdf-134">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="eefdf-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="eefdf-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eefdf-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="eefdf-136">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="eefdf-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
