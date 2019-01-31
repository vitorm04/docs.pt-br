---
title: <add> De <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 799715ef008274ead6b745e8ab97e769cb59e6b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261588"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="bd3fb-102">\<Adicionar > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="bd3fb-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="bd3fb-103">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="bd3fb-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="bd3fb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bd3fb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd3fb-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="bd3fb-105">\<behaviors></span></span>  
<span data-ttu-id="bd3fb-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bd3fb-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bd3fb-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="bd3fb-107">\<behavior></span></span>  
<span data-ttu-id="bd3fb-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="bd3fb-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="bd3fb-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="bd3fb-109">\<defaultPorts></span></span>  
<span data-ttu-id="bd3fb-110">\<add></span><span class="sxs-lookup"><span data-stu-id="bd3fb-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd3fb-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd3fb-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd3fb-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bd3fb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bd3fb-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bd3fb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd3fb-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="bd3fb-114">Attributes</span></span>  
  
|<span data-ttu-id="bd3fb-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="bd3fb-115">Attribute</span></span>|<span data-ttu-id="bd3fb-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd3fb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd3fb-117">porta</span><span class="sxs-lookup"><span data-stu-id="bd3fb-117">port</span></span>|<span data-ttu-id="bd3fb-118">Um inteiro que especifica o número de porta de comunicação padrão</span><span class="sxs-lookup"><span data-stu-id="bd3fb-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="bd3fb-119">esquema</span><span class="sxs-lookup"><span data-stu-id="bd3fb-119">scheme</span></span>|<span data-ttu-id="bd3fb-120">Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associado a uma porta de comunicação.</span><span class="sxs-lookup"><span data-stu-id="bd3fb-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd3fb-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bd3fb-121">Child Elements</span></span>  
 <span data-ttu-id="bd3fb-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bd3fb-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd3fb-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bd3fb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bd3fb-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="bd3fb-124">Element</span></span>|<span data-ttu-id="bd3fb-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd3fb-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd3fb-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="bd3fb-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="bd3fb-127">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="bd3fb-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd3fb-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd3fb-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElement>
