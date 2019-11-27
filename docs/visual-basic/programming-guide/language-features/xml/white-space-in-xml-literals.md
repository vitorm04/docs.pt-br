---
title: Espaço em branco em literais XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 56ededeb12d07e979bc86b03924e1ae0f0432822
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336002"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="d3529-102">Espaço em branco em literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3529-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="d3529-103">O compilador Visual Basic incorpora apenas os caracteres de espaço em branco significativos de um literal XML quando ele cria um objeto [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3529-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="d3529-104">Os caracteres de espaço em branco insignificantes não são incorporados.</span><span class="sxs-lookup"><span data-stu-id="d3529-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="d3529-105">Espaço em branco significativo e insignificante</span><span class="sxs-lookup"><span data-stu-id="d3529-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="d3529-106">Os caracteres de espaço em branco em literais XML são significativos em apenas três áreas:</span><span class="sxs-lookup"><span data-stu-id="d3529-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="d3529-107">Quando estão em um valor de atributo.</span><span class="sxs-lookup"><span data-stu-id="d3529-107">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="d3529-108">Quando eles fazem parte do conteúdo de texto de um elemento e o texto também contém outros caracteres.</span><span class="sxs-lookup"><span data-stu-id="d3529-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="d3529-109">Quando estão em uma expressão inserida para o conteúdo de texto de um elemento.</span><span class="sxs-lookup"><span data-stu-id="d3529-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="d3529-110">Caso contrário, o compilador trata caracteres de espaço em branco como insignificantes e não inclui, em seguida, no objeto [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] para o literal.</span><span class="sxs-lookup"><span data-stu-id="d3529-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="d3529-111">Para incluir um espaço em branco insignificante em um literal XML, use uma expressão inserida que contenha um literal de cadeia de caracteres com o espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="d3529-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3529-112">Se o atributo `xml:space` aparecer em um literal de elemento XML, o compilador Visual Basic incluirá o atributo no objeto <xref:System.Xml.Linq.XElement>, mas a adição desse atributo não alterará a forma como o compilador trata o espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="d3529-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d3529-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d3529-113">Examples</span></span>  
 <span data-ttu-id="d3529-114">O exemplo a seguir contém dois elementos XML, externo e interno.</span><span class="sxs-lookup"><span data-stu-id="d3529-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="d3529-115">Ambos os elementos contêm espaço em branco em seu conteúdo de texto.</span><span class="sxs-lookup"><span data-stu-id="d3529-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="d3529-116">O espaço em branco no elemento externo é insignificante porque contém apenas espaços em branco e um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="d3529-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="d3529-117">O espaço em branco no elemento interno é significativo porque contém espaço em branco e texto.</span><span class="sxs-lookup"><span data-stu-id="d3529-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="d3529-118">Quando executado, esse código exibe o texto a seguir.</span><span class="sxs-lookup"><span data-stu-id="d3529-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3529-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3529-119">See also</span></span>

- [<span data-ttu-id="d3529-120">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3529-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
