---
title: "Criando Interfaces genéricas variáveis (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 324e2a906e84950aa9019bbf68a524458492646e
ms.lasthandoff: 03/13/2017

---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Criando Interfaces genéricas variantes (Visual Basic)
Você pode declarar parâmetros de tipo genérico em interfaces como covariant ou contravariant. *Covariância* permite que os métodos de interface mais derivada tipos de retorno daquele definido pelos parâmetros de tipo genérico. *Contravariância* permite que os métodos de interface com tipos de argumento que são menos derivados que aquele especificado pelos parâmetros genéricos. Uma interface genérica que tenha covariant ou contravariant parâmetros de tipo genérico é chamado *variante*.  
  
> [!NOTE]
>  O .NET framework 4 introduziu o suporte de variação de várias interfaces genéricas existentes. Para obter a lista das interfaces de variantes no .NET Framework, consulte [variação em Interfaces genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Declaração Interfaces genéricas variáveis  
 Você pode declarar interfaces genéricas variáveis usando a `in` e `out` palavras-chave para parâmetros de tipo genérico.  
  
> [!IMPORTANT]
>  `ByRef`os parâmetros no Visual Basic não podem ser variant. Tipos de valor também têm suporte para variação.  
  
 Você pode declarar um parâmetro de tipo genérico covariante usando o `out` palavra-chave. O tipo de covariante deve satisfazer as condições a seguir:  
  
-   O tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos do método. Isso é ilustrado no exemplo a seguir, no qual o tipo `R` é declarado covariante.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     Há uma exceção a essa regra. Se você tiver um delegado genérico contravariant como um parâmetro de método, você pode usar o tipo como um parâmetro de tipo genérico para o delegado. Isso é ilustrado pelo tipo `R` no exemplo a seguir. Para obter mais informações, consulte [variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [usando variação para delegações Func e Action genérica (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   O tipo não é usado como uma restrição genérica para os métodos de interface. Isso é ilustrado no código a seguir.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 Você pode declarar um contravariant de parâmetro de tipo genérico usando o `in` palavra-chave. O tipo contravariant pode ser usado apenas como um tipo de argumentos de método e não como um tipo de retorno dos métodos de interface. O tipo contravariant também pode ser usado para restrições genéricas. O código a seguir mostra como declarar uma interface contravariant e usar uma restrição genérica para um de seus métodos.  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 Também é possível oferecer suporte a covariância e contravariância na mesma interface, mas para os parâmetros de tipo diferente, conforme mostrado no exemplo de código a seguir.  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 No Visual Basic, você não pode declarar os eventos em interfaces variantes sem especificar o tipo de delegado. Além disso, uma interface variante não pode ter aninhado classes, enums ou estruturas, mas podem ter aninhados interfaces. Isso é ilustrado no código a seguir.  
  
```vb  
Interface ICovariant(Of Out R)  
    ' The following statement generates a compiler error.  
    ' Event SampleEvent()  
    ' The following statement specifies the delegate type and   
    ' does not generate an error.  
    Event AnotherEvent As EventHandler  
  
    ' The following statements generate compiler errors,  
    ' because a variant interface cannot have  
    ' nested enums, classes, or structures.  
  
    'Enum SampleEnum : test : End Enum  
    'Class SampleClass : End Class  
    'Structure SampleStructure : Dim value As Integer : End Structure  
  
    ' Variant interfaces can have nested interfaces.  
    Interface INested : End Interface  
End Interface  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Implementando Interfaces genéricas variáveis  
 Você pode implementar interfaces genéricas variáveis em classes usando a mesma sintaxe que é usada para interfaces invariáveis. O exemplo de código a seguir mostra como implementar uma interface covariante em uma classe genérica.  
  
```vb  
Interface ICovariant(Of Out R)  
    Function GetSomething() As R  
End Interface  
  
Class SampleImplementation(Of R)  
    Implements ICovariant(Of R)  
    Public Function GetSomething() As R _  
    Implements ICovariant(Of R).GetSomething  
        ' Some code.  
    End Function  
End Class  
```  
  
 Classes que implementam interfaces variantes são invariáveis. Por exemplo, considere o código a seguir.  
  
```vb  
 The interface is covariant.  
Dim ibutton As ICovariant(Of Button) =  
    New SampleImplementation(Of Button)  
Dim iobj As ICovariant(Of Object) = ibutton  
  
' The class is invariant.  
Dim button As SampleImplementation(Of Button) =  
    New SampleImplementation(Of Button)  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim obj As SampleImplementation(Of Object) = button  
```  
  
## <a name="extending-variant-generic-interfaces"></a>Estendendo Interfaces genéricas variáveis  
 Quando você estende uma interface genérica variante, você deve usar o `in` e `out` palavras-chave para especificar explicitamente se a interface derivada oferece suporte a variação. O compilador não deduzir a variação da interface que está sendo estendida. Por exemplo, considere as seguintes interfaces.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T)  
End Interface  
  
Interface IExtCovariant(Of Out T)  
    Inherits ICovariant(Of T)  
End Interface  
```  
  
 No `Invariant(Of T)` de interface, o parâmetro de tipo genérico `T` é invariável, enquanto no `IExtCovariant (Of Out T)`o parâmetro de tipo é covariante, embora ambas as interfaces estendem a mesma interface. A mesma regra é aplicada aos parâmetros de tipo genérico contravariant.  
  
 Você pode criar uma interface que estende tanto o interface em que o parâmetro de tipo genérico `T` é covariante e a interface onde é contravariant em caso da estender o parâmetro de tipo genérico de interface `T` é invariável. Isso é ilustrado no exemplo de código a seguir.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 No entanto, se um parâmetro de tipo genérico `T` é declarado covariante em uma interface, você não pode declará-lo contravariant na interface de extensão, ou vice-versa. Isso é ilustrado no exemplo de código a seguir.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>Evitar ambiguidade  
 Ao implementar interfaces genéricas variantes, variação, às vezes, pode levar a ambiguidade. Isso deve ser evitado.  
  
 Por exemplo, se você implementar explicitamente a mesma interface genérica variante com parâmetros de tipo genérico diferentes em uma classe, ele pode criar ambiguidade. O compilador não produz um erro nesse caso, mas ele não estiver especificado qual implementação de interface será escolhida em tempo de execução. Isso pode levar a erros sutis no seu código. Considere o exemplo de código a seguir.  
  
> [!NOTE]
>  Com `Option Strict Off`, Visual Basic gera um aviso de compilador quando há uma implementação de interface ambíguo. Com `Option Strict On`, Visual Basic gera um erro do compilador.  
  
```vb  
' Simple class hierarchy.  
Class Animal  
End Class  
  
Class Cat  
    Inherits Animal  
End Class  
  
Class Dog  
    Inherits Animal  
End Class  
  
' This class introduces ambiguity  
' because IEnumerable(Of Out T) is covariant.  
Class Pets  
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)  
  
    Public Function GetEnumerator() As IEnumerator(Of Cat) _  
        Implements IEnumerable(Of Cat).GetEnumerator  
        Console.WriteLine("Cat")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator(Of Dog) _  
        Implements IEnumerable(Of Dog).GetEnumerator  
        Console.WriteLine("Dog")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator2() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
        ' Some code.  
    End Function  
End Class  
  
Sub Main()  
    Dim pets As IEnumerable(Of Animal) = New Pets()  
    pets.GetEnumerator()  
End Sub  
```  
  
 Neste exemplo, ele está especificado como o `pets.GetEnumerator` método escolhe entre `Cat` e `Dog`. Isso pode causar problemas em seu código.  
  
## <a name="see-also"></a>Consulte também  
 [Variação em Interfaces genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)   
 [Usando variação para delegações Func e Action genérica (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
