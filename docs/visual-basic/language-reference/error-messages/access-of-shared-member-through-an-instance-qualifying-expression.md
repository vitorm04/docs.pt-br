---
title: Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9bbec233435ab728657c1b99e26ab157d4657093
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada
Uma variável de instância de uma classe ou estrutura é usada para acessar um `Shared` variável, propriedade, procedimento ou evento definido na classe ou estrutura. Esse aviso também pode ocorrer se uma variável de instância é usada para acessar um membro implicitamente compartilhado de uma classe ou estrutura, como uma constante de enumeração, ou uma classe aninhada ou estrutura.  
  
 A finalidade de compartilhar um membro é criar uma única cópia do membro e disponibilizar essa cópia única para cada instância da classe ou estrutura na qual ela é declarada. É consistente com essa finalidade para acessar um `Shared` membro por meio do nome de sua classe ou estrutura, em vez de por meio de uma variável que contém uma instância individual de classe ou estrutura.  
  
 Acessando um `Shared` membro por meio de uma variável de instância pode tornar seu código mais difícil de entender, ocultando o fato de que o membro é `Shared`. Além disso, se tal acesso for parte de uma expressão que executa outras ações, como uma `Function` procedimento que retorna uma instância do membro compartilhado, o Visual Basic ignora a expressão e quaisquer outras ações executaria caso contrário.  
  
 Para obter mais informações e um exemplo, consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
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
>  Ser alerta para os efeitos de escopo quando dois elementos de programação com o mesmo nome. No exemplo anterior, se você declarar uma instância usando `Dim testClass as testClass = Nothing`, o compilador trata uma chamada para `testClass.sayHello()` como o acesso do método por meio do nome da classe e nenhum aviso ocorre.  
  
## <a name="see-also"></a>Consulte também  
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Escopo no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
