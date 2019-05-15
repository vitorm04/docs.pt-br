---
title: Processar dados XML usando o modelo DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34d22d8329f0bc26c1e29653137211bf300d324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647818"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="05bff-102">Processar dados XML usando o modelo DOM</span><span class="sxs-lookup"><span data-stu-id="05bff-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="05bff-103">O DOM (Document Object Model) XML trata dados XML como um conjunto padrão de objetos e é usado para processar dados XML na memória.</span><span class="sxs-lookup"><span data-stu-id="05bff-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="05bff-104">O namespace `System.Xml` fornece uma representação programática de documentos XML, fragmentos, nós ou conjuntos de nós.</span><span class="sxs-lookup"><span data-stu-id="05bff-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="05bff-105">É baseado nas recomendações de núcleo de nível 1 do DOM do W3C e de núcleo de nível 2 do DOM.</span><span class="sxs-lookup"><span data-stu-id="05bff-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="05bff-106">A classe <xref:System.Xml.XmlDocument> representa um documento XML.</span><span class="sxs-lookup"><span data-stu-id="05bff-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="05bff-107">Ele inclui membros para recuperar e criar todos outros objetos XML.</span><span class="sxs-lookup"><span data-stu-id="05bff-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="05bff-108">Com o <xref:System.Xml.XmlDocument> e suas classes relacionadas, você pode criar documentos XML, carregar e acessar dados, modificar dados e salvar alterações.</span><span class="sxs-lookup"><span data-stu-id="05bff-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05bff-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="05bff-109">In This Section</span></span>  
  
- [<span data-ttu-id="05bff-110">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="05bff-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="05bff-111">Tipos de nós XML</span><span class="sxs-lookup"><span data-stu-id="05bff-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
- [<span data-ttu-id="05bff-112">Hierarquia de DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="05bff-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="05bff-113">Mapeando a hierarquia de objetos para dados XML</span><span class="sxs-lookup"><span data-stu-id="05bff-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="05bff-114">Criação de documentos XML</span><span class="sxs-lookup"><span data-stu-id="05bff-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
- [<span data-ttu-id="05bff-115">Ler um documento XML no DOM</span><span class="sxs-lookup"><span data-stu-id="05bff-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="05bff-116">Inserção de nós em um documento XML</span><span class="sxs-lookup"><span data-stu-id="05bff-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="05bff-117">Removendo nós, conteúdo e os valores de um documento XML</span><span class="sxs-lookup"><span data-stu-id="05bff-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="05bff-118">Modificando nós, conteúdo e os valores em um documento XML</span><span class="sxs-lookup"><span data-stu-id="05bff-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="05bff-119">Validando um documento XML no DOM</span><span class="sxs-lookup"><span data-stu-id="05bff-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="05bff-120">Salvando e escrevendo um documento</span><span class="sxs-lookup"><span data-stu-id="05bff-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="05bff-121">Selecionar nós usando a navegação XPath</span><span class="sxs-lookup"><span data-stu-id="05bff-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="05bff-122">Resolvendo recursos externos</span><span class="sxs-lookup"><span data-stu-id="05bff-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
- [<span data-ttu-id="05bff-123">Comparação de objeto usando XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="05bff-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="05bff-124">Coleções de nó em NamedNodeMaps e em NodeLists</span><span class="sxs-lookup"><span data-stu-id="05bff-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="05bff-125">Atualizações dinâmicas a NodeLists e a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="05bff-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="05bff-126">Suporte a Namespace em DOM</span><span class="sxs-lookup"><span data-stu-id="05bff-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="05bff-127">Tratamento de eventos em um documento XML usando o XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="05bff-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="05bff-128">Estendendo o DOM</span><span class="sxs-lookup"><span data-stu-id="05bff-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="05bff-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="05bff-129">Related Sections</span></span>  
 [<span data-ttu-id="05bff-130">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="05bff-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="05bff-131">Discute o processamento de XML usando a classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="05bff-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
