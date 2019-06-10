---
title: Modificação de elementos, atributos e nós em uma árvore XML3
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484239"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="f31ae-102">Modificando elementos, atributos e nós em uma árvore XML</span><span class="sxs-lookup"><span data-stu-id="f31ae-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="f31ae-103">A tabela a seguir resume os métodos e as propriedades que você pode usar para modificar um elemento, seus elementos filho ou seus atributos.</span><span class="sxs-lookup"><span data-stu-id="f31ae-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="f31ae-104">Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f31ae-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="f31ae-105">Método</span><span class="sxs-lookup"><span data-stu-id="f31ae-105">Method</span></span>|<span data-ttu-id="f31ae-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f31ae-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-107">Substitui um elemento pelo XML analisado.</span><span class="sxs-lookup"><span data-stu-id="f31ae-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-108">Remove todo o conteúdo (nós filho e atributos) de um elemento.</span><span class="sxs-lookup"><span data-stu-id="f31ae-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-109">Remove os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="f31ae-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-110">Substitui todo o conteúdo (nós filho e atributos) de um elemento.</span><span class="sxs-lookup"><span data-stu-id="f31ae-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-111">Substitui os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="f31ae-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-112">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="f31ae-112">Sets the value of an attribute.</span></span> <span data-ttu-id="f31ae-113">Cria o atributo se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="f31ae-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="f31ae-114">Se o valor for definido como `null`, o método removerá o atributo.</span><span class="sxs-lookup"><span data-stu-id="f31ae-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-115">Define o valor de um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="f31ae-115">Sets the value of a child element.</span></span> <span data-ttu-id="f31ae-116">Cria o elemento se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="f31ae-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="f31ae-117">Se o valor for definido como `null`, o método removerá o elemento.</span><span class="sxs-lookup"><span data-stu-id="f31ae-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-118">Substitui o conteúdo (nós filho) de um elemento pelo texto especificado.</span><span class="sxs-lookup"><span data-stu-id="f31ae-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-119">Define o valor de um elemento.</span><span class="sxs-lookup"><span data-stu-id="f31ae-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="f31ae-120">Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f31ae-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="f31ae-121">Método</span><span class="sxs-lookup"><span data-stu-id="f31ae-121">Method</span></span>|<span data-ttu-id="f31ae-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f31ae-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-123">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="f31ae-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-124">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="f31ae-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="f31ae-125">Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XNode> (incluindo <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="f31ae-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="f31ae-126">Método</span><span class="sxs-lookup"><span data-stu-id="f31ae-126">Method</span></span>|<span data-ttu-id="f31ae-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="f31ae-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-128">Substitui um nó pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f31ae-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="f31ae-129">Os métodos a seguir modificam uma classe <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="f31ae-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="f31ae-130">Método</span><span class="sxs-lookup"><span data-stu-id="f31ae-130">Method</span></span>|<span data-ttu-id="f31ae-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="f31ae-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="f31ae-132">Substitui os nós filho pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f31ae-132">Replaces the children nodes with new content.</span></span>|  
