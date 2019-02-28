---
title: Literal de instrução de processamento XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 1906c9101f9a53bde13698d0ed17b7b8d0988c1d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981368"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="a81ae-102">Literal de instrução de processamento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a81ae-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="a81ae-103">Um valor literal que representa um <xref:System.Xml.Linq.XProcessingInstruction> objeto.</span><span class="sxs-lookup"><span data-stu-id="a81ae-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a81ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a81ae-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="a81ae-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a81ae-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="a81ae-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a81ae-106">Required.</span></span> <span data-ttu-id="a81ae-107">Indica o início da instrução de processamento XML literal.</span><span class="sxs-lookup"><span data-stu-id="a81ae-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="a81ae-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a81ae-108">Required.</span></span> <span data-ttu-id="a81ae-109">O nome que indica qual aplicativo os destinos de instrução de processamento.</span><span class="sxs-lookup"><span data-stu-id="a81ae-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="a81ae-110">Não é possível começar com "xml" ou "XML".</span><span class="sxs-lookup"><span data-stu-id="a81ae-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="a81ae-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a81ae-111">Optional.</span></span> <span data-ttu-id="a81ae-112">Cadeia de caracteres que indica como o aplicativo é direcionado por `piName` deve processar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="a81ae-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="a81ae-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a81ae-113">Required.</span></span> <span data-ttu-id="a81ae-114">Indica o fim da instrução de processamento.</span><span class="sxs-lookup"><span data-stu-id="a81ae-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a81ae-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a81ae-115">Return Value</span></span>  
 <span data-ttu-id="a81ae-116">Um objeto <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="a81ae-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a81ae-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="a81ae-117">Remarks</span></span>  
 <span data-ttu-id="a81ae-118">Literais de instrução de processamento XML indicam como os aplicativos devem processar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="a81ae-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="a81ae-119">Quando um aplicativo carrega um documento XML, o aplicativo pode verificar as instruções de processamento de XML para determinar como processar o documento.</span><span class="sxs-lookup"><span data-stu-id="a81ae-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="a81ae-120">O aplicativo interpreta o significado dos `piName` e `piData`.</span><span class="sxs-lookup"><span data-stu-id="a81ae-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="a81ae-121">O literal de documento XML usa a sintaxe é semelhante da instrução de processamento de XML.</span><span class="sxs-lookup"><span data-stu-id="a81ae-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="a81ae-122">Para obter mais informações, consulte [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a81ae-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a81ae-123">O `piName` elemento não pode começar com as cadeias de caracteres "xml" ou "XML", porque esses identificadores de reserva a especificação XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="a81ae-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="a81ae-124">Você pode atribuir um literal de instrução de processamento de XML a uma variável ou incluí-lo em um literal de documento XML.</span><span class="sxs-lookup"><span data-stu-id="a81ae-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a81ae-125">Um literal XML pode abranger várias linhas sem a necessidade de caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="a81ae-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="a81ae-126">Isso permite que você copie o conteúdo de um documento XML e colá-lo diretamente em um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a81ae-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="a81ae-127">O compilador do Visual Basic converte o literal de instrução de processamento XML em uma chamada para o <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="a81ae-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a81ae-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a81ae-128">Example</span></span>  
 <span data-ttu-id="a81ae-129">O exemplo a seguir cria uma instrução de processamento identificando uma folha de estilo para um documento XML.</span><span class="sxs-lookup"><span data-stu-id="a81ae-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="a81ae-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a81ae-130">See also</span></span>
- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="a81ae-131">Literal de Documento XML</span><span class="sxs-lookup"><span data-stu-id="a81ae-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="a81ae-132">Literais XML</span><span class="sxs-lookup"><span data-stu-id="a81ae-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="a81ae-133">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a81ae-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
