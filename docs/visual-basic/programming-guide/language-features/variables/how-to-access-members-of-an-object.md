---
title: 'Como: Acessar membros de um objeto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: de00e428cc3d9d7a5688e853b0ff4295fec5b3e9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322752"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Como: Acessar membros de um objeto (Visual Basic)
Quando você tiver uma variável de objeto que se refere a um objeto, você geralmente deseja trabalhar com os membros desse objeto, como seus métodos, propriedades, campos e eventos. Por exemplo, depois de criar um novo <xref:System.Windows.Forms.Form> do objeto, você poderá definir seus <xref:System.Windows.Forms.Control.Text%2A> propriedade ou chamada seu <xref:System.Windows.Forms.Control.Focus%2A> método.  
  
## <a name="accessing-members"></a>Acessando membros  
 Você pode acessar membros de um objeto por meio da variável que faz referência a ele.  
  
#### <a name="to-access-members-of-an-object"></a>Para acessar membros de um objeto  
  
-   Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Se o membro for [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), você não precisa de uma variável para acessá-lo.  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>Acessando membros de um objeto do tipo conhecido  
 Se você souber o tipo de um objeto em tempo de compilação, você pode usar *vinculação inicial* para uma variável que faz referência a ele.  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Para acessar membros de um objeto para o qual você sabe o tipo em tempo de compilação  
  
1. Declare a variável de objeto para ser do tipo do objeto que você pretende atribuir à variável.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     Com o `Option Strict On`, você pode atribuir apenas <xref:System.Windows.Forms.Form> objetos (ou objetos de um tipo derivam de <xref:System.Windows.Forms.Form>) para `extraForm`. Se você definiu uma classe ou estrutura com uma ampliação `CType` conversão <xref:System.Windows.Forms.Form>, você também pode atribuir essa classe ou estrutura para `extraForm`.  
  
2. Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Você pode acessar todos os métodos e propriedades específicas para o <xref:System.Windows.Forms.Form> classe, não importa o que o `Option Strict` é de configuração.  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>Acessando membros de um objeto de tipo desconhecido  
 Se você não souber o tipo de um objeto em tempo de compilação, você deve usar *ligação tardia* para qualquer variável que faz referência a ele.  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Para acessar membros de um objeto para o qual você não souber o tipo em tempo de compilação  
  
1. Declarar a variável de objeto para ser o [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Declarando uma variável como `Object` é o mesmo que declarar como <xref:System.Object?displayProperty=nameWithType>.)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     Com o `Option Strict On`, você pode acessar somente os membros que são definidos na <xref:System.Object> classe.  
  
2. Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Para poder acessar os membros de qualquer objeto que você atribui à variável de objeto, você deve definir `Option Strict Off`. Quando você fizer isso, o compilador não pode garantir que um determinado membro é exposto pelo objeto que você atribui à variável. Se o objeto não expõe um membro que você tentar acessar, um <xref:System.MemberAccessException> ocorrerá uma exceção.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Declaração de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
