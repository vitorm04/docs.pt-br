---
title: "Como agilizar o acesso a um objeto com um caminho de qualifica&#231;&#227;o longo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variáveis de objeto, acessando"
  - "variáveis [Visual Basic], acessando"
  - "variáveis [Visual Basic], Objeto "
  - "bloco With"
  - "Instrução With"
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como agilizar o acesso a um objeto com um caminho de qualifica&#231;&#227;o longo (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Se você acessar um objeto que requer um caminho de qualificação de vários métodos e propriedades com frequência, você pode acelerar seu código não repetindo o caminho de qualificação.  
  
 Há duas maneiras de evitar repetir o caminho de qualificação.  Você pode atribuir o objeto a uma variável, ou você pode usá\-lo em um bloco `With`... `End With`.  
  
### Para acelerar o acesso a um objeto intensamente qualificado atribuindo\-o a uma variável  
  
1.  Declare uma variável do tipo de objeto que você está acessando com frequência.  Especifique o caminho de qualificação na parte da declaração de inicialização.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Use a variável para acessar membros do objeto.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### Para acelerar o acesso a um objeto intensamente qualificado usando um bloco With...End With  
  
1.  Coloque o caminho de qualificação em uma instrução `With`.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Acesse membros do objeto dentro do bloco `With`, antes da instrução `End With`.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## Consulte também  
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)