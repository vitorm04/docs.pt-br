---
title: Variação em delegados
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 11146bc4a60f55fc0373f0b5dfa5d44dcf748a5b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349010"
---
# <a name="variance-in-delegates-visual-basic"></a>Variance in Delegates (Visual Basic)

.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic. Isso significa que você pode atribuir a delegados não apenas os métodos que têm assinaturas correspondentes, mas também métodos que retornam tipos mais derivados (covariância) ou que aceitam parâmetros que têm tipos menos derivados (contravariância) do que o especificado pelo tipo de delegado. Isso inclui delegados genéricos e não genéricos.

Por exemplo, considere o código a seguir, que tem duas classes e dois delegados: genérico e não genérico.

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

Quando cria delegados dos tipos `SampleDelegate` ou `SampleDelegate(Of A, R)`, você pode atribuir qualquer um dos seguintes métodos a esses delegados.

```vb
' Matching signature.
Public Shared Function ASecondRFirst(
    ByVal second As Second) As First
    Return New First()
End Function

' The return type is more derived.
Public Shared Function ASecondRSecond(
    ByVal second As Second) As Second
    Return New Second()
End Function

' The argument type is less derived.
Public Shared Function AFirstRFirst(
    ByVal first As First) As First
    Return New First()
End Function

' The return type is more derived
' and the argument type is less derived.
Public Shared Function AFirstRSecond(
    ByVal first As First) As Second
    Return New Second()
End Function
```

O exemplo de código a seguir ilustra a conversão implícita entre a assinatura do método e o tipo de delegado.

```vb
' Assigning a method with a matching signature
' to a non-generic delegate. No conversion is necessary.
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a non-generic delegate.
' The implicit conversion is used.
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond

' Assigning a method with a matching signature to a generic delegate.
' No conversion is necessary.
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a generic delegate.
' The implicit conversion is used.
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond
```

For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

## <a name="variance-in-generic-type-parameters"></a>Variação em parâmetros de tipo genérico

In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.

Para habilitar a conversão implícita, você precisa declarar explicitamente os parâmetros genéricos em um delegado como covariante ou contravariante usando a palavra-chave `in` ou `out`.

O exemplo de código a seguir mostra como você pode criar um delegado que tem um parâmetro de tipo genérico covariante.

```vb
' Type T is declared covariant by using the out keyword.
Public Delegate Function SampleGenericDelegate(Of Out T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "
    ' You can assign delegates to each other,
    ' because the type T is declared covariant.
    Dim dObject As SampleGenericDelegate(Of Object) = dString
End Sub
```

Se você usar somente o suporte à para fazer a correspondência de assinaturas de método com tipos de delegados e não usar as palavras-chave `in` e `out`, você poderá perceber que, às vezes, é possível instanciar delegados com métodos ou expressões lambda idênticas, mas não é possível atribuir um delegado a outro.

In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`. Você pode corrigir esse problema marcando o parâmetro genérico `T` com a palavra-chave `out`.

```vb
Public Delegate Function SampleGenericDelegate(Of T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "

    ' You can assign the dObject delegate
    ' to the same lambda expression as dString delegate
    ' because of the variance support for
    ' matching method signatures with delegate types.
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "

    ' The following statement generates a compiler error
    ' because the generic type T is not marked as covariant.
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString

End Sub
```

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Delegados genéricos que têm parâmetros de tipo variante no .NET Framework

O .NET Framework 4 introduziu o suporte à variação para parâmetros de tipo genérico em diversos delegados genéricos existentes:

- `Action` delega do namespace <xref:System>, por exemplo, <xref:System.Action%601> e <xref:System.Action%602>

- `Func` delega do namespace <xref:System>, por exemplo, <xref:System.Func%601> e <xref:System.Func%602>

- O delegado <xref:System.Predicate%601>

- O delegado <xref:System.Comparison%601>

- O delegado <xref:System.Converter%602>

For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Declarando parâmetros de tipo variante em delegados genéricos

Se um delegado genérico tiver parâmetros de tipo genérico covariantes ou contravariantes, ele poderá ser considerado um *delegado genérico variante*.

Você pode declarar um parâmetro de tipo genérico covariante em um delegado genérico usando a palavra-chave `out`. O tipo covariante pode ser usado apenas como um tipo de retorno de método e não como um tipo de argumentos de método. O exemplo de código a seguir mostra como declarar um delegado genérico covariante.

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

Você pode declarar um parâmetro de tipo genérico contravariante em um delegado genérico usando a palavra-chave `in`. O tipo contravariante pode ser usado apenas como um tipo de argumentos de método e não como um tipo de retorno de método. O exemplo de código a seguir mostra como declarar um delegado genérico contravariante.

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> `ByRef` parameters in Visual Basic can't be marked as variant.

Também é possível dar suporte à variância e à covariância no mesmo delegado, mas para parâmetros de tipo diferente. Isso é mostrado no exemplo a seguir.

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Instanciando e invocando delegados genéricos variantes

Você pode instanciar e invocar delegados variantes da mesma forma como instancia e invoca delegados invariantes. No exemplo a seguir, um delegado é instanciado por uma expressão lambda.

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a>Combinando delegados genéricos variantes

Você não deve combinar delegados variantes. O método <xref:System.Delegate.Combine%2A> não dá suporte à conversão de delegados variantes e espera que os delegados sejam exatamente do mesmo tipo. This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Variação em parâmetros de tipo genérico para tipos de referência e valor

A variação para parâmetros de tipo genérico tem suporte apenas para tipos de referência. For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.

O exemplo a seguir demonstra que a variação em parâmetros de tipo genérico não tem suporte para tipos de valor.

```vb
' The type T is covariant.
Public Delegate Function DVariant(Of Out T)() As T
' The type T is invariant.
Public Delegate Function DInvariant(Of T)() As T
Sub Test()
    Dim i As Integer = 0
    Dim dInt As DInvariant(Of Integer) = Function() i
    Dim dVariantInt As DVariant(Of Integer) = Function() i

    ' All of the following statements generate a compiler error
    ' because type variance in generic parameters is not supported
    ' for value types, even if generic type parameters are declared variant.
    ' Dim dObject As DInvariant(Of Object) = dInt
    ' Dim dLong As DInvariant(Of Long) = dInt
    ' Dim dVariantObject As DInvariant(Of Object) = dInt
    ' Dim dVariantLong As DInvariant(Of Long) = dInt
End Sub
```

## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Relaxed Delegate Conversion in Visual Basic

Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types. For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate. For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="see-also"></a>Consulte também

- [Genéricos](../../../../standard/generics/index.md)
- [Usando variação para delegados genéricos Func e Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
