---
title: Não é possível aplicar a resolução de sobrecarga com associação tardia a '<procedurename>' porque a instância de acesso é um tipo de interface
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 7f2ae3bb0e7c09d966c53fb17b1cbe675dfce8b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814049"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>Resolução de sobrecarga com associação tardia não pode ser aplicada a '\<procedurename >' porque a instância de acesso é um tipo de interface
O compilador está tentando resolver uma referência a uma propriedade ou procedimento sobrecarregado, mas a referência falha porque um argumento é do tipo `Object` e o objeto da referência tem o tipo de dados de uma interface. O `Object` argumento força o compilador a resolver a referência de associação tardia.  
  
 Nessas circunstâncias, o compilador resolve a sobrecarga por meio da classe de implementação, em vez de por meio da interface subjacente. Se a classe renomeia uma das versões sobrecarregadas, o compilador não considera essa versão como uma sobrecarga porque seu nome é diferente. Isso por sua vez faz com que o compilador deverá ignorar a versão renomeada quando ela pode ter sido a escolha correta para resolver a referência.  
  
 **ID do erro:** BC30933  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use `CType` para lançar um argumento de `Object` para o tipo especificado pela assinatura da sobrecarga que você deseja chamar.  
  
     Observe que ele não ajuda a converter o objeto que faz referência a interface subjacente. Você deve converter o argumento para evitar esse erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma chamada para uma sobrecarga `Sub` procedimento que causa esse erro em tempo de compilação.  
  
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
  
 No exemplo anterior, se o compilador permitia a chamada para `s1` conforme foi escrito, a resolução podem ocorrer por meio da classe `c1` em vez da interface `i1`. Isso significa que o compilador não consideraria `s2` porque seu nome é diferente `c1`, mesmo que ele seja a escolha correta, conforme definido pelo `i1`.  
  
 Você pode corrigir o erro alterando a chamada para qualquer uma das seguintes linhas de código:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Cada uma das linhas de código converte explicitamente o `Object` variável `o1` para um dos tipos de parâmetro definido para as sobrecargas.  
  
## <a name="see-also"></a>Consulte também

- [Sobrecarga de Procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Resolução de Sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)
