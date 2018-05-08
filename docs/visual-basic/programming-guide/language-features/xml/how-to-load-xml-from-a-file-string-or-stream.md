---
title: Como carregar XML a partir de um arquivo, cadeia de caracteres ou fluxo (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 241f6552e46d7689b42a409ba44bc747984773ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Como carregar XML a partir de um arquivo, cadeia de caracteres ou fluxo (Visual Basic)
Você pode criar [literais XML](../../../../visual-basic/language-reference/xml-literals/index.md) e populá-los com o conteúdo de uma fonte externa, como um arquivo, uma cadeia de caracteres ou um fluxo usando vários métodos. Esses métodos são mostrados nos exemplos a seguir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>Para carregar o XML de um arquivo  
  
-   Para popular um literal XML como um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto a partir de um arquivo, use o `Load` método. Esse método pode usar um caminho de arquivo, o fluxo de texto ou o fluxo de XML como entrada.  
  
     O exemplo de código a seguir mostra o uso do <xref:System.Xml.Linq.XDocument.Load%28System.String%29> para popular um <xref:System.Xml.Linq.XDocument> objeto com XML de um arquivo de texto.  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a>Para carregar XML de uma cadeia de caracteres  
  
-   Para popular um literal XML como um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> do objeto de cadeia de caracteres, você pode usar o `Parse` método.  
  
     O exemplo de código a seguir mostra o uso do <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> para popular um <xref:System.Xml.Linq.XDocument> objeto com XML de uma cadeia de caracteres.  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a>Para carregar XML de um fluxo  
  
-   Para popular um literal XML como um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> do objeto de um fluxo, você pode usar o `Load` método ou o <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> método.  
  
 O exemplo de código a seguir mostra o uso do <xref:System.Xml.Linq.XNode.ReadFrom%2A> para popular um <xref:System.Xml.Linq.XDocument> objeto com XML de um fluxo XML.  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
