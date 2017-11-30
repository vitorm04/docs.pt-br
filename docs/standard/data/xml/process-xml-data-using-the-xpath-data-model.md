---
title: Processar dados XML usando o modelo de dados XPath
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d2c8db03d494be13a93df06a359e4e4294c22a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="process-xml-data-using-the-xpath-data-model"></a><span data-ttu-id="a6c13-102">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="a6c13-102">Process XML Data Using the XPath Data Model</span></span>
<span data-ttu-id="a6c13-103">O namespace <xref:System.Xml?displayProperty=nameWithType> fornece uma representação programática de documentos XML, fragmentos, nós ou conjuntos de nós na memória, usando as classes <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="a6c13-103">The <xref:System.Xml?displayProperty=nameWithType> namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets in-memory, using the <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> classes.</span></span>  
  
 <span data-ttu-id="a6c13-104">A classe <xref:System.Xml.XPath.XPathDocument> fornece uma representação rápida, somente leitura e na memória de um documento XML usando o modelo de dados XPath.</span><span class="sxs-lookup"><span data-stu-id="a6c13-104">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="a6c13-105">A classe <xref:System.Xml.XmlDocument> fornece uma representação editável e na memória de um documento XML que implementa o núcleo de nível 1 do DOM (Modelo de Objeto de Documento) do W3C e o nível 2 do DOM principal.</span><span class="sxs-lookup"><span data-stu-id="a6c13-105">The <xref:System.Xml.XmlDocument> class provides an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="a6c13-106">Ambas as classes implementam a interface <xref:System.Xml.XPath.IXPathNavigable> e retornam um objeto <xref:System.Xml.XPath.XPathNavigator> usado para selecionar, avaliar, navegar e, em alguns casos, editar os dados XML subjacentes.</span><span class="sxs-lookup"><span data-stu-id="a6c13-106">Both classes implement the <xref:System.Xml.XPath.IXPathNavigable> interface and return an <xref:System.Xml.XPath.XPathNavigator> object used to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="a6c13-107">As seções a seguir descrevem a funcionalidade da classe <xref:System.Xml.XPath.XPathNavigator> com base na classe que ela retorna.</span><span class="sxs-lookup"><span data-stu-id="a6c13-107">The following sections describe the functionality of the <xref:System.Xml.XPath.XPathNavigator> class based on the class that returns it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6c13-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a6c13-108">In This Section</span></span>  
 [<span data-ttu-id="a6c13-109">Lendo dados XML usando XPathDocument e XmlDocument</span><span class="sxs-lookup"><span data-stu-id="a6c13-109">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 <span data-ttu-id="a6c13-110">Descreve como criar um objeto da classe <xref:System.Xml.XPath.XPathDocument> somente leitura para ler um documento XML e como criar um objeto da classe <xref:System.Xml.XmlDocument> editável para ler e editar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="a6c13-110">Describes how to create a read-only <xref:System.Xml.XPath.XPathDocument> class object to read an XML document and how to create an editable <xref:System.Xml.XmlDocument> class object to read and edit an XML document.</span></span> <span data-ttu-id="a6c13-111">Este tópico também descreve como retornar um objeto <xref:System.Xml.XPath.XPathNavigator> de cada classe para navegar e editar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="a6c13-111">This topic also describes how return an <xref:System.Xml.XPath.XPathNavigator> object from each class to navigate and edit an XML document.</span></span>  
  
 [<span data-ttu-id="a6c13-112">Selecionando, avaliando e correspondente de dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a6c13-112">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="a6c13-113">Descreve os métodos da classe <xref:System.Xml.XPath.XPathNavigator> usada para selecionar nós em um objeto <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> usando uma consulta XPath, avaliar e examinar os resultados de uma expressão XPath e determinar se um nó em um documento XML corresponde uma expressão XPath determinada.</span><span class="sxs-lookup"><span data-stu-id="a6c13-113">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an XML document matches a given XPath expression.</span></span>  
  
 [<span data-ttu-id="a6c13-114">Acessando dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a6c13-114">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="a6c13-115">Descreve os métodos da classe <xref:System.Xml.XPath.XPathNavigator> usada para navegar nós, extrair dados XML e acessar dados XML fortemente tipados em um objeto <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a6c13-115">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="a6c13-116">Editando dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a6c13-116">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="a6c13-117">Descreve os métodos da classe <xref:System.Xml.XPath.XPathNavigator> usada para inserir, modificar e remover os nós e os valores de um documento XML contido em um objeto <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a6c13-117">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="a6c13-118">Validação de esquema usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a6c13-118">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="a6c13-119">Descreve as maneiras para validar o conteúdo XML contido em um objeto <xref:System.Xml.XPath.XPathDocument> ou de <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a6c13-119">Describes the ways to validate the XML content contained in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c13-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6c13-120">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="a6c13-121">Processar dados XML usando o modelo DOM</span><span class="sxs-lookup"><span data-stu-id="a6c13-121">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
