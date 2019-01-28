---
title: Serializando árvores XML (C#)
ms.date: 07/20/2015
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
ms.openlocfilehash: a1c39c4c85cbd01fa7c3f3f99f2dfae49e3721d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583438"
---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="6ea0b-102">Serializando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6ea0b-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="6ea0b-103">Serializar uma árvore XML significa gerar o XML a partir da árvore XML.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="6ea0b-104">Você pode fazer a serialização para um arquivo, para uma implementação concreta da classe <xref:System.IO.TextWriter> ou a uma implementação concreta de um <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="6ea0b-105">Você pode controlar vários aspectos da serialização.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="6ea0b-106">Por exemplo, você pode determinar se recuará o XML serializado e se gravará uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ea0b-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6ea0b-107">In This Section</span></span>  
  
|<span data-ttu-id="6ea0b-108">Tópico</span><span class="sxs-lookup"><span data-stu-id="6ea0b-108">Topic</span></span>|<span data-ttu-id="6ea0b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ea0b-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6ea0b-110">Preservar espaço em branco para serializar</span><span class="sxs-lookup"><span data-stu-id="6ea0b-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="6ea0b-111">Descreve como controlar o comportamento de espaço em branco durante a serialização das árvores XML.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="6ea0b-112">Serializando com uma declaração XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6ea0b-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="6ea0b-113">Descreve como serializar uma árvore XML que inclua uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="6ea0b-114">Serializando arquivos, o TextWriters, e o XmlWriters</span><span class="sxs-lookup"><span data-stu-id="6ea0b-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="6ea0b-115">Descreve como serializar um documento para um <xref:System.IO.File>, um <xref:System.IO.TextWriter> ou um <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="6ea0b-116">Serializando para um XmlReader (invocando XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="6ea0b-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="6ea0b-117">Descreve como criar um <xref:System.Xml.XmlReader> que permita que outro módulo leia o conteúdo de uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ea0b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ea0b-118">See also</span></span>

- [<span data-ttu-id="6ea0b-119">Guia de Programação (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6ea0b-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
