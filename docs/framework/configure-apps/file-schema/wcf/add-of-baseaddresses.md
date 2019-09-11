---
title: <add> de <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850589"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="c6c07-102">\<Adicionar > de \<baseaddresss ></span><span class="sxs-lookup"><span data-stu-id="c6c07-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="c6c07-103">Representa um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="c6c07-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
<span data-ttu-id="c6c07-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6c07-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c6c07-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c6c07-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c6c07-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Serviços >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="c6c07-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="c6c07-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de serviço**](service.md)</span><span class="sxs-lookup"><span data-stu-id="c6c07-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="c6c07-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do host**](host.md)</span><span class="sxs-lookup"><span data-stu-id="c6c07-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="c6c07-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do baseAddress**](baseaddresses.md)</span><span class="sxs-lookup"><span data-stu-id="c6c07-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)</span></span>\
<span data-ttu-id="c6c07-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="c6c07-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6c07-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6c07-111">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="c6c07-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="c6c07-112">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6c07-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c6c07-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c6c07-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c6c07-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6c07-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6c07-115">Attributes</span></span>  
  
|<span data-ttu-id="c6c07-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="c6c07-116">Attribute</span></span>|<span data-ttu-id="c6c07-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6c07-117">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="c6c07-118">Uma cadeia de caracteres que especifica um endereço base usado pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="c6c07-118">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6c07-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6c07-119">Child Elements</span></span>  
 <span data-ttu-id="c6c07-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c6c07-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6c07-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c6c07-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c6c07-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6c07-122">Element</span></span>|<span data-ttu-id="c6c07-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6c07-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6c07-124">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="c6c07-124">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="c6c07-125">Uma coleção de elementos `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="c6c07-125">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6c07-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6c07-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="c6c07-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c6c07-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
