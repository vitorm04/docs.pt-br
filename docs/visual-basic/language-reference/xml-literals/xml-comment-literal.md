---
title: Literal de comentário XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 8d9db66aabe344bd5c8f9a92ac8618b7bc1abb43
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349395"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="73aaf-102">Literal de comentário XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73aaf-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="73aaf-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span><span class="sxs-lookup"><span data-stu-id="73aaf-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73aaf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73aaf-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="73aaf-105">Partes</span><span class="sxs-lookup"><span data-stu-id="73aaf-105">Parts</span></span>  
  
|<span data-ttu-id="73aaf-106">Termo</span><span class="sxs-lookup"><span data-stu-id="73aaf-106">Term</span></span>|<span data-ttu-id="73aaf-107">Definição</span><span class="sxs-lookup"><span data-stu-id="73aaf-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="73aaf-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="73aaf-108">Required.</span></span> <span data-ttu-id="73aaf-109">Denotes the start of the XML comment.</span><span class="sxs-lookup"><span data-stu-id="73aaf-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="73aaf-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="73aaf-110">Required.</span></span> <span data-ttu-id="73aaf-111">Text to appear in the XML comment.</span><span class="sxs-lookup"><span data-stu-id="73aaf-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="73aaf-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span><span class="sxs-lookup"><span data-stu-id="73aaf-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="73aaf-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="73aaf-113">Required.</span></span> <span data-ttu-id="73aaf-114">Denotes the end of the XML comment.</span><span class="sxs-lookup"><span data-stu-id="73aaf-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="73aaf-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="73aaf-115">Return Value</span></span>  
 <span data-ttu-id="73aaf-116">Um objeto <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="73aaf-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73aaf-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="73aaf-117">Remarks</span></span>  
 <span data-ttu-id="73aaf-118">XML comment literals do not contain document content; they contain information about the document.</span><span class="sxs-lookup"><span data-stu-id="73aaf-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="73aaf-119">The XML comment section ends with the sequence "-->".</span><span class="sxs-lookup"><span data-stu-id="73aaf-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="73aaf-120">This implies the following points:</span><span class="sxs-lookup"><span data-stu-id="73aaf-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="73aaf-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span><span class="sxs-lookup"><span data-stu-id="73aaf-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="73aaf-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span><span class="sxs-lookup"><span data-stu-id="73aaf-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="73aaf-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span><span class="sxs-lookup"><span data-stu-id="73aaf-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73aaf-124">An XML literal can span multiple lines without using line continuation characters.</span><span class="sxs-lookup"><span data-stu-id="73aaf-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="73aaf-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span><span class="sxs-lookup"><span data-stu-id="73aaf-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="73aaf-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span><span class="sxs-lookup"><span data-stu-id="73aaf-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73aaf-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73aaf-127">Example</span></span>  
 <span data-ttu-id="73aaf-128">The following example creates an XML comment that contains the text "This is a comment".</span><span class="sxs-lookup"><span data-stu-id="73aaf-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="73aaf-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73aaf-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="73aaf-130">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="73aaf-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="73aaf-131">Literais XML</span><span class="sxs-lookup"><span data-stu-id="73aaf-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="73aaf-132">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73aaf-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
