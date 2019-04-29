---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 02d4a4ed1e96983e132a1943dd39f9f885e5596a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781843"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="ef133-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="ef133-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="ef133-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ef133-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef133-104">ID</span><span class="sxs-lookup"><span data-stu-id="ef133-104">ID</span></span>|<span data-ttu-id="ef133-105">212</span><span class="sxs-lookup"><span data-stu-id="ef133-105">212</span></span>|  
|<span data-ttu-id="ef133-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ef133-106">Keywords</span></span>|<span data-ttu-id="ef133-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ef133-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ef133-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ef133-108">Level</span></span>|<span data-ttu-id="ef133-109">Informações</span><span class="sxs-lookup"><span data-stu-id="ef133-109">Information</span></span>|  
|<span data-ttu-id="ef133-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ef133-110">Channel</span></span>|<span data-ttu-id="ef133-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="ef133-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef133-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef133-112">Description</span></span>  
 <span data-ttu-id="ef133-113">Esse evento é emitido depois que o modelo de serviço tem chamado a `BeforeCall` método em um `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="ef133-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ef133-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ef133-114">Message</span></span>  
 <span data-ttu-id="ef133-115">O Dispatcher invocado BeforeCall em um ParameterInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="ef133-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ef133-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ef133-116">Details</span></span>  
  
|<span data-ttu-id="ef133-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ef133-117">Data Item Name</span></span>|<span data-ttu-id="ef133-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ef133-118">Data Item Type</span></span>|<span data-ttu-id="ef133-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef133-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ef133-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="ef133-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="ef133-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="ef133-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="ef133-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="ef133-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="ef133-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="ef133-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ef133-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="ef133-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ef133-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="ef133-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ef133-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ef133-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ef133-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ef133-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
