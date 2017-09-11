---
title: Serializando arquivos, TextWriters e XmlWriters3 | Documentos do Microsoft
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
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f8f8672004b0704b00ff60e5b58256f664bcbd82
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="ba37d-102">Serializando arquivos, o TextWriters, e o XmlWriters</span><span class="sxs-lookup"><span data-stu-id="ba37d-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="ba37d-103">Você pode serializar árvores XML a um <xref:System.IO.File>, um <xref:System.IO.TextWriter>, ou <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="ba37d-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="ba37d-104">Você pode serializar qualquer componente XML, incluindo <xref:System.Xml.Linq.XDocument>e <xref:System.Xml.Linq.XElement>, em uma cadeia de caracteres usando o `ToString` método.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="ba37d-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="ba37d-105">Se você desejar suprimir formatação ao serializar a uma cadeia de caracteres, você pode usar o <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>método.</xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ba37d-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="ba37d-106">Comportamento de Thedefault quando serializar a um arquivo é formatar o documento XML resultante (recuo).</span><span class="sxs-lookup"><span data-stu-id="ba37d-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="ba37d-107">Quando você identar, o espaço em branco irrisória na árvore XML não é preservada.</span><span class="sxs-lookup"><span data-stu-id="ba37d-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="ba37d-108">Para serializar com formatação, use uma das sobrecargas dos métodos a seguir não são <xref:System.Xml.Linq.SaveOptions>como um argumento:</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="ba37d-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="ba37d-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ba37d-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="ba37d-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ba37d-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="ba37d-111">Se você quiser a opção não recuar e preservar espaço em branco irrisória na árvore XML, use uma das sobrecargas dos métodos a seguir que usa <xref:System.Xml.Linq.SaveOptions>como um argumento:</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="ba37d-111">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="ba37d-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ba37d-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="ba37d-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ba37d-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="ba37d-114">Para exemplos, consulte o tópico de referência apropriado.</span><span class="sxs-lookup"><span data-stu-id="ba37d-114">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba37d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba37d-115">See Also</span></span>  
 [<span data-ttu-id="ba37d-116">Serializando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba37d-116">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
