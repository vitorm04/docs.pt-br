---
title: Modificando elementos, atributos e nós em um Tree1 XML
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 002e87d58ad1a3730889225bf4b3e50448431f2d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360924"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="27087-102">Modificando elementos, atributos e nós em uma árvore XML</span><span class="sxs-lookup"><span data-stu-id="27087-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="27087-103">A tabela a seguir resume os métodos e as propriedades que você pode usar para modificar um elemento, seus elementos filho ou seus atributos.</span><span class="sxs-lookup"><span data-stu-id="27087-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="27087-104">Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="27087-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="27087-105">Método</span><span class="sxs-lookup"><span data-stu-id="27087-105">Method</span></span>|<span data-ttu-id="27087-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="27087-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-107">Substitui um elemento pelo XML analisado.</span><span class="sxs-lookup"><span data-stu-id="27087-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-108">Remove todo o conteúdo (nós filho e atributos) de um elemento.</span><span class="sxs-lookup"><span data-stu-id="27087-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-109">Remove os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="27087-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-110">Substitui todo o conteúdo (nós filho e atributos) de um elemento.</span><span class="sxs-lookup"><span data-stu-id="27087-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-111">Substitui os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="27087-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-112">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="27087-112">Sets the value of an attribute.</span></span> <span data-ttu-id="27087-113">Cria o atributo se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="27087-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="27087-114">Se o valor for definido como `null`, o método removerá o atributo.</span><span class="sxs-lookup"><span data-stu-id="27087-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-115">Define o valor de um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="27087-115">Sets the value of a child element.</span></span> <span data-ttu-id="27087-116">Cria o elemento se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="27087-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="27087-117">Se o valor for definido como `null`, o método removerá o elemento.</span><span class="sxs-lookup"><span data-stu-id="27087-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-118">Substitui o conteúdo (nós filho) de um elemento pelo texto especificado.</span><span class="sxs-lookup"><span data-stu-id="27087-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-119">Define o valor de um elemento.</span><span class="sxs-lookup"><span data-stu-id="27087-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="27087-120">Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="27087-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="27087-121">Método</span><span class="sxs-lookup"><span data-stu-id="27087-121">Method</span></span>|<span data-ttu-id="27087-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="27087-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-123">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="27087-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-124">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="27087-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="27087-125">Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XNode> (incluindo <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="27087-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="27087-126">Método</span><span class="sxs-lookup"><span data-stu-id="27087-126">Method</span></span>|<span data-ttu-id="27087-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="27087-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-128">Substitui um nó pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="27087-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="27087-129">Os métodos a seguir modificam uma classe <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="27087-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="27087-130">Método</span><span class="sxs-lookup"><span data-stu-id="27087-130">Method</span></span>|<span data-ttu-id="27087-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="27087-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="27087-132">Substitui os nós filho pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="27087-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27087-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="27087-133">See also</span></span>

- [<span data-ttu-id="27087-134">Modificando árvores XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27087-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
