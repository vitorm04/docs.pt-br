---
title: "Espaço em branco em literais XML (Visual Basic) | Documentos do Microsoft"
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
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4fc3d30a9c71cbd732597c5e3f32bd01eb489a80
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="93275-102">Espaço em branco em literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93275-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="93275-103">O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador incorpora somente os caracteres de espaço em branco significativo de um literal XML quando ele cria uma [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objeto.</span><span class="sxs-lookup"><span data-stu-id="93275-103">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] object.</span></span> <span data-ttu-id="93275-104">Os caracteres de espaço em branco insignificante não são incorporados.</span><span class="sxs-lookup"><span data-stu-id="93275-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="93275-105">Espaço em branco significativo e irrisória</span><span class="sxs-lookup"><span data-stu-id="93275-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="93275-106">Caracteres de espaço em branco em literais XML são significativos apenas três áreas:</span><span class="sxs-lookup"><span data-stu-id="93275-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="93275-107">Quando eles estão em um valor de atributo.</span><span class="sxs-lookup"><span data-stu-id="93275-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="93275-108">Quando eles fazem parte de conteúdo de texto um elemento do e o texto também contém outros caracteres.</span><span class="sxs-lookup"><span data-stu-id="93275-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="93275-109">Quando eles estiverem em uma expressão inserida para o conteúdo de texto de um elemento.</span><span class="sxs-lookup"><span data-stu-id="93275-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="93275-110">Caso contrário, o compilador trata caracteres de espaço em branco como insignificante e não inclui, em seguida, o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objeto para o literal.</span><span class="sxs-lookup"><span data-stu-id="93275-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="93275-111">Para incluir espaço em branco insignificante em um literal XML, use uma expressão incorporada que contém uma cadeia de caracteres literal com o espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="93275-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93275-112">Se o `xml:space` atributo aparece em um elemento XML literal, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador inclui o atributo no <xref:System.Xml.Linq.XElement>objeto, mas adicionar esse atributo não alterar como o compilador trata espaços em branco.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="93275-112">If the `xml:space` attribute appears in an XML element literal, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="93275-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="93275-113">Examples</span></span>  
 <span data-ttu-id="93275-114">O exemplo a seguir contém dois elementos XML, externos e internos.</span><span class="sxs-lookup"><span data-stu-id="93275-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="93275-115">Os dois elementos contêm espaços em branco em seu conteúdo de texto.</span><span class="sxs-lookup"><span data-stu-id="93275-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="93275-116">O espaço em branco no elemento externo é insignificante, porque ele contém somente espaço em branco e um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="93275-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="93275-117">O espaço em branco no elemento interno é significativo porque ele contém espaços em branco e texto.</span><span class="sxs-lookup"><span data-stu-id="93275-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 <span data-ttu-id="93275-118">[!code-vb[29 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="93275-118">[!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]</span></span>  
  
 <span data-ttu-id="93275-119">Quando executado, esse código exibe o texto a seguir.</span><span class="sxs-lookup"><span data-stu-id="93275-119">When run, this code displays the following text.</span></span>  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93275-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93275-120">See Also</span></span>  
 [<span data-ttu-id="93275-121">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93275-121">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
