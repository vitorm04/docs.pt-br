---
title: "Acesso de membro compartilhado através de uma instância; a expressão de qualificação não será avaliada | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
dev_langs:
- VB
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
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
ms.openlocfilehash: 39be3c95d5acc20afe3a33be9d4db48c09f99a9c
ms.lasthandoff: 03/13/2017

---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada
Uma variável de instância de uma classe ou estrutura é usada para acessar um `Shared` variável, propriedade, procedimento ou evento definido na classe ou estrutura. Esse aviso também pode ocorrer se uma variável de instância é usada para acessar um membro implicitamente compartilhado de uma classe ou estrutura, como uma constante de enumeração, ou uma classe aninhada ou estrutura.  
  
 A finalidade de compartilhar um membro é criar uma única cópia do membro e disponibilizar essa cópia única para cada instância da classe ou estrutura na qual ela é declarada. É consistente com essa finalidade para acessar um `Shared` membro através do nome de sua classe ou estrutura, e não por meio de uma variável que contém uma instância individual da classe ou estrutura.  
  
 Acessando um `Shared` membro por meio de uma variável de instância pode tornar seu código mais difícil de entender, ocultando o fato de que o membro é `Shared`. Além disso, se esse acesso é parte de uma expressão que executa outras ações, como um `Function` procedimento que retorna uma instância de membro compartilhado, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ignora a expressão e quaisquer outras ações executaria caso contrário.  
  
 Para obter mais informações e um exemplo, consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42025  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use o nome da classe ou estrutura que define o `Shared` membro para acessá-lo, conforme mostrado no exemplo a seguir.  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  Esteja alerta os efeitos do escopo quando dois elementos de programação com o mesmo nome. No exemplo anterior, se você declarar uma instância usando `Dim testClass as testClass = Nothing`, o compilador trata uma chamada para `testClass.sayHello()` quando ocorre um acesso do método com o nome da classe e nenhum aviso.  
  
## <a name="see-also"></a>Consulte também  
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Escopo no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
