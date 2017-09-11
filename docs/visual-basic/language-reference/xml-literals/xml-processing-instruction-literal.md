---
title: "(Visual Basic) de Literal de instrução de processamento XML | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
dev_langs:
- VB
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
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
ms.openlocfilehash: 2ae976530ed3028677a1fef39db92265591df530
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="ed1ff-102">Literal de instrução de processamento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed1ff-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="ed1ff-103">Um literal que representa um <xref:System.Xml.Linq.XProcessingInstruction>objeto.</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="ed1ff-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed1ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed1ff-104">Syntax</span></span>  
  
```  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="ed1ff-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ed1ff-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="ed1ff-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-106">Required.</span></span> <span data-ttu-id="ed1ff-107">Indica o início do literal de instrução de processamento XML.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="ed1ff-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-108">Required.</span></span> <span data-ttu-id="ed1ff-109">Nome que indica quais aplicativos os destinos de instrução de processamento.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="ed1ff-110">Não é possível começar com "xml" ou "XML".</span><span class="sxs-lookup"><span data-stu-id="ed1ff-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="ed1ff-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-111">Optional.</span></span> <span data-ttu-id="ed1ff-112">Cadeia de caracteres que indica como o aplicativo de destino `piName` deve processar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="ed1ff-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-113">Required.</span></span> <span data-ttu-id="ed1ff-114">Indica o fim da instrução de processamento.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed1ff-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ed1ff-115">Return Value</span></span>  
 <span data-ttu-id="ed1ff-116">Um <xref:System.Xml.Linq.XProcessingInstruction>objeto.</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="ed1ff-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed1ff-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed1ff-117">Remarks</span></span>  
 <span data-ttu-id="ed1ff-118">Literais de instrução de processamento XML indicam como os aplicativos devem processar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="ed1ff-119">Quando um aplicativo carrega um documento XML, o aplicativo pode verificar as instruções de processamento de XML para determinar como processar o documento.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="ed1ff-120">O aplicativo interpreta o significado de `piName` e `piData`.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="ed1ff-121">O literal de documento XML usa a sintaxe é semelhante da instrução de processamento XML.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="ed1ff-122">Para obter mais informações, consulte [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="ed1ff-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed1ff-123">O `piName` elemento não pode começar com as cadeias de caracteres "xml" ou "XML", porque os identificadores de reserva a especificação XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="ed1ff-124">Você pode atribuir um literal de instrução de processamento XML para uma variável ou incluí-lo em um literal de documento XML.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed1ff-125">Um literal XML pode abranger várias linhas sem a necessidade de caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="ed1ff-126">Isso permite que você copiar o conteúdo de um documento XML e colá-lo diretamente em um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-126">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="ed1ff-127">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte o literal de instrução de processamento XML em uma chamada para o <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>construtor.</xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="ed1ff-127">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed1ff-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ed1ff-128">Example</span></span>  
 <span data-ttu-id="ed1ff-129">O exemplo a seguir cria uma instrução de processamento identificando uma folha de estilo para um documento XML.</span><span class="sxs-lookup"><span data-stu-id="ed1ff-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 <span data-ttu-id="ed1ff-130">[!code-vb[VbXMLSamples&#28;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ed1ff-130">[!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed1ff-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed1ff-131">See Also</span></span>  
 <span data-ttu-id="ed1ff-132"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="ed1ff-132"><xref:System.Xml.Linq.XProcessingInstruction></span></span>   
<span data-ttu-id="ed1ff-133"> [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span><span class="sxs-lookup"><span data-stu-id="ed1ff-133"> [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span></span>  
<span data-ttu-id="ed1ff-134"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="ed1ff-134"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="ed1ff-135"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="ed1ff-135"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
