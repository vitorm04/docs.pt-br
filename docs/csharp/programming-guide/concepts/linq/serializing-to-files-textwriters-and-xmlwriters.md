---
title: Serializando arquivos, o TextWriters, e o XmlWriters
description: Saiba mais sobre as opções para serializar árvores XML para um arquivo, um TextWriter ou um XmlWriter em C# usando os métodos ToString ou Save.
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 43c51ae7e9bf1a7848d45fd900424d6186671e53
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302380"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="2404e-103">Serializando arquivos, o TextWriters, e o XmlWriters</span><span class="sxs-lookup"><span data-stu-id="2404e-103">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="2404e-104">Você pode serializar árvores XML a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, ou a <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="2404e-104">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="2404e-105">Você pode serializar qualquer componente XML, incluindo <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement>, uma cadeia de caracteres usando o método `ToString` .</span><span class="sxs-lookup"><span data-stu-id="2404e-105">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="2404e-106">Se você desejar suprimir formatação ao serializar a uma cadeia de caracteres, você pode usar o método de <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2404e-106">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2404e-107">O comportamento padrão ao serializar para um arquivo é formatar (recuar) o documento XML resultante.</span><span class="sxs-lookup"><span data-stu-id="2404e-107">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="2404e-108">Quando você identar, o espaço em branco irrisória na árvore XML não é preservada.</span><span class="sxs-lookup"><span data-stu-id="2404e-108">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="2404e-109">Para serializar com formatação, use uma das sobrecargas dos seguintes métodos que não têm <xref:System.Xml.Linq.SaveOptions> como um argumento:</span><span class="sxs-lookup"><span data-stu-id="2404e-109">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="2404e-110">Se você desejar que a opção não recuar e não preservar espaço em branco irrisória na árvore XML, use uma das sobrecargas dos seguintes métodos que leva <xref:System.Xml.Linq.SaveOptions> como um argumento:</span><span class="sxs-lookup"><span data-stu-id="2404e-110">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="2404e-111">Para exemplos, consulte o tópico de referência apropriado.</span><span class="sxs-lookup"><span data-stu-id="2404e-111">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="2404e-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="2404e-112">See also</span></span>

- [<span data-ttu-id="2404e-113">Serializando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2404e-113">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
