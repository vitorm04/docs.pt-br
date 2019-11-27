---
title: Como criar documentação XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 41b7ef1f435fd0a4f20c4ca2936e2d91e155f7c5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347415"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Como criar documentação XML no Visual Basic

Este exemplo mostra como adicionar comentários de documentação XML ao seu código.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>Para criar a documentação XML para um tipo ou membro

1. No **Editor de código**, posicione o cursor na linha acima do tipo ou do membro para o qual você deseja criar a documentação.

2. Digite `'''` (três aspas simples).

    Um esqueleto XML para o tipo ou membro é adicionado no **Editor de código**.

3. Adicione informações descritivas entre as marcas apropriadas.

    > [!NOTE]
    > Se você adicionar linhas adicionais no bloco de documentação XML, cada linha deverá começar com `'''`.

4. Adicione um código adicional que use o tipo ou o membro com os novos comentários de documentação XML.

    O IntelliSense exibe o texto da marca de > de resumo \<para o tipo ou o membro.

5. Compile o código para gerar um arquivo XML contendo os comentários da documentação. Para obter mais informações, confira [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

## <a name="see-also"></a>Consulte também

- [Documentando o Código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
