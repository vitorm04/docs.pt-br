---
title: <add> de <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850386"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="9c844-102">\<Adicionar > de \<NamespaceTable ></span><span class="sxs-lookup"><span data-stu-id="9c844-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="9c844-103">Representa um elemento de configuração que contém um namespace para mapeamento de prefixo que pode ser usado em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="9c844-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
<span data-ttu-id="9c844-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c844-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9c844-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9c844-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9c844-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de roteamento**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="9c844-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="9c844-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de NamespaceTable**](namespacetable.md)</span><span class="sxs-lookup"><span data-stu-id="9c844-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)</span></span>\
<span data-ttu-id="9c844-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="9c844-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c844-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c844-109">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c844-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c844-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9c844-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c844-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c844-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c844-112">Attributes</span></span>  
  
|<span data-ttu-id="9c844-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9c844-113">Attribute</span></span>|<span data-ttu-id="9c844-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c844-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c844-115">namespace</span><span class="sxs-lookup"><span data-stu-id="9c844-115">namespace</span></span>|<span data-ttu-id="9c844-116">Uma cadeia de caracteres que contém o namespace.</span><span class="sxs-lookup"><span data-stu-id="9c844-116">A string containing the namespace.</span></span>|  
|<span data-ttu-id="9c844-117">prefix</span><span class="sxs-lookup"><span data-stu-id="9c844-117">prefix</span></span>|<span data-ttu-id="9c844-118">Uma cadeia de caracteres que contém o prefixo para este namespace.</span><span class="sxs-lookup"><span data-stu-id="9c844-118">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c844-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c844-119">Child Elements</span></span>  
 <span data-ttu-id="9c844-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9c844-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c844-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c844-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9c844-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c844-122">Element</span></span>|<span data-ttu-id="9c844-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c844-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c844-124">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="9c844-124">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="9c844-125">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usados em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="9c844-125">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c844-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c844-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
