---
title: "Preservar espaço em branco ao carregar ou analisar XML2 | Documentos do Microsoft"
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
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
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
ms.openlocfilehash: a2872c1e2354c0a0bd106f7fb945542ce37e7774
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="db6cb-102">Preservar espaço em branco para carregar ou ao analisar XML</span><span class="sxs-lookup"><span data-stu-id="db6cb-102">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="db6cb-103">Este tópico descreve como controlar o comportamento de espaço em branco de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="db6cb-103">This topic describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="db6cb-104">Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo.</span><span class="sxs-lookup"><span data-stu-id="db6cb-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="db6cb-105">Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados.</span><span class="sxs-lookup"><span data-stu-id="db6cb-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="db6cb-106">Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="db6cb-106">This is the default behavior for [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="db6cb-107">Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="db6cb-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="db6cb-108">Você pode não querer modificar este recuo de nenhuma forma.</span><span class="sxs-lookup"><span data-stu-id="db6cb-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="db6cb-109">Para fazer isso em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você preserva o espaço em branco quando você carregar ou analisar XML e desativa o formatação quando você serializa XML.</span><span class="sxs-lookup"><span data-stu-id="db6cb-109">To do this in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="db6cb-110">Este tópico descreve o comportamento de espaço em branco dos métodos que preenchem árvores XML.</span><span class="sxs-lookup"><span data-stu-id="db6cb-110">This topic describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="db6cb-111">Para obter informações sobre como controlar o espaço em branco quando você serializa árvores XML, consulte [preservar espaço em branco ao serializar](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="db6cb-111">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="db6cb-112">Comportamento dos métodos que preenchem árvores XML</span><span class="sxs-lookup"><span data-stu-id="db6cb-112">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="db6cb-113">Os seguintes métodos na <xref:System.Xml.Linq.XElement>e <xref:System.Xml.Linq.XDocument>classes preencher uma árvore XML.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="db6cb-113">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="db6cb-114">Você pode preencher uma árvore XML de um arquivo, um <xref:System.IO.TextReader>, um <xref:System.Xml.XmlReader>, ou uma cadeia de caracteres:</xref:System.Xml.XmlReader> </xref:System.IO.TextReader></span><span class="sxs-lookup"><span data-stu-id="db6cb-114">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
-   <span data-ttu-id="db6cb-115"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="db6cb-115"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="db6cb-116"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="db6cb-116"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="db6cb-117"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="db6cb-117"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="db6cb-118"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="db6cb-118"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="db6cb-119">Se o método não utiliza <xref:System.Xml.Linq.LoadOptions>como um argumento, o método não irá preservar espaço em branco insignificante.</xref:System.Xml.Linq.LoadOptions></span><span class="sxs-lookup"><span data-stu-id="db6cb-119">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="db6cb-120">Na maioria dos casos, se o método usa <xref:System.Xml.Linq.LoadOptions>como um argumento, você pode opcionalmente preservar espaço em branco irrisória como nós de texto na árvore XML.</xref:System.Xml.Linq.LoadOptions></span><span class="sxs-lookup"><span data-stu-id="db6cb-120">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="db6cb-121">No entanto, se o método é carregar XML de um <xref:System.Xml.XmlReader>, o <xref:System.Xml.XmlReader>determina se o espaço em branco será preservado ou não.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="db6cb-121">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="db6cb-122">Definindo <xref:System.Xml.Linq.LoadOptions>não terá efeito.</xref:System.Xml.Linq.LoadOptions></span><span class="sxs-lookup"><span data-stu-id="db6cb-122">Setting <xref:System.Xml.Linq.LoadOptions> will have no effect.</span></span>  
  
 <span data-ttu-id="db6cb-123">Com esses métodos, se o espaço em branco é preservado, espaço em branco irrisória é inserido na árvore XML como <xref:System.Xml.Linq.XText>nós.</xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="db6cb-123">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="db6cb-124">Se o espaço em branco não é preservada, os nós de texto não são inseridos.</span><span class="sxs-lookup"><span data-stu-id="db6cb-124">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="db6cb-125">Você pode criar uma árvore XML usando <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="db6cb-125">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="db6cb-126">Nós que são gravados para o <xref:System.Xml.XmlWriter>são preenchidos na árvore.</xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="db6cb-126">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="db6cb-127">No entanto, quando você cria uma árvore XML usando esse método, todos os nós são mantidos, independentemente se o nó é o espaço em branco ou não, ou se o espaço em branco é significativo ou não.</span><span class="sxs-lookup"><span data-stu-id="db6cb-127">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6cb-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db6cb-128">See Also</span></span>  
 [<span data-ttu-id="db6cb-129">Análise de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db6cb-129">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
