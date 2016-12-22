---
title: "Vari&#225;veis de objeto no Visual Basic | Microsoft Docs"
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
  - "variáveis de objeto"
  - "variáveis de objeto, sobre variáveis de objeto"
  - "objetos [Visual Basic], acessando"
  - "variáveis [Visual Basic], Objeto "
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;veis de objeto no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Além disso, para armazenar valores diretamente, uma variável pode referir\-se a um objeto.  Você atribui um objeto a uma variável pelas mesmas razões que você atribui qualquer valor a uma variável:  
  
-   Um nome de variável é geralmente mais curto e fácil de lembrar que a caminho completo de métodos e propriedades necessáriss para acessar o próprio objeto.  
  
-   Usar uma variável que faz referência a um objeto é mais eficiente do que repetidamente acessar o próprio objeto através dos métodos ou propriedades necessários.  
  
-   Você pode alterar uma variável para fazer referência a outros objetos enquanto o seu código estiver sendo executado.  
  
## Tornando o código menor  
 Você pode usar variáveis de objeto para diminuir o código que você tem que digitar.  O exemplo a seguir usa o caminho completo de métodos e propriedades para acessar um objeto <xref:System.Windows.Forms.Control>.  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 Você pode reduzir esse código e acelerar a execução, se você usar um variável de objeto para o controle.  Você deve declarar a variável de objeto com a classe específica que você pretende atribuir a ela \(`Control` neste caso\).  Depois de atribuir um objeto à variável, você pode tratá\-la exatamente do mesmo jeito que você trata o objeto ao qual ela se refere.  Você pode definir ou recuperar as propriedades do objeto ou usar qualquer um dos seus métodos.  O exemplo a seguir usa uma variável de objeto para simplificar o código no exemplo anterior.  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## Consulte também  
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Como agilizar o acesso a um objeto com um caminho de qualificação longo](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)   
 [Declaração de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Valores de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)