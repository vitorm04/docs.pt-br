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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd487238ebe327a5f89b737fdf764d94f955a411
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="137e6-102">&lt;adicionar&gt; &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="137e6-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="137e6-103">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="137e6-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="137e6-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="137e6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="137e6-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="137e6-105">\<behaviors></span></span>  
<span data-ttu-id="137e6-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="137e6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="137e6-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="137e6-107">\<behavior></span></span>  
<span data-ttu-id="137e6-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="137e6-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="137e6-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="137e6-109">\<defaultPorts></span></span>  
<span data-ttu-id="137e6-110">\<add></span><span class="sxs-lookup"><span data-stu-id="137e6-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137e6-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="137e6-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="137e6-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="137e6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="137e6-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="137e6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="137e6-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="137e6-114">Attributes</span></span>  
  
|<span data-ttu-id="137e6-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="137e6-115">Attribute</span></span>|<span data-ttu-id="137e6-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="137e6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="137e6-117">porta</span><span class="sxs-lookup"><span data-stu-id="137e6-117">port</span></span>|<span data-ttu-id="137e6-118">Um inteiro que especifica o número de porta de comunicação padrão</span><span class="sxs-lookup"><span data-stu-id="137e6-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="137e6-119">esquema</span><span class="sxs-lookup"><span data-stu-id="137e6-119">scheme</span></span>|<span data-ttu-id="137e6-120">Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associados a uma porta de comunicação.</span><span class="sxs-lookup"><span data-stu-id="137e6-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="137e6-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="137e6-121">Child Elements</span></span>  
 <span data-ttu-id="137e6-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="137e6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="137e6-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="137e6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="137e6-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="137e6-124">Element</span></span>|<span data-ttu-id="137e6-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="137e6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="137e6-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="137e6-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="137e6-127">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="137e6-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="137e6-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="137e6-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
