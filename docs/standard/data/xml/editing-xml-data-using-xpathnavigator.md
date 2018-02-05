---
title: Editando dados XML usando XPathNavigator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1f91616-3115-4264-9821-c66589d11d11
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a967ee63a5ae9e9cc3abc5250af40ea7ba836a07
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="editing-xml-data-using-xpathnavigator"></a><span data-ttu-id="4bdea-102">Editando dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4bdea-102">Editing XML Data using XPathNavigator</span></span>
<span data-ttu-id="4bdea-103">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece métodos para inserir, altera e remover nós e valores de um documento XML contido em <xref:System.Xml.XmlDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="4bdea-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="4bdea-104">Para usar qualquer um desses métodos para inserir, para alterar, e remover os nós e os valores, o objeto de <xref:System.Xml.XPath.XPathNavigator> deve ser editável, isto é, sua propriedade de <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> deve ser verdadeira.</span><span class="sxs-lookup"><span data-stu-id="4bdea-104">In order to use any of these methods to insert, modify, and remove nodes and values, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be true.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4bdea-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4bdea-105">In This Section</span></span>  
 [<span data-ttu-id="4bdea-106">Inserir dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4bdea-106">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="4bdea-107">Descreve como inserir no irmão, o filho, os nós de atributo e os valores a um objeto de <xref:System.Xml.XmlDocument> usando a classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="4bdea-107">Describes how to insert sibling, child, attribute nodes and values in to an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="4bdea-108">Modificar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4bdea-108">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="4bdea-109">Descreve como alterar nós e valores em um objeto de <xref:System.Xml.XmlDocument> usando a classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="4bdea-109">Describes how to modify nodes and values in an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="4bdea-110">Remover os dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4bdea-110">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="4bdea-111">Descreve como remover os nós e valores de um objeto de <xref:System.Xml.XmlDocument> usando a classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="4bdea-111">Describes how to remove nodes and values from an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdea-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bdea-112">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="4bdea-113">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="4bdea-113">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="4bdea-114">Lendo dados XML usando XPathDocument e XmlDocument</span><span class="sxs-lookup"><span data-stu-id="4bdea-114">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="4bdea-115">Selecionando, avaliando e correspondendo dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4bdea-115">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="4bdea-116">Acessando dados XML usando o XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4bdea-116">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="4bdea-117">Validação de esquema usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4bdea-117">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
