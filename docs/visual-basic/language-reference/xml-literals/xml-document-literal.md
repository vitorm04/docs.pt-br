---
title: Literal de documento XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
dev_langs:
- VB
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
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
ms.openlocfilehash: 5d64faddad66eba4029969654388ba7df17e5854
ms.lasthandoff: 03/13/2017

---
# <a name="xml-document-literal-visual-basic"></a>Literal de documento XML (Visual Basic)
Um literal que representa um <xref:System.Xml.Linq.XDocument>objeto.</xref:System.Xml.Linq.XDocument>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`piCommentList`|Opcional. Lista de instruções de processamento de XML e comentários XML. Usa o seguinte formato:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Cada `piComment`pode ser uma das seguintes opções:<br /><br /> -   [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Necessário. Elemento raiz do documento. O formato é um dos seguintes:<br /><br /> <ul><li>[Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Expressão incorporada do formulário `<%=` `elementExp` `%>`. O `elementExp` retorna um dos seguintes:<br /><br /> <ul><li>Um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement></li><li>Uma coleção que contém um <xref:System.Xml.Linq.XElement>objeto e qualquer número de <xref:System.Xml.Linq.XProcessingInstruction>e <xref:System.Xml.Linq.XComment>objetos.</xref:System.Xml.Linq.XComment> </xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></li></ul></li></ul><br /> Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Valor de retorno  
 Um <xref:System.Xml.Linq.XDocument>objeto.</xref:System.Xml.Linq.XDocument>  
  
## <a name="remarks"></a>Comentários  
 Um literal de documento XML é identificada pela declaração XML no início do literal. Embora cada documento XML deve ter exatamente um elemento XML de raiz, ele pode ter qualquer número de instruções de processamento de XML e comentários XML.  
  
 Um literal de documento XML não pode aparecer em um elemento XML.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha. Isso permite que você copiar o conteúdo de um documento XML e colá-lo diretamente em um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte o literal de documento XML em chamadas para o <xref:System.Xml.Linq.XDocument.%23ctor%2A>e <xref:System.Xml.Linq.XDeclaration.%23ctor%2A>construtores.</xref:System.Xml.Linq.XDeclaration.%23ctor%2A> </xref:System.Xml.Linq.XDocument.%23ctor%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um documento XML que tem uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.  
  
 [!code-vb[30 VbXMLSamples](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>   
 <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>   
 <xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument>   
 [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)   
 [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Expressões Inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
