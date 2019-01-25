---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 1aa292a3fe06af9cf1dbc53ebf5bbdf9841be8d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687369"
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="7659e-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="7659e-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="7659e-103">Especifica a depuração de serviço para um objeto de retorno de chamada do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7659e-103">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="7659e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7659e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7659e-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7659e-105">\<behaviors></span></span>  
<span data-ttu-id="7659e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7659e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7659e-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7659e-107">\<behavior></span></span>  
<span data-ttu-id="7659e-108">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="7659e-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7659e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7659e-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="7659e-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="7659e-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7659e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7659e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7659e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7659e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7659e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="7659e-113">Attributes</span></span>  
  
|<span data-ttu-id="7659e-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="7659e-114">Attribute</span></span>|<span data-ttu-id="7659e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="7659e-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="7659e-116">Um valor que especifica se objetos de retorno de chamada do cliente retornam informações de exceção gerenciada em falhas SOAP para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7659e-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="7659e-117">Se você definir esse atributo como `true` programaticamente, você pode habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada do cliente para o serviço para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="7659e-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="7659e-118">**Cuidado:**  Retornando informações de exceção gerenciada para os clientes podem ser um risco à segurança.</span><span class="sxs-lookup"><span data-stu-id="7659e-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="7659e-119">Isso ocorre porque os detalhes da exceção expõem informações sobre a implementação de serviço interno que pode ser usada por clientes não autorizados.</span><span class="sxs-lookup"><span data-stu-id="7659e-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7659e-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7659e-120">Child Elements</span></span>  
 <span data-ttu-id="7659e-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7659e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7659e-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7659e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7659e-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="7659e-123">Element</span></span>|<span data-ttu-id="7659e-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="7659e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7659e-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7659e-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7659e-126">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7659e-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7659e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7659e-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
