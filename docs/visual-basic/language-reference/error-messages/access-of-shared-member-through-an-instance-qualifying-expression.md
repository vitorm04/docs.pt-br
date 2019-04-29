---
title: Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 8e6ddab16c59d7ce95d96b377e3f372f6ebe5278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751599"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada
Uma variável de instância de uma classe ou estrutura é usada para acessar um `Shared` variável, propriedade, procedimento ou evento definido na classe ou estrutura. Esse aviso também pode ocorrer se uma variável de instância é usada para acessar um membro implicitamente compartilhado de uma classe ou estrutura, como uma constante ou enumeração, ou uma classe aninhada ou estrutura.  
  
 A finalidade de compartilhar um membro é apenas uma única cópia desse membro de criar e disponibilizar essa cópia única para todas as instâncias da classe ou estrutura na qual ela é declarada. Ele fiquem consistentes com essa finalidade para acessar um `Shared` membro por meio do nome de sua classe ou estrutura, em vez de por meio de uma variável que contém uma instância individual da classe ou estrutura.  
  
 Acessando uma `Shared` membro por meio de uma variável de instância pode tornar seu código mais difícil de entender, ocultando o fato de que o membro é `Shared`. Além disso, se tal acesso for parte de uma expressão que executa outras ações, como um `Function` procedimento que retorna uma instância de membro compartilhado, o Visual Basic ignora a expressão e quaisquer outras ações que ele executaria.  
  
 Para obter mais informações e um exemplo, consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42025  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Use o nome da classe ou estrutura que define o `Shared` membro para acessá-lo, conforme mostrado no exemplo a seguir.  
  
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
>  Ser alerta para os efeitos de escopo quando dois elementos de programação têm o mesmo nome. No exemplo anterior, se você declarar uma instância por meio `Dim testClass as testClass = Nothing`, o compilador trata uma chamada para `testClass.sayHello()` como um acesso do método por meio do nome de classe e nenhum aviso ocorre.  
  
## <a name="see-also"></a>Consulte também

- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Escopo no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
