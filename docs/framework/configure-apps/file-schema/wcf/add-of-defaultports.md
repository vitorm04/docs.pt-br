---
title: <add> de <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: d2723dad14a63c4b05fdb70157f7eb21d193d3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926702"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="5879b-102">\<Adicionar > de \<DefaultPorts ></span><span class="sxs-lookup"><span data-stu-id="5879b-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="5879b-103">Um ponto de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="5879b-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="5879b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5879b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5879b-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5879b-105">\<behaviors></span></span>  
<span data-ttu-id="5879b-106">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="5879b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5879b-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="5879b-107">\<behavior></span></span>  
<span data-ttu-id="5879b-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="5879b-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="5879b-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5879b-109">\<defaultPorts></span></span>  
<span data-ttu-id="5879b-110">\<add></span><span class="sxs-lookup"><span data-stu-id="5879b-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5879b-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5879b-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5879b-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5879b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5879b-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5879b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5879b-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="5879b-114">Attributes</span></span>  
  
|<span data-ttu-id="5879b-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="5879b-115">Attribute</span></span>|<span data-ttu-id="5879b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="5879b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5879b-117">porta</span><span class="sxs-lookup"><span data-stu-id="5879b-117">port</span></span>|<span data-ttu-id="5879b-118">Um inteiro que especifica o número da porta de comunicação padrão</span><span class="sxs-lookup"><span data-stu-id="5879b-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="5879b-119">esquema</span><span class="sxs-lookup"><span data-stu-id="5879b-119">scheme</span></span>|<span data-ttu-id="5879b-120">Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associado a uma porta de comunicação.</span><span class="sxs-lookup"><span data-stu-id="5879b-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5879b-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5879b-121">Child Elements</span></span>  
 <span data-ttu-id="5879b-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5879b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5879b-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5879b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5879b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="5879b-124">Element</span></span>|<span data-ttu-id="5879b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5879b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5879b-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5879b-126">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="5879b-127">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="5879b-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5879b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5879b-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
