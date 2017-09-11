---
title: Literal de documento XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
dev_langs:
- VB
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
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
ms.openlocfilehash: 5e173c8bc89f61925c3e6127fb3cac61379aeffa
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="26f04-102">Literal de documento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f04-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="26f04-103">Um literal que representa um <xref:System.Xml.Linq.XDocument>objeto.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="26f04-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26f04-104">Syntax</span></span>  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="26f04-105">Partes</span><span class="sxs-lookup"><span data-stu-id="26f04-105">Parts</span></span>  
  
|<span data-ttu-id="26f04-106">Termo</span><span class="sxs-lookup"><span data-stu-id="26f04-106">Term</span></span>|<span data-ttu-id="26f04-107">Definição</span><span class="sxs-lookup"><span data-stu-id="26f04-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="26f04-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="26f04-108">Optional.</span></span> <span data-ttu-id="26f04-109">Declarando que o documento usa a codificação de texto literal.</span><span class="sxs-lookup"><span data-stu-id="26f04-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="26f04-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="26f04-110">Optional.</span></span> <span data-ttu-id="26f04-111">Texto literal.</span><span class="sxs-lookup"><span data-stu-id="26f04-111">Literal text.</span></span> <span data-ttu-id="26f04-112">Deve ser "Sim" ou "não".</span><span class="sxs-lookup"><span data-stu-id="26f04-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="26f04-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="26f04-113">Optional.</span></span> <span data-ttu-id="26f04-114">Lista de instruções de processamento de XML e comentários XML.</span><span class="sxs-lookup"><span data-stu-id="26f04-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="26f04-115">Usa o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="26f04-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="26f04-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="26f04-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="26f04-117">Cada `piComment`pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="26f04-117">Each `piComment`can be one of the following:</span></span><br /><br /><span data-ttu-id="26f04-118"> -   [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="26f04-118"> -   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="26f04-119">-   [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="26f04-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="26f04-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="26f04-120">Required.</span></span> <span data-ttu-id="26f04-121">Elemento raiz do documento.</span><span class="sxs-lookup"><span data-stu-id="26f04-121">Root element of the document.</span></span> <span data-ttu-id="26f04-122">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="26f04-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="26f04-123">[Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="26f04-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="26f04-124">Expressão incorporada do formulário `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="26f04-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="26f04-125">O `elementExp` retorna um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="26f04-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="26f04-126">Um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="26f04-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="26f04-127">Uma coleção que contém um <xref:System.Xml.Linq.XElement>objeto e qualquer número de <xref:System.Xml.Linq.XProcessingInstruction>e <xref:System.Xml.Linq.XComment>objetos.</xref:System.Xml.Linq.XComment> </xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="26f04-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="26f04-128">Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="26f04-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="26f04-129">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="26f04-129">Return Value</span></span>  
 <span data-ttu-id="26f04-130">Um <xref:System.Xml.Linq.XDocument>objeto.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="26f04-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26f04-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="26f04-131">Remarks</span></span>  
 <span data-ttu-id="26f04-132">Um literal de documento XML é identificada pela declaração XML no início do literal.</span><span class="sxs-lookup"><span data-stu-id="26f04-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="26f04-133">Embora cada documento XML deve ter exatamente um elemento XML de raiz, ele pode ter qualquer número de instruções de processamento de XML e comentários XML.</span><span class="sxs-lookup"><span data-stu-id="26f04-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="26f04-134">Um literal de documento XML não pode aparecer em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="26f04-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26f04-135">Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="26f04-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="26f04-136">Isso permite que você copiar o conteúdo de um documento XML e colá-lo diretamente em um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="26f04-136">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="26f04-137">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte o literal de documento XML em chamadas para o <xref:System.Xml.Linq.XDocument.%23ctor%2A>e <xref:System.Xml.Linq.XDeclaration.%23ctor%2A>construtores.</xref:System.Xml.Linq.XDeclaration.%23ctor%2A> </xref:System.Xml.Linq.XDocument.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="26f04-137">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26f04-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26f04-138">Example</span></span>  
 <span data-ttu-id="26f04-139">O exemplo a seguir cria um documento XML que tem uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.</span><span class="sxs-lookup"><span data-stu-id="26f04-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 <span data-ttu-id="26f04-140">[!code-vb[30 VbXMLSamples](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="26f04-140">[!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f04-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26f04-141">See Also</span></span>  
 <span data-ttu-id="26f04-142"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="26f04-142"><xref:System.Xml.Linq.XElement></span></span>   
 <span data-ttu-id="26f04-143"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="26f04-143"><xref:System.Xml.Linq.XProcessingInstruction></span></span>   
 <span data-ttu-id="26f04-144"><xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="26f04-144"><xref:System.Xml.Linq.XComment></span></span>   
 <span data-ttu-id="26f04-145"><xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="26f04-145"><xref:System.Xml.Linq.XDocument></span></span>   
<span data-ttu-id="26f04-146"> [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md) </span><span class="sxs-lookup"><span data-stu-id="26f04-146"> [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md) </span></span>  
<span data-ttu-id="26f04-147"> [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span><span class="sxs-lookup"><span data-stu-id="26f04-147"> [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span></span>  
<span data-ttu-id="26f04-148"> [Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="26f04-148"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="26f04-149"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="26f04-149"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="26f04-150"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="26f04-150"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="26f04-151"> [Expressões Inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)</span><span class="sxs-lookup"><span data-stu-id="26f04-151"> [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)</span></span>
