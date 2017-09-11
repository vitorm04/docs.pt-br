---
title: "Modificando elementos, atributos e nós em um Tree1 XML | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 88531f2af88074f4406c4859354860829efda69f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="47ff0-102">Modificando elementos, atributos e nós em uma árvore XML</span><span class="sxs-lookup"><span data-stu-id="47ff0-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="47ff0-103">A tabela a seguir resume os métodos e as propriedades que você pode usar para modificar um elemento, seus elementos filho ou seus atributos.</span><span class="sxs-lookup"><span data-stu-id="47ff0-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="47ff0-104">Os seguintes métodos modificam <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="47ff0-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="47ff0-105">Método</span><span class="sxs-lookup"><span data-stu-id="47ff0-105">Method</span></span>|<span data-ttu-id="47ff0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="47ff0-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="47ff0-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-108">Substitui um elemento pelo XML analisado.</span><span class="sxs-lookup"><span data-stu-id="47ff0-108">Replaces an element with parsed XML.</span></span>|  
|<span data-ttu-id="47ff0-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-110">Remove todo o conteúdo (nós filho e atributos) de um elemento.</span><span class="sxs-lookup"><span data-stu-id="47ff0-110">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="47ff0-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-112">Remove os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="47ff0-112">Removes the attributes of an element.</span></span>|  
|<span data-ttu-id="47ff0-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-114">Substitui todo o conteúdo (nós filho e atributos) de um elemento.</span><span class="sxs-lookup"><span data-stu-id="47ff0-114">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="47ff0-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-116">Substitui os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="47ff0-116">Replaces the attributes of an element.</span></span>|  
|<span data-ttu-id="47ff0-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-118">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="47ff0-118">Sets the value of an attribute.</span></span> <span data-ttu-id="47ff0-119">Cria o atributo se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="47ff0-119">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="47ff0-120">Se o valor for definido como `null`, o método removerá o atributo.</span><span class="sxs-lookup"><span data-stu-id="47ff0-120">If the value is set to `null`, removes the attribute.</span></span>|  
|<span data-ttu-id="47ff0-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-122">Define o valor de um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="47ff0-122">Sets the value of a child element.</span></span> <span data-ttu-id="47ff0-123">Cria o elemento se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="47ff0-123">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="47ff0-124">Se o valor for definido como `null`, o método removerá o elemento.</span><span class="sxs-lookup"><span data-stu-id="47ff0-124">If the value is set to `null`, removes the element.</span></span>|  
|<span data-ttu-id="47ff0-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-126">Substitui o conteúdo (nós filho) de um elemento pelo texto especificado.</span><span class="sxs-lookup"><span data-stu-id="47ff0-126">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<span data-ttu-id="47ff0-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-128">Define o valor de um elemento.</span><span class="sxs-lookup"><span data-stu-id="47ff0-128">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="47ff0-129">Os seguintes métodos modificam <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="47ff0-129">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="47ff0-130">Método</span><span class="sxs-lookup"><span data-stu-id="47ff0-130">Method</span></span>|<span data-ttu-id="47ff0-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="47ff0-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="47ff0-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-133">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="47ff0-133">Sets the value of an attribute.</span></span>|  
|<span data-ttu-id="47ff0-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-135">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="47ff0-135">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="47ff0-136">Os seguintes métodos modificam uma <xref:System.Xml.Linq.XNode>(incluindo um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>).</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="47ff0-136">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="47ff0-137">Método</span><span class="sxs-lookup"><span data-stu-id="47ff0-137">Method</span></span>|<span data-ttu-id="47ff0-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="47ff0-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="47ff0-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-140">Substitui um nó pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="47ff0-140">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="47ff0-141">Os seguintes métodos modificam uma <xref:System.Xml.Linq.XContainer>(um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>).</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="47ff0-141">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="47ff0-142">Método</span><span class="sxs-lookup"><span data-stu-id="47ff0-142">Method</span></span>|<span data-ttu-id="47ff0-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="47ff0-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="47ff0-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="47ff0-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="47ff0-145">Substitui os nós filho pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="47ff0-145">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47ff0-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47ff0-146">See Also</span></span>  
 [<span data-ttu-id="47ff0-147">Modificando árvores XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47ff0-147">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
