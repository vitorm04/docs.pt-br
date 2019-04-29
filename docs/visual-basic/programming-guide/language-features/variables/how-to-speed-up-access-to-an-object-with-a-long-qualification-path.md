---
title: 'Como: Acelerar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 94c838a69aab9fcae9dc0c79b6038ee90e2369e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769038"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Como: Acelerar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)
Se você acessa com frequência um objeto que exija um demarcador de qualificação de vários métodos e propriedades, você pode acelerar o seu código não repetindo o demarcador de qualificação.  
  
 Há duas maneiras de evitar repetir o demarcador de qualificação. Você pode atribuir o objeto a uma variável, ou você pode usá-lo em um `With`... `End With` bloco.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Para acelerar o acesso a um objeto intensamente qualificado atribuindo-a uma variável  
  
1. Declare uma variável do tipo do objeto que você está acessando com frequência. Especifique o caminho de qualificação na parte da declaração de inicialização.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2. Use a variável para acessar membros do objeto.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Para acelerar o acesso a um objeto intensamente qualificado usando um With... Bloco End With  
  
1. Coloque o caminho de qualificação em um `With` instrução.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2. Acessar membros do objeto dentro de `With` bloquear, antes de `End With` instrução.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
