---
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: ada3ced31def2bb821b975e09f50ad83f28d56bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459711"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="133a6-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="133a6-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="133a6-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="133a6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="133a6-104">ID</span><span class="sxs-lookup"><span data-stu-id="133a6-104">ID</span></span>|<span data-ttu-id="133a6-105">211</span><span class="sxs-lookup"><span data-stu-id="133a6-105">211</span></span>|  
|<span data-ttu-id="133a6-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="133a6-106">Keywords</span></span>|<span data-ttu-id="133a6-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="133a6-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="133a6-108">Nível</span><span class="sxs-lookup"><span data-stu-id="133a6-108">Level</span></span>|<span data-ttu-id="133a6-109">Informações</span><span class="sxs-lookup"><span data-stu-id="133a6-109">Information</span></span>|  
|<span data-ttu-id="133a6-110">Canal</span><span class="sxs-lookup"><span data-stu-id="133a6-110">Channel</span></span>|<span data-ttu-id="133a6-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="133a6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="133a6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="133a6-112">Description</span></span>  
 <span data-ttu-id="133a6-113">Esse evento é emitido após o modelo de serviço foi invocado o `AfterCall` método em um `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="133a6-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="133a6-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="133a6-114">Message</span></span>  
 <span data-ttu-id="133a6-115">O Dispatcher invocou 'AfterCall' em um ParameterInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="133a6-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="133a6-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="133a6-116">Details</span></span>  
  
|<span data-ttu-id="133a6-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="133a6-117">Data Item Name</span></span>|<span data-ttu-id="133a6-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="133a6-118">Data Item Type</span></span>|<span data-ttu-id="133a6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="133a6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="133a6-120">Nome do tipo</span><span class="sxs-lookup"><span data-stu-id="133a6-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="133a6-121">O FullName do CLR do tipo de chamada `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="133a6-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="133a6-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="133a6-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="133a6-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="133a6-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="133a6-124">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="133a6-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="133a6-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="133a6-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="133a6-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="133a6-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="133a6-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="133a6-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
