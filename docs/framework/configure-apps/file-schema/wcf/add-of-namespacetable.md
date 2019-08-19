---
title: <add> de <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 32eff2e7bfdf1aee4c7d37a0e06166afba3cb398
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566739"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="253da-102">\<Adicionar > de \<NamespaceTable ></span><span class="sxs-lookup"><span data-stu-id="253da-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="253da-103">Representa um elemento de configuração que contém um namespace para mapeamento de prefixo que pode ser usado em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="253da-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="253da-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="253da-104">\<system.serviceModel></span></span>  
<span data-ttu-id="253da-105">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="253da-105">\<routing></span></span>  
<span data-ttu-id="253da-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="253da-106">\<namespaceTable></span></span>  
<span data-ttu-id="253da-107">\<add></span><span class="sxs-lookup"><span data-stu-id="253da-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="253da-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="253da-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="253da-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="253da-109">Attributes and Elements</span></span>  
 <span data-ttu-id="253da-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="253da-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="253da-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="253da-111">Attributes</span></span>  
  
|<span data-ttu-id="253da-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="253da-112">Attribute</span></span>|<span data-ttu-id="253da-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="253da-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="253da-114">namespace</span><span class="sxs-lookup"><span data-stu-id="253da-114">namespace</span></span>|<span data-ttu-id="253da-115">Uma cadeia de caracteres que contém o namespace.</span><span class="sxs-lookup"><span data-stu-id="253da-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="253da-116">prefix</span><span class="sxs-lookup"><span data-stu-id="253da-116">prefix</span></span>|<span data-ttu-id="253da-117">Uma cadeia de caracteres que contém o prefixo para este namespace.</span><span class="sxs-lookup"><span data-stu-id="253da-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="253da-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="253da-118">Child Elements</span></span>  
 <span data-ttu-id="253da-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="253da-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="253da-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="253da-120">Parent Elements</span></span>  
  
|<span data-ttu-id="253da-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="253da-121">Element</span></span>|<span data-ttu-id="253da-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="253da-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="253da-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="253da-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="253da-124">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usados em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="253da-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="253da-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="253da-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
