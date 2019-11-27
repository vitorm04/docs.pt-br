---
title: Como carregar XML a partir de um arquivo, cadeia de caracteres ou fluxo
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7a2a0513a066ae8ea8a70f7a5ae340ab29de7d25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330956"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Como carregar XML a partir de um arquivo, cadeia de caracteres ou fluxo (Visual Basic)

Você pode criar [literais XML](../../../../visual-basic/language-reference/xml-literals/index.md) e preenchê-los com o conteúdo de uma fonte externa, como um arquivo, uma cadeia de caracteres ou um fluxo usando vários métodos. Esses métodos são mostrados nos exemplos a seguir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Para carregar XML de um arquivo

Para preencher um literal XML, como um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto de um arquivo, use o método `Load`. Esse método pode pegar um caminho de arquivo, um fluxo de texto ou um fluxo XML como entrada.

O exemplo de código a seguir mostra o uso do método <xref:System.Xml.Linq.XDocument.Load%28System.String%29> para popular um objeto <xref:System.Xml.Linq.XDocument> com XML de um arquivo de texto.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Para carregar XML de uma cadeia de caracteres

Para popular um literal XML como um objeto <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> de uma cadeia de caracteres, você pode usar o método `Parse`.

O exemplo de código a seguir mostra o uso do método <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> para popular um objeto <xref:System.Xml.Linq.XDocument> com XML de uma cadeia de caracteres.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Para carregar XML de um fluxo

Para preencher um literal XML, como um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto de um fluxo, você pode usar o método `Load` ou o método <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>.

O exemplo de código a seguir mostra o uso do método <xref:System.Xml.Linq.XNode.ReadFrom%2A> para popular um objeto <xref:System.Xml.Linq.XDocument> com XML de um fluxo XML.

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
