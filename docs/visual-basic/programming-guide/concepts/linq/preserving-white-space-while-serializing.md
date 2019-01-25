---
title: Preservar o espaço em branco ao Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: cbfa9a39c52a40831627429f7ffc9971e0074a50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602033"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="d56b8-102">Preservar espaço em branco para serializar</span><span class="sxs-lookup"><span data-stu-id="d56b8-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="d56b8-103">Este tópico descreve como controlar o espaço em branco para serializar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="d56b8-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="d56b8-104">Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo.</span><span class="sxs-lookup"><span data-stu-id="d56b8-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="d56b8-105">Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados.</span><span class="sxs-lookup"><span data-stu-id="d56b8-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="d56b8-106">Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d56b8-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="d56b8-107">Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="d56b8-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="d56b8-108">Você pode não querer modificar este recuo de nenhuma forma.</span><span class="sxs-lookup"><span data-stu-id="d56b8-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="d56b8-109">Para fazer isso em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você preserva o espaço em branco quando você carregar ou analisar XML e desativa o formatação quando você serializa XML.</span><span class="sxs-lookup"><span data-stu-id="d56b8-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="d56b8-110">Comportamento de espaço em branco de métodos que serialize árvores XML</span><span class="sxs-lookup"><span data-stu-id="d56b8-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="d56b8-111">Os seguintes métodos nas classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XDocument> serialize uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="d56b8-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="d56b8-112">Você pode serializar uma árvore XML para um arquivo, um <xref:System.IO.TextReader>, ou um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d56b8-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d56b8-113">O método de `ToString` serializa a uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d56b8-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d56b8-114">Se o método não utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, o método irá formatar (corte XML serializável.)</span><span class="sxs-lookup"><span data-stu-id="d56b8-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="d56b8-115">Nesse caso, qualquer espaço em branco irrisória na árvore XML é descartado.</span><span class="sxs-lookup"><span data-stu-id="d56b8-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="d56b8-116">Se o método utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, então você pode especificar que o formato de método não (corte XML serializável.)</span><span class="sxs-lookup"><span data-stu-id="d56b8-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="d56b8-117">Nesse caso, qualquer espaço em branco na árvore XML é preservada.</span><span class="sxs-lookup"><span data-stu-id="d56b8-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56b8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d56b8-118">See also</span></span>
- [<span data-ttu-id="d56b8-119">Serializando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d56b8-119">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
