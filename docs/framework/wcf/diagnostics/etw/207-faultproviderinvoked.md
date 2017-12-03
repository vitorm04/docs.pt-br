---
title: 207 - FaultProviderInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71fce60ca658c159df11588be149cda17ad2303d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="d6776-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="d6776-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="d6776-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d6776-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6776-104">ID</span><span class="sxs-lookup"><span data-stu-id="d6776-104">ID</span></span>|<span data-ttu-id="d6776-105">207</span><span class="sxs-lookup"><span data-stu-id="d6776-105">207</span></span>|  
|<span data-ttu-id="d6776-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d6776-106">Keywords</span></span>|<span data-ttu-id="d6776-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d6776-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d6776-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d6776-108">Level</span></span>|<span data-ttu-id="d6776-109">Informações</span><span class="sxs-lookup"><span data-stu-id="d6776-109">Information</span></span>|  
|<span data-ttu-id="d6776-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d6776-110">Channel</span></span>|<span data-ttu-id="d6776-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="d6776-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d6776-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6776-112">Description</span></span>  
 <span data-ttu-id="d6776-113">Esse evento é emitido após um `FaultProvider` foi chamado.</span><span class="sxs-lookup"><span data-stu-id="d6776-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d6776-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d6776-114">Message</span></span>  
 <span data-ttu-id="d6776-115">O Dispatcher invocou um FaultProvider do tipo '%1' com uma exceção do tipo '%2'.</span><span class="sxs-lookup"><span data-stu-id="d6776-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d6776-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d6776-116">Details</span></span>  
  
|<span data-ttu-id="d6776-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d6776-117">Data Item Name</span></span>|<span data-ttu-id="d6776-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d6776-118">Data Item Type</span></span>|<span data-ttu-id="d6776-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6776-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d6776-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="d6776-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="d6776-121">O FullName do CLR do tipo de chamada `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="d6776-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="d6776-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="d6776-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="d6776-123">O FullName do CLR da exceção que o `FaultProvider` tem operado.</span><span class="sxs-lookup"><span data-stu-id="d6776-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="d6776-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="d6776-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="d6776-125">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="d6776-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d6776-126">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="d6776-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d6776-127">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="d6776-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d6776-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d6776-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d6776-129">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d6776-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
