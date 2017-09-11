---
title: "Conteúdo válido de XElement e XDocument Objects2 | Documentos do Microsoft"
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
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ecdcd4c2c0ec61cf248c9e210d42abb750e0546b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="b8881-102">Conteúdo válido de objetos XElement e XDocument</span><span class="sxs-lookup"><span data-stu-id="b8881-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="b8881-103">Este tópico descreve os argumentos válidos que podem ser passados para os construtores e os métodos que você usa para adicionar conteúdo a elementos e documentos.</span><span class="sxs-lookup"><span data-stu-id="b8881-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="b8881-104">Conteúdo válido</span><span class="sxs-lookup"><span data-stu-id="b8881-104">Valid Content</span></span>  
 <span data-ttu-id="b8881-105">As consultas geralmente avaliam para <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601>do <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="b8881-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="b8881-106">Você pode passar coleções de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>objetos para o <xref:System.Xml.Linq.XElement>construtor.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b8881-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="b8881-107">Portanto, é conveniente passar os resultados de uma consulta como conteúdo em métodos e os construtores que você usa para popular árvores XML.</span><span class="sxs-lookup"><span data-stu-id="b8881-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="b8881-108">Ao adicionar conteúdo simples, vários tipos podem ser passados para esse método.</span><span class="sxs-lookup"><span data-stu-id="b8881-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="b8881-109">Os tipos válidos incluem:</span><span class="sxs-lookup"><span data-stu-id="b8881-109">Valid types include the following:</span></span>  
  
-   <span data-ttu-id="b8881-110"><xref:System.String></xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b8881-110"><xref:System.String></span></span>  
  
-   <span data-ttu-id="b8881-111"><xref:System.Double></xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="b8881-111"><xref:System.Double></span></span>  
  
-   <span data-ttu-id="b8881-112"><xref:System.Single></xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="b8881-112"><xref:System.Single></span></span>  
  
-   <span data-ttu-id="b8881-113"><xref:System.Decimal></xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b8881-113"><xref:System.Decimal></span></span>  
  
-   <span data-ttu-id="b8881-114"><xref:System.Boolean></xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="b8881-114"><xref:System.Boolean></span></span>  
  
-   <span data-ttu-id="b8881-115"><xref:System.DateTime></xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="b8881-115"><xref:System.DateTime></span></span>  
  
-   <span data-ttu-id="b8881-116"><xref:System.TimeSpan></xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="b8881-116"><xref:System.TimeSpan></span></span>  
  
-   <span data-ttu-id="b8881-117"><xref:System.DateTimeOffset></xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="b8881-117"><xref:System.DateTimeOffset></span></span>  
  
