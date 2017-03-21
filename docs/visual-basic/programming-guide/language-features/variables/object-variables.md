---
title: "Objeto variáveis no Visual Basic | Documentos do Microsoft"
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
- object variables, about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 49aa189c46bfad01c093c2afe16fa8a41bf09940
ms.lasthandoff: 03/13/2017

---
# <a name="object-variables-in-visual-basic"></a>Variáveis de objeto no Visual Basic
Além de armazenar valores diretamente, uma variável pode se referir a um objeto. Você atribui um objeto a uma variável pelas mesmas razões que você atribui qualquer valor a uma variável:  
  
-   Um nome de variável é geralmente mais curto e fácil de lembrar que o caminho completo de métodos e propriedades necessárias para acessar o próprio objeto.  
  
-   Usando uma variável que faz referência a um objeto é mais eficiente do que repetidamente acessar o próprio objeto por meio de métodos ou propriedades necessários.  
  
-   Você pode alterar uma variável para fazer referência a outros objetos enquanto seu código está em execução.  
  
## <a name="making-code-shorter"></a>Tornando o código menor  
 Você pode usar variáveis de objeto para diminuir o código que você tem que digitar. O exemplo a seguir usa o caminho completo de métodos e propriedades para acessar um <xref:System.Windows.Forms.Control>objeto.</xref:System.Windows.Forms.Control>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 Você pode reduzir esse código e acelerar a execução, se você usar uma variável de objeto para o controle. Você deve declarar a variável de objeto com a classe específica que você pretende atribuir a ela (`Control` nesse caso). Depois de atribuir um objeto à variável, você pode tratá-lo exatamente como você trata o objeto ao qual se refere. Você pode definir ou recuperar as propriedades do objeto ou usar qualquer um dos seus métodos. O exemplo a seguir usa uma variável de objeto para simplificar o código no exemplo anterior.  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a>Consulte também  
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Como: acelerar o acesso a um objeto com um longo caminho de qualificação](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)   
 [Declaração de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Atribuição de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
