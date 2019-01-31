---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: b1de2a304a5dc4295497ea1f3b395240cb5ca9bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254906"
---
# <a name="privacynoticeat"></a><span data-ttu-id="a3dfb-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="a3dfb-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="a3dfb-102">Representa um elemento de configuração que especifica um aviso de privacidade usado na associação `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="a3dfb-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="a3dfb-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a3dfb-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a3dfb-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a3dfb-104">\<bindings></span></span>  
<span data-ttu-id="a3dfb-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a3dfb-105">\<customBinding></span></span>  
<span data-ttu-id="a3dfb-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="a3dfb-106">\<binding></span></span>  
<span data-ttu-id="a3dfb-107">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="a3dfb-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3dfb-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3dfb-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="a3dfb-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="a3dfb-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3dfb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a3dfb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a3dfb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a3dfb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3dfb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a3dfb-112">Attributes</span></span>  
  
|<span data-ttu-id="a3dfb-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a3dfb-113">Attribute</span></span>|<span data-ttu-id="a3dfb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3dfb-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="a3dfb-115">Uma cadeia de caracteres que especifica o URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="a3dfb-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="a3dfb-116">Um inteiro que especifica a versão deste aviso de privacidade.</span><span class="sxs-lookup"><span data-stu-id="a3dfb-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3dfb-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a3dfb-117">Child Elements</span></span>  
 <span data-ttu-id="a3dfb-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a3dfb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3dfb-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a3dfb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a3dfb-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3dfb-120">Element</span></span>|<span data-ttu-id="a3dfb-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3dfb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3dfb-122">\<binding></span><span class="sxs-lookup"><span data-stu-id="a3dfb-122">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a3dfb-123">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="a3dfb-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3dfb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3dfb-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a3dfb-125">Associações</span><span class="sxs-lookup"><span data-stu-id="a3dfb-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a3dfb-126">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="a3dfb-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a3dfb-127">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a3dfb-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a3dfb-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a3dfb-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
