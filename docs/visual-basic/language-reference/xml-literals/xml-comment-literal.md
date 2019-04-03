---
title: Literal de comentário XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 149bbac6d301a9c2f166d05698e3780171126cb3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827270"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="56068-102">Literal de comentário XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56068-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="56068-103">Um valor literal que representa um <xref:System.Xml.Linq.XComment> objeto.</span><span class="sxs-lookup"><span data-stu-id="56068-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56068-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56068-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="56068-105">Partes</span><span class="sxs-lookup"><span data-stu-id="56068-105">Parts</span></span>  
  
|<span data-ttu-id="56068-106">Termo</span><span class="sxs-lookup"><span data-stu-id="56068-106">Term</span></span>|<span data-ttu-id="56068-107">Definição</span><span class="sxs-lookup"><span data-stu-id="56068-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="56068-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="56068-108">Required.</span></span> <span data-ttu-id="56068-109">Indica o início do comentário XML.</span><span class="sxs-lookup"><span data-stu-id="56068-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="56068-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="56068-110">Required.</span></span> <span data-ttu-id="56068-111">Texto a ser exibido no comentário XML.</span><span class="sxs-lookup"><span data-stu-id="56068-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="56068-112">Não pode conter uma série de dois hífens (-) ou terminar com um hífen adjacente à marca de fechamento.</span><span class="sxs-lookup"><span data-stu-id="56068-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="56068-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="56068-113">Required.</span></span> <span data-ttu-id="56068-114">Indica o fim do comentário XML.</span><span class="sxs-lookup"><span data-stu-id="56068-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="56068-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="56068-115">Return Value</span></span>  
 <span data-ttu-id="56068-116">Um objeto <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="56068-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56068-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="56068-117">Remarks</span></span>  
 <span data-ttu-id="56068-118">Literais de comentário XML não contêm conteúdo do documento; eles contêm informações sobre o documento.</span><span class="sxs-lookup"><span data-stu-id="56068-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="56068-119">A seção de comentário XML termina com a sequência "-->".</span><span class="sxs-lookup"><span data-stu-id="56068-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="56068-120">Isso significa que os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="56068-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="56068-121">Você não pode usar uma expressão inserida em um literal de comentário XML porque os delimitadores de expressão incorporada são conteúdo válido de comentário XML.</span><span class="sxs-lookup"><span data-stu-id="56068-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="56068-122">Seções de comentário XML não podem ser aninhadas, porque `content` não pode conter o valor "-->".</span><span class="sxs-lookup"><span data-stu-id="56068-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="56068-123">Você pode atribuir um literal de comentário XML para uma variável, ou você pode incluí-lo em um elemento XML literal.</span><span class="sxs-lookup"><span data-stu-id="56068-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56068-124">Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="56068-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="56068-125">Esse recurso permite que você copie o conteúdo de um documento XML e colá-lo diretamente em um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="56068-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="56068-126">O compilador do Visual Basic converte o literal de comentário XML em uma chamada para o <xref:System.Xml.Linq.XComment.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="56068-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56068-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56068-127">Example</span></span>  
 <span data-ttu-id="56068-128">O exemplo a seguir cria um comentário XML que contém o texto "Este é um comentário".</span><span class="sxs-lookup"><span data-stu-id="56068-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="56068-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56068-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="56068-130">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="56068-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="56068-131">Literais XML</span><span class="sxs-lookup"><span data-stu-id="56068-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="56068-132">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56068-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
