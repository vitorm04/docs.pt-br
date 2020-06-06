---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398066"
---
# \<defaultPorts>
<span data-ttu-id="3cafc-101">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="3cafc-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="3cafc-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3cafc-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cafc-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3cafc-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3cafc-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3cafc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cafc-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="3cafc-105">Attributes</span></span>  
 <span data-ttu-id="3cafc-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3cafc-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3cafc-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3cafc-107">Child Elements</span></span>  
  
|<span data-ttu-id="3cafc-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="3cafc-108">Element</span></span>|<span data-ttu-id="3cafc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cafc-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cafc-110">\<add>desse\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="3cafc-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="3cafc-111">Um ponto de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="3cafc-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3cafc-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3cafc-112">Parent Elements</span></span>  
  
|<span data-ttu-id="3cafc-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="3cafc-113">Element</span></span>|<span data-ttu-id="3cafc-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cafc-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="3cafc-115">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="3cafc-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3cafc-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="3cafc-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
