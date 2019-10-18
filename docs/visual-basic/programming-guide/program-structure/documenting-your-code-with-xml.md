---
title: Documentando o código com XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 58c8716450fd8310b81050c86dc297c5b7527761
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524499"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Documentando o código com XML (Visual Basic)

No Visual Basic, você pode documentar seu código usando XML

## <a name="xml-documentation-comments"></a>Comentários da documentação XML

Visual Basic fornece uma maneira fácil de criar automaticamente a documentação XML para projetos. Você pode gerar automaticamente um esqueleto XML para seus tipos e membros e, em seguida, fornecer resumos, documentação descritiva para cada parâmetro e outros comentários. Com a configuração apropriada, a documentação XML é emitida automaticamente em um arquivo XML com o mesmo nome que o seu projeto e a extensão. xml. Para obter mais informações, confira [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

O arquivo XML pode ser consumido ou manipulado de outra forma como XML. Esse arquivo está localizado no mesmo diretório que o arquivo. exe ou. dll de saída do seu projeto.

A documentação XML começa com `'''`. O processamento desses comentários tem algumas restrições:

- A documentação deve ser em XML bem formado. Se o XML não estiver bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário dizendo que foi encontrado um erro.

- Os desenvolvedores são livres para criar seu próprio conjunto de marcas. Há um conjunto recomendado de marcas (consulte "seções relacionadas" neste tópico). Algumas das marcas recomendadas têm significado especial:

  - A marca \<param> é usada para descrever parâmetros. Se ela for usada, o compilador verificará se o parâmetro existe e se todos os parâmetros são descritos na documentação. Se a verificação falhar, o compilador emitirá um aviso.

  - O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código. O compilador verifica se esse elemento de código existe. Se a verificação falhar, o compilador emitirá um aviso. O compilador também respeita quaisquer instruções `Imports` ao procurar um tipo descrito no atributo `cref`.

  - A marca > de \<summary é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.

## <a name="related-sections"></a>Seções relacionadas

Para obter detalhes sobre como criar um arquivo XML com comentários de documentação, consulte os seguintes tópicos:

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)

- [Processando o Arquivo XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Ferramentas XML no Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Consulte também

- [Desenvolvendo aplicativos com o Visual Basic](../../../visual-basic/developing-apps/index.md)
- [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)
