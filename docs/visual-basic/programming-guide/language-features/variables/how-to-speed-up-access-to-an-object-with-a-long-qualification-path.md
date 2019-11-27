---
title: Como agilizar o acesso a um objeto com um demarcador de qualificação longo
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 83670ae6af0904156b08398024658cf504b7663f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346824"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Como agilizar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)

Se você acessar com frequência um objeto que requer um caminho de qualificação de vários métodos e propriedades, você pode acelerar seu código não repetindo o caminho de qualificação.

Há duas maneiras de evitar a repetição do caminho de qualificação. Você pode atribuir o objeto a uma variável ou pode usá-lo em um bloco `With`...`End With`.

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Para acelerar o acesso a um objeto muito qualificado atribuindo-o a uma variável

1. Declare uma variável do tipo do objeto que você está acessando com frequência. Especifique o caminho de qualificação na parte de inicialização da declaração.

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. Use a variável para acessar os membros do objeto.

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Para acelerar o acesso a um objeto muito qualificado usando um com... Terminar com bloco

1. Coloque o caminho de qualificação em uma instrução `With`.

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. Acesse os membros do objeto dentro do bloco de `With`, antes da instrução `End With`.

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Consulte também

- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
