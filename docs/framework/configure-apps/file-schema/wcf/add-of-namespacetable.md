---
title: '&lt;adicionar&gt; &lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 5ae672f12a2ef58efc9738624c113855e59e02b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="03b74-102">&lt;adicionar&gt; &lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="03b74-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="03b74-103">Representa um elemento de configuração que contém o namespace para mapeamento de prefixo que pode ser usado em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="03b74-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="03b74-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="03b74-104">\<system.serviceModel></span></span>  
<span data-ttu-id="03b74-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="03b74-105">\<routing></span></span>  
<span data-ttu-id="03b74-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="03b74-106">\<namespaceTable></span></span>  
<span data-ttu-id="03b74-107">\<add></span><span class="sxs-lookup"><span data-stu-id="03b74-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03b74-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03b74-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03b74-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="03b74-109">Attributes and Elements</span></span>  
 <span data-ttu-id="03b74-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="03b74-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03b74-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="03b74-111">Attributes</span></span>  
  
|<span data-ttu-id="03b74-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="03b74-112">Attribute</span></span>|<span data-ttu-id="03b74-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="03b74-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03b74-114">namespace</span><span class="sxs-lookup"><span data-stu-id="03b74-114">namespace</span></span>|<span data-ttu-id="03b74-115">Uma cadeia de caracteres que contém o namespace.</span><span class="sxs-lookup"><span data-stu-id="03b74-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="03b74-116">Prefixo</span><span class="sxs-lookup"><span data-stu-id="03b74-116">prefix</span></span>|<span data-ttu-id="03b74-117">Uma cadeia de caracteres que contém o prefixo para esse namespace.</span><span class="sxs-lookup"><span data-stu-id="03b74-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03b74-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="03b74-118">Child Elements</span></span>  
 <span data-ttu-id="03b74-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="03b74-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03b74-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="03b74-120">Parent Elements</span></span>  
  
|<span data-ttu-id="03b74-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="03b74-121">Element</span></span>|<span data-ttu-id="03b74-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="03b74-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03b74-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="03b74-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="03b74-124">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usadas em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="03b74-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03b74-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03b74-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