-   <span data-ttu-id="b8881-118">Qualquer tipo que implemente `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="b8881-118">Any type that implements `Object.ToString`.</span></span>  
  
-   <span data-ttu-id="b8881-119">Qualquer tipo que implemente <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="b8881-119">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="b8881-120">Ao adicionar conteúdo complexo, vários tipos podem ser passados para esse método:</span><span class="sxs-lookup"><span data-stu-id="b8881-120">When adding complex content, various types can be passed to this method:</span></span>  
  
-   <span data-ttu-id="b8881-121"><xref:System.Xml.Linq.XObject></xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="b8881-121"><xref:System.Xml.Linq.XObject></span></span>  
  
-   <span data-ttu-id="b8881-122"><xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="b8881-122"><xref:System.Xml.Linq.XNode></span></span>  
  
-   <span data-ttu-id="b8881-123"><xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="b8881-123"><xref:System.Xml.Linq.XAttribute></span></span>  
  
-   <span data-ttu-id="b8881-124">Qualquer tipo que implementa<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="b8881-124">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="b8881-125">Se um objeto implementa <xref:System.Collections.Generic.IEnumerable%601>, a coleção do objeto é enumerada e todos os itens na coleção serão adicionados.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="b8881-125">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="b8881-126">Se a coleção contiver <xref:System.Xml.Linq.XNode>ou <xref:System.Xml.Linq.XAttribute>objetos, cada item da coleção será adicionado separadamente.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="b8881-126">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="b8881-127">Se a coleção contiver texto (ou objetos que são convertidos em texto), o texto da coleção será concatenado e adicionado como um único nó de texto.</span><span class="sxs-lookup"><span data-stu-id="b8881-127">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="b8881-128">Se o conteúdo for `null`, nada será adicionado.</span><span class="sxs-lookup"><span data-stu-id="b8881-128">If content is `null`, nothing is added.</span></span> <span data-ttu-id="b8881-129">Ao passar itens de um coleção, a coleção pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="b8881-129">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="b8881-130">Um item `null` na coleção não tem nenhum efeito na árvore.</span><span class="sxs-lookup"><span data-stu-id="b8881-130">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="b8881-131">Um atributo adicionado deve ter um nome exclusivo dentro do elemento que o contém.</span><span class="sxs-lookup"><span data-stu-id="b8881-131">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="b8881-132">Ao adicionar <xref:System.Xml.Linq.XNode>ou <xref:System.Xml.Linq.XAttribute>objetos, se o novo conteúdo não tem nenhum pai, em seguida, os objetos serão simplesmente anexados à árvore XML.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="b8881-132">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="b8881-133">Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="b8881-133">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="b8881-134">Conteúdo válido para documentos</span><span class="sxs-lookup"><span data-stu-id="b8881-134">Valid Content for Documents</span></span>  
 <span data-ttu-id="b8881-135">Atributos e conteúdo simples não podem ser adicionados a um documento.</span><span class="sxs-lookup"><span data-stu-id="b8881-135">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="b8881-136">Não há muitos cenários que exigem a criação de um <xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="b8881-136">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="b8881-137">Em vez disso, normalmente você pode criar suas árvores XML com um <xref:System.Xml.Linq.XElement>nó raiz.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b8881-137">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="b8881-138">A menos que você tenha um requisito específico para criar um documento (por exemplo, porque você precisa criar comentários e instruções de processamento no nível superior ou precisa dar suporte a tipos de documento), geralmente é mais conveniente usar <xref:System.Xml.Linq.XElement>como o nó raiz.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b8881-138">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="b8881-139">O conteúdo válido de um documento inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b8881-139">Valid content for a document includes the following:</span></span>  
  
-   <span data-ttu-id="b8881-140">Zero ou um <xref:System.Xml.Linq.XDocumentType>objetos.</xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="b8881-140">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="b8881-141">Os tipos de documento devem vir antes do elemento.</span><span class="sxs-lookup"><span data-stu-id="b8881-141">The document types must come before the element.</span></span>  
  
-   <span data-ttu-id="b8881-142">Zero ou um elemento.</span><span class="sxs-lookup"><span data-stu-id="b8881-142">Zero or one element.</span></span>  
  
-   <span data-ttu-id="b8881-143">Zero ou mais comentários.</span><span class="sxs-lookup"><span data-stu-id="b8881-143">Zero or more comments.</span></span>  
  
-   <span data-ttu-id="b8881-144">Zero ou mais instruções de processamento.</span><span class="sxs-lookup"><span data-stu-id="b8881-144">Zero or more processing instructions.</span></span>  
  
-   <span data-ttu-id="b8881-145">Zero ou mais nós de texto que contêm somente espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="b8881-145">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="b8881-146">Construtores e funções que permitem adicionar conteúdo</span><span class="sxs-lookup"><span data-stu-id="b8881-146">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="b8881-147">Os métodos a seguir permitem que você adicione conteúdo filho a um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>:</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b8881-147">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="b8881-148">Método</span><span class="sxs-lookup"><span data-stu-id="b8881-148">Method</span></span>|<span data-ttu-id="b8881-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8881-149">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b8881-150"><xref:System.Xml.Linq.XElement.%23ctor%2A></xref:System.Xml.Linq.XElement.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-150"><xref:System.Xml.Linq.XElement.%23ctor%2A></span></span>|<span data-ttu-id="b8881-151">Constrói um <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b8881-151">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="b8881-152"><xref:System.Xml.Linq.XDocument.%23ctor%2A></xref:System.Xml.Linq.XDocument.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-152"><xref:System.Xml.Linq.XDocument.%23ctor%2A></span></span>|<span data-ttu-id="b8881-153">Constrói um <xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="b8881-153">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<span data-ttu-id="b8881-154"><xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XContainer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-154"><xref:System.Xml.Linq.XContainer.Add%2A></span></span>|<span data-ttu-id="b8881-155">Adiciona ao final do conteúdo filho do <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b8881-155">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<span data-ttu-id="b8881-156"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-156"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span></span>|<span data-ttu-id="b8881-157">Adiciona conteúdo após o <xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="b8881-157">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<span data-ttu-id="b8881-158"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-158"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span></span>|<span data-ttu-id="b8881-159">Adiciona conteúdo antes de <xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="b8881-159">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<span data-ttu-id="b8881-160"><xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XContainer.AddFirst%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-160"><xref:System.Xml.Linq.XContainer.AddFirst%2A></span></span>|<span data-ttu-id="b8881-161">Adiciona o conteúdo no início do conteúdo filho de <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="b8881-161">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="b8881-162"><xref:System.Xml.Linq.XElement.ReplaceAll%2A></xref:System.Xml.Linq.XElement.ReplaceAll%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-162"><xref:System.Xml.Linq.XElement.ReplaceAll%2A></span></span>|<span data-ttu-id="b8881-163">Substitui todo o conteúdo (nós filho e atributos) de <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b8881-163">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="b8881-164"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-164"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></span></span>|<span data-ttu-id="b8881-165">Substitui os atributos de <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b8881-165">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="b8881-166"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-166"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></span></span>|<span data-ttu-id="b8881-167">Substitui os nós filho pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="b8881-167">Replaces the children nodes with new content.</span></span>|  
|<span data-ttu-id="b8881-168"><xref:System.Xml.Linq.XNode.ReplaceWith%2A></xref:System.Xml.Linq.XNode.ReplaceWith%2A></span><span class="sxs-lookup"><span data-stu-id="b8881-168"><xref:System.Xml.Linq.XNode.ReplaceWith%2A></span></span>|<span data-ttu-id="b8881-169">Substitui um nó pelo novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="b8881-169">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8881-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8881-170">See Also</span></span>  
 [<span data-ttu-id="b8881-171">Criando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8881-171">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
