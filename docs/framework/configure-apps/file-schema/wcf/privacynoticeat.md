---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 5e772e23b21c566c906be854e33b924698dcf3e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158702"
---
# \<privacyNoticeAt>

<span data-ttu-id="474db-101">Representa um elemento de configuração que especifica um aviso de privacidade usado na associação `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="474db-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="474db-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="474db-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="474db-103">Tipo</span><span class="sxs-lookup"><span data-stu-id="474db-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="474db-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="474db-104">Attributes and Elements</span></span>  

 <span data-ttu-id="474db-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="474db-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="474db-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="474db-106">Attributes</span></span>  
  
|<span data-ttu-id="474db-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="474db-107">Attribute</span></span>|<span data-ttu-id="474db-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="474db-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="474db-109">Uma cadeia de caracteres que especifica o URI no qual o aviso de privacidade está localizado.</span><span class="sxs-lookup"><span data-stu-id="474db-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="474db-110">Um inteiro que especifica a versão deste aviso de privacidade.</span><span class="sxs-lookup"><span data-stu-id="474db-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="474db-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="474db-111">Child Elements</span></span>  

 <span data-ttu-id="474db-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="474db-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="474db-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="474db-113">Parent Elements</span></span>  
  
|<span data-ttu-id="474db-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="474db-114">Element</span></span>|<span data-ttu-id="474db-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="474db-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="474db-116">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="474db-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="474db-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="474db-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="474db-118">Associações</span><span class="sxs-lookup"><span data-stu-id="474db-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="474db-119">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="474db-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="474db-120">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="474db-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
