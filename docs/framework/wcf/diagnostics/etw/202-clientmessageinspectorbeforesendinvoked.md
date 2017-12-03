---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 461c9e423abb7b34edec4135f05f8fcf66244cfc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="4d308-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="4d308-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="4d308-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4d308-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4d308-104">ID</span><span class="sxs-lookup"><span data-stu-id="4d308-104">ID</span></span>|<span data-ttu-id="4d308-105">202</span><span class="sxs-lookup"><span data-stu-id="4d308-105">202</span></span>|  
|<span data-ttu-id="4d308-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="4d308-106">Keywords</span></span>|<span data-ttu-id="4d308-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4d308-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4d308-108">Nível</span><span class="sxs-lookup"><span data-stu-id="4d308-108">Level</span></span>|<span data-ttu-id="4d308-109">Informações</span><span class="sxs-lookup"><span data-stu-id="4d308-109">Information</span></span>|  
|<span data-ttu-id="4d308-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4d308-110">Channel</span></span>|<span data-ttu-id="4d308-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="4d308-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4d308-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d308-112">Description</span></span>  
 <span data-ttu-id="4d308-113">Esse evento é emitido após o modelo de serviço foi invocado o `BeforeSendRequest` método em um Inspetor de mensagem do cliente.</span><span class="sxs-lookup"><span data-stu-id="4d308-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4d308-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="4d308-114">Message</span></span>  
 <span data-ttu-id="4d308-115">O Dispatcher invocou 'BeforeSendRequest' em um ClientMessageInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="4d308-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4d308-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4d308-116">Details</span></span>  
  
|<span data-ttu-id="4d308-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="4d308-117">Data Item Name</span></span>|<span data-ttu-id="4d308-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="4d308-118">Data Item Type</span></span>|<span data-ttu-id="4d308-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d308-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4d308-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="4d308-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="4d308-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="4d308-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="4d308-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="4d308-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="4d308-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="4d308-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4d308-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="4d308-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4d308-125">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="4d308-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4d308-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4d308-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4d308-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4d308-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
