---
title: "Não é possível inferir o(s) tipo(s) de dados do(s) parâmetro(s) de tipo a partir destes argumentos"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b290c25286dce2236823919e8287db9abefc0dd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>Não é possível inferir o(s) tipo(s) de dados do(s) parâmetro(s) de tipo a partir destes argumentos
Tipos de dados dos parâmetros de tipo não podem ser inferidos a partir destes argumentos. Especificando os dados tipos explicitamente talvez corrija esse erro.  
  
 Esse erro ocorre quando ocorre falha na resolução de sobrecarga. Isso ocorre como uma mensagem subordinada que indica por que um candidato a sobrecarga específica foi eliminado. A mensagem de erro explica que o compilador não pode usar a inferência de tipo para localizar tipos de dados para os parâmetros de tipo.  
  
> [!NOTE]
>  Quando especificar argumentos não é uma opção (por exemplo, para operadores de consulta em expressões de consulta), a mensagem de erro aparece sem a segunda frase.  
  
 O código a seguir demonstra o erro.  
  
```vb  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 **ID do erro:** BC36647 e BC36644  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Você poderá especificar um tipo de dados para o parâmetro de tipo ou os parâmetros em vez de depender de inferência de tipo.  
  
## <a name="see-also"></a>Consulte também  
 [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Procedimentos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
