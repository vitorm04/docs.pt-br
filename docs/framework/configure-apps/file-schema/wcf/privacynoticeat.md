---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738770"
---
# <a name="privacynoticeat"></a><span data-ttu-id="51f1c-101">\<privacyNoticeAt ></span><span class="sxs-lookup"><span data-stu-id="51f1c-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="51f1c-102">Representa um elemento de configuração que especifica um aviso de privacidade usado na associação `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="51f1c-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
<span data-ttu-id="51f1c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="51f1c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="51f1c-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="51f1c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="51f1c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="51f1c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="51f1c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="51f1c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="51f1c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="51f1c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="51f1c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<privacyNotice >**</span><span class="sxs-lookup"><span data-stu-id="51f1c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51f1c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51f1c-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="51f1c-110">Digite</span><span class="sxs-lookup"><span data-stu-id="51f1c-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51f1c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="51f1c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="51f1c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="51f1c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51f1c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="51f1c-113">Attributes</span></span>  
  
|<span data-ttu-id="51f1c-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="51f1c-114">Attribute</span></span>|<span data-ttu-id="51f1c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="51f1c-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="51f1c-116">Uma cadeia de caracteres que especifica o URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="51f1c-117">Um inteiro que especifica a versão deste aviso de privacidade.</span><span class="sxs-lookup"><span data-stu-id="51f1c-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51f1c-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="51f1c-118">Child Elements</span></span>  
 <span data-ttu-id="51f1c-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="51f1c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51f1c-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="51f1c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="51f1c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="51f1c-121">Element</span></span>|<span data-ttu-id="51f1c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="51f1c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51f1c-123">\<binding ></span><span class="sxs-lookup"><span data-stu-id="51f1c-123">\<binding></span></span>](bindings.md)|<span data-ttu-id="51f1c-124">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="51f1c-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51f1c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51f1c-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="51f1c-126">Associações</span><span class="sxs-lookup"><span data-stu-id="51f1c-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="51f1c-127">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="51f1c-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="51f1c-128">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="51f1c-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="51f1c-129">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="51f1c-129">\<customBinding></span></span>](custombinding.md)
