---
title: Conteúdo válido de objetos XElement e XDocument3
description: Saiba mais sobre os argumentos válidos que podem ser passados para construtores e métodos que você usa para adicionar conteúdo a elementos e documentos.
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: dfafbe76b078db6c22b475770ebadaff38c75ba8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302250"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="0f84b-103">Conteúdo válido de objetos XElement e XDocument</span><span class="sxs-lookup"><span data-stu-id="0f84b-103">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="0f84b-104">Este tópico descreve os argumentos válidos que podem ser passados para os construtores e os métodos que você usa para adicionar conteúdo a elementos e documentos.</span><span class="sxs-lookup"><span data-stu-id="0f84b-104">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="0f84b-105">Conteúdo válido</span><span class="sxs-lookup"><span data-stu-id="0f84b-105">Valid Content</span></span>  
 <span data-ttu-id="0f84b-106">As consultas geralmente avaliam para <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-106">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="0f84b-107">Você pode passar coleções de <xref:System.Xml.Linq.XElement> ou de objetos <xref:System.Xml.Linq.XAttribute> para o construtor de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-107">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="0f84b-108">Portanto, é conveniente passar os resultados de uma consulta como conteúdo em métodos e os construtores que você usa para popular árvores XML.</span><span class="sxs-lookup"><span data-stu-id="0f84b-108">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="0f84b-109">Ao adicionar conteúdo simples, vários tipos podem ser passados para esse método.</span><span class="sxs-lookup"><span data-stu-id="0f84b-109">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="0f84b-110">Os tipos válidos incluem:</span><span class="sxs-lookup"><span data-stu-id="0f84b-110">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="0f84b-111">Qualquer tipo que implemente `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="0f84b-111">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="0f84b-112">Qualquer tipo que implemente <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-112">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="0f84b-113">Ao adicionar conteúdo complexo, vários tipos podem ser passados para esse método:</span><span class="sxs-lookup"><span data-stu-id="0f84b-113">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="0f84b-114">Qualquer tipo que implementa <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="0f84b-114">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="0f84b-115">Se um objeto implementar <xref:System.Collections.Generic.IEnumerable%601>, a coleção no objeto será enumerada, e todos os itens da coleção serão adicionados.</span><span class="sxs-lookup"><span data-stu-id="0f84b-115">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="0f84b-116">Se a coleção contiver objetos <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, cada item da coleção será adicionado separadamente.</span><span class="sxs-lookup"><span data-stu-id="0f84b-116">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="0f84b-117">Se a coleção contiver texto (ou objetos que são convertidos em texto), o texto da coleção será concatenado e adicionado como um único nó de texto.</span><span class="sxs-lookup"><span data-stu-id="0f84b-117">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="0f84b-118">Se o conteúdo for `null`, nada será adicionado.</span><span class="sxs-lookup"><span data-stu-id="0f84b-118">If content is `null`, nothing is added.</span></span> <span data-ttu-id="0f84b-119">Ao passar itens de um coleção, a coleção pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="0f84b-119">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="0f84b-120">Um item `null` na coleção não tem nenhum efeito na árvore.</span><span class="sxs-lookup"><span data-stu-id="0f84b-120">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="0f84b-121">Um atributo adicionado deve ter um nome exclusivo dentro do elemento que o contém.</span><span class="sxs-lookup"><span data-stu-id="0f84b-121">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="0f84b-122">Ao adicionar objetos <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, se o novo conteúdo não tiver um pai, os objetos serão simplesmente anexados à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="0f84b-122">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="0f84b-123">Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="0f84b-123">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="0f84b-124">Conteúdo válido para documentos</span><span class="sxs-lookup"><span data-stu-id="0f84b-124">Valid Content for Documents</span></span>  
 <span data-ttu-id="0f84b-125">Atributos e conteúdo simples não podem ser adicionados a um documento.</span><span class="sxs-lookup"><span data-stu-id="0f84b-125">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="0f84b-126">Não há muitos cenários que exijam a criação de um <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-126">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="0f84b-127">Em vez disso, você normalmente pode criar suas árvores XML com um nó raiz de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-127">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="0f84b-128">A menos que você tenha um requisito específico para criar um documento (por exemplo, porque você precisa criar instruções de processamento e comentários no nível superior ou precisa dar suporte a tipos de documento), geralmente é mais conveniente usar <xref:System.Xml.Linq.XElement> como o nó raiz.</span><span class="sxs-lookup"><span data-stu-id="0f84b-128">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="0f84b-129">O conteúdo válido de um documento inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f84b-129">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="0f84b-130">Zero ou um objeto <xref:System.Xml.Linq.XDocumentType>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-130">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="0f84b-131">Os tipos de documento devem vir antes do elemento.</span><span class="sxs-lookup"><span data-stu-id="0f84b-131">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="0f84b-132">Zero ou um elemento.</span><span class="sxs-lookup"><span data-stu-id="0f84b-132">Zero or one element.</span></span>  
  
- <span data-ttu-id="0f84b-133">Zero ou mais comentários.</span><span class="sxs-lookup"><span data-stu-id="0f84b-133">Zero or more comments.</span></span>  
  
- <span data-ttu-id="0f84b-134">Zero ou mais instruções de processamento.</span><span class="sxs-lookup"><span data-stu-id="0f84b-134">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="0f84b-135">Zero ou mais nós de texto que contêm somente espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="0f84b-135">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="0f84b-136">Construtores e funções que permitem adicionar conteúdo</span><span class="sxs-lookup"><span data-stu-id="0f84b-136">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="0f84b-137">Os métodos a seguir permitem adicionar conteúdo filho a um <xref:System.Xml.Linq.XElement> ou a um <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="0f84b-137">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="0f84b-138">Método</span><span class="sxs-lookup"><span data-stu-id="0f84b-138">Method</span></span>|<span data-ttu-id="0f84b-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f84b-139">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="0f84b-140">Constrói um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-140">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="0f84b-141">Constrói um <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-141">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="0f84b-142">Adiciona ao final do conteúdo filho do <xref:System.Xml.Linq.XElement> ou do <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-142">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="0f84b-143">Adiciona conteúdo depois de <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-143">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="0f84b-144">Adiciona conteúdo antes de <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-144">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="0f84b-145">Adiciona conteúdo ao início do conteúdo filho de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-145">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="0f84b-146">Substitui todo o conteúdo (nós filho e atributos) de um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-146">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="0f84b-147">Substitui os atributos de um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0f84b-147">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="0f84b-148">Substitui os nós filho pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0f84b-148">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="0f84b-149">Substitui um nó pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0f84b-149">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f84b-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="0f84b-150">See also</span></span>

- [<span data-ttu-id="0f84b-151">Criando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0f84b-151">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
