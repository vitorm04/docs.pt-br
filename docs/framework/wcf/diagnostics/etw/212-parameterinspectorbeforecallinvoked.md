---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d043bbf4b6484e2d2bcc7840fa08ebc371dca02a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="baa79-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="baa79-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="baa79-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="baa79-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="baa79-104">ID</span><span class="sxs-lookup"><span data-stu-id="baa79-104">ID</span></span>|<span data-ttu-id="baa79-105">212</span><span class="sxs-lookup"><span data-stu-id="baa79-105">212</span></span>|  
|<span data-ttu-id="baa79-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="baa79-106">Keywords</span></span>|<span data-ttu-id="baa79-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="baa79-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="baa79-108">Nível</span><span class="sxs-lookup"><span data-stu-id="baa79-108">Level</span></span>|<span data-ttu-id="baa79-109">Informações</span><span class="sxs-lookup"><span data-stu-id="baa79-109">Information</span></span>|  
|<span data-ttu-id="baa79-110">Canal</span><span class="sxs-lookup"><span data-stu-id="baa79-110">Channel</span></span>|<span data-ttu-id="baa79-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="baa79-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="baa79-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="baa79-112">Description</span></span>  
 <span data-ttu-id="baa79-113">Esse evento é emitido após o modelo de serviço foi invocado o `BeforeCall` método em um `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="baa79-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="baa79-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="baa79-114">Message</span></span>  
 <span data-ttu-id="baa79-115">O Dispatcher invocou 'BeforeCall' em um ParameterInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="baa79-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="baa79-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="baa79-116">Details</span></span>  
  
|<span data-ttu-id="baa79-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="baa79-117">Data Item Name</span></span>|<span data-ttu-id="baa79-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="baa79-118">Data Item Type</span></span>|<span data-ttu-id="baa79-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="baa79-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="baa79-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="baa79-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="baa79-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="baa79-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="baa79-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="baa79-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="baa79-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="baa79-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="baa79-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="baa79-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="baa79-125">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="baa79-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="baa79-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="baa79-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="baa79-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="baa79-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
