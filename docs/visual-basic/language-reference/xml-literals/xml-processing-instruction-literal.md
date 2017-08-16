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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2903297fa22cd8dc10bc4b12abaa754d4f6284f2
ms.lasthandoff: 03/13/2017

---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literal de instrução de processamento XML (Visual Basic)
Um literal que representa um <xref:System.Xml.Linq.XProcessingInstruction>objeto.</xref:System.Xml.Linq.XProcessingInstruction>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Partes  
 `<?`  
 Necessário. Indica o início do literal de instrução de processamento XML.  
  
 `piName`  
 Necessário. Nome que indica quais aplicativos os destinos de instrução de processamento. Não é possível começar com "xml" ou "XML".  
  
 `piData`  
 Opcional. Cadeia de caracteres que indica como o aplicativo de destino `piName` deve processar o documento XML.  
  
 `?>`  
 Necessário. Indica o fim da instrução de processamento.  
  
## <a name="return-value"></a>Valor de retorno  
 Um <xref:System.Xml.Linq.XProcessingInstruction>objeto.</xref:System.Xml.Linq.XProcessingInstruction>  
  
## <a name="remarks"></a>Comentários  
 Literais de instrução de processamento XML indicam como os aplicativos devem processar um documento XML. Quando um aplicativo carrega um documento XML, o aplicativo pode verificar as instruções de processamento de XML para determinar como processar o documento. O aplicativo interpreta o significado de `piName` e `piData`.  
  
 O literal de documento XML usa a sintaxe é semelhante da instrução de processamento XML. Para obter mais informações, consulte [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
>  O `piName` elemento não pode começar com as cadeias de caracteres "xml" ou "XML", porque os identificadores de reserva a especificação XML 1.0.  
  
 Você pode atribuir um literal de instrução de processamento XML para uma variável ou incluí-lo em um literal de documento XML.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas sem a necessidade de caracteres de continuação de linha. Isso permite que você copiar o conteúdo de um documento XML e colá-lo diretamente em um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte o literal de instrução de processamento XML em uma chamada para o <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>construtor.</xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma instrução de processamento identificando uma folha de estilo para um documento XML.  
  
 [!code-vb[VbXMLSamples&#28;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>   
 [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
