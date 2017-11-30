---
title: "Como agilizar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d91eeaeb034a4c8b4fefcffdf2fdebe72127d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
