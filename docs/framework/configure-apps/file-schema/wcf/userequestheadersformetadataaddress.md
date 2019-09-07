---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399198"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="545af-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="545af-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="545af-102">Habilita a recuperação de informações de endereço de metadados dos cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="545af-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="545af-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="545af-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="545af-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="545af-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="545af-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="545af-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="545af-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="545af-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="545af-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="545af-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="545af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> useRequestHeadersForMetadataAddress**</span><span class="sxs-lookup"><span data-stu-id="545af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="545af-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="545af-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="545af-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="545af-110">Attributes and Elements</span></span>  
 <span data-ttu-id="545af-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="545af-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="545af-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="545af-112">Attributes</span></span>  
 <span data-ttu-id="545af-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="545af-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="545af-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="545af-114">Child Elements</span></span>  
  
|<span data-ttu-id="545af-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="545af-115">Element</span></span>|<span data-ttu-id="545af-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="545af-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="545af-117">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="545af-117">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="545af-118">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="545af-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="545af-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="545af-119">Parent Elements</span></span>  
  
|<span data-ttu-id="545af-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="545af-120">Element</span></span>|<span data-ttu-id="545af-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="545af-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="545af-122">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="545af-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="545af-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="545af-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="545af-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="545af-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
