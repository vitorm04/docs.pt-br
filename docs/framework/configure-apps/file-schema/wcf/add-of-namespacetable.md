---
title: <add> De <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e65b66170465a8b3bb60754feebb7730b959d9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089712"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="f563d-102">\<Adicionar > de \<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="f563d-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="f563d-103">Representa um elemento de configuração que contém um namespace para o prefixo de mapeamento que pode ser usado em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="f563d-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="f563d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f563d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f563d-105">\<routing></span><span class="sxs-lookup"><span data-stu-id="f563d-105">\<routing></span></span>  
<span data-ttu-id="f563d-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="f563d-106">\<namespaceTable></span></span>  
<span data-ttu-id="f563d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f563d-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f563d-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f563d-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f563d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f563d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f563d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f563d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f563d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f563d-111">Attributes</span></span>  
  
|<span data-ttu-id="f563d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f563d-112">Attribute</span></span>|<span data-ttu-id="f563d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f563d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f563d-114">namespace</span><span class="sxs-lookup"><span data-stu-id="f563d-114">namespace</span></span>|<span data-ttu-id="f563d-115">Uma cadeia de caracteres que contém o namespace.</span><span class="sxs-lookup"><span data-stu-id="f563d-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="f563d-116">prefix</span><span class="sxs-lookup"><span data-stu-id="f563d-116">prefix</span></span>|<span data-ttu-id="f563d-117">Uma cadeia de caracteres que contém o prefixo para este namespace.</span><span class="sxs-lookup"><span data-stu-id="f563d-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f563d-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f563d-118">Child Elements</span></span>  
 <span data-ttu-id="f563d-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f563d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f563d-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f563d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f563d-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f563d-121">Element</span></span>|<span data-ttu-id="f563d-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f563d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f563d-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="f563d-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="f563d-124">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que pode ser usado em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="f563d-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f563d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f563d-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
