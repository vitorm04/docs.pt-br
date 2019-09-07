---
title: <add> de <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400650"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="41840-102">\<Adicionar > de \<DefaultPorts ></span><span class="sxs-lookup"><span data-stu-id="41840-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="41840-103">Um ponto de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="41840-103">A default communications endpoint that the client application listens to.</span></span>  
  
<span data-ttu-id="41840-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="41840-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="41840-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="41840-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="41840-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="41840-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="41840-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="41840-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="41840-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="41840-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="41840-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> useRequestHeadersForMetadataAddress**](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="41840-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="41840-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de DefaultPorts**](defaultports.md)</span><span class="sxs-lookup"><span data-stu-id="41840-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)</span></span>\
<span data-ttu-id="41840-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="41840-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41840-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41840-112">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41840-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="41840-113">Attributes and Elements</span></span>  
 <span data-ttu-id="41840-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="41840-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41840-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="41840-115">Attributes</span></span>  
  
|<span data-ttu-id="41840-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="41840-116">Attribute</span></span>|<span data-ttu-id="41840-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="41840-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41840-118">porta</span><span class="sxs-lookup"><span data-stu-id="41840-118">port</span></span>|<span data-ttu-id="41840-119">Um inteiro que especifica o número da porta de comunicação padrão</span><span class="sxs-lookup"><span data-stu-id="41840-119">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="41840-120">esquema</span><span class="sxs-lookup"><span data-stu-id="41840-120">scheme</span></span>|<span data-ttu-id="41840-121">Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associado a uma porta de comunicação.</span><span class="sxs-lookup"><span data-stu-id="41840-121">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41840-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="41840-122">Child Elements</span></span>  
 <span data-ttu-id="41840-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="41840-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41840-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="41840-124">Parent Elements</span></span>  
  
|<span data-ttu-id="41840-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="41840-125">Element</span></span>|<span data-ttu-id="41840-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="41840-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41840-127">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="41840-127">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="41840-128">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="41840-128">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41840-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41840-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
