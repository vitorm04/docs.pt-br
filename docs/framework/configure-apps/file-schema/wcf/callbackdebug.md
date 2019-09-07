---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400563"
---
# <a name="callbackdebug"></a><span data-ttu-id="eda70-101">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="eda70-101">\<callbackDebug></span></span>
<span data-ttu-id="eda70-102">Especifica a depuração de serviço para um objeto de retorno de chamada Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="eda70-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
<span data-ttu-id="eda70-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eda70-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eda70-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="eda70-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="eda70-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="eda70-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="eda70-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="eda70-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="eda70-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="eda70-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="eda70-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> callbackDebug**</span><span class="sxs-lookup"><span data-stu-id="eda70-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda70-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eda70-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="eda70-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="eda70-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eda70-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eda70-111">Attributes and Elements</span></span>  
 <span data-ttu-id="eda70-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eda70-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eda70-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="eda70-113">Attributes</span></span>  
  
|<span data-ttu-id="eda70-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="eda70-114">Attribute</span></span>|<span data-ttu-id="eda70-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="eda70-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="eda70-116">Um valor que especifica se os objetos de retorno de chamada do cliente retornam informações de exceção gerenciada em falhas de SOAP de volta ao serviço.</span><span class="sxs-lookup"><span data-stu-id="eda70-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="eda70-117">Se você definir esse atributo como `true` programaticamente, poderá habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada do cliente de volta para o serviço para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="eda70-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="eda70-118">**Cuidado:**  Retornar informações de exceção gerenciada aos clientes pode ser um risco de segurança.</span><span class="sxs-lookup"><span data-stu-id="eda70-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="eda70-119">Isso ocorre porque os detalhes da exceção expõem informações sobre a implementação do serviço interno que pode ser usada por clientes não autorizados.</span><span class="sxs-lookup"><span data-stu-id="eda70-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eda70-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eda70-120">Child Elements</span></span>  
 <span data-ttu-id="eda70-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="eda70-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eda70-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eda70-122">Parent Elements</span></span>  
  
|<span data-ttu-id="eda70-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="eda70-123">Element</span></span>|<span data-ttu-id="eda70-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="eda70-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eda70-125">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="eda70-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="eda70-126">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="eda70-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eda70-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eda70-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
