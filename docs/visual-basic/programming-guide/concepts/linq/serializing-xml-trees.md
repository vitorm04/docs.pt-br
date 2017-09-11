---
title: "Serializando árvores XML (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 2c340695-a726-4030-85be-6975d8a149cf
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
ms.openlocfilehash: a63e875b1c1391ec1bb2b0ae64be9f9cff28d87d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-xml-trees-visual-basic"></a><span data-ttu-id="13d71-102">Serializando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13d71-102">Serializing XML Trees (Visual Basic)</span></span>
<span data-ttu-id="13d71-103">Serializar uma árvore XML significa gerar o XML a partir da árvore XML.</span><span class="sxs-lookup"><span data-stu-id="13d71-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="13d71-104">Você pode serializar para um arquivo, para uma implementação concreta da <xref:System.IO.TextWriter>classe, ou para uma implementação concreta de <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter></span><span class="sxs-lookup"><span data-stu-id="13d71-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="13d71-105">Você pode controlar vários aspectos da serialização.</span><span class="sxs-lookup"><span data-stu-id="13d71-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="13d71-106">Por exemplo, você pode determinar se recuará o XML serializado e se gravará uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="13d71-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13d71-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="13d71-107">In This Section</span></span>  
  
|<span data-ttu-id="13d71-108">Tópico</span><span class="sxs-lookup"><span data-stu-id="13d71-108">Topic</span></span>|<span data-ttu-id="13d71-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="13d71-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="13d71-110">Preservar espaço em branco para serializar</span><span class="sxs-lookup"><span data-stu-id="13d71-110">Preserving White Space While Serializing</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="13d71-111">Descreve como controlar o comportamento de espaço em branco durante a serialização das árvores XML.</span><span class="sxs-lookup"><span data-stu-id="13d71-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="13d71-112">Serializando com uma declaração XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13d71-112">Serializing with an XML Declaration (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="13d71-113">Descreve como serializar uma árvore XML que inclua uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="13d71-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="13d71-114">Serializando arquivos, o TextWriters, e o XmlWriters</span><span class="sxs-lookup"><span data-stu-id="13d71-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="13d71-115">Descreve como serializar um documento para um <xref:System.IO.File>, um <xref:System.IO.TextWriter>, ou <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="13d71-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="13d71-116">Serializando um XmlReader (chamada XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13d71-116">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="13d71-117">Descreve como criar um <xref:System.Xml.XmlReader>que permite que outro módulo leia o conteúdo de uma árvore XML.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="13d71-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13d71-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13d71-118">See Also</span></span>  
 [<span data-ttu-id="13d71-119">Guia de programação (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13d71-119">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
