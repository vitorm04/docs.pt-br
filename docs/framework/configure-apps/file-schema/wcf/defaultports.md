---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398066"
---
# <a name="defaultports"></a><span data-ttu-id="2001f-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="2001f-101">\<defaultPorts></span></span>
<span data-ttu-id="2001f-102">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="2001f-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="2001f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2001f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2001f-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2001f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2001f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2001f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="2001f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2001f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="2001f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2001f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="2001f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> useRequestHeadersForMetadataAddress**](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="2001f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="2001f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de DefaultPorts**</span><span class="sxs-lookup"><span data-stu-id="2001f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2001f-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2001f-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2001f-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2001f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2001f-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2001f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2001f-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="2001f-113">Attributes</span></span>  
 <span data-ttu-id="2001f-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2001f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2001f-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2001f-115">Child Elements</span></span>  
  
|<span data-ttu-id="2001f-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="2001f-116">Element</span></span>|<span data-ttu-id="2001f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2001f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2001f-118">\<Adicionar > de \<DefaultPorts ></span><span class="sxs-lookup"><span data-stu-id="2001f-118">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="2001f-119">Um ponto de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="2001f-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2001f-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2001f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2001f-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="2001f-121">Element</span></span>|<span data-ttu-id="2001f-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2001f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2001f-123">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="2001f-123">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="2001f-124">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="2001f-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2001f-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2001f-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
