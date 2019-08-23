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
ms.openlocfilehash: 8a489be46295c213b7a8b355eb3c9786d49dd8f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958508"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="4ac2a-102">Literal de documento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ac2a-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="4ac2a-103">Um literal que representa <xref:System.Xml.Linq.XDocument> um objeto.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac2a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ac2a-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="4ac2a-105">Partes</span><span class="sxs-lookup"><span data-stu-id="4ac2a-105">Parts</span></span>  
  
|<span data-ttu-id="4ac2a-106">Termo</span><span class="sxs-lookup"><span data-stu-id="4ac2a-106">Term</span></span>|<span data-ttu-id="4ac2a-107">Definição</span><span class="sxs-lookup"><span data-stu-id="4ac2a-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="4ac2a-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-108">Optional.</span></span> <span data-ttu-id="4ac2a-109">Texto literal que declara a codificação usada pelo documento.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="4ac2a-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-110">Optional.</span></span> <span data-ttu-id="4ac2a-111">Texto literal.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-111">Literal text.</span></span> <span data-ttu-id="4ac2a-112">Deve ser "Yes" ou "no".</span><span class="sxs-lookup"><span data-stu-id="4ac2a-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="4ac2a-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-113">Optional.</span></span> <span data-ttu-id="4ac2a-114">Lista de instruções de processamento XML e comentários XML.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="4ac2a-115">Usa o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="4ac2a-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="4ac2a-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="4ac2a-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="4ac2a-117">Cada `piComment` um pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4ac2a-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="4ac2a-118">-   [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4ac2a-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="4ac2a-119">-   [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4ac2a-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="4ac2a-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-120">Required.</span></span> <span data-ttu-id="4ac2a-121">Elemento raiz do documento.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-121">Root element of the document.</span></span> <span data-ttu-id="4ac2a-122">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4ac2a-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="4ac2a-123">[Literal de elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4ac2a-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="4ac2a-124">Expressão inserida do formulário `<%=`. `elementExp` `%>`</span><span class="sxs-lookup"><span data-stu-id="4ac2a-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="4ac2a-125">O `elementExp` retorna um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4ac2a-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="4ac2a-126">Um objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="4ac2a-127">Uma coleção que contém um <xref:System.Xml.Linq.XElement> objeto e qualquer número de <xref:System.Xml.Linq.XProcessingInstruction> objetos <xref:System.Xml.Linq.XComment> e.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="4ac2a-128">Para obter mais informações, consulte [expressões inseridas em XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4ac2a-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="4ac2a-129">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4ac2a-129">Return Value</span></span>  
 <span data-ttu-id="4ac2a-130">Um objeto <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ac2a-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ac2a-131">Remarks</span></span>  
 <span data-ttu-id="4ac2a-132">Um literal de documento XML é identificado pela declaração XML no início do literal.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="4ac2a-133">Embora cada literal de documento XML deva ter exatamente um elemento XML raiz, ele pode ter qualquer número de instruções de processamento XML e comentários XML.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="4ac2a-134">Um literal de documento XML não pode aparecer em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ac2a-135">Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="4ac2a-136">Isso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="4ac2a-137">O compilador de Visual Basic converte o literal de documento XML em chamadas <xref:System.Xml.Linq.XDocument.%23ctor%2A> para <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> os construtores e.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ac2a-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ac2a-138">Example</span></span>  
 <span data-ttu-id="4ac2a-139">O exemplo a seguir cria um documento XML que tem uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.</span><span class="sxs-lookup"><span data-stu-id="4ac2a-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="4ac2a-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ac2a-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="4ac2a-141">Literal de Instrução de Processamento XML</span><span class="sxs-lookup"><span data-stu-id="4ac2a-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [<span data-ttu-id="4ac2a-142">Literal de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="4ac2a-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="4ac2a-143">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="4ac2a-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="4ac2a-144">Literais XML</span><span class="sxs-lookup"><span data-stu-id="4ac2a-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="4ac2a-145">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ac2a-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="4ac2a-146">Expressões Inseridas no XML</span><span class="sxs-lookup"><span data-stu-id="4ac2a-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
