---
title: 'Como: acessar membros de um objeto (Visual Basic) | Documentos do Microsoft'
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
- members, accessing
- object variables, accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: 20
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
ms.openlocfilehash: e832a0c1922f567f4ed253711f97ee0043a49982
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Como acessar membros de um objeto (Visual Basic)
Quando você tiver uma variável de objeto que se refere a um objeto, você geralmente deseja trabalhar com os membros desse objeto, como seus métodos, propriedades, campos e eventos. Por exemplo, depois de ter criado um novo <xref:System.Windows.Forms.Form>de objeto, você talvez queira definir seu <xref:System.Windows.Forms.Control.Text%2A>propriedade ou chamada seu <xref:System.Windows.Forms.Control.Focus%2A>método.</xref:System.Windows.Forms.Control.Focus%2A> </xref:System.Windows.Forms.Control.Text%2A> </xref:System.Windows.Forms.Form>  
  
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
  
1.  Declare a variável de objeto para ser do tipo de objeto que você pretende atribuir à variável.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     Com `Option Strict On`, você pode atribuir apenas <xref:System.Windows.Forms.Form>objetos (ou objetos de um tipo derivam de <xref:System.Windows.Forms.Form>) para `extraForm`.</xref:System.Windows.Forms.Form> </xref:System.Windows.Forms.Form> Se você tiver definido uma classe ou estrutura com uma ampliação `CType` conversão em <xref:System.Windows.Forms.Form>, você também pode atribuir essa classe ou estrutura para `extraForm`.</xref:System.Windows.Forms.Form>  
  
2.  Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Você pode acessar todos os métodos e propriedades específicas para o <xref:System.Windows.Forms.Form>classe, não importa o que o `Option Strict` configuração é</xref:System.Windows.Forms.Form>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>Acessando membros de um objeto de tipo desconhecido  
 Se você não souber o tipo de um objeto em tempo de compilação, você deve usar *ligação tardia* para qualquer variável que faz referência a ele.  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Para acessar membros de um objeto para o qual você não sabe o tipo em tempo de compilação  
  
1.  Declarar a variável de objeto para ser o [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Declarar uma variável como `Object` é o mesmo que declarar como <xref:System.Object?displayProperty=fullName>.)</xref:System.Object?displayProperty=fullName>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     Com `Option Strict On`, você pode acessar somente os membros que são definidos na <xref:System.Object>classe.</xref:System.Object>  
  
2.  Use o operador de acesso de membro (`.`) entre o nome da variável de objeto e o nome do membro.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Para poder acessar os membros de qualquer objeto que você atribuir à variável de objeto, você deve definir `Option Strict Off`. Quando você fizer isso, o compilador não pode garantir que um determinado membro é exposto pelo objeto que você atribui à variável. Se o objeto não expõe um membro que você tentar acessar, uma <xref:System.MemberAccessException>ocorrerá uma exceção.</xref:System.MemberAccessException>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object></xref:System.Object>   
 <xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form>   
 <xref:System.MemberAccessException></xref:System.MemberAccessException>   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Declaração de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
