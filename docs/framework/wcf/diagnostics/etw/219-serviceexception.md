---
title: 219 - ServiceException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5750748f2885418b8992ce54bbdf6a92b8e1fe39
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="219---serviceexception"></a><span data-ttu-id="75214-102">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="75214-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="75214-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="75214-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75214-104">ID</span><span class="sxs-lookup"><span data-stu-id="75214-104">ID</span></span>|<span data-ttu-id="75214-105">219</span><span class="sxs-lookup"><span data-stu-id="75214-105">219</span></span>|  
|<span data-ttu-id="75214-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="75214-106">Keywords</span></span>|<span data-ttu-id="75214-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="75214-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="75214-108">Nível</span><span class="sxs-lookup"><span data-stu-id="75214-108">Level</span></span>|<span data-ttu-id="75214-109">Erro</span><span class="sxs-lookup"><span data-stu-id="75214-109">Error</span></span>|  
|<span data-ttu-id="75214-110">Canal</span><span class="sxs-lookup"><span data-stu-id="75214-110">Channel</span></span>|<span data-ttu-id="75214-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="75214-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="75214-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="75214-112">Description</span></span>  
 <span data-ttu-id="75214-113">Esse evento é emitido quando um serviço WCF encontra uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="75214-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="75214-114">Isso inclui exceções sem tratamento durante a ativação, durante o processamento de mensagem e no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="75214-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="75214-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="75214-115">Message</span></span>  
 <span data-ttu-id="75214-116">Ocorreu uma exceção sem tratamento do tipo '%2' durante o processamento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="75214-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="75214-117">ToString completo da exceção: %1.</span><span class="sxs-lookup"><span data-stu-id="75214-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="75214-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="75214-118">Details</span></span>  
  
|<span data-ttu-id="75214-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="75214-119">Data Item Name</span></span>|<span data-ttu-id="75214-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="75214-120">Data Item Type</span></span>|<span data-ttu-id="75214-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="75214-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="75214-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="75214-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="75214-123">O resultado da chamada `ToString`() na exceção CLR.</span><span class="sxs-lookup"><span data-stu-id="75214-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="75214-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="75214-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="75214-125">O FullName do CLR do tipo da exceção.</span><span class="sxs-lookup"><span data-stu-id="75214-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="75214-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="75214-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="75214-127">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="75214-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="75214-128">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="75214-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="75214-129">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="75214-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="75214-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="75214-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="75214-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="75214-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
