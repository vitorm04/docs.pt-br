---
title: Preservar espaço em branco ao serializar3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 7fd0a38d2a9ed8c4712b8e9a03a24a23b408f38a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45624295"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="25710-102">Preservar espaço em branco para serializar</span><span class="sxs-lookup"><span data-stu-id="25710-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="25710-103">Este tópico descreve como controlar o espaço em branco para serializar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="25710-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="25710-104">Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo.</span><span class="sxs-lookup"><span data-stu-id="25710-104">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="25710-105">Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados.</span><span class="sxs-lookup"><span data-stu-id="25710-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="25710-106">Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25710-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="25710-107">Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="25710-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="25710-108">Você pode não querer modificar este recuo de nenhuma forma.</span><span class="sxs-lookup"><span data-stu-id="25710-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="25710-109">Para fazer isso em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você preserva o espaço em branco quando você carregar ou analisar XML e desativa o formatação quando você serializa XML.</span><span class="sxs-lookup"><span data-stu-id="25710-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="25710-110">Comportamento de espaço em branco de métodos que serializam árvores XML</span><span class="sxs-lookup"><span data-stu-id="25710-110">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="25710-111">Os seguintes métodos nas classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XDocument> serialize uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="25710-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="25710-112">Você pode serializar uma árvore XML para um arquivo, um <xref:System.IO.TextReader>, ou um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="25710-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="25710-113">O método de `ToString` serializa a uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="25710-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="25710-114">Se o método não utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, o método irá formatar (corte XML serializável.)</span><span class="sxs-lookup"><span data-stu-id="25710-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="25710-115">Nesse caso, qualquer espaço em branco irrisória na árvore XML é descartado.</span><span class="sxs-lookup"><span data-stu-id="25710-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="25710-116">Se o método utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, então você pode especificar que o formato de método não (corte XML serializável.)</span><span class="sxs-lookup"><span data-stu-id="25710-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="25710-117">Nesse caso, qualquer espaço em branco na árvore XML é preservada.</span><span class="sxs-lookup"><span data-stu-id="25710-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25710-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25710-118">See Also</span></span>

- [<span data-ttu-id="25710-119">Serializando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="25710-119">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
