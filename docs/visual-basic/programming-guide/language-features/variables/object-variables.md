---
title: Variáveis de objeto no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: cc5be13293a89e73d1790e94a99d7936f1711e12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961227"
---
# <a name="object-variables-in-visual-basic"></a>Variáveis de objeto no Visual Basic

Além de armazenar valores diretamente, uma variável pode se referir a um objeto. Você pode atribuir um objeto a uma variável pelas mesmas razões que atribuir qualquer valor a uma variável:

- Um nome de variável é geralmente mais curta e fácil de lembrar que o caminho completo de métodos e propriedades necessárias para acessar o objeto em si.

- Usando uma variável que faz referência a um objeto é mais eficiente do que repetidamente acessar o objeto em si por meio de métodos ou propriedades necessários.

- Você pode alterar uma variável para fazer referência a outros objetos enquanto seu código está em execução.

## <a name="making-code-shorter"></a>Tornar o código mais curto

Você pode usar variáveis de objeto para diminuir o código que você tem que digitar. O exemplo a seguir usa o caminho completo de métodos e propriedades para acessar um <xref:System.Windows.Forms.Control> objeto.

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

Você pode reduzir esse código e acelerar a execução, se você usar uma variável de objeto para o controle. Você deve declarar a variável de objeto com a classe específica que você pretende atribuir a ela (`Control` nesse caso). Depois de atribuir um objeto à variável, você pode tratá-lo exatamente conforme você tratar o objeto ao qual se refere. Você pode definir ou recuperar as propriedades do objeto ou usar qualquer um dos seus métodos. O exemplo a seguir usa uma variável de objeto para simplificar o código no exemplo anterior.

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>Consulte também

- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Como: Acelerar o acesso a um objeto com um demarcador de qualificação longo](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
