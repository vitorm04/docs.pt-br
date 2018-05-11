---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: eb060cfa79b75452deae67705126a24b7ca9ffef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="5fdeb-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="5fdeb-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="5fdeb-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5fdeb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fdeb-104">ID</span><span class="sxs-lookup"><span data-stu-id="5fdeb-104">ID</span></span>|<span data-ttu-id="5fdeb-105">204</span><span class="sxs-lookup"><span data-stu-id="5fdeb-105">204</span></span>|  
|<span data-ttu-id="5fdeb-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5fdeb-106">Keywords</span></span>|<span data-ttu-id="5fdeb-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5fdeb-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5fdeb-108">Nível</span><span class="sxs-lookup"><span data-stu-id="5fdeb-108">Level</span></span>|<span data-ttu-id="5fdeb-109">Informações</span><span class="sxs-lookup"><span data-stu-id="5fdeb-109">Information</span></span>|  
|<span data-ttu-id="5fdeb-110">Canal</span><span class="sxs-lookup"><span data-stu-id="5fdeb-110">Channel</span></span>|<span data-ttu-id="5fdeb-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="5fdeb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5fdeb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5fdeb-112">Description</span></span>  
 <span data-ttu-id="5fdeb-113">Esse evento é emitido após o modelo de serviço foi invocado o `BeforeCall` método em um Inspetor de parâmetro do cliente.</span><span class="sxs-lookup"><span data-stu-id="5fdeb-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5fdeb-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5fdeb-114">Message</span></span>  
 <span data-ttu-id="5fdeb-115">O Dispatcher invocou 'BeforeCall' em um ClientParameterInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="5fdeb-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5fdeb-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5fdeb-116">Details</span></span>  
  
|<span data-ttu-id="5fdeb-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="5fdeb-117">Data Item Name</span></span>|<span data-ttu-id="5fdeb-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="5fdeb-118">Data Item Type</span></span>|<span data-ttu-id="5fdeb-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5fdeb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5fdeb-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="5fdeb-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="5fdeb-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="5fdeb-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="5fdeb-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="5fdeb-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="5fdeb-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="5fdeb-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5fdeb-124">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="5fdeb-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5fdeb-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="5fdeb-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5fdeb-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5fdeb-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5fdeb-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5fdeb-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
