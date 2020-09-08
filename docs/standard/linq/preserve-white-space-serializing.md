---
title: Preservar espaço em branco ao serializar-LINQ to XML
description: Você pode controlar o espaço em branco de várias maneiras ao serializar uma árvore XML.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d907e68a2df3905794b555954330f31b5e75655
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551903"
---
# <a name="preserve-white-space-while-serializing-linq-to-xml"></a><span data-ttu-id="325f5-103">Preservar espaço em branco ao serializar (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="325f5-103">Preserve white space while serializing (LINQ to XML)</span></span>

<span data-ttu-id="325f5-104">Este artigo descreve como controlar o espaço em branco ao serializar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="325f5-104">This article describes how to control white space when serializing an XML tree.</span></span>

<span data-ttu-id="325f5-105">Um cenário comum é ler XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (ou seja, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo.</span><span class="sxs-lookup"><span data-stu-id="325f5-105">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="325f5-106">Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados.</span><span class="sxs-lookup"><span data-stu-id="325f5-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="325f5-107">Esse é o comportamento padrão para LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="325f5-107">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="325f5-108">Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="325f5-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="325f5-109">Você pode não querer modificar este recuo de nenhuma forma.</span><span class="sxs-lookup"><span data-stu-id="325f5-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="325f5-110">Para fazer isso no LINQ to XML, você preserva o espaço em branco quando carrega ou analisa o XML e desabilita a formatação ao serializar o XML.</span><span class="sxs-lookup"><span data-stu-id="325f5-110">To do this in LINQ to XML, you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>

## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="325f5-111">Comportamento de espaço em branco de métodos que serializam árvores XML</span><span class="sxs-lookup"><span data-stu-id="325f5-111">White-space behavior of methods that serialize XML trees</span></span>

<span data-ttu-id="325f5-112">Os seguintes métodos nas classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XDocument> serialize uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="325f5-112">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="325f5-113">Você pode serializar uma árvore XML para um arquivo, um <xref:System.IO.TextReader>, ou um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="325f5-113">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="325f5-114">O método de `ToString` serializa a uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="325f5-114">The `ToString` method serializes to a string.</span></span>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- [<span data-ttu-id="325f5-115">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="325f5-115">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
- [<span data-ttu-id="325f5-116">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="325f5-116">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)

<span data-ttu-id="325f5-117">Se o método não usar <xref:System.Xml.Linq.SaveOptions> como um argumento, o método formatará (recuará) o XML serializado.</span><span class="sxs-lookup"><span data-stu-id="325f5-117">If the method doesn't take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="325f5-118">Nesse caso, qualquer espaço em branco irrisória na árvore XML é descartado.</span><span class="sxs-lookup"><span data-stu-id="325f5-118">In this case, all insignificant white space in the XML tree is discarded.</span></span>

<span data-ttu-id="325f5-119">Se o método utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, então você pode especificar que o formato de método não (corte XML serializável.)</span><span class="sxs-lookup"><span data-stu-id="325f5-119">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="325f5-120">Nesse caso, qualquer espaço em branco na árvore XML é preservada.</span><span class="sxs-lookup"><span data-stu-id="325f5-120">In this case, all white space in the XML tree is preserved.</span></span>
