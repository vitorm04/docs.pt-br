---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738770"
---
# \<privacyNoticeAt>
<span data-ttu-id="81603-101">Representa um elemento de configuração que especifica um aviso de privacidade usado na associação `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="81603-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="81603-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81603-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="81603-103">Type</span><span class="sxs-lookup"><span data-stu-id="81603-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81603-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="81603-104">Attributes and Elements</span></span>  
 <span data-ttu-id="81603-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="81603-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81603-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="81603-106">Attributes</span></span>  
  
|<span data-ttu-id="81603-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="81603-107">Attribute</span></span>|<span data-ttu-id="81603-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="81603-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="81603-109">Uma cadeia de caracteres que especifica o URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="81603-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="81603-110">Um inteiro que especifica a versão deste aviso de privacidade.</span><span class="sxs-lookup"><span data-stu-id="81603-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81603-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="81603-111">Child Elements</span></span>  
 <span data-ttu-id="81603-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="81603-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81603-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="81603-113">Parent Elements</span></span>  
  
|<span data-ttu-id="81603-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="81603-114">Element</span></span>|<span data-ttu-id="81603-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="81603-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="81603-116">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="81603-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81603-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="81603-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="81603-118">Associações</span><span class="sxs-lookup"><span data-stu-id="81603-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="81603-119">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="81603-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="81603-120">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="81603-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
