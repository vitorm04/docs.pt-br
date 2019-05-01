---
title: Espaço em branco em literais XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 08be345557d10a528aa03234883eba1b3a31beaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054933"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="7ce0f-102">Espaço em branco em literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ce0f-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="7ce0f-103">O compilador do Visual Basic incorpora somente os caracteres de espaço em branco significativo de um literal XML quando ele cria um [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="7ce0f-104">Os caracteres de espaço em branco insignificante não são incorporados.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="7ce0f-105">Espaço em branco significativo e irrisória</span><span class="sxs-lookup"><span data-stu-id="7ce0f-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="7ce0f-106">Caracteres de espaço em branco em literais XML são significativos em apenas três áreas:</span><span class="sxs-lookup"><span data-stu-id="7ce0f-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="7ce0f-107">Quando eles estão em um valor de atributo.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-107">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="7ce0f-108">Quando eles fazem parte de um elemento conteúdo de texto e o texto também contiver outros caracteres.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="7ce0f-109">Quando eles estão em uma expressão inserida para o conteúdo de texto de um elemento.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="7ce0f-110">Caso contrário, o compilador trata caracteres de espaço em branco como insignificante e não inclui, em seguida, no [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto para o literal.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="7ce0f-111">Para incluir espaço em branco insignificante em um literal XML, use uma expressão inserida que contém uma cadeia de caracteres literal com o espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ce0f-112">Se o `xml:space` atributo é exibido em um elemento XML literal, o compilador do Visual Basic inclui o atributo no <xref:System.Xml.Linq.XElement> objeto, mas adicionando esse atributo não altera como o compilador trata espaços em branco.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7ce0f-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7ce0f-113">Examples</span></span>  
 <span data-ttu-id="7ce0f-114">O exemplo a seguir contém dois elementos XML, externos e internos.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="7ce0f-115">Ambos os elementos de contenham espaço em branco em seu conteúdo de texto.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="7ce0f-116">O espaço em branco no elemento externo é insignificante, porque ele contém apenas espaços em branco e um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="7ce0f-117">O espaço em branco no elemento interno é significativo porque ele contém espaço em branco e texto.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="7ce0f-118">Quando executado, esse código exibe o texto a seguir.</span><span class="sxs-lookup"><span data-stu-id="7ce0f-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ce0f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ce0f-119">See also</span></span>

- [<span data-ttu-id="7ce0f-120">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ce0f-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
