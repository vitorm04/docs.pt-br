---
title: "Expressão lambda não será removida deste manipulador de eventos | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42326
- vbc42326
dev_langs:
- VB
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
caps.latest.revision: 8
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
ms.openlocfilehash: bdf7ad8f8a116c818e72d67150d72d0c96a4dc3b
ms.lasthandoff: 03/13/2017

---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>A expressão lambda não será removida deste manipulador de eventos
A expressão lambda não será removida deste manipulador de eventos. Atribua a expressão lambda a uma variável e use a variável para adicionar e remover o evento.  
  
 Quando as expressões lambda são usadas com manipuladores de eventos, você não verá o comportamento esperado. O compilador gera um novo método para cada definição da expressão lambda, mesmo se eles forem idênticos. Portanto, o código a seguir exibe `False`.  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1  
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1  
        Console.WriteLine(fun1 = fun2)  
    End Sub  
  
    Delegate Function ChangeInteger(ByVal x As Integer) As Integer  
  
End Module  
```  
  
 Quando as expressões lambda são usadas com manipuladores de eventos, isso pode causar resultados inesperados. No exemplo a seguir, a expressão lambda é adicionado por `AddHandler` não é removido o `RemoveHandler` instrução.  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Sub Main()  
  
        ' The following line adds one listener to the event.  
        AddHandler ProcessInteger, Function(m As Integer) m  
  
        ' The following statement searches the current listeners   
        ' for a match to remove. However, this lambda is not the same  
        ' as the previous one, so nothing is removed.  
        RemoveHandler ProcessInteger, Function(m As Integer) m  
  
    End Sub  
End Module  
```  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42326  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Para evitar o aviso e remova a expressão lambda, atribua a expressão lambda a uma variável e usar a variável em ambos os `AddHandler` e `RemoveHandler` instruções, conforme mostrado no exemplo a seguir.  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Dim PrintHandler As ProcessIntegerEventHandler  
  
    Sub Main()  
  
        ' Assign the lambda expression to a variable.  
        PrintHandler = Function(m As Integer) m  
  
        ' Use the variable to add the listener.  
        AddHandler ProcessInteger, PrintHandler  
  
        ' Use the variable again when you want to remove the listener.  
        RemoveHandler ProcessInteger, PrintHandler  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a>Consulte também  
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
