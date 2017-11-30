---
title: Literal CDATA XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 906fd2494dd952c08088b9b7e38dba4505780481
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="347a9-102">Literal CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="347a9-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="347a9-103">Um valor literal que representa um <xref:System.Xml.Linq.XCData> objeto.</span><span class="sxs-lookup"><span data-stu-id="347a9-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="347a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="347a9-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="347a9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="347a9-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="347a9-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="347a9-106">Required.</span></span> <span data-ttu-id="347a9-107">Indica o início da seção CDATA do XML.</span><span class="sxs-lookup"><span data-stu-id="347a9-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="347a9-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="347a9-108">Required.</span></span> <span data-ttu-id="347a9-109">Conteúdo de texto seja exibido na seção CDATA do XML.</span><span class="sxs-lookup"><span data-stu-id="347a9-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="347a9-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="347a9-110">Required.</span></span> <span data-ttu-id="347a9-111">Indica o fim da seção.</span><span class="sxs-lookup"><span data-stu-id="347a9-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="347a9-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="347a9-112">Return Value</span></span>  
 <span data-ttu-id="347a9-113">Um objeto <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="347a9-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="347a9-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="347a9-114">Remarks</span></span>  
 <span data-ttu-id="347a9-115">Seções XML CDATA contêm texto não processado que deve ser incluído, mas não analisado, com o XML que o contém.</span><span class="sxs-lookup"><span data-stu-id="347a9-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="347a9-116">Uma seção CDATA XML pode conter qualquer texto.</span><span class="sxs-lookup"><span data-stu-id="347a9-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="347a9-117">Isso inclui caracteres XML reservados.</span><span class="sxs-lookup"><span data-stu-id="347a9-117">This includes reserved XML characters.</span></span> <span data-ttu-id="347a9-118">Seção XML CDATA termina com a sequência "]] >".</span><span class="sxs-lookup"><span data-stu-id="347a9-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="347a9-119">Isso implica que os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="347a9-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="347a9-120">Você não pode usar uma expressão inserida em um literal XML CDATA porque os delimitadores de expressão inserida são conteúdo XML CDATA válido.</span><span class="sxs-lookup"><span data-stu-id="347a9-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="347a9-121">Seções XML CDATA não podem ser aninhadas, porque `content` não pode conter o valor "]] >".</span><span class="sxs-lookup"><span data-stu-id="347a9-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="347a9-122">Você pode atribuir um literal XML CDATA a uma variável ou incluí-lo em um literal de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="347a9-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="347a9-123">Um literal XML pode abranger várias linhas, mas não usa caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="347a9-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="347a9-124">Isso permite que você copiar o conteúdo de um documento XML e cole-o diretamente em um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="347a9-124">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="347a9-125">O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte o literal XML CDATA para uma chamada para o <xref:System.Xml.Linq.XCData.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="347a9-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="347a9-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="347a9-126">Example</span></span>  
 <span data-ttu-id="347a9-127">O exemplo a seguir cria uma seção CDATA que contém o texto "pode conter literal \<XML > marcas".</span><span class="sxs-lookup"><span data-stu-id="347a9-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="347a9-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="347a9-128">See Also</span></span>  
 <xref:System.Xml.Linq.XCData>  
 [<span data-ttu-id="347a9-129">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="347a9-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="347a9-130">Literais XML</span><span class="sxs-lookup"><span data-stu-id="347a9-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="347a9-131">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="347a9-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
