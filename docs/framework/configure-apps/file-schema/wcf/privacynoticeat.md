---
title: '&lt;privacyNoticeAt&gt;'
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2914a3716b9e2adb6ebc47fd73ccee027a3b65da
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="39c84-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="39c84-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="39c84-103">Representa um elemento de configuração que especifica um aviso de privacidade usado na associação `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="39c84-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="39c84-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="39c84-104">\<system.serviceModel></span></span>  
<span data-ttu-id="39c84-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="39c84-105">\<bindings></span></span>  
<span data-ttu-id="39c84-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="39c84-106">\<customBinding></span></span>  
<span data-ttu-id="39c84-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="39c84-107">\<binding></span></span>  
<span data-ttu-id="39c84-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="39c84-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c84-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39c84-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="39c84-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="39c84-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39c84-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39c84-111">Attributes and Elements</span></span>  
 <span data-ttu-id="39c84-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="39c84-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39c84-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="39c84-113">Attributes</span></span>  
  
|<span data-ttu-id="39c84-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="39c84-114">Attribute</span></span>|<span data-ttu-id="39c84-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="39c84-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="39c84-116">Uma cadeia de caracteres que especifica o URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="39c84-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="39c84-117">Um inteiro que especifica a versão deste aviso de privacidade.</span><span class="sxs-lookup"><span data-stu-id="39c84-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39c84-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39c84-118">Child Elements</span></span>  
 <span data-ttu-id="39c84-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="39c84-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39c84-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39c84-120">Parent Elements</span></span>  
  
|<span data-ttu-id="39c84-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="39c84-121">Element</span></span>|<span data-ttu-id="39c84-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="39c84-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39c84-123">\<associação ></span><span class="sxs-lookup"><span data-stu-id="39c84-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="39c84-124">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="39c84-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39c84-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39c84-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="39c84-126">Associações</span><span class="sxs-lookup"><span data-stu-id="39c84-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="39c84-127">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="39c84-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="39c84-128">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="39c84-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="39c84-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="39c84-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
