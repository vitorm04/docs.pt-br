---
title: <add> De <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 5200c8893a89488b72c2c71d1a3703bf2aad1235
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136741"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="826f9-102">\<Adicionar > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="826f9-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="826f9-103">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="826f9-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="826f9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="826f9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="826f9-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="826f9-105">\<behaviors></span></span>  
<span data-ttu-id="826f9-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="826f9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="826f9-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="826f9-107">\<behavior></span></span>  
<span data-ttu-id="826f9-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="826f9-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="826f9-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="826f9-109">\<defaultPorts></span></span>  
<span data-ttu-id="826f9-110">\<add></span><span class="sxs-lookup"><span data-stu-id="826f9-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826f9-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="826f9-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="826f9-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="826f9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="826f9-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="826f9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="826f9-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="826f9-114">Attributes</span></span>  
  
|<span data-ttu-id="826f9-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="826f9-115">Attribute</span></span>|<span data-ttu-id="826f9-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="826f9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="826f9-117">porta</span><span class="sxs-lookup"><span data-stu-id="826f9-117">port</span></span>|<span data-ttu-id="826f9-118">Um inteiro que especifica o número de porta de comunicação padrão</span><span class="sxs-lookup"><span data-stu-id="826f9-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="826f9-119">esquema</span><span class="sxs-lookup"><span data-stu-id="826f9-119">scheme</span></span>|<span data-ttu-id="826f9-120">Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associado a uma porta de comunicação.</span><span class="sxs-lookup"><span data-stu-id="826f9-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="826f9-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="826f9-121">Child Elements</span></span>  
 <span data-ttu-id="826f9-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="826f9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="826f9-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="826f9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="826f9-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="826f9-124">Element</span></span>|<span data-ttu-id="826f9-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="826f9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="826f9-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="826f9-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="826f9-127">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="826f9-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="826f9-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="826f9-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
