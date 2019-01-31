---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 842f989ab1f2f0b9e8fe08e8fd729f983e846ffc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261562"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="b102b-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="b102b-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="b102b-102">Habilita a recuperação de informações de endereço de metadados dos cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b102b-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="b102b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b102b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b102b-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b102b-104">\<behaviors></span></span>  
<span data-ttu-id="b102b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b102b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="b102b-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b102b-106">\<behavior></span></span>  
<span data-ttu-id="b102b-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="b102b-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b102b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b102b-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b102b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b102b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b102b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b102b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b102b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b102b-111">Attributes</span></span>  
 <span data-ttu-id="b102b-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b102b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b102b-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b102b-113">Child Elements</span></span>  
  
|<span data-ttu-id="b102b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b102b-114">Element</span></span>|<span data-ttu-id="b102b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b102b-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b102b-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="b102b-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="b102b-117">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="b102b-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b102b-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b102b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b102b-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b102b-119">Element</span></span>|<span data-ttu-id="b102b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b102b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b102b-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b102b-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b102b-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="b102b-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b102b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b102b-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
