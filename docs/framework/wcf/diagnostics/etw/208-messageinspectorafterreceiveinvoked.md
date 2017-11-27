---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cdb89eb9f2a50db20f6da53a2b3f527aef8c0ed1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="a2391-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="a2391-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="a2391-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a2391-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a2391-104">ID</span><span class="sxs-lookup"><span data-stu-id="a2391-104">ID</span></span>|<span data-ttu-id="a2391-105">208</span><span class="sxs-lookup"><span data-stu-id="a2391-105">208</span></span>|  
|<span data-ttu-id="a2391-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a2391-106">Keywords</span></span>|<span data-ttu-id="a2391-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a2391-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a2391-108">Nível</span><span class="sxs-lookup"><span data-stu-id="a2391-108">Level</span></span>|<span data-ttu-id="a2391-109">Informações</span><span class="sxs-lookup"><span data-stu-id="a2391-109">Information</span></span>|  
|<span data-ttu-id="a2391-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a2391-110">Channel</span></span>|<span data-ttu-id="a2391-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="a2391-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a2391-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2391-112">Description</span></span>  
 <span data-ttu-id="a2391-113">Esse evento é emitido após o modelo de serviço foi invocado o `AfterReceive` método em um Inspetor de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a2391-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a2391-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="a2391-114">Message</span></span>  
 <span data-ttu-id="a2391-115">O Dispatcher invocou 'AfterReceiveReply' em um MessageInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="a2391-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a2391-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a2391-116">Details</span></span>  
  
|<span data-ttu-id="a2391-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="a2391-117">Data Item Name</span></span>|<span data-ttu-id="a2391-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="a2391-118">Data Item Type</span></span>|<span data-ttu-id="a2391-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2391-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a2391-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="a2391-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="a2391-121">O FullName do CLR do tipo de chamada `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="a2391-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="a2391-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="a2391-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="a2391-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="a2391-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a2391-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="a2391-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a2391-125">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="a2391-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a2391-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a2391-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a2391-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a2391-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
