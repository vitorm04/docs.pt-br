---
title: <add> de <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850589"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="4b109-102">\<add> de \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="4b109-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="4b109-103">Representa um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="4b109-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="4b109-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b109-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="4b109-105">Type</span><span class="sxs-lookup"><span data-stu-id="4b109-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b109-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4b109-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4b109-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4b109-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b109-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="4b109-108">Attributes</span></span>  
  
|<span data-ttu-id="4b109-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="4b109-109">Attribute</span></span>|<span data-ttu-id="4b109-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b109-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="4b109-111">Uma cadeia de caracteres que especifica um endereço base usado pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="4b109-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b109-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4b109-112">Child Elements</span></span>  
 <span data-ttu-id="4b109-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4b109-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b109-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4b109-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4b109-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="4b109-115">Element</span></span>|<span data-ttu-id="4b109-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b109-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="4b109-117">Uma coleção de elementos `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="4b109-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b109-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="4b109-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="4b109-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="4b109-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
