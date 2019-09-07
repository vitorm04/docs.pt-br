---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400072"
---
# <a name="persistenceprovider"></a><span data-ttu-id="ae527-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="ae527-101">\<persistenceProvider></span></span>
<span data-ttu-id="ae527-102">Especifica o tipo da implementação do provedor de persistência a ser usado, bem como o tempo limite a ser usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="ae527-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
<span data-ttu-id="ae527-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ae527-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ae527-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ae527-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ae527-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ae527-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ae527-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ae527-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="ae527-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ae527-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="ae527-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> PersistenceProvider**</span><span class="sxs-lookup"><span data-stu-id="ae527-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae527-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae527-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae527-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ae527-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ae527-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ae527-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae527-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ae527-112">Attributes</span></span>  
  
|<span data-ttu-id="ae527-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ae527-113">Attribute</span></span>|<span data-ttu-id="ae527-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae527-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae527-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="ae527-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="ae527-116">Um <xref:System.TimeSpan> valor que especifica o tempo limite usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="ae527-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="ae527-117">O padrão é "00:00:30".</span><span class="sxs-lookup"><span data-stu-id="ae527-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="ae527-118">tipo</span><span class="sxs-lookup"><span data-stu-id="ae527-118">type</span></span>|<span data-ttu-id="ae527-119">Uma cadeia de caracteres que especifica o tipo do alocador de provedor de persistência a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ae527-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae527-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ae527-120">Child Elements</span></span>  
 <span data-ttu-id="ae527-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ae527-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae527-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ae527-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ae527-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae527-123">Element</span></span>|<span data-ttu-id="ae527-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae527-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae527-125">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="ae527-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ae527-126">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="ae527-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae527-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae527-127">Remarks</span></span>  
 <span data-ttu-id="ae527-128">Esse elemento Especifica o provedor de persistência a ser usado para serializar o estado de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="ae527-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="ae527-129">Ele deve ser usado junto com o `wsHttpContextBinding` que passa informações de estado em cabeçalhos HTTP.</span><span class="sxs-lookup"><span data-stu-id="ae527-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae527-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae527-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
