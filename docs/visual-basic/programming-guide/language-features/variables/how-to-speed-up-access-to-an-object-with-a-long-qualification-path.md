---
title: "Como: acelerar o acesso a um objeto com um caminho de qualificação longo (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement
- With block
- object variables, accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6e94613dbde440898542e0e194cdf1891651fa0a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Como agilizar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)
Se acessar um objeto que requer um caminho de qualificação de vários métodos e propriedades com frequência, você pode acelerar o seu código não repetindo o caminho de qualificação.  
  
 Há duas maneiras de evitar repetir o caminho de qualificação. Você pode atribuir o objeto a uma variável, ou você pode usá-lo em um `With`... `End With` bloco.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Para acelerar o acesso a um objeto intensamente qualificado atribuindo-a uma variável  
  
1.  Declare uma variável do tipo de objeto que você está acessando com frequência. Especifique o caminho de qualificação na parte da declaração de inicialização.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Use a variável para acessar membros do objeto.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Para acelerar o acesso a um objeto intensamente qualificado usando um bloco With... Bloco End With  
  
1.  Coloque o caminho de qualificação em uma `With` instrução.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Acesse membros do objeto dentro do `With` bloquear, antes de `End With` instrução.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
