---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: 57192b44a0c3babc77fcca13ad4a1433b85bfdd7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781934"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="448e5-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="448e5-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="448e5-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="448e5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="448e5-104">ID</span><span class="sxs-lookup"><span data-stu-id="448e5-104">ID</span></span>|<span data-ttu-id="448e5-105">203</span><span class="sxs-lookup"><span data-stu-id="448e5-105">203</span></span>|  
|<span data-ttu-id="448e5-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="448e5-106">Keywords</span></span>|<span data-ttu-id="448e5-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="448e5-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="448e5-108">Nível</span><span class="sxs-lookup"><span data-stu-id="448e5-108">Level</span></span>|<span data-ttu-id="448e5-109">Informações</span><span class="sxs-lookup"><span data-stu-id="448e5-109">Information</span></span>|  
|<span data-ttu-id="448e5-110">Canal</span><span class="sxs-lookup"><span data-stu-id="448e5-110">Channel</span></span>|<span data-ttu-id="448e5-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="448e5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="448e5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="448e5-112">Description</span></span>  
 <span data-ttu-id="448e5-113">Esse evento é emitido depois que o modelo de serviço tenha chamado o `AfterCall` método em um Inspetor de parâmetro do cliente.</span><span class="sxs-lookup"><span data-stu-id="448e5-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="448e5-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="448e5-114">Message</span></span>  
 <span data-ttu-id="448e5-115">O Dispatcher invocado AfterCall em um ClientParameterInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="448e5-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="448e5-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="448e5-116">Details</span></span>  
  
|<span data-ttu-id="448e5-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="448e5-117">Data Item Name</span></span>|<span data-ttu-id="448e5-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="448e5-118">Data Item Type</span></span>|<span data-ttu-id="448e5-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="448e5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="448e5-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="448e5-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="448e5-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="448e5-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="448e5-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="448e5-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="448e5-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="448e5-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="448e5-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="448e5-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="448e5-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="448e5-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="448e5-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="448e5-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="448e5-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="448e5-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
