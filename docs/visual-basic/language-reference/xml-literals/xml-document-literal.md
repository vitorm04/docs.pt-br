---
title: Literal de documento XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 008b5857418a572046797bf061a05f265669d427
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-document-literal-visual-basic"></a>Literal de documento XML (Visual Basic)
Um valor literal que representa um <xref:System.Xml.Linq.XDocument> objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`encoding`|Opcional. Declarando que o documento usa a codificação de texto literal.|  
|`standalone`|Opcional. Texto literal. Deve ser "Sim" ou "não".|  
|`piCommentList`|Opcional. Lista de instruções de processamento de XML e comentários XML. Usa o seguinte formato:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Cada `piComment` pode ser um dos seguintes:<br /><br /> -   [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Necessário. Elemento raiz do documento. O formato é um dos seguintes:<br /><br /> <ul><li>[Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Expressão inserida do formulário `<%=` `elementExp` `%>`. O `elementExp` retorna um dos seguintes:<br /><br /> <ul><li>Um objeto <xref:System.Xml.Linq.XElement>.</li><li>Uma coleção que contém um <xref:System.Xml.Linq.XElement> objeto e qualquer número de <xref:System.Xml.Linq.XProcessingInstruction> e <xref:System.Xml.Linq.XComment> objetos.</li></ul></li></ul><br /> Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XDocument>.  
  
## <a name="remarks"></a>Comentários  
 Um literal de documento XML é identificado pela declaração XML no início do literal. Embora cada literal de documento XML deve ter exatamente um elemento raiz XML, ele pode ter qualquer número de instruções de processamento de XML e comentários XML.  
  
 Um literal de documento XML não pode aparecer em um elemento XML.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha. Isso permite que você copiar o conteúdo de um documento XML e cole-o diretamente em um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programa.  
  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte o literal de documento XML em chamadas para o <xref:System.Xml.Linq.XDocument.%23ctor%2A> e <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> construtores.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um documento XML que tem uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [Literal de Instrução de Processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [Literal de Comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [Literal do Elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Expressões Inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
