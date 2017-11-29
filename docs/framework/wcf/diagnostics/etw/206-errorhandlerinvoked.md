---
title: 206 - ErrorHandlerInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84470cbaf7ba7951ef59b130c696462079216cde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="931c0-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="931c0-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="931c0-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="931c0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="931c0-104">ID</span><span class="sxs-lookup"><span data-stu-id="931c0-104">ID</span></span>|<span data-ttu-id="931c0-105">206</span><span class="sxs-lookup"><span data-stu-id="931c0-105">206</span></span>|  
|<span data-ttu-id="931c0-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="931c0-106">Keywords</span></span>|<span data-ttu-id="931c0-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="931c0-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="931c0-108">Nível</span><span class="sxs-lookup"><span data-stu-id="931c0-108">Level</span></span>|<span data-ttu-id="931c0-109">Informações</span><span class="sxs-lookup"><span data-stu-id="931c0-109">Information</span></span>|  
|<span data-ttu-id="931c0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="931c0-110">Channel</span></span>|<span data-ttu-id="931c0-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="931c0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="931c0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="931c0-112">Description</span></span>  
 <span data-ttu-id="931c0-113">Esse evento é emitido após um `ErrorHandler` teve a oportunidade de manipular uma exceção que ocorreu em uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="931c0-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="931c0-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="931c0-114">Message</span></span>  
 <span data-ttu-id="931c0-115">O Dispatcher invocou um ErrorHandler do tipo '%1' com uma exceção do tipo '%3'.</span><span class="sxs-lookup"><span data-stu-id="931c0-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="931c0-116">ErrorHandled = = '%2'.</span><span class="sxs-lookup"><span data-stu-id="931c0-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="931c0-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="931c0-117">Details</span></span>  
  
|<span data-ttu-id="931c0-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="931c0-118">Data Item Name</span></span>|<span data-ttu-id="931c0-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="931c0-119">Data Item Type</span></span>|<span data-ttu-id="931c0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="931c0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="931c0-121">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="931c0-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="931c0-122">O FullName do CLR do tipo de chamada `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="931c0-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="931c0-123">Tratado</span><span class="sxs-lookup"><span data-stu-id="931c0-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="931c0-124">`true`Se o manipulador de erro tratadas o erro, caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="931c0-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="931c0-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="931c0-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="931c0-126">O FullName do CLR da exceção que estava sendo tratada.</span><span class="sxs-lookup"><span data-stu-id="931c0-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="931c0-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="931c0-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="931c0-128">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="931c0-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="931c0-129">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="931c0-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="931c0-130">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="931c0-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="931c0-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="931c0-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="931c0-132">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="931c0-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
