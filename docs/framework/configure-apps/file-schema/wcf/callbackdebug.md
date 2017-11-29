---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 93b89787795cb58644b79ae4795e7a036741e138
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="8284c-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="8284c-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="8284c-103">Especifica o serviço de depuração para um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] objeto de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="8284c-103">Specifies service debugging for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] callback object.</span></span>  
  
 <span data-ttu-id="8284c-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8284c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8284c-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="8284c-105">\<behaviors></span></span>  
<span data-ttu-id="8284c-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8284c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="8284c-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="8284c-107">\<behavior></span></span>  
<span data-ttu-id="8284c-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="8284c-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8284c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8284c-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="8284c-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="8284c-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8284c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8284c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8284c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8284c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8284c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="8284c-113">Attributes</span></span>  
  
|<span data-ttu-id="8284c-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="8284c-114">Attribute</span></span>|<span data-ttu-id="8284c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8284c-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="8284c-116">Um valor que especifica se os objetos de retorno de chamada do cliente retornam informações de exceção gerenciada em falhas SOAP para o serviço.</span><span class="sxs-lookup"><span data-stu-id="8284c-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="8284c-117">Se você definir esse atributo como `true` programaticamente, você pode habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada do cliente para o serviço para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="8284c-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="8284c-118">**Cuidado:** retornando informações de exceção gerenciada em clientes podem ser um risco à segurança.</span><span class="sxs-lookup"><span data-stu-id="8284c-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="8284c-119">Isso ocorre porque os detalhes da exceção expõem informações sobre a implementação de serviço interno que pode ser usada por clientes não autorizados.</span><span class="sxs-lookup"><span data-stu-id="8284c-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8284c-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8284c-120">Child Elements</span></span>  
 <span data-ttu-id="8284c-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8284c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8284c-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8284c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8284c-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="8284c-123">Element</span></span>|<span data-ttu-id="8284c-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="8284c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8284c-125">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="8284c-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8284c-126">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8284c-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8284c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8284c-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
