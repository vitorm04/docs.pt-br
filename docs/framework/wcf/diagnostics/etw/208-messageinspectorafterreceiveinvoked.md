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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 670650c612ac01ab9c82028388a4524d2f08fd79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="0878e-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="0878e-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="0878e-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0878e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0878e-104">ID</span><span class="sxs-lookup"><span data-stu-id="0878e-104">ID</span></span>|<span data-ttu-id="0878e-105">208</span><span class="sxs-lookup"><span data-stu-id="0878e-105">208</span></span>|  
|<span data-ttu-id="0878e-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="0878e-106">Keywords</span></span>|<span data-ttu-id="0878e-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0878e-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0878e-108">Nível</span><span class="sxs-lookup"><span data-stu-id="0878e-108">Level</span></span>|<span data-ttu-id="0878e-109">Informações</span><span class="sxs-lookup"><span data-stu-id="0878e-109">Information</span></span>|  
|<span data-ttu-id="0878e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0878e-110">Channel</span></span>|<span data-ttu-id="0878e-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="0878e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0878e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0878e-112">Description</span></span>  
 <span data-ttu-id="0878e-113">Esse evento é emitido após o modelo de serviço foi invocado o `AfterReceive` método em um Inspetor de mensagem.</span><span class="sxs-lookup"><span data-stu-id="0878e-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0878e-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="0878e-114">Message</span></span>  
 <span data-ttu-id="0878e-115">O Dispatcher invocou 'AfterReceiveReply' em um MessageInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="0878e-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0878e-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0878e-116">Details</span></span>  
  
|<span data-ttu-id="0878e-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="0878e-117">Data Item Name</span></span>|<span data-ttu-id="0878e-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="0878e-118">Data Item Type</span></span>|<span data-ttu-id="0878e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0878e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0878e-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="0878e-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="0878e-121">O FullName do CLR do tipo de chamada `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="0878e-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="0878e-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="0878e-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="0878e-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="0878e-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0878e-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="0878e-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0878e-125">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="0878e-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0878e-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0878e-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0878e-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0878e-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
