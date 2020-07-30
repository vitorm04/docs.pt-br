---
title: Preservar espaço em branco ao serializar3
description: Saiba como controlar o espaço em branco ao serializar uma árvore XML usando métodos nas classes XElement e XDocument.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 01e68671e2fde1a2b5b1d0bc429841077ba0205f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303407"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="1d0d7-103">Preservar espaço em branco para serializar</span><span class="sxs-lookup"><span data-stu-id="1d0d7-103">Preserving White Space While Serializing</span></span>
<span data-ttu-id="1d0d7-104">Este tópico descreve como controlar o espaço em branco para serializar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-104">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="1d0d7-105">Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-105">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="1d0d7-106">Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="1d0d7-107">Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d0d7-107">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="1d0d7-108">Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="1d0d7-109">Você pode não querer modificar este recuo de nenhuma forma.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="1d0d7-110">Para fazer isso em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você preserva o espaço em branco quando você carregar ou analisar XML e desativa o formatação quando você serializa XML.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-110">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="1d0d7-111">Comportamento de espaço em branco de métodos que serializam árvores XML</span><span class="sxs-lookup"><span data-stu-id="1d0d7-111">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="1d0d7-112">Os seguintes métodos nas classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XDocument> serialize uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-112">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="1d0d7-113">Você pode serializar uma árvore XML para um arquivo, um <xref:System.IO.TextReader>, ou um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-113">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="1d0d7-114">O método de `ToString` serializa a uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-114">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="1d0d7-115">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="1d0d7-115">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="1d0d7-116">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="1d0d7-116">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="1d0d7-117">Se o método não utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, o método irá formatar (corte XML serializável.)</span><span class="sxs-lookup"><span data-stu-id="1d0d7-117">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="1d0d7-118">Nesse caso, qualquer espaço em branco irrisória na árvore XML é descartado.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-118">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="1d0d7-119">Se o método utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, então você pode especificar que o formato de método não (corte XML serializável.)</span><span class="sxs-lookup"><span data-stu-id="1d0d7-119">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="1d0d7-120">Nesse caso, qualquer espaço em branco na árvore XML é preservada.</span><span class="sxs-lookup"><span data-stu-id="1d0d7-120">In this case, all white space in the XML tree is preserved.</span></span>  
