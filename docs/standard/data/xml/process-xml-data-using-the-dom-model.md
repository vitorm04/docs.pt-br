---
title: Processar dados XML usando o modelo DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
ms.openlocfilehash: 242554cc948ef16972ffd26d5464dae2727ed339
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290831"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="8a8a0-102">Processar dados XML usando o modelo DOM</span><span class="sxs-lookup"><span data-stu-id="8a8a0-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="8a8a0-103">O DOM (Document Object Model) XML trata dados XML como um conjunto padrão de objetos e é usado para processar dados XML na memória.</span><span class="sxs-lookup"><span data-stu-id="8a8a0-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="8a8a0-104">O namespace `System.Xml` fornece uma representação programática de documentos XML, fragmentos, nós ou conjuntos de nós.</span><span class="sxs-lookup"><span data-stu-id="8a8a0-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="8a8a0-105">É baseado nas recomendações de núcleo de nível 1 do DOM do W3C e de núcleo de nível 2 do DOM.</span><span class="sxs-lookup"><span data-stu-id="8a8a0-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="8a8a0-106">A classe <xref:System.Xml.XmlDocument> representa um documento XML.</span><span class="sxs-lookup"><span data-stu-id="8a8a0-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="8a8a0-107">Ele inclui membros para recuperar e criar todos outros objetos XML.</span><span class="sxs-lookup"><span data-stu-id="8a8a0-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="8a8a0-108">Com o <xref:System.Xml.XmlDocument> e suas classes relacionadas, você pode criar documentos XML, carregar e acessar dados, modificar dados e salvar alterações.</span><span class="sxs-lookup"><span data-stu-id="8a8a0-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a8a0-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8a8a0-109">In This Section</span></span>  
  
- [<span data-ttu-id="8a8a0-110">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="8a8a0-110">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="8a8a0-111">Tipos de nós XML</span><span class="sxs-lookup"><span data-stu-id="8a8a0-111">Types of XML Nodes</span></span>](types-of-xml-nodes.md)  
  
- [<span data-ttu-id="8a8a0-112">Hierarquia DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="8a8a0-112">XML Document Object Model (DOM) Hierarchy</span></span>](xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="8a8a0-113">Mapeando a hierarquia do objeto para dados XML</span><span class="sxs-lookup"><span data-stu-id="8a8a0-113">Mapping the Object Hierarchy to XML Data</span></span>](mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="8a8a0-114">Criação de documentos XML</span><span class="sxs-lookup"><span data-stu-id="8a8a0-114">XML Document Creation</span></span>](xml-document-creation.md)  
  
- [<span data-ttu-id="8a8a0-115">Lendo um documento XML no DOM</span><span class="sxs-lookup"><span data-stu-id="8a8a0-115">Reading an XML Document into the DOM</span></span>](reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="8a8a0-116">Inserindo nós em um documento XML</span><span class="sxs-lookup"><span data-stu-id="8a8a0-116">Inserting Nodes into an XML Document</span></span>](inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="8a8a0-117">Removendo os nós, conteúdo, e valores de um documento XML</span><span class="sxs-lookup"><span data-stu-id="8a8a0-117">Removing Nodes, Content, and Values from an XML Document</span></span>](removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="8a8a0-118">Modificando nós, conteúdo e valores em documentos XML</span><span class="sxs-lookup"><span data-stu-id="8a8a0-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="8a8a0-119">Validando um documento XML no DOM</span><span class="sxs-lookup"><span data-stu-id="8a8a0-119">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="8a8a0-120">Salvando e escrevendo um documento</span><span class="sxs-lookup"><span data-stu-id="8a8a0-120">Saving and Writing a Document</span></span>](saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="8a8a0-121">Selecionar nós usando a navegação XPath</span><span class="sxs-lookup"><span data-stu-id="8a8a0-121">Select Nodes Using XPath Navigation</span></span>](select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="8a8a0-122">Resolvendo recursos externos</span><span class="sxs-lookup"><span data-stu-id="8a8a0-122">Resolving External Resources</span></span>](resolving-external-resources.md)  
  
- [<span data-ttu-id="8a8a0-123">Comparação de objeto usando XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="8a8a0-123">Object Comparison Using XmlNameTable</span></span>](object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="8a8a0-124">Coleções de nó em NamedNodeMaps e em NodeLists</span><span class="sxs-lookup"><span data-stu-id="8a8a0-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="8a8a0-125">Atualizações dinâmicas a NodeLists e a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="8a8a0-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="8a8a0-126">Suporte do namespace em DOM</span><span class="sxs-lookup"><span data-stu-id="8a8a0-126">Namespace Support in the DOM</span></span>](namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="8a8a0-127">Tratamento de eventos em um documento XML usando o XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="8a8a0-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="8a8a0-128">Estendendo os DOM</span><span class="sxs-lookup"><span data-stu-id="8a8a0-128">Extending the DOM</span></span>](extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="8a8a0-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8a8a0-129">Related Sections</span></span>  
 [<span data-ttu-id="8a8a0-130">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="8a8a0-130">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="8a8a0-131">Discute o processamento de XML usando a classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="8a8a0-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
