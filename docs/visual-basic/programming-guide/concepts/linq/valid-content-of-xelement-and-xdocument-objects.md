---
title: "Conteúdo válido de XElement e XDocument Objects2"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5093ef1c2974bcb980d97d4839af35bb69044a90
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="37159-102">Conteúdo válido de objetos XElement e XDocument</span><span class="sxs-lookup"><span data-stu-id="37159-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="37159-103">Este tópico descreve os argumentos válidos que podem ser passados para os construtores e os métodos que você usa para adicionar conteúdo a elementos e documentos.</span><span class="sxs-lookup"><span data-stu-id="37159-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="37159-104">Conteúdo válido</span><span class="sxs-lookup"><span data-stu-id="37159-104">Valid Content</span></span>  
 <span data-ttu-id="37159-105">As consultas geralmente avaliam para <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="37159-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="37159-106">Você pode passar coleções de <xref:System.Xml.Linq.XElement> ou de objetos <xref:System.Xml.Linq.XAttribute> para o construtor de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="37159-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="37159-107">Portanto, é conveniente passar os resultados de uma consulta como conteúdo em métodos e os construtores que você usa para popular árvores XML.</span><span class="sxs-lookup"><span data-stu-id="37159-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="37159-108">Ao adicionar conteúdo simples, vários tipos podem ser passados para esse método.</span><span class="sxs-lookup"><span data-stu-id="37159-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="37159-109">Os tipos válidos incluem:</span><span class="sxs-lookup"><span data-stu-id="37159-109">Valid types include the following:</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   <span data-ttu-id="37159-110">Qualquer tipo que implemente `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="37159-110">Any type that implements `Object.ToString`.</span></span>  
  
-   <span data-ttu-id="37159-111">Qualquer tipo que implemente <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="37159-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="37159-112">Ao adicionar conteúdo complexo, vários tipos podem ser passados para esse método:</span><span class="sxs-lookup"><span data-stu-id="37159-112">When adding complex content, various types can be passed to this method:</span></span>  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   <span data-ttu-id="37159-113">Qualquer tipo que implemente <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="37159-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="37159-114">Se um objeto implementar <xref:System.Collections.Generic.IEnumerable%601>, a coleção no objeto será enumerada, e todos os itens da coleção serão adicionados.</span><span class="sxs-lookup"><span data-stu-id="37159-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="37159-115">Se a coleção contiver objetos <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, cada item da coleção será adicionado separadamente.</span><span class="sxs-lookup"><span data-stu-id="37159-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="37159-116">Se a coleção contiver texto (ou objetos que são convertidos em texto), o texto da coleção será concatenado e adicionado como um único nó de texto.</span><span class="sxs-lookup"><span data-stu-id="37159-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="37159-117">Se o conteúdo for `null`, nada será adicionado.</span><span class="sxs-lookup"><span data-stu-id="37159-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="37159-118">Ao passar itens de um coleção, a coleção pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="37159-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="37159-119">Um item `null` na coleção não tem nenhum efeito na árvore.</span><span class="sxs-lookup"><span data-stu-id="37159-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="37159-120">Um atributo adicionado deve ter um nome exclusivo dentro do elemento que o contém.</span><span class="sxs-lookup"><span data-stu-id="37159-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="37159-121">Ao adicionar objetos <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, se o novo conteúdo não tiver um pai, os objetos serão simplesmente anexados à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="37159-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="37159-122">Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="37159-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="37159-123">Conteúdo válido para documentos</span><span class="sxs-lookup"><span data-stu-id="37159-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="37159-124">Atributos e conteúdo simples não podem ser adicionados a um documento.</span><span class="sxs-lookup"><span data-stu-id="37159-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="37159-125">Não há muitos cenários que exijam a criação de um <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="37159-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="37159-126">Em vez disso, você normalmente pode criar suas árvores XML com um nó raiz de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="37159-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="37159-127">A menos que você tenha um requisito específico para criar um documento (por exemplo, porque você precisa criar instruções de processamento e comentários no nível superior ou precisa dar suporte a tipos de documento), geralmente é mais conveniente usar <xref:System.Xml.Linq.XElement> como o nó raiz.</span><span class="sxs-lookup"><span data-stu-id="37159-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="37159-128">O conteúdo válido de um documento inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="37159-128">Valid content for a document includes the following:</span></span>  
  
-   <span data-ttu-id="37159-129">Zero ou um objeto <xref:System.Xml.Linq.XDocumentType>.</span><span class="sxs-lookup"><span data-stu-id="37159-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="37159-130">Os tipos de documento devem vir antes do elemento.</span><span class="sxs-lookup"><span data-stu-id="37159-130">The document types must come before the element.</span></span>  
  
-   <span data-ttu-id="37159-131">Zero ou um elemento.</span><span class="sxs-lookup"><span data-stu-id="37159-131">Zero or one element.</span></span>  
  
-   <span data-ttu-id="37159-132">Zero ou mais comentários.</span><span class="sxs-lookup"><span data-stu-id="37159-132">Zero or more comments.</span></span>  
  
-   <span data-ttu-id="37159-133">Zero ou mais instruções de processamento.</span><span class="sxs-lookup"><span data-stu-id="37159-133">Zero or more processing instructions.</span></span>  
  
-   <span data-ttu-id="37159-134">Zero ou mais nós de texto que contêm somente espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="37159-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="37159-135">Construtores e funções que permitem adicionar conteúdo</span><span class="sxs-lookup"><span data-stu-id="37159-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="37159-136">Os métodos a seguir permitem adicionar conteúdo filho a um <xref:System.Xml.Linq.XElement> ou a um <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="37159-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="37159-137">Método</span><span class="sxs-lookup"><span data-stu-id="37159-137">Method</span></span>|<span data-ttu-id="37159-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="37159-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="37159-139">Constrói um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="37159-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="37159-140">Constrói um <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="37159-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="37159-141">Adiciona ao final do conteúdo filho do <xref:System.Xml.Linq.XElement> ou do <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="37159-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="37159-142">Adiciona conteúdo depois de <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="37159-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="37159-143">Adiciona conteúdo antes de <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="37159-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="37159-144">Adiciona conteúdo ao início do conteúdo filho de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="37159-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="37159-145">Substitui todo o conteúdo (nós filho e atributos) de um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="37159-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="37159-146">Substitui os atributos de um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="37159-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="37159-147">Substitui os nós filho pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="37159-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="37159-148">Substitui um nó pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="37159-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37159-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37159-149">See Also</span></span>  
 [<span data-ttu-id="37159-150">Criando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37159-150">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
