---
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512132"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="717d8-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="717d8-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="717d8-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="717d8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="717d8-104">ID</span><span class="sxs-lookup"><span data-stu-id="717d8-104">ID</span></span>|<span data-ttu-id="717d8-105">225</span><span class="sxs-lookup"><span data-stu-id="717d8-105">225</span></span>|  
|<span data-ttu-id="717d8-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="717d8-106">Keywords</span></span>|<span data-ttu-id="717d8-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="717d8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="717d8-108">Nível</span><span class="sxs-lookup"><span data-stu-id="717d8-108">Level</span></span>|<span data-ttu-id="717d8-109">Informações</span><span class="sxs-lookup"><span data-stu-id="717d8-109">Information</span></span>|  
|<span data-ttu-id="717d8-110">Canal</span><span class="sxs-lookup"><span data-stu-id="717d8-110">Channel</span></span>|<span data-ttu-id="717d8-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="717d8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="717d8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="717d8-112">Description</span></span>  
 <span data-ttu-id="717d8-113">Este evento é emitida quando correlação conteudo base é usada para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="717d8-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="717d8-114">Contém as chaves de correlação que são aplicadas para correlacionar uma mensagem a uma instância.</span><span class="sxs-lookup"><span data-stu-id="717d8-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="717d8-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="717d8-115">Message</span></span>  
 <span data-ttu-id="717d8-116">Chave calculada “%1 " de correlação usando o %2 " dos valores no escopo pai “%3 ".</span><span class="sxs-lookup"><span data-stu-id="717d8-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="717d8-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="717d8-117">Details</span></span>  
  
|<span data-ttu-id="717d8-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="717d8-118">Data Item Name</span></span>|<span data-ttu-id="717d8-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="717d8-119">Data Item Type</span></span>|<span data-ttu-id="717d8-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="717d8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="717d8-121">Chave de instância</span><span class="sxs-lookup"><span data-stu-id="717d8-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="717d8-122">A tecla que foi gerada de correlação avalia.</span><span class="sxs-lookup"><span data-stu-id="717d8-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="717d8-123">Valores</span><span class="sxs-lookup"><span data-stu-id="717d8-123">Values</span></span>|`xs:string`|<span data-ttu-id="717d8-124">Os valores que foram usados para calcular a chave de instância de correlação.</span><span class="sxs-lookup"><span data-stu-id="717d8-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="717d8-125">Escopo pai</span><span class="sxs-lookup"><span data-stu-id="717d8-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="717d8-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="717d8-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="717d8-127">Os serviços hospedados da Web, este campo identificam exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="717d8-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="717d8-128">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="717d8-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="717d8-129">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="717d8-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="717d8-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="717d8-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="717d8-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="717d8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
