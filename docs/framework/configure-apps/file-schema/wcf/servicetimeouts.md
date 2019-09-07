---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399556"
---
# <a name="servicetimeouts"></a><span data-ttu-id="a3909-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="a3909-101">\<serviceTimeouts></span></span>
<span data-ttu-id="a3909-102">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="a3909-102">Specifies the timeout for a service.</span></span>  
  
<span data-ttu-id="a3909-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a3909-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a3909-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a3909-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a3909-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a3909-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a3909-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a3909-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="a3909-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a3909-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="a3909-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<>s de tempo limite**</span><span class="sxs-lookup"><span data-stu-id="a3909-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3909-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3909-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="a3909-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="a3909-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3909-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a3909-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a3909-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a3909-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3909-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a3909-113">Attributes</span></span>  
  
|<span data-ttu-id="a3909-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a3909-114">Attribute</span></span>|<span data-ttu-id="a3909-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3909-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="a3909-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir do cliente para o servidor.</span><span class="sxs-lookup"><span data-stu-id="a3909-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="a3909-117">O padrão é "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="a3909-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3909-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a3909-118">Child Elements</span></span>  
 <span data-ttu-id="a3909-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a3909-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3909-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a3909-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a3909-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3909-121">Element</span></span>|<span data-ttu-id="a3909-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3909-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3909-123">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="a3909-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a3909-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="a3909-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3909-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3909-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
