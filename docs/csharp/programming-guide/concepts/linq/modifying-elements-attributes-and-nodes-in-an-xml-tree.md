---
title: Modificando elementos, atributos e nós em uma árvore XML
description: Saiba mais sobre métodos e propriedades que você pode usar para modificar um elemento, seus nós filho ou seus atributos.
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: bfff882dc57a4f6f4b228563ac923122097d88d0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303160"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="1dcc4-103">Modificando elementos, atributos e nós em uma árvore XML</span><span class="sxs-lookup"><span data-stu-id="1dcc4-103">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="1dcc4-104">A tabela a seguir resume os métodos e as propriedades que você pode usar para modificar um elemento, seus elementos filho ou seus atributos.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-104">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="1dcc4-105">Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-105">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="1dcc4-106">Método</span><span class="sxs-lookup"><span data-stu-id="1dcc4-106">Method</span></span>|<span data-ttu-id="1dcc4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dcc4-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-108">Substitui um elemento pelo XML analisado.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-108">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-109">Remove todo o conteúdo (nós filho e atributos) de um elemento.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-109">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-110">Remove os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-110">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-111">Substitui todo o conteúdo (nós filho e atributos) de um elemento.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-111">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-112">Substitui os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-112">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-113">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-113">Sets the value of an attribute.</span></span> <span data-ttu-id="1dcc4-114">Cria o atributo se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-114">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="1dcc4-115">Se o valor for definido como `null`, o método removerá o atributo.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-115">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-116">Define o valor de um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-116">Sets the value of a child element.</span></span> <span data-ttu-id="1dcc4-117">Cria o elemento se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-117">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="1dcc4-118">Se o valor for definido como `null`, o método removerá o elemento.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-118">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-119">Substitui o conteúdo (nós filho) de um elemento pelo texto especificado.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-119">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-120">Define o valor de um elemento.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-120">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="1dcc4-121">Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-121">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="1dcc4-122">Método</span><span class="sxs-lookup"><span data-stu-id="1dcc4-122">Method</span></span>|<span data-ttu-id="1dcc4-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dcc4-123">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-124">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-124">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-125">Define o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-125">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="1dcc4-126">Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XNode> (incluindo <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="1dcc4-126">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="1dcc4-127">Método</span><span class="sxs-lookup"><span data-stu-id="1dcc4-127">Method</span></span>|<span data-ttu-id="1dcc4-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dcc4-128">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-129">Substitui um nó pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-129">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="1dcc4-130">Os métodos a seguir modificam uma classe <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="1dcc4-130">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="1dcc4-131">Método</span><span class="sxs-lookup"><span data-stu-id="1dcc4-131">Method</span></span>|<span data-ttu-id="1dcc4-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dcc4-132">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="1dcc4-133">Substitui os nós filho pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-133">Replaces the children nodes with new content.</span></span>|  
