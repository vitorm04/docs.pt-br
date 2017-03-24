---
title: "Variação em delegações (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cbab7da8c97ca202f8a4d0a1a65b8fa240cca32d
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-delegates-visual-basic"></a>Variação em delegações (Visual Basic)
.NET framework 3.5 introduziu o suporte a variação para assinaturas de método correspondentes com tipos de delegados em todos os delegados em c# e Visual Basic. Isso significa que você pode atribuir a representantes não apenas métodos que têm assinaturas correspondentes, mas também métodos que retornam tipos (covariância) mais derivados ou que aceitam parâmetros que têm menos tipos derivados (contravariância) que o especificado pelo tipo de delegado. Isso inclui delegados genéricos e não genérico.  
  
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
  
 Quando você cria delegados do `SampleDelegate` ou `SampleDelegate(Of A, R)` tipos, você pode atribuir qualquer um dos seguintes métodos para esses delegados.  
  
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
  
 Para obter mais exemplos, consulte [usando variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) e [usando variação para delegações Func e Action genérica (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Variação em parâmetros de tipo genérico  
 No .NET Framework 4 e posterior, você pode habilitar a conversão implícita entre delegados, para que possam ser atribuídos representantes genéricos com diferentes tipos especificados pelos parâmetros de tipo genérico uns aos outros, se os tipos são herdados de si conforme exigido por variância.  
  
 Para habilitar a conversão implícita, você deve declarar explicitamente os parâmetros genéricos em um delegado como covariant ou contravariant usando o `in` ou `out` palavra-chave.  
  
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
  
 Se você usar somente suporte a variação para corresponder assinaturas de método com tipos delegados e não use o `in` e `out` palavras-chave, você pode achar que, às vezes, você pode instanciar delegados com métodos ou expressões lambda idênticas, mas não é possível atribuir um delegado para outro.  
  
 No exemplo de código a seguir, `SampleGenericDelegate(Of String)` não pode ser explicitamente convertido em `SampleGenericDelegate(Of Object)`, embora `String` herda `Object`. Você pode corrigir esse problema, marcando o parâmetro genérico `T` com o `out` palavra-chave.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Parâmetros de tipo de delegados genéricos com Variant no .NET Framework  
 .NET framework 4 introduziu o suporte de variação de parâmetros de tipo genérico em vários representantes genéricos existentes:  
  
-   `Action`delega a <xref:System>espaço para nome, por exemplo, <xref:System.Action%601>e <xref:System.Action%602></xref:System.Action%602> </xref:System.Action%601> </xref:System>  
  
-   `Func`delega a <xref:System>espaço para nome, por exemplo, <xref:System.Func%601>e <xref:System.Func%602></xref:System.Func%602> </xref:System.Func%601> </xref:System>  
  
-   O <xref:System.Predicate%601>delegado</xref:System.Predicate%601>  
  
-   O <xref:System.Comparison%601>delegado</xref:System.Comparison%601>  
  
-   O <xref:System.Converter%602>delegado</xref:System.Converter%602>  
  
 Para obter mais informações e exemplos, consulte [usando variação para delegações Func e Action genérica (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Declarar parâmetros de tipo Variant em delegados genéricos  
 Se um delegado genérico tem covariant ou contravariant parâmetros de tipo genérico, ele pode ser considerado um *delegado genérico variante*.  
  
 Você pode declarar um parâmetro de tipo genérico covariante um delegado genérico usando o `out` palavra-chave. O tipo de covariante pode ser usado apenas como um tipo de retorno do método e não como um tipo de argumentos do método. O exemplo de código a seguir mostra como declarar um delegado genérico covariante.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Você pode declarar um contravariant de parâmetro de tipo genérico em um delegado genérico usando o `in` palavra-chave. O tipo contravariant pode ser usado apenas como um tipo de argumentos de método e não como um tipo de retorno do método. O exemplo de código a seguir mostra como declarar um delegado genérico contravariant.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  `ByRef`parâmetros no Visual Basic não podem ser marcados como variante.  
  
 Também é possível oferecer suporte a variância e covariância o mesmo delegado, mas para os parâmetros de tipo diferente. Isso é mostrado no exemplo a seguir.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Instanciar e invocando delegados genéricos variantes  
 Você pode criar uma instância e invocam delegados variantes como instanciar e invocam delegados invariáveis. No exemplo a seguir, o delegado é instanciado por uma expressão lambda.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
### <a name="combining-variant-generic-delegates"></a>A combinação de delegados genéricos variantes  
 Você não deve combinar delegados variantes. O <xref:System.Delegate.Combine%2A>método não dá suporte a conversão de delegado variant e delegados a ser exatamente o mesmo tipo de espera.</xref:System.Delegate.Combine%2A> Isso pode levar a uma exceção de tempo de execução quando você combina delegados usando o <xref:System.Delegate.Combine%2A>método (em c# e Visual Basic) ou usando o `+` operador (em c#), conforme mostrado no exemplo de código a seguir.</xref:System.Delegate.Combine%2A>  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Variância em parâmetros de tipo genérico para tipos de referência e valor  
 Variância de parâmetros de tipo genérico tem suporte para somente tipos de referência. Por exemplo, `DVariant(Of Int)`não pode ser convertido implicitamente em `DVariant(Of Object)` ou `DVariant(Of Long)`, pois inteiro é um tipo de valor.  
  
 O exemplo a seguir demonstra essa variação no tipo genérico parâmetros não há suporte para tipos de valor.  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Conversão de delegado reduzida no Visual Basic  
 Conversão de delegado reduzida permite mais flexibilidade na correspondência de assinaturas de método com tipos delegados. Por exemplo, ele permite omitir as especificações do parâmetro e omitir valores de retorno da função quando você atribui um método a um delegado. Para obter mais informações, consulte [conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="see-also"></a>Consulte também  
 [Classes genéricas](https://msdn.microsoft.com/library/ms172192)   
 [Usando variação para delegações Func e Action genérica (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
