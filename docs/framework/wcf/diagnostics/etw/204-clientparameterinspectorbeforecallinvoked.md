---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: eb060cfa79b75452deae67705126a24b7ca9ffef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782025"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="42222-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="42222-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="42222-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="42222-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42222-104">ID</span><span class="sxs-lookup"><span data-stu-id="42222-104">ID</span></span>|<span data-ttu-id="42222-105">204</span><span class="sxs-lookup"><span data-stu-id="42222-105">204</span></span>|  
|<span data-ttu-id="42222-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="42222-106">Keywords</span></span>|<span data-ttu-id="42222-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="42222-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="42222-108">Nível</span><span class="sxs-lookup"><span data-stu-id="42222-108">Level</span></span>|<span data-ttu-id="42222-109">Informações</span><span class="sxs-lookup"><span data-stu-id="42222-109">Information</span></span>|  
|<span data-ttu-id="42222-110">Canal</span><span class="sxs-lookup"><span data-stu-id="42222-110">Channel</span></span>|<span data-ttu-id="42222-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="42222-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="42222-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="42222-112">Description</span></span>  
 <span data-ttu-id="42222-113">Esse evento é emitido depois que o modelo de serviço tenha chamado o `BeforeCall` método em um Inspetor de parâmetro do cliente.</span><span class="sxs-lookup"><span data-stu-id="42222-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="42222-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="42222-114">Message</span></span>  
 <span data-ttu-id="42222-115">O Dispatcher invocado BeforeCall em um ClientParameterInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="42222-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="42222-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="42222-116">Details</span></span>  
  
|<span data-ttu-id="42222-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="42222-117">Data Item Name</span></span>|<span data-ttu-id="42222-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="42222-118">Data Item Type</span></span>|<span data-ttu-id="42222-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="42222-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="42222-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="42222-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="42222-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="42222-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="42222-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="42222-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="42222-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="42222-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="42222-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="42222-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="42222-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="42222-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="42222-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="42222-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="42222-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="42222-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
