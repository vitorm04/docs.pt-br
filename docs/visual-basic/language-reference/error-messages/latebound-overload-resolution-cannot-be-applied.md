---
title: "Resolução de sobrecarga latebound não pode ser aplicada a &#39; &lt;procedurename&gt;&#39; porque a instância de acesso é um tipo de interface"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>Resolução de sobrecarga latebound não pode ser aplicada a &#39; &lt;procedurename&gt;&#39; porque a instância de acesso é um tipo de interface
O compilador está tentando resolver uma referência a uma propriedade ou procedimento sobrecarregado, mas a referência falha porque um argumento é do tipo `Object` e o objeto da referência possui o tipo de dados de uma interface. O `Object` argumento força o compilador para resolver a referência de associação tardia.  
  
 Nessas circunstâncias, o compilador resolve a sobrecarga por meio da classe de implementação, em vez de por meio da interface subjacente. Se a classe renomeia uma das versões sobrecarregadas, o compilador não considera que a versão seja um sobrecarregamento porque seu nome é diferente. Por sua vez, isso faz o compilador ignorar a versão renomeada quando ela pode ter sido a escolha correta para resolver a referência.  
  
 **ID do erro:** BC30933  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use `CType` para converter o argumento de `Object` para o tipo especificado pela assinatura da sobrecarga que você deseja chamar.  
  
     Observe que isso não ajuda para converter o objeto que faz referência a interface subjacente. Você deve converter o argumento para evitar esse erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma chamada para um sobrecarregados `Sub` procedimento que causa esse erro em tempo de compilação.  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 No exemplo anterior, se o compilador permitisse a chamada a `s1` como escrito, a resolução teria se realizado por meio da classe `c1` em vez da interface `i1`. Isso significa que o compilador não consideraria `s2` porque seu nome é diferente em `c1`, mesmo que é a opção correta conforme definido pelo `i1`.  
  
 Você pode corrigir o erro alterando a chamada para qualquer uma das linhas de código a seguir:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Cada uma das linhas de código converte explicitamente o `Object` variável `o1` para um dos tipos de parâmetro definidos para as sobrecargas.  
  
## <a name="see-also"></a>Consulte também  
 [Sobrecarga de Procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Resolução de Sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)
