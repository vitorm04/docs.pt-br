---
title: 'Como: Acelerar o acesso a um objeto com um longo caminho de qualificação (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: a8e50a2ed04037b48091321dc0c9ac2ea1db35f4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631092"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Como: Acelerar o acesso a um objeto com um longo caminho de qualificação (Visual Basic)

Se você acessar com frequência um objeto que requer um caminho de qualificação de vários métodos e propriedades, você pode acelerar seu código não repetindo o caminho de qualificação.

Há duas maneiras de evitar a repetição do caminho de qualificação. Você pode atribuir o objeto a uma variável ou pode usá-lo em um `With`... `End With` bloquear.

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

1. Coloque o caminho de qualificação em `With` uma instrução.

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. Acesse os membros do objeto dentro `With` do bloco, antes `End With` da instrução.

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Consulte também

- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
