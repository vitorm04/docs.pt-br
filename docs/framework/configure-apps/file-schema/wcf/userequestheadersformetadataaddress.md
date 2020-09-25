---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: a323e6da0eb173e303d70cc3b7309b898a805573
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172808"
---
# \<useRequestHeadersForMetadataAddress>

<span data-ttu-id="339cd-101">Habilita a recuperação de informações de endereço de metadados dos cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="339cd-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="339cd-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="339cd-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="339cd-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="339cd-103">Attributes and Elements</span></span>  

 <span data-ttu-id="339cd-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="339cd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="339cd-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="339cd-105">Attributes</span></span>  

 <span data-ttu-id="339cd-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="339cd-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="339cd-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="339cd-107">Child Elements</span></span>  
  
|<span data-ttu-id="339cd-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="339cd-108">Element</span></span>|<span data-ttu-id="339cd-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="339cd-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="339cd-110">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="339cd-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="339cd-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="339cd-111">Parent Elements</span></span>  
  
|<span data-ttu-id="339cd-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="339cd-112">Element</span></span>|<span data-ttu-id="339cd-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="339cd-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="339cd-114">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="339cd-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="339cd-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="339cd-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
