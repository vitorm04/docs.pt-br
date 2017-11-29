---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b736d9e2827708caea54fbe230b0b638492adb96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="a992b-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="a992b-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="a992b-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a992b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a992b-104">ID</span><span class="sxs-lookup"><span data-stu-id="a992b-104">ID</span></span>|<span data-ttu-id="a992b-105">203</span><span class="sxs-lookup"><span data-stu-id="a992b-105">203</span></span>|  
|<span data-ttu-id="a992b-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a992b-106">Keywords</span></span>|<span data-ttu-id="a992b-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a992b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a992b-108">Nível</span><span class="sxs-lookup"><span data-stu-id="a992b-108">Level</span></span>|<span data-ttu-id="a992b-109">Informações</span><span class="sxs-lookup"><span data-stu-id="a992b-109">Information</span></span>|  
|<span data-ttu-id="a992b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a992b-110">Channel</span></span>|<span data-ttu-id="a992b-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="a992b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a992b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a992b-112">Description</span></span>  
 <span data-ttu-id="a992b-113">Esse evento é emitido após o modelo de serviço foi invocado o `AfterCall` método em um Inspetor de parâmetro do cliente.</span><span class="sxs-lookup"><span data-stu-id="a992b-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a992b-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="a992b-114">Message</span></span>  
 <span data-ttu-id="a992b-115">O Dispatcher invocou 'AfterCall' em um ClientParameterInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="a992b-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a992b-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a992b-116">Details</span></span>  
  
|<span data-ttu-id="a992b-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="a992b-117">Data Item Name</span></span>|<span data-ttu-id="a992b-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="a992b-118">Data Item Type</span></span>|<span data-ttu-id="a992b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a992b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a992b-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="a992b-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="a992b-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="a992b-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="a992b-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="a992b-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="a992b-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="a992b-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a992b-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="a992b-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a992b-125">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="a992b-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a992b-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a992b-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a992b-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a992b-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
