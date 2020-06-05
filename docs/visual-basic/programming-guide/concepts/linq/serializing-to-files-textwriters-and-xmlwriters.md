---
title: Serializando para arquivos, textwriters e XmlWriters3
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: d8b929ef02b8fd9c6a9f29ea997a754699a6e1c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403557"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="3b045-102">Serializando arquivos, o TextWriters, e o XmlWriters</span><span class="sxs-lookup"><span data-stu-id="3b045-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="3b045-103">Você pode serializar árvores XML a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, ou a <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="3b045-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="3b045-104">Você pode serializar qualquer componente XML, incluindo <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement>, uma cadeia de caracteres usando o método `ToString` .</span><span class="sxs-lookup"><span data-stu-id="3b045-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="3b045-105">Se você desejar suprimir formatação ao serializar a uma cadeia de caracteres, você pode usar o método de <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3b045-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="3b045-106">O comportamento padrão ao serializar para um arquivo é formatar (recuar) o documento XML resultante.</span><span class="sxs-lookup"><span data-stu-id="3b045-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="3b045-107">Quando você identar, o espaço em branco irrisória na árvore XML não é preservada.</span><span class="sxs-lookup"><span data-stu-id="3b045-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="3b045-108">Para serializar com formatação, use uma das sobrecargas dos seguintes métodos que não têm <xref:System.Xml.Linq.SaveOptions> como um argumento:</span><span class="sxs-lookup"><span data-stu-id="3b045-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="3b045-109">Se você desejar que a opção não recuar e não preservar espaço em branco irrisória na árvore XML, use uma das sobrecargas dos seguintes métodos que leva <xref:System.Xml.Linq.SaveOptions> como um argumento:</span><span class="sxs-lookup"><span data-stu-id="3b045-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="3b045-110">Para exemplos, consulte o tópico de referência apropriado.</span><span class="sxs-lookup"><span data-stu-id="3b045-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b045-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="3b045-111">See also</span></span>

- [<span data-ttu-id="3b045-112">Serializando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b045-112">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
