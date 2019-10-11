---
title: Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 773a97c301e7cb5bec0234ae466d487ec9716437
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250343"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada

Uma variável de instância de uma classe ou estrutura é usada para acessar uma variável, uma propriedade, um procedimento ou um evento `Shared` definido nessa classe ou estrutura. Esse aviso também pode ocorrer se uma variável de instância for usada para acessar um membro implicitamente compartilhado de uma classe ou estrutura, como uma constante ou enumeração, ou uma classe ou estrutura aninhada.

A finalidade de compartilhar um membro é criar apenas uma única cópia desse membro e disponibilizar essa cópia única para cada instância da classe ou estrutura na qual ela é declarada. Ele é consistente com essa finalidade para acessar um membro `Shared` por meio do nome de sua classe ou estrutura, em vez de uma variável que mantém uma instância individual dessa classe ou estrutura.

Acessar um membro `Shared` por meio de uma variável de instância pode tornar seu código mais difícil de entender ao obscurecer o fato de que o membro é `Shared`. Além disso, se esse acesso for parte de uma expressão que executa outras ações, como um procedimento `Function` que retorna uma instância do membro compartilhado, Visual Basic ignora a expressão e quaisquer outras ações que poderiam ser executadas.  
  
Para obter mais informações e um exemplo, consulte [compartilhado](../modifiers/shared.md).  
  
Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
**ID do erro:** BC42025  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
Use o nome da classe ou estrutura que define o membro `Shared` para acessá-lo, conforme mostrado no exemplo a seguir:
  
```vb
Public Class TestClass
    Public Shared Sub SayHello()
        MsgBox("Hello")
    End Sub
End Class
  
Module Program
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New TestClass()
        tc.SayHello()
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        TestClass.SayHello()
    End Sub  
End Module  
```  
  
> [!NOTE]
> Seja alerta para os efeitos do escopo quando dois elementos de programação tiverem o mesmo nome. No exemplo anterior, se você declarar uma instância usando `Dim testClass as testClass = Nothing`, o compilador tratará uma chamada para `testClass.sayHello()` como um acesso do método por meio do nome da classe e não ocorrerá nenhum aviso.
  
## <a name="see-also"></a>Consulte também

- [Compartilhado](../modifiers/shared.md)
- [Escopo no Visual Basic](../../programming-guide/language-features/declared-elements/scope.md)
