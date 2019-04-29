---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 969461d0e5bdc9f8c49b7a019a6000af5af77eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788720"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="54315-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="54315-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="54315-102">Habilita a recuperação de informações de endereço de metadados dos cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="54315-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="54315-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="54315-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="54315-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="54315-104">\<behaviors></span></span>  
<span data-ttu-id="54315-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="54315-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="54315-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="54315-106">\<behavior></span></span>  
<span data-ttu-id="54315-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="54315-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54315-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54315-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54315-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54315-109">Attributes and Elements</span></span>  
 <span data-ttu-id="54315-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54315-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54315-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="54315-111">Attributes</span></span>  
 <span data-ttu-id="54315-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="54315-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54315-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54315-113">Child Elements</span></span>  
  
|<span data-ttu-id="54315-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="54315-114">Element</span></span>|<span data-ttu-id="54315-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="54315-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54315-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="54315-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="54315-117">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="54315-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54315-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54315-118">Parent Elements</span></span>  
  
|<span data-ttu-id="54315-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="54315-119">Element</span></span>|<span data-ttu-id="54315-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="54315-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54315-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="54315-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="54315-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="54315-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54315-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54315-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
