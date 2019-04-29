---
title: Literal CDATA XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: ee269ca5cf9635fec35165d1ea65d6a6483cadef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938615"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="dc584-102">Literal CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc584-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="dc584-103">Um valor literal que representa um <xref:System.Xml.Linq.XCData> objeto.</span><span class="sxs-lookup"><span data-stu-id="dc584-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc584-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc584-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="dc584-105">Partes</span><span class="sxs-lookup"><span data-stu-id="dc584-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="dc584-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="dc584-106">Required.</span></span> <span data-ttu-id="dc584-107">Indica o início da seção CDATA do XML.</span><span class="sxs-lookup"><span data-stu-id="dc584-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="dc584-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="dc584-108">Required.</span></span> <span data-ttu-id="dc584-109">Conteúdo do texto seja exibido na seção CDATA do XML.</span><span class="sxs-lookup"><span data-stu-id="dc584-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="dc584-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="dc584-110">Required.</span></span> <span data-ttu-id="dc584-111">Indica o fim da seção.</span><span class="sxs-lookup"><span data-stu-id="dc584-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc584-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dc584-112">Return Value</span></span>  
 <span data-ttu-id="dc584-113">Um objeto <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="dc584-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc584-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc584-114">Remarks</span></span>  
 <span data-ttu-id="dc584-115">As seções CDATA XML contêm o texto não processado que deve ser incluído, mas não analisado com o XML que o contém.</span><span class="sxs-lookup"><span data-stu-id="dc584-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="dc584-116">Uma seção CDATA XML pode conter qualquer texto.</span><span class="sxs-lookup"><span data-stu-id="dc584-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="dc584-117">Isso inclui caracteres XML reservados.</span><span class="sxs-lookup"><span data-stu-id="dc584-117">This includes reserved XML characters.</span></span> <span data-ttu-id="dc584-118">A seção CDATA XML termina com a sequência "]] >".</span><span class="sxs-lookup"><span data-stu-id="dc584-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="dc584-119">Isso significa que os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="dc584-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="dc584-120">Você não pode usar uma expressão inserida em um literal XML CDATA porque os delimitadores de expressão incorporada são conteúdo XML CDATA válido.</span><span class="sxs-lookup"><span data-stu-id="dc584-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="dc584-121">As seções CDATA XML não podem ser aninhadas, porque `content` não pode conter o valor "]] >".</span><span class="sxs-lookup"><span data-stu-id="dc584-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="dc584-122">Você pode atribuir um literal XML CDATA a uma variável ou incluí-lo em um elemento XML literal.</span><span class="sxs-lookup"><span data-stu-id="dc584-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc584-123">Um literal XML pode abranger várias linhas, mas não usa caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="dc584-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="dc584-124">Isso permite que você copie o conteúdo de um documento XML e colá-lo diretamente em um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dc584-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="dc584-125">O compilador do Visual Basic converte o literal XML CDATA em uma chamada para o <xref:System.Xml.Linq.XCData.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="dc584-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc584-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc584-126">Example</span></span>  
 <span data-ttu-id="dc584-127">O exemplo a seguir cria uma seção CDATA que contém o texto "pode conter literal \<XML > marcas".</span><span class="sxs-lookup"><span data-stu-id="dc584-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="dc584-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc584-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="dc584-129">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="dc584-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="dc584-130">Literais XML</span><span class="sxs-lookup"><span data-stu-id="dc584-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="dc584-131">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc584-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
