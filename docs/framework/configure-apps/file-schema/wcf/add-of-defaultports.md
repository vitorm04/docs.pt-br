---
title: '&lt;adicionar&gt; &lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2aa63c7a5e730b2fb45f614cb2fe5f88444cee4a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="87e98-102">&lt;adicionar&gt; &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="87e98-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="87e98-103">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="87e98-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="87e98-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="87e98-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87e98-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="87e98-105">\<behaviors></span></span>  
<span data-ttu-id="87e98-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="87e98-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="87e98-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="87e98-107">\<behavior></span></span>  
<span data-ttu-id="87e98-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="87e98-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="87e98-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="87e98-109">\<defaultPorts></span></span>  
<span data-ttu-id="87e98-110">\<add></span><span class="sxs-lookup"><span data-stu-id="87e98-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e98-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87e98-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87e98-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="87e98-112">Attributes and Elements</span></span>  
 <span data-ttu-id="87e98-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="87e98-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87e98-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="87e98-114">Attributes</span></span>  
  
|<span data-ttu-id="87e98-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="87e98-115">Attribute</span></span>|<span data-ttu-id="87e98-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="87e98-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87e98-117">porta</span><span class="sxs-lookup"><span data-stu-id="87e98-117">port</span></span>|<span data-ttu-id="87e98-118">Um inteiro que especifica o número de porta de comunicação padrão</span><span class="sxs-lookup"><span data-stu-id="87e98-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="87e98-119">esquema</span><span class="sxs-lookup"><span data-stu-id="87e98-119">scheme</span></span>|<span data-ttu-id="87e98-120">Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associados a uma porta de comunicação.</span><span class="sxs-lookup"><span data-stu-id="87e98-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87e98-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="87e98-121">Child Elements</span></span>  
 <span data-ttu-id="87e98-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="87e98-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87e98-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="87e98-123">Parent Elements</span></span>  
  
|<span data-ttu-id="87e98-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="87e98-124">Element</span></span>|<span data-ttu-id="87e98-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="87e98-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87e98-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="87e98-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="87e98-127">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="87e98-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87e98-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87e98-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
