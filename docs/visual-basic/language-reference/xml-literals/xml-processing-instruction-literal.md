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
ms.openlocfilehash: c589d3f4ac6bbb9aa9b2b8f2535888bddbf9c934
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958474"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literal de instrução de processamento XML (Visual Basic)
Um literal que representa <xref:System.Xml.Linq.XProcessingInstruction> um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Partes  
 `<?`  
 Necessário. Indica o início do literal de instrução de processamento XML.  
  
 `piName`  
 Necessário. Nome que indica a qual aplicativo a instrução de processamento se destina. Não é possível começar com "XML" ou "XML".  
  
 `piData`  
 Opcional. Cadeia de caracteres que indica como o `piName` aplicativo de destino deve processar o documento XML.  
  
 `?>`  
 Necessário. Denota o fim da instrução de processamento.  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Comentários  
 Literais de instrução de processamento XML indicam como os aplicativos devem processar um documento XML. Quando um aplicativo carrega um documento XML, o aplicativo pode verificar as instruções de processamento XML para determinar como processar o documento. O aplicativo interpreta o significado de `piName` e. `piData`  
  
 O literal de documento XML usa sintaxe semelhante à da instrução de processamento XML. Para obter mais informações, consulte [literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
> O `piName` elemento não pode começar com as cadeias de caracteres "XML" ou "XML", pois a especificação XML 1,0 reserva esses identificadores.  
  
 Você pode atribuir um literal de instrução de processamento XML a uma variável ou incluí-la em um literal de documento XML.  
  
> [!NOTE]
> Um literal XML pode abranger várias linhas sem precisar de caracteres de continuação de linha. Isso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.  
  
 O compilador Visual Basic converte o literal de instrução de processamento XML em uma chamada <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> para o construtor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma instrução de processamento que identifica uma folha de estilo para um documento XML.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XProcessingInstruction>
- [Literal de Documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
