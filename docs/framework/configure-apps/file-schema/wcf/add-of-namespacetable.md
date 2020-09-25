---
title: <add> de <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7d055d4933f1ad625d6842f91a140f668c05c64e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204990"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="ed012-102">\<add> de \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="ed012-102">\<add> of \<namespaceTable></span></span>

<span data-ttu-id="ed012-103">Representa um elemento de configuração que contém um namespace para mapeamento de prefixo que pode ser usado em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="ed012-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ed012-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed012-104">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed012-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ed012-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ed012-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ed012-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed012-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ed012-107">Attributes</span></span>  
  
|<span data-ttu-id="ed012-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ed012-108">Attribute</span></span>|<span data-ttu-id="ed012-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed012-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed012-110">namespace</span><span class="sxs-lookup"><span data-stu-id="ed012-110">namespace</span></span>|<span data-ttu-id="ed012-111">Uma cadeia de caracteres que contém o namespace.</span><span class="sxs-lookup"><span data-stu-id="ed012-111">A string containing the namespace.</span></span>|  
|<span data-ttu-id="ed012-112">prefixo</span><span class="sxs-lookup"><span data-stu-id="ed012-112">prefix</span></span>|<span data-ttu-id="ed012-113">Uma cadeia de caracteres que contém o prefixo para este namespace.</span><span class="sxs-lookup"><span data-stu-id="ed012-113">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed012-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ed012-114">Child Elements</span></span>  

 <span data-ttu-id="ed012-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ed012-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed012-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ed012-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ed012-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed012-117">Element</span></span>|<span data-ttu-id="ed012-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed012-118">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="ed012-119">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usados em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="ed012-119">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed012-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="ed012-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
