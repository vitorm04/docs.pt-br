---
title: Como agilizar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: d52d13feb0f85065c0623b5937f558b841c036dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Como agilizar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)
Se você acessar frequentemente um objeto que requer um caminho de qualificação de vários métodos e propriedades, você pode acelerar o seu código não repetindo o caminho de qualificação.  
  
 Há duas maneiras de evitar repetir o caminho de qualificação. Você pode atribuir o objeto a uma variável, ou você pode usá-lo em um `With`... `End With` bloco.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Para agilizar o acesso a um objeto intensamente qualificado atribuindo-a uma variável  
  
1.  Declare uma variável do tipo de objeto que você está acessando com frequência. Especifique o caminho de qualificação na parte da declaração de inicialização.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Use a variável para acessar os membros do objeto.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Para agilizar o acesso a um objeto intensamente qualificado usando um With... Bloco End With  
  
1.  Coloque o caminho de qualificação em um `With` instrução.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Acesse membros do objeto dentro de `With` bloquear, antes de `End With` instrução.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
