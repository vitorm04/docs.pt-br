---
title: Manipulando XML no Visual Basic | Documentos do Microsoft
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
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 62b955d78eb507aab4c786e84f3044ba54a38ebc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="16c1d-102">Manipulando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16c1d-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="16c1d-103">Você pode usar *literais XML* para carregar XML de uma fonte externa, como uma cadeia de caracteres, arquivo ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="16c1d-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="16c1d-104">Você pode usar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] para manipular o XML e usar [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] para consultar o XML.</span><span class="sxs-lookup"><span data-stu-id="16c1d-104">You can then use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16c1d-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="16c1d-105">In This Section</span></span>  
 [<span data-ttu-id="16c1d-106">Como carregar XML de um arquivo, cadeia de caracteres ou fluxo</span><span class="sxs-lookup"><span data-stu-id="16c1d-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="16c1d-107">Demonstra como carregar XML em um <xref:System.Xml.Linq.XDocument>ou <xref:System.Xml.Linq.XElement>objeto a partir de um arquivo de texto, cadeia de caracteres ou fluxo.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="16c1d-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="16c1d-108">Como transformar XML usando LINQ</span><span class="sxs-lookup"><span data-stu-id="16c1d-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="16c1d-109">Demonstra como transformar o conteúdo de um <xref:System.Xml.Linq.XDocument>objeto em um novo documento XML.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="16c1d-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="16c1d-110">Como modificar literais XML</span><span class="sxs-lookup"><span data-stu-id="16c1d-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="16c1d-111">Demonstra como modificar os elementos, atributos e valores em um literal XML.</span><span class="sxs-lookup"><span data-stu-id="16c1d-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="16c1d-112">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="16c1d-112">Related Sections</span></span>  
 [<span data-ttu-id="16c1d-113">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="16c1d-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="16c1d-114">Fornece links para seções que descrevem as várias propriedades de acesso do XML.</span><span class="sxs-lookup"><span data-stu-id="16c1d-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="16c1d-115">Visão geral de LINQ to XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16c1d-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="16c1d-116">Fornece uma introdução ao uso [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="16c1d-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="16c1d-117">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16c1d-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="16c1d-118">Fornece uma introdução ao uso de literais XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="16c1d-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="16c1d-119">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16c1d-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="16c1d-120">Demonstra como acessar partes de um elemento XML ou documento no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="16c1d-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="16c1d-121">XML</span><span class="sxs-lookup"><span data-stu-id="16c1d-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="16c1d-122">Fornece links para seções que descrevem como usar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="16c1d-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c1d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16c1d-123">See Also</span></span>  
 <span data-ttu-id="16c1d-124">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="16c1d-124">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="16c1d-125"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="16c1d-125"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="16c1d-126"> [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="16c1d-126"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
