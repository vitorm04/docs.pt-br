---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854971"
---
# <a name="timeouts"></a><span data-ttu-id="355dd-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="355dd-101">\<timeOuts></span></span>
<span data-ttu-id="355dd-102">Representa um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="355dd-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
<span data-ttu-id="355dd-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="355dd-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="355dd-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="355dd-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="355dd-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Serviços >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="355dd-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="355dd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de serviço**](service.md)</span><span class="sxs-lookup"><span data-stu-id="355dd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="355dd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do host**](host.md)</span><span class="sxs-lookup"><span data-stu-id="355dd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="355dd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Tempos limite >**</span><span class="sxs-lookup"><span data-stu-id="355dd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="355dd-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="355dd-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="355dd-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="355dd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="355dd-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="355dd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="355dd-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="355dd-112">Attributes</span></span>  
  
|<span data-ttu-id="355dd-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="355dd-113">Attribute</span></span>|<span data-ttu-id="355dd-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="355dd-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="355dd-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço fechar.</span><span class="sxs-lookup"><span data-stu-id="355dd-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="355dd-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço abrir.</span><span class="sxs-lookup"><span data-stu-id="355dd-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="355dd-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="355dd-117">Child Elements</span></span>  
 <span data-ttu-id="355dd-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="355dd-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="355dd-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="355dd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="355dd-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="355dd-120">Element</span></span>|<span data-ttu-id="355dd-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="355dd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="355dd-122">\<host></span><span class="sxs-lookup"><span data-stu-id="355dd-122">\<host></span></span>](host.md)|<span data-ttu-id="355dd-123">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="355dd-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="355dd-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="355dd-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="355dd-125">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="355dd-125">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
