---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 08ca8a2bfcf5b905152f7e64a45cbae4992a7b78
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192367"
---
# \<defaultPorts>

<span data-ttu-id="06a41-101">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="06a41-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="06a41-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06a41-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06a41-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="06a41-103">Attributes and Elements</span></span>  

 <span data-ttu-id="06a41-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="06a41-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06a41-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="06a41-105">Attributes</span></span>  

 <span data-ttu-id="06a41-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="06a41-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06a41-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="06a41-107">Child Elements</span></span>  
  
|<span data-ttu-id="06a41-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="06a41-108">Element</span></span>|<span data-ttu-id="06a41-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="06a41-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06a41-110">\<add> desse \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="06a41-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="06a41-111">Um ponto de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="06a41-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06a41-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="06a41-112">Parent Elements</span></span>  
  
|<span data-ttu-id="06a41-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="06a41-113">Element</span></span>|<span data-ttu-id="06a41-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="06a41-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="06a41-115">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="06a41-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06a41-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="06a41-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
