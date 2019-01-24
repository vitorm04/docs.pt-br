---
title: Literal de documento XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: 09ab9d0bf3feeea70ddbc094183406a6fd646c1c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690508"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="64974-102">Literal de documento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64974-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="64974-103">Um valor literal que representa um <xref:System.Xml.Linq.XDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="64974-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64974-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64974-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="64974-105">Partes</span><span class="sxs-lookup"><span data-stu-id="64974-105">Parts</span></span>  
  
|<span data-ttu-id="64974-106">Termo</span><span class="sxs-lookup"><span data-stu-id="64974-106">Term</span></span>|<span data-ttu-id="64974-107">Definição</span><span class="sxs-lookup"><span data-stu-id="64974-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="64974-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="64974-108">Optional.</span></span> <span data-ttu-id="64974-109">Declarando a qual o documento usa a codificação de texto literal.</span><span class="sxs-lookup"><span data-stu-id="64974-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="64974-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="64974-110">Optional.</span></span> <span data-ttu-id="64974-111">Texto literal.</span><span class="sxs-lookup"><span data-stu-id="64974-111">Literal text.</span></span> <span data-ttu-id="64974-112">Deve ser "Sim" ou "não".</span><span class="sxs-lookup"><span data-stu-id="64974-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="64974-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="64974-113">Optional.</span></span> <span data-ttu-id="64974-114">Lista de instruções de processamento de XML e comentários XML.</span><span class="sxs-lookup"><span data-stu-id="64974-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="64974-115">Recebe o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="64974-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="64974-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="64974-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="64974-117">Cada `piComment` pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="64974-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="64974-118">-   [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="64974-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="64974-119">-   [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="64974-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="64974-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="64974-120">Required.</span></span> <span data-ttu-id="64974-121">Elemento raiz do documento.</span><span class="sxs-lookup"><span data-stu-id="64974-121">Root element of the document.</span></span> <span data-ttu-id="64974-122">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="64974-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="64974-123">[Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="64974-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="64974-124">Expressão do formulário incorporada `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="64974-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="64974-125">O `elementExp` retorna um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="64974-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="64974-126">Um objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="64974-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="64974-127">Uma coleção que contém um <xref:System.Xml.Linq.XElement> objeto e qualquer número de <xref:System.Xml.Linq.XProcessingInstruction> e <xref:System.Xml.Linq.XComment> objetos.</span><span class="sxs-lookup"><span data-stu-id="64974-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="64974-128">Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="64974-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="64974-129">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="64974-129">Return Value</span></span>  
 <span data-ttu-id="64974-130">Um objeto <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="64974-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64974-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="64974-131">Remarks</span></span>  
 <span data-ttu-id="64974-132">Um literal de documento XML é identificada pela declaração XML no início do literal.</span><span class="sxs-lookup"><span data-stu-id="64974-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="64974-133">Embora cada literal de documento XML deve ter exatamente um elemento raiz XML, ele pode ter qualquer número de instruções de processamento de XML e comentários XML.</span><span class="sxs-lookup"><span data-stu-id="64974-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="64974-134">Um literal de documento XML não pode aparecer em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="64974-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64974-135">Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="64974-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="64974-136">Isso permite que você copie o conteúdo de um documento XML e colá-lo diretamente em um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="64974-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="64974-137">O compilador do Visual Basic converte o literal de documento XML em chamadas para o <xref:System.Xml.Linq.XDocument.%23ctor%2A> e <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> construtores.</span><span class="sxs-lookup"><span data-stu-id="64974-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64974-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64974-138">Example</span></span>  
 <span data-ttu-id="64974-139">O exemplo a seguir cria um documento XML que tem uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.</span><span class="sxs-lookup"><span data-stu-id="64974-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="64974-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64974-140">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="64974-141">Literal de Instrução de Processamento XML</span><span class="sxs-lookup"><span data-stu-id="64974-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [<span data-ttu-id="64974-142">Literal de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="64974-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="64974-143">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="64974-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="64974-144">Literais XML</span><span class="sxs-lookup"><span data-stu-id="64974-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="64974-145">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64974-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="64974-146">Expressões Inseridas no XML</span><span class="sxs-lookup"><span data-stu-id="64974-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
