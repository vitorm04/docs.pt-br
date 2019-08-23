---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 91e7bd63bf496f2c38776d88173ed2ac12a3b888
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926317"
---
# <a name="callbackdebug"></a><span data-ttu-id="ce604-101">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="ce604-101">\<callbackDebug></span></span>
<span data-ttu-id="ce604-102">Especifica a depuração de serviço para um objeto de retorno de chamada Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ce604-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="ce604-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ce604-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ce604-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ce604-104">\<behaviors></span></span>  
<span data-ttu-id="ce604-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ce604-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="ce604-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="ce604-106">\<behavior></span></span>  
<span data-ttu-id="ce604-107">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="ce604-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce604-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce604-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="ce604-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="ce604-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce604-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ce604-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ce604-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ce604-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce604-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce604-112">Attributes</span></span>  
  
|<span data-ttu-id="ce604-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ce604-113">Attribute</span></span>|<span data-ttu-id="ce604-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce604-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="ce604-115">Um valor que especifica se os objetos de retorno de chamada do cliente retornam informações de exceção gerenciada em falhas de SOAP de volta ao serviço.</span><span class="sxs-lookup"><span data-stu-id="ce604-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="ce604-116">Se você definir esse atributo como `true` programaticamente, poderá habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada do cliente de volta para o serviço para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="ce604-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="ce604-117">**Cuidado:**  Retornar informações de exceção gerenciada aos clientes pode ser um risco de segurança.</span><span class="sxs-lookup"><span data-stu-id="ce604-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="ce604-118">Isso ocorre porque os detalhes da exceção expõem informações sobre a implementação do serviço interno que pode ser usada por clientes não autorizados.</span><span class="sxs-lookup"><span data-stu-id="ce604-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce604-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ce604-119">Child Elements</span></span>  
 <span data-ttu-id="ce604-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ce604-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce604-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ce604-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ce604-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce604-122">Element</span></span>|<span data-ttu-id="ce604-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce604-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce604-124">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="ce604-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ce604-125">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce604-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce604-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce604-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
