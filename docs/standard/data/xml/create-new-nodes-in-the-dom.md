---
title: Criar novos nós no DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 390ffa1dd9f2e76372b0e4fcbf2916918b64d748
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44260091"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="44aa6-102">Criar novos nós no DOM</span><span class="sxs-lookup"><span data-stu-id="44aa6-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="44aa6-103">O <xref:System.Xml.XmlDocument> tem um método de criação para todos os tipos de nó.</span><span class="sxs-lookup"><span data-stu-id="44aa6-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="44aa6-104">Forneça o método com um nome se necessário, e conteúdo ou outros parâmetros para os nós que têm conteúdo (por exemplo, um nó de texto), e o nó é criado.</span><span class="sxs-lookup"><span data-stu-id="44aa6-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="44aa6-105">Os seguintes métodos são os que precisam de um nome e alguns outros parâmetros preenchidos para criar um nó apropriado.</span><span class="sxs-lookup"><span data-stu-id="44aa6-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 <span data-ttu-id="44aa6-106">Outros tipos de nós têm mais requisitos do que apenas fornecer dados para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="44aa6-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="44aa6-107">Para saber mais sobre atributos, confira [Criando novos atributos para elementos no DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="44aa6-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="44aa6-108">Para saber mais sobre elementos e validação de nomes de atributos, confira [O elemento XML e a verificação de nome de atributo ao criar novos nós](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="44aa6-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="44aa6-109">Para criar referências de entidade, confira [Criando novas referências de entidades](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="44aa6-109">For creating entity references, see [Creating New Entity References](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span></span> <span data-ttu-id="44aa6-110">Para saber mais sobre como os namespaces afetam a expansão de referências de entidade, confira [Efeito do namespace na expansão de referência de entidade para novos nós contendo elementos e atributos](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="44aa6-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="44aa6-111">Assim que os novos nós são criados, há vários métodos disponíveis para inseri-los na árvore.</span><span class="sxs-lookup"><span data-stu-id="44aa6-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="44aa6-112">A tabela lista os métodos com uma descrição de onde o novo nó aparece no DOM (Document Object Model) XML.</span><span class="sxs-lookup"><span data-stu-id="44aa6-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="44aa6-113">Método</span><span class="sxs-lookup"><span data-stu-id="44aa6-113">Method</span></span>|<span data-ttu-id="44aa6-114">Posicionamento do nó</span><span class="sxs-lookup"><span data-stu-id="44aa6-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="44aa6-115">Inserido antes do nó de referência.</span><span class="sxs-lookup"><span data-stu-id="44aa6-115">Inserted before the reference node.</span></span> <span data-ttu-id="44aa6-116">Por exemplo, para inserir o novo nó na posição 5:</span><span class="sxs-lookup"><span data-stu-id="44aa6-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="44aa6-117">Para obter mais informações, consulte o método <xref:System.Xml.XmlNode.InsertBefore%2A>.</span><span class="sxs-lookup"><span data-stu-id="44aa6-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="44aa6-118">Inserido após o nó de referência.</span><span class="sxs-lookup"><span data-stu-id="44aa6-118">Inserted after the reference node.</span></span> <span data-ttu-id="44aa6-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="44aa6-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="44aa6-120">Para obter mais informações, consulte o método <xref:System.Xml.XmlNode.InsertAfter%2A>.</span><span class="sxs-lookup"><span data-stu-id="44aa6-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="44aa6-121">Adiciona o nó no final da lista de nós filho para o nó determinado.</span><span class="sxs-lookup"><span data-stu-id="44aa6-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="44aa6-122">Se o nó que está sendo adicionado for um <xref:System.Xml.XmlDocumentFragment>, todo o conteúdo do fragmento do documento é movido para a lista filho deste nó.</span><span class="sxs-lookup"><span data-stu-id="44aa6-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="44aa6-123">Para obter mais informações, consulte o método <xref:System.Xml.XmlNode.AppendChild%2A>.</span><span class="sxs-lookup"><span data-stu-id="44aa6-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="44aa6-124">Adiciona o nó no início da lista de nós filho do nó determinado.</span><span class="sxs-lookup"><span data-stu-id="44aa6-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="44aa6-125">Se o nó que está sendo adicionado for um <xref:System.Xml.XmlDocumentFragment>, todo o conteúdo do fragmento do documento é movido para a lista filho deste nó.</span><span class="sxs-lookup"><span data-stu-id="44aa6-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="44aa6-126">Para obter mais informações, consulte o método <xref:System.Xml.XmlNode.PrependChild%2A>.</span><span class="sxs-lookup"><span data-stu-id="44aa6-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="44aa6-127">Adiciona um nó <xref:System.Xml.XmlAttribute> ao final da coleção de atributos associada a um elemento.</span><span class="sxs-lookup"><span data-stu-id="44aa6-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="44aa6-128">Para obter mais informações, consulte o método <xref:System.Xml.XmlAttributeCollection.Append%2A>.</span><span class="sxs-lookup"><span data-stu-id="44aa6-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44aa6-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44aa6-129">See also</span></span>

- [<span data-ttu-id="44aa6-130">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="44aa6-130">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
