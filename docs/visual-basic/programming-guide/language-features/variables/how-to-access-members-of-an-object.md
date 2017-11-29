---
title: Como acessar membros de um objeto (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 85fa4932b449bf7b9ecb3902fc17fd954ea8cfac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Como acessar membros de um objeto (Visual Basic)
Quando você tiver uma variável de objeto que se refere a um objeto, você geralmente deseja trabalhar com os membros do objeto, como seus métodos, propriedades, campos e eventos. Por exemplo, depois de criar um novo <xref:System.Windows.Forms.Form> do objeto, talvez você queira definir seu <xref:System.Windows.Forms.Control.Text%2A> propriedade ou chamada seu <xref:System.Windows.Forms.Control.Focus%2A> método.  
  
## <a name="accessing-members"></a>Acessando membros  
 Você pode acessar membros de um objeto através da variável que faz referência a ele.  
  
#### <a name="to-access-members-of-an-object"></a>Para acessar membros de um objeto  
  
-   Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Se o membro for [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), você não precisa de uma variável para acessá-lo.  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>Acessando membros de um objeto do tipo conhecido  
 Se você souber o tipo de um objeto em tempo de compilação, você pode usar *associação inicial* para uma variável que faz referência a ele.  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Para acessar membros de um objeto para o qual você souber o tipo em tempo de compilação  
  
1.  Declare a variável de objeto para ser do tipo de objeto que você pretende atribuir à variável.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     Com `Option Strict On`, você pode atribuir apenas <xref:System.Windows.Forms.Form> objetos (ou objetos de um tipo derivam de <xref:System.Windows.Forms.Form>) para `extraForm`. Se você definiu uma classe ou estrutura com um widening `CType` conversão <xref:System.Windows.Forms.Form>, você também pode atribuir essa classe ou estrutura para `extraForm`.  
  
2.  Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Você pode acessar todos os métodos e propriedades específicas para o <xref:System.Windows.Forms.Form> classe, não importa o que o `Option Strict` é de configuração.  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>Acessando membros de um objeto de tipo desconhecido  
 Se você não souber o tipo de um objeto em tempo de compilação, você deve usar *associação tardia* para qualquer variável que faz referência a ele.  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Para acessar membros de um objeto para o qual você não souber o tipo em tempo de compilação  
  
1.  Declarar a variável de objeto para ser o [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Declarar uma variável como `Object` é o mesmo que declará-la como <xref:System.Object?displayProperty=nameWithType>.)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     Com `Option Strict On`, você pode acessar somente os membros que são definidos no <xref:System.Object> classe.  
  
2.  Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Para poder acessar os membros de qualquer objeto que você atribuir à variável de objeto, você deve definir `Option Strict Off`. Quando você fizer isso, o compilador não pode garantir que um determinado membro é exposto pelo objeto que você atribui à variável. Se o objeto não expõe um membro que você tentar acessar, uma <xref:System.MemberAccessException> ocorrerá uma exceção.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
