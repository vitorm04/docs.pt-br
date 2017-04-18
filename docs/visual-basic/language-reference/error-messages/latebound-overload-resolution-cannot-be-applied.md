---
title: "Resolução de sobrecarga com associação tardia não pode ser aplicada a &quot;&lt;procedurename&gt;&quot; porque a instância de acesso é um tipo de interface | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
dev_langs:
- VB
helpviewer_keywords:
- overload resolution, with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 861aa0514dcf77af45daee15a91e521a2ccda9ea
ms.lasthandoff: 03/13/2017

---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>Resolução de sobrecarga com associação tardia não pode ser aplicada a '&lt;procedurename&gt;' porque a instância de acesso é um tipo de interface
O compilador está tentando resolver uma referência a uma propriedade ou procedimento sobrecarregado, mas a referência falha porque um argumento é do tipo `Object` e o objeto da referência possui o tipo de dados de uma interface. O `Object` argumento força o compilador a resolver a referência de ligação tardia.  
  
 Nessas circunstâncias, o compilador resolve o sobrecarregamento através da classe de implementação, em vez de por meio da interface subjacente. Se a classe renomeia uma das versões sobrecarregadas, o compilador não considera que aquela versão seja um sobrecarregamento porque seu nome é diferente. Isso por sua vez faz o compilador ignorar a versão renomeada quando ela pode ter sido a escolha correta para resolver a referência.  
  
 **ID do erro:** BC30933  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use `CType` para lançar um argumento de `Object` para o tipo especificado pela assinatura do sobrecarregamento que você deseja chamar.  
  
     Observe que isso não ajuda a converter o objeto que faz referência a interface subjacente. Você deve converter o argumento para evitar esse erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma chamada para um sobrecarregado `Sub` procedimento que causa esse erro em tempo de compilação.  
  
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
  
 No exemplo anterior, se o compilador permitisse a chamada a `s1` como escrito, a resolução teria se realizado através da classe `c1` em vez da interface `i1`. Isso significa que o compilador não consideraria `s2` porque seu nome é diferente em `c1`, embora seja a escolha correta como definido pelo `i1`.  
  
 Você pode corrigir o erro alterando a chamada para qualquer uma das seguintes linhas de código:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Cada uma das linhas de código explicitamente converte o `Object` variável `o1` para um dos tipos de parâmetro definido para as sobrecargas.  
  
## <a name="see-also"></a>Consulte também  
 [Sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Resolução de sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)
