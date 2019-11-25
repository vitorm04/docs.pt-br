---
title: Documentando o código com XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: bdf0da7a8acc919e4a1d66b81e30c9ed912dd321
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347449"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Documentando o código com XML (Visual Basic)

In Visual Basic, you can document your code using XML

## <a name="xml-documentation-comments"></a>Comentários da documentação XML

Visual Basic provides an easy way to automatically create XML documentation for projects. You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks. With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension. Para obter mais informações, confira [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

The XML file can be consumed or otherwise manipulated as XML. This file is located in the same directory as the output .exe or .dll file of your project.

XML documentation starts with `'''`. O processamento desses comentários tem algumas restrições:

- A documentação deve ser em XML bem formado. If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.

- Os desenvolvedores são livres para criar seu próprio conjunto de marcas. There is a recommended set of tags (see "Related Sections" in this topic). Algumas das marcas recomendadas têm significado especial:

  - A marca \<param> é usada para descrever parâmetros. Se ela for usada, o compilador verificará se o parâmetro existe e se todos os parâmetros são descritos na documentação. If the verification fails, the compiler issues a warning.

  - O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código. O compilador verifica se esse elemento de código existe. If the verification fails, the compiler issues a warning. The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.

  - The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.

## <a name="related-sections"></a>Seções relacionadas

For details on creating an XML file with documentation comments, see the following topics:

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)

- [Processando o Arquivo XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Ferramentas XML no Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Consulte também

- [Desenvolvendo aplicativos com o Visual Basic](../../../visual-basic/developing-apps/index.md)
- [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)
