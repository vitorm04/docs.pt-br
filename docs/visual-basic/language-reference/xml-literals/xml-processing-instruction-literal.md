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
ms.openlocfilehash: e6d4c200822f58c7dbe5bf423282740d4aa86ac3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604127"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literal de instrução de processamento XML (Visual Basic)
Um valor literal que representa um <xref:System.Xml.Linq.XProcessingInstruction> objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Partes  
 `<?`  
 Necessário. Indica o início do literal de instrução de processamento XML.  
  
 `piName`  
 Necessário. Nome que indica qual aplicativo os destinos de instrução de processamento. Não pode começar com "xml" ou "XML".  
  
 `piData`  
 Opcional. Cadeia de caracteres que indica como o aplicativo de destino `piName` deve processar o documento XML.  
  
 `?>`  
 Necessário. Indica o fim da instrução de processamento.  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Comentários  
 Literais de instrução de processamento XML indicam como os aplicativos devem processar um documento XML. Quando um aplicativo carrega um documento XML, o aplicativo pode verificar se as instruções de processamento de XML para determinar como processar o documento. O aplicativo interpreta o significado de `piName` e `piData`.  
  
 O literal de documento XML usa a sintaxe é semelhante a que a instrução de processamento de XML. Para obter mais informações, consulte [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
>  O `piName` elemento não pode começar com as cadeias de caracteres "xml" ou "XML", porque os identificadores de reserva de especificação do XML 1.0.  
  
 Você pode atribuir um literal de instrução de processamento XML a uma variável ou incluí-lo em um literal de documento XML.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas sem a necessidade de caracteres de continuação de linha. Isso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.  
  
 O compilador do Visual Basic converte o literal de instrução de processamento XML em uma chamada para o <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> construtor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma instrução de processamento identifica uma folha de estilo para um documento XML.  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [Literal de Documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
