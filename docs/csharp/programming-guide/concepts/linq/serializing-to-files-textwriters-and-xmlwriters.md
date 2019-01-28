---
title: Serializando arquivos, o TextWriters e o XmlWriters1
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 19371c0422c607171ccbea1235ea4348852d801c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498811"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="b7378-102">Serializando arquivos, o TextWriters, e o XmlWriters</span><span class="sxs-lookup"><span data-stu-id="b7378-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="b7378-103">Você pode serializar árvores XML a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, ou a <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b7378-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="b7378-104">Você pode serializar qualquer componente XML, incluindo <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement>, uma cadeia de caracteres usando o método `ToString` .</span><span class="sxs-lookup"><span data-stu-id="b7378-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="b7378-105">Se você desejar suprimir formatação ao serializar a uma cadeia de caracteres, você pode usar o método de <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b7378-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b7378-106">O comportamento padrão ao serializar para um arquivo é formatar (recuar) o documento XML resultante.</span><span class="sxs-lookup"><span data-stu-id="b7378-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="b7378-107">Quando você identar, o espaço em branco irrisória na árvore XML não é preservada.</span><span class="sxs-lookup"><span data-stu-id="b7378-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="b7378-108">Para serializar com formatação, use uma das sobrecargas dos seguintes métodos que não têm <xref:System.Xml.Linq.SaveOptions> como um argumento:</span><span class="sxs-lookup"><span data-stu-id="b7378-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="b7378-109">Se você desejar que a opção não recuar e não preservar espaço em branco irrisória na árvore XML, use uma das sobrecargas dos seguintes métodos que leva <xref:System.Xml.Linq.SaveOptions> como um argumento:</span><span class="sxs-lookup"><span data-stu-id="b7378-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="b7378-110">Para exemplos, consulte o tópico de referência apropriado.</span><span class="sxs-lookup"><span data-stu-id="b7378-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7378-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7378-111">See also</span></span>

- [<span data-ttu-id="b7378-112">Serializando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b7378-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
