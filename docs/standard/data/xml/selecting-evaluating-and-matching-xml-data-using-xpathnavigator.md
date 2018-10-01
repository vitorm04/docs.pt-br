---
title: Selecionando, avaliando e correspondente de dados XML usando XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2544070bb7ea891a804edd559a5d58e08b071771
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47193129"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="c7308-102">Selecionando, avaliando e correspondente de dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c7308-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="c7308-103">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece métodos para nós selecionados em um objeto de <xref:System.Xml.XPath.XPathDocument> ou de <xref:System.Xml.XmlDocument> usando uma consulta XPath, valores e examina os resultados de uma expressão XPath, e determina se um nó em um objeto de <xref:System.Xml.XPath.XPathDocument> ou de <xref:System.Xml.XmlDocument> corresponde uma expressão XPath determinada.</span><span class="sxs-lookup"><span data-stu-id="c7308-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="c7308-104">Esses e outros conceitos relacionados à selecionar, classificar e aos nós em um objeto de <xref:System.Xml.XPath.XPathDocument> ou de <xref:System.Xml.XmlDocument> são descritos nos tópicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7308-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7308-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c7308-105">In This Section</span></span>  
 [<span data-ttu-id="c7308-106">Selecionar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c7308-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="c7308-107">Descreve o conjunto de métodos da classe <xref:System.Xml.XPath.XPathNavigator> usados para selecionar um conjunto de nós em um objeto de <xref:System.Xml.XPath.XPathDocument> ou de <xref:System.Xml.XmlDocument> usando uma expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="c7308-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="c7308-108">Avaliar as expressões XPath usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c7308-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="c7308-109">Descreve o método de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> usada para avaliar uma expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="c7308-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="c7308-110">Correspondência de nós usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c7308-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="c7308-111">Descreve o método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> usada para determinar se um nó corresponde uma expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="c7308-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="c7308-112">Tipos de nós reconhecidos com consultas XPath</span><span class="sxs-lookup"><span data-stu-id="c7308-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="c7308-113">Descreve os tipos de nós reconhecidas em uma consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="c7308-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="c7308-114">Consultas e Namespaces de XPath</span><span class="sxs-lookup"><span data-stu-id="c7308-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="c7308-115">Descreve o uso de namespaces em uma consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="c7308-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="c7308-116">Expressões XPath compilados</span><span class="sxs-lookup"><span data-stu-id="c7308-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="c7308-117">Descreve a classe de <xref:System.Xml.XPath.XPathExpression> que representa uma consulta XPath compilado.</span><span class="sxs-lookup"><span data-stu-id="c7308-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7308-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7308-118">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="c7308-119">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="c7308-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="c7308-120">Lendo dados XML usando XPathDocument e XmlDocument</span><span class="sxs-lookup"><span data-stu-id="c7308-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
- [<span data-ttu-id="c7308-121">Acessando dados XML usando o XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c7308-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="c7308-122">Editando dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c7308-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="c7308-123">Validação de esquema usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c7308-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
