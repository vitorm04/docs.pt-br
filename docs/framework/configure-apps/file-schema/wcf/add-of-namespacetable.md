---
title: <add> De <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 0e463ffa87e67bc5f100f9acf38ace6450b0ce40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268698"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="842d1-102">\<Adicionar > de \<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="842d1-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="842d1-103">Representa um elemento de configuração que contém um namespace para o prefixo de mapeamento que pode ser usado em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="842d1-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="842d1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="842d1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="842d1-105">\<routing></span><span class="sxs-lookup"><span data-stu-id="842d1-105">\<routing></span></span>  
<span data-ttu-id="842d1-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="842d1-106">\<namespaceTable></span></span>  
<span data-ttu-id="842d1-107">\<add></span><span class="sxs-lookup"><span data-stu-id="842d1-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="842d1-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="842d1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="842d1-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="842d1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="842d1-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="842d1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="842d1-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="842d1-111">Attributes</span></span>  
  
|<span data-ttu-id="842d1-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="842d1-112">Attribute</span></span>|<span data-ttu-id="842d1-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="842d1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="842d1-114">namespace</span><span class="sxs-lookup"><span data-stu-id="842d1-114">namespace</span></span>|<span data-ttu-id="842d1-115">Uma cadeia de caracteres que contém o namespace.</span><span class="sxs-lookup"><span data-stu-id="842d1-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="842d1-116">prefix</span><span class="sxs-lookup"><span data-stu-id="842d1-116">prefix</span></span>|<span data-ttu-id="842d1-117">Uma cadeia de caracteres que contém o prefixo para este namespace.</span><span class="sxs-lookup"><span data-stu-id="842d1-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="842d1-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="842d1-118">Child Elements</span></span>  
 <span data-ttu-id="842d1-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="842d1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="842d1-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="842d1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="842d1-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="842d1-121">Element</span></span>|<span data-ttu-id="842d1-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="842d1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="842d1-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="842d1-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="842d1-124">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que pode ser usado em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="842d1-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="842d1-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="842d1-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
