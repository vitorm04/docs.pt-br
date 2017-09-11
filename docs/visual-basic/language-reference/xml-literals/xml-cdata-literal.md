---
title: Literal CDATA XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
dev_langs:
- VB
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
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
ms.openlocfilehash: 6bf12a5dd5b24b0a915cb15f41cb8947c33e94b0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="1fb35-102">Literal CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fb35-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="1fb35-103">Um literal que representa um <xref:System.Xml.Linq.XCData>objeto.</xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="1fb35-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb35-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1fb35-104">Syntax</span></span>  
  
```  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="1fb35-105">Partes</span><span class="sxs-lookup"><span data-stu-id="1fb35-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="1fb35-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1fb35-106">Required.</span></span> <span data-ttu-id="1fb35-107">Indica o início da seção CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="1fb35-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="1fb35-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1fb35-108">Required.</span></span> <span data-ttu-id="1fb35-109">Conteúdo do texto apareça na seção CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="1fb35-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="1fb35-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1fb35-110">Required.</span></span> <span data-ttu-id="1fb35-111">Indica o fim da seção.</span><span class="sxs-lookup"><span data-stu-id="1fb35-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fb35-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1fb35-112">Return Value</span></span>  
 <span data-ttu-id="1fb35-113">Um <xref:System.Xml.Linq.XCData>objeto.</xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="1fb35-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fb35-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="1fb35-114">Remarks</span></span>  
 <span data-ttu-id="1fb35-115">Seções XML CDATA contêm texto não processado que deve ser incluído, mas não analisado, com o XML que o contém.</span><span class="sxs-lookup"><span data-stu-id="1fb35-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="1fb35-116">Uma seção CDATA XML pode conter qualquer texto.</span><span class="sxs-lookup"><span data-stu-id="1fb35-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="1fb35-117">Isso inclui caracteres XML reservados.</span><span class="sxs-lookup"><span data-stu-id="1fb35-117">This includes reserved XML characters.</span></span> <span data-ttu-id="1fb35-118">Seção XML CDATA termina com a sequência "]] >".</span><span class="sxs-lookup"><span data-stu-id="1fb35-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="1fb35-119">Isso implica nos seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="1fb35-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="1fb35-120">Você não pode usar uma expressão inserida em um literal XML CDATA porque os delimitadores de expressão inserida são conteúdo XML CDATA válido.</span><span class="sxs-lookup"><span data-stu-id="1fb35-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="1fb35-121">Seções XML CDATA não podem ser aninhadas, porque `content` não pode conter o valor "]] >".</span><span class="sxs-lookup"><span data-stu-id="1fb35-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="1fb35-122">Você pode atribuir um literal XML CDATA a uma variável ou incluí-lo em um literal de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="1fb35-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fb35-123">Um literal XML pode abranger várias linhas, mas não usa caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="1fb35-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="1fb35-124">Isso permite que você copiar o conteúdo de um documento XML e colá-lo diretamente em um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="1fb35-124">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="1fb35-125">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte o literal XML CDATA para uma chamada para o <xref:System.Xml.Linq.XCData.%23ctor%2A>construtor.</xref:System.Xml.Linq.XCData.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="1fb35-125">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fb35-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1fb35-126">Example</span></span>  
 <span data-ttu-id="1fb35-127">O exemplo a seguir cria uma seção CDATA que contém o texto "pode conter literal \<XML > marcas".</span><span class="sxs-lookup"><span data-stu-id="1fb35-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 <span data-ttu-id="1fb35-128">[!code-vb[VbXMLSamples&#23;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1fb35-128">[!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb35-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fb35-129">See Also</span></span>  
 <span data-ttu-id="1fb35-130"><xref:System.Xml.Linq.XCData></xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="1fb35-130"><xref:System.Xml.Linq.XCData></span></span>   
<span data-ttu-id="1fb35-131"> [Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="1fb35-131"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="1fb35-132"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="1fb35-132"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="1fb35-133"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="1fb35-133"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
