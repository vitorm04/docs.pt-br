---
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: ada3ced31def2bb821b975e09f50ad83f28d56bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781856"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="14f62-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="14f62-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="14f62-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="14f62-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14f62-104">ID</span><span class="sxs-lookup"><span data-stu-id="14f62-104">ID</span></span>|<span data-ttu-id="14f62-105">211</span><span class="sxs-lookup"><span data-stu-id="14f62-105">211</span></span>|  
|<span data-ttu-id="14f62-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="14f62-106">Keywords</span></span>|<span data-ttu-id="14f62-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="14f62-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="14f62-108">Nível</span><span class="sxs-lookup"><span data-stu-id="14f62-108">Level</span></span>|<span data-ttu-id="14f62-109">Informações</span><span class="sxs-lookup"><span data-stu-id="14f62-109">Information</span></span>|  
|<span data-ttu-id="14f62-110">Canal</span><span class="sxs-lookup"><span data-stu-id="14f62-110">Channel</span></span>|<span data-ttu-id="14f62-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="14f62-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14f62-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="14f62-112">Description</span></span>  
 <span data-ttu-id="14f62-113">Esse evento é emitido depois que o modelo de serviço tem chamado a `AfterCall` método em um `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="14f62-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="14f62-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="14f62-114">Message</span></span>  
 <span data-ttu-id="14f62-115">O Dispatcher invocado AfterCall em um ParameterInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="14f62-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="14f62-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="14f62-116">Details</span></span>  
  
|<span data-ttu-id="14f62-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="14f62-117">Data Item Name</span></span>|<span data-ttu-id="14f62-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="14f62-118">Data Item Type</span></span>|<span data-ttu-id="14f62-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="14f62-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="14f62-120">Nome do tipo</span><span class="sxs-lookup"><span data-stu-id="14f62-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="14f62-121">O FullName do CLR do tipo de chamada `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="14f62-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="14f62-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="14f62-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="14f62-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="14f62-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="14f62-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="14f62-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="14f62-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="14f62-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="14f62-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="14f62-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="14f62-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="14f62-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
