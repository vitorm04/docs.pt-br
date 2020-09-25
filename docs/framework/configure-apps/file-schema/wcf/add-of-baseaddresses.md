---
title: <add> de <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: cd0ef5cc5f0f809bdafa23bd312e7e30fcdccc21
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181603"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="cf249-102">\<add> de \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="cf249-102">\<add> of \<baseAddresses></span></span>

<span data-ttu-id="cf249-103">Representa um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="cf249-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="cf249-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf249-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="cf249-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="cf249-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf249-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cf249-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cf249-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cf249-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf249-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="cf249-108">Attributes</span></span>  
  
|<span data-ttu-id="cf249-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="cf249-109">Attribute</span></span>|<span data-ttu-id="cf249-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf249-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="cf249-111">Uma cadeia de caracteres que especifica um endereço base usado pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="cf249-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf249-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cf249-112">Child Elements</span></span>  

 <span data-ttu-id="cf249-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cf249-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf249-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cf249-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cf249-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf249-115">Element</span></span>|<span data-ttu-id="cf249-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf249-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="cf249-117">Uma coleção de elementos `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="cf249-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf249-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="cf249-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="cf249-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="cf249-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
