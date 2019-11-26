---
title: Literal de instrução de processamento XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3602a81feae9287a77d060bb46f10eefee4fc05d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347041"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literal de instrução de processamento XML (Visual Basic)
A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Partes  
 `<?`  
 Necessário. Denotes the start of the XML processing instruction literal.  
  
 `piName`  
 Necessário. Name indicating which application the processing instruction targets. Cannot begin with "xml" or "XML".  
  
 `piData`  
 Opcional. String indicating how the application targeted by `piName` should process the XML document.  
  
 `?>`  
 Necessário. Denotes the end of the processing instruction.  
  
## <a name="return-value"></a>Valor retornado  
 Um objeto <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Comentários  
 XML processing instruction literals indicate how applications should process an XML document. When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document. The application interprets the meaning of `piName` and `piData`.  
  
 The XML document literal uses syntax that is similar to that of the XML processing instruction. For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
> The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.  
  
 You can assign an XML processing instruction literal to a variable or include it in an XML document literal.  
  
> [!NOTE]
> An XML literal can span multiple lines without needing line continuation characters. This enables you to copy content from an XML document and paste it directly into a Visual Basic program.  
  
 The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.  
  
## <a name="example"></a>Exemplo  
 The following example creates a processing instruction identifying a style-sheet for an XML document.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XProcessingInstruction>
- [Literal de Documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
