---
title: Literal de Instrução de Processamento XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 9bd1781e01bc4cbf1ce5da8c454ab2f5a679aead
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400170"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="b1875-102">Literal de instrução de processamento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1875-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="b1875-103">Um literal que representa um <xref:System.Xml.Linq.XProcessingInstruction> objeto.</span><span class="sxs-lookup"><span data-stu-id="b1875-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1875-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1875-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="b1875-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b1875-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="b1875-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b1875-106">Required.</span></span> <span data-ttu-id="b1875-107">Indica o início do literal de instrução de processamento XML.</span><span class="sxs-lookup"><span data-stu-id="b1875-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="b1875-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b1875-108">Required.</span></span> <span data-ttu-id="b1875-109">Nome que indica a qual aplicativo a instrução de processamento se destina.</span><span class="sxs-lookup"><span data-stu-id="b1875-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="b1875-110">Não é possível começar com "XML" ou "XML".</span><span class="sxs-lookup"><span data-stu-id="b1875-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="b1875-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b1875-111">Optional.</span></span> <span data-ttu-id="b1875-112">Cadeia de caracteres que indica como o aplicativo de destino `piName` deve processar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="b1875-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="b1875-113">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b1875-113">Required.</span></span> <span data-ttu-id="b1875-114">Denota o fim da instrução de processamento.</span><span class="sxs-lookup"><span data-stu-id="b1875-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1875-115">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="b1875-115">Return Value</span></span>  
 <span data-ttu-id="b1875-116">Um objeto <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="b1875-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1875-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1875-117">Remarks</span></span>  
 <span data-ttu-id="b1875-118">Literais de instrução de processamento XML indicam como os aplicativos devem processar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="b1875-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="b1875-119">Quando um aplicativo carrega um documento XML, o aplicativo pode verificar as instruções de processamento XML para determinar como processar o documento.</span><span class="sxs-lookup"><span data-stu-id="b1875-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="b1875-120">O aplicativo interpreta o significado de `piName` e `piData` .</span><span class="sxs-lookup"><span data-stu-id="b1875-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="b1875-121">O literal de documento XML usa sintaxe semelhante à da instrução de processamento XML.</span><span class="sxs-lookup"><span data-stu-id="b1875-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="b1875-122">Para obter mais informações, consulte [literal de documento XML](xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b1875-122">For more information, see [XML Document Literal](xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1875-123">O `piName` elemento não pode começar com as cadeias de caracteres "XML" ou "XML", pois a especificação xml 1,0 reserva esses identificadores.</span><span class="sxs-lookup"><span data-stu-id="b1875-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="b1875-124">Você pode atribuir um literal de instrução de processamento XML a uma variável ou incluí-la em um literal de documento XML.</span><span class="sxs-lookup"><span data-stu-id="b1875-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1875-125">Um literal XML pode abranger várias linhas sem precisar de caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="b1875-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="b1875-126">Isso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b1875-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="b1875-127">O compilador Visual Basic converte o literal de instrução de processamento XML em uma chamada para o <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> Construtor.</span><span class="sxs-lookup"><span data-stu-id="b1875-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1875-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1875-128">Example</span></span>  
 <span data-ttu-id="b1875-129">O exemplo a seguir cria uma instrução de processamento que identifica uma folha de estilo para um documento XML.</span><span class="sxs-lookup"><span data-stu-id="b1875-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="b1875-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="b1875-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="b1875-131">Literal de Documento XML</span><span class="sxs-lookup"><span data-stu-id="b1875-131">XML Document Literal</span></span>](xml-document-literal.md)
- [<span data-ttu-id="b1875-132">Literais XML</span><span class="sxs-lookup"><span data-stu-id="b1875-132">XML Literals</span></span>](index.md)
- [<span data-ttu-id="b1875-133">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1875-133">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
