---
title: <add> de <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e2a2e26099f2d31116e4a89297fc1ac984c480d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920075"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="afae7-102">\<Adicionar > de \<NamespaceTable ></span><span class="sxs-lookup"><span data-stu-id="afae7-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="afae7-103">Representa um elemento de configuração que contém um namespace para mapeamento de prefixo que pode ser usado em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="afae7-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="afae7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="afae7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="afae7-105">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="afae7-105">\<routing></span></span>  
<span data-ttu-id="afae7-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="afae7-106">\<namespaceTable></span></span>  
<span data-ttu-id="afae7-107">\<add></span><span class="sxs-lookup"><span data-stu-id="afae7-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afae7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="afae7-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afae7-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="afae7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="afae7-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="afae7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afae7-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="afae7-111">Attributes</span></span>  
  
|<span data-ttu-id="afae7-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="afae7-112">Attribute</span></span>|<span data-ttu-id="afae7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="afae7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afae7-114">namespace</span><span class="sxs-lookup"><span data-stu-id="afae7-114">namespace</span></span>|<span data-ttu-id="afae7-115">Uma cadeia de caracteres que contém o namespace.</span><span class="sxs-lookup"><span data-stu-id="afae7-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="afae7-116">prefix</span><span class="sxs-lookup"><span data-stu-id="afae7-116">prefix</span></span>|<span data-ttu-id="afae7-117">Uma cadeia de caracteres que contém o prefixo para este namespace.</span><span class="sxs-lookup"><span data-stu-id="afae7-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afae7-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="afae7-118">Child Elements</span></span>  
 <span data-ttu-id="afae7-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="afae7-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afae7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="afae7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="afae7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="afae7-121">Element</span></span>|<span data-ttu-id="afae7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="afae7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afae7-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="afae7-123">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="afae7-124">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usados em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="afae7-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afae7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afae7-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
