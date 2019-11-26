---
title: Literal de comentário XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 8d9db66aabe344bd5c8f9a92ac8618b7bc1abb43
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349395"
---
# <a name="xml-comment-literal-visual-basic"></a>Literal de comentário XML (Visual Basic)
A literal representing an <xref:System.Xml.Linq.XComment> object.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`<!--`|Necessário. Denotes the start of the XML comment.|  
|`content`|Necessário. Text to appear in the XML comment. Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.|  
|`-->`|Necessário. Denotes the end of the XML comment.|  
  
## <a name="return-value"></a>Valor retornado  
 Um objeto <xref:System.Xml.Linq.XComment>.  
  
## <a name="remarks"></a>Comentários  
 XML comment literals do not contain document content; they contain information about the document. The XML comment section ends with the sequence "-->". This implies the following points:  
  
- You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.  
  
- XML comment sections cannot be nested, because `content` cannot contain the value "-->".  
  
 You can assign an XML comment literal to a variable, or you can include it in an XML element literal.  
  
> [!NOTE]
> An XML literal can span multiple lines without using line continuation characters. This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.  
  
 The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.  
  
## <a name="example"></a>Exemplo  
 The following example creates an XML comment that contains the text "This is a comment".  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XComment>
- [Literal do Elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
