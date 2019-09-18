---
title: 'Como: Carregar XML de um arquivo, Cadeia de caracteres ou fluxo (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: ba88ae19abc216a318d6c2069ab0846d5db8a346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054172"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Como: Carregar XML de um arquivo, Cadeia de caracteres ou fluxo (Visual Basic)

Você pode criar [literais XML](../../../../visual-basic/language-reference/xml-literals/index.md) e preenchê-los com o conteúdo de uma fonte externa, como um arquivo, uma cadeia de caracteres ou um fluxo usando vários métodos. Esses métodos são mostrados nos exemplos a seguir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Para carregar XML de um arquivo

Para popular um literal XML como um <xref:System.Xml.Linq.XElement> objeto ou <xref:System.Xml.Linq.XDocument> de um arquivo, use o `Load` método. Esse método pode pegar um caminho de arquivo, um fluxo de texto ou um fluxo XML como entrada.

O exemplo de código a seguir mostra o uso <xref:System.Xml.Linq.XDocument.Load%28System.String%29> do método para popular <xref:System.Xml.Linq.XDocument> um objeto com XML de um arquivo de texto.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Para carregar XML de uma cadeia de caracteres

Para popular um literal XML como um <xref:System.Xml.Linq.XElement> objeto ou <xref:System.Xml.Linq.XDocument> de uma cadeia de caracteres, você pode usar o `Parse` método.

O exemplo de código a seguir mostra o uso <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> do método para popular <xref:System.Xml.Linq.XDocument> um objeto com XML a partir de uma cadeia de caracteres.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Para carregar XML de um fluxo

Para preencher um literal <xref:System.Xml.Linq.XElement> XML como um objeto ou <xref:System.Xml.Linq.XDocument> de um fluxo, você pode usar o `Load` método ou o <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> método.

O exemplo de código a seguir mostra o uso <xref:System.Xml.Linq.XNode.ReadFrom%2A> do método para popular <xref:System.Xml.Linq.XDocument> um objeto com XML de um fluxo XML.

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [Literais XML](../../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
