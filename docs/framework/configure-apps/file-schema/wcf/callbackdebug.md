---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 62ce1bc179c7215d4988e4c6bda08025c3d3e5de
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286306"
---
# <a name="callbackdebug"></a><span data-ttu-id="2fc38-101">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="2fc38-101">\<callbackDebug></span></span>
<span data-ttu-id="2fc38-102">Especifica a depuração de serviço para um objeto de retorno de chamada do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2fc38-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="2fc38-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2fc38-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2fc38-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="2fc38-104">\<behaviors></span></span>  
<span data-ttu-id="2fc38-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="2fc38-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="2fc38-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2fc38-106">\<behavior></span></span>  
<span data-ttu-id="2fc38-107">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="2fc38-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc38-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fc38-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="2fc38-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="2fc38-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fc38-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2fc38-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2fc38-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2fc38-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fc38-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="2fc38-112">Attributes</span></span>  
  
|<span data-ttu-id="2fc38-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="2fc38-113">Attribute</span></span>|<span data-ttu-id="2fc38-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc38-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="2fc38-115">Um valor que especifica se objetos de retorno de chamada do cliente retornam informações de exceção gerenciada em falhas SOAP para o serviço.</span><span class="sxs-lookup"><span data-stu-id="2fc38-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="2fc38-116">Se você definir esse atributo como `true` programaticamente, você pode habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada do cliente para o serviço para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="2fc38-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="2fc38-117">**Cuidado:**  Retornando informações de exceção gerenciada para os clientes podem ser um risco à segurança.</span><span class="sxs-lookup"><span data-stu-id="2fc38-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="2fc38-118">Isso ocorre porque os detalhes da exceção expõem informações sobre a implementação de serviço interno que pode ser usada por clientes não autorizados.</span><span class="sxs-lookup"><span data-stu-id="2fc38-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fc38-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2fc38-119">Child Elements</span></span>  
 <span data-ttu-id="2fc38-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2fc38-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fc38-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2fc38-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2fc38-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="2fc38-122">Element</span></span>|<span data-ttu-id="2fc38-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc38-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fc38-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2fc38-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2fc38-125">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2fc38-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2fc38-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc38-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
