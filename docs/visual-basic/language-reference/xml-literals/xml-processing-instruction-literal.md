---
title: Literal de instrução de processamento XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ce0f2d0dff80072beefdb4f84643ea28e2cf165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="2fbb6-102">Literal de instrução de processamento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fbb6-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="2fbb6-103">Um valor literal que representa um <xref:System.Xml.Linq.XProcessingInstruction> objeto.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fbb6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fbb6-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="2fbb6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="2fbb6-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="2fbb6-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-106">Required.</span></span> <span data-ttu-id="2fbb6-107">Indica o início do literal de instrução de processamento XML.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="2fbb6-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-108">Required.</span></span> <span data-ttu-id="2fbb6-109">Nome que indica qual aplicativo os destinos de instrução de processamento.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="2fbb6-110">Não pode começar com "xml" ou "XML".</span><span class="sxs-lookup"><span data-stu-id="2fbb6-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="2fbb6-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-111">Optional.</span></span> <span data-ttu-id="2fbb6-112">Cadeia de caracteres que indica como o aplicativo de destino `piName` deve processar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="2fbb6-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-113">Required.</span></span> <span data-ttu-id="2fbb6-114">Indica o fim da instrução de processamento.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fbb6-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2fbb6-115">Return Value</span></span>  
 <span data-ttu-id="2fbb6-116">Um objeto <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fbb6-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="2fbb6-117">Remarks</span></span>  
 <span data-ttu-id="2fbb6-118">Literais de instrução de processamento XML indicam como os aplicativos devem processar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="2fbb6-119">Quando um aplicativo carrega um documento XML, o aplicativo pode verificar se as instruções de processamento de XML para determinar como processar o documento.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="2fbb6-120">O aplicativo interpreta o significado de `piName` e `piData`.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="2fbb6-121">O literal de documento XML usa a sintaxe é semelhante a que a instrução de processamento de XML.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="2fbb6-122">Para obter mais informações, consulte [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2fbb6-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fbb6-123">O `piName` elemento não pode começar com as cadeias de caracteres "xml" ou "XML", porque os identificadores de reserva de especificação do XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="2fbb6-124">Você pode atribuir um literal de instrução de processamento XML a uma variável ou incluí-lo em um literal de documento XML.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fbb6-125">Um literal XML pode abranger várias linhas sem a necessidade de caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="2fbb6-126">Isso permite que você copiar o conteúdo de um documento XML e cole-o diretamente em um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-126">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="2fbb6-127">O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte o literal de instrução de processamento XML em uma chamada para o <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-127">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fbb6-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fbb6-128">Example</span></span>  
 <span data-ttu-id="2fbb6-129">O exemplo a seguir cria uma instrução de processamento identifica uma folha de estilo para um documento XML.</span><span class="sxs-lookup"><span data-stu-id="2fbb6-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2fbb6-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fbb6-130">See Also</span></span>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [<span data-ttu-id="2fbb6-131">Literal de Documento XML</span><span class="sxs-lookup"><span data-stu-id="2fbb6-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="2fbb6-132">Literais XML</span><span class="sxs-lookup"><span data-stu-id="2fbb6-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="2fbb6-133">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2fbb6-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
