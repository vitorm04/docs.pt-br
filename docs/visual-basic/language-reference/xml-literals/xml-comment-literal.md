---
title: "Literal de comentário XML (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralComment
dev_langs:
- VB
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
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
ms.openlocfilehash: ab896399b664c658710c24d9799218ff3d81aecc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="4ce3e-102">Literal de comentário XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ce3e-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="4ce3e-103">Um literal que representa um <xref:System.Xml.Linq.XComment>objeto.</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="4ce3e-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ce3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ce3e-104">Syntax</span></span>  
  
```  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="4ce3e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="4ce3e-105">Parts</span></span>  
  
|<span data-ttu-id="4ce3e-106">Termo</span><span class="sxs-lookup"><span data-stu-id="4ce3e-106">Term</span></span>|<span data-ttu-id="4ce3e-107">Definição</span><span class="sxs-lookup"><span data-stu-id="4ce3e-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="4ce3e-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-108">Required.</span></span> <span data-ttu-id="4ce3e-109">Indica o início do comentário XML.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="4ce3e-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-110">Required.</span></span> <span data-ttu-id="4ce3e-111">Texto a ser exibido no comentário XML.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="4ce3e-112">Não pode conter uma série de dois hifens (-) ou terminar com um hífen adjacente à marca de fechamento.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="4ce3e-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-113">Required.</span></span> <span data-ttu-id="4ce3e-114">Indica o fim do comentário XML.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="4ce3e-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4ce3e-115">Return Value</span></span>  
 <span data-ttu-id="4ce3e-116">Um <xref:System.Xml.Linq.XComment>objeto.</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="4ce3e-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ce3e-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ce3e-117">Remarks</span></span>  
 <span data-ttu-id="4ce3e-118">Literais de comentário XML não contêm o conteúdo do documento; elas contêm informações sobre o documento.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="4ce3e-119">A seção de comentário XML termina com a sequência "-->".</span><span class="sxs-lookup"><span data-stu-id="4ce3e-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="4ce3e-120">Isso implica nos seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="4ce3e-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="4ce3e-121">Você não pode usar uma expressão inserida em um literal de comentário XML porque os delimitadores de expressão inserida são conteúdo válido de comentário XML.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="4ce3e-122">Seções de comentário XML não podem ser aninhadas, porque `content` não pode conter o valor "-->".</span><span class="sxs-lookup"><span data-stu-id="4ce3e-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="4ce3e-123">Você pode atribuir um literal de comentário XML para uma variável, ou você pode incluí-lo em um literal de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ce3e-124">Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="4ce3e-125">Esse recurso permite que você copiar o conteúdo de um documento XML e colá-lo diretamente em um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="4ce3e-125">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="4ce3e-126">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte o literal de comentário XML para uma chamada para o <xref:System.Xml.Linq.XComment.%23ctor%2A>construtor.</xref:System.Xml.Linq.XComment.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="4ce3e-126">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ce3e-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ce3e-127">Example</span></span>  
 <span data-ttu-id="4ce3e-128">O exemplo a seguir cria um comentário XML que contém o texto "Este é um comentário".</span><span class="sxs-lookup"><span data-stu-id="4ce3e-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 <span data-ttu-id="4ce3e-129">[!code-vb[VbXMLSamples n º&9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4ce3e-129">[!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce3e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ce3e-130">See Also</span></span>  
 <span data-ttu-id="4ce3e-131"><xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="4ce3e-131"><xref:System.Xml.Linq.XComment></span></span>   
<span data-ttu-id="4ce3e-132"> [Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="4ce3e-132"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="4ce3e-133"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="4ce3e-133"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="4ce3e-134"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="4ce3e-134"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
