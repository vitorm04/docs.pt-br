---
title: "Como: adicionar métodos personalizados para consultas LINQ (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
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
ms.openlocfilehash: 166eb731d41e009c374ba55f929eed302793ecd0
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Como: adicionar métodos personalizados para consultas LINQ (Visual Basic)
Você pode estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando métodos de extensão para o <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601> Por exemplo, além do padrão médio ou máximo de operações, você pode criar um método de agregação personalizado para calcular um valor único de uma sequência de valores. Você também pode criar um método que funciona como um filtro personalizado ou uma transformação de dados específicos para uma sequência de valores e retorna uma nova sequência. São exemplos de tais métodos <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>e <xref:System.Linq.Enumerable.Reverse%2A>.</xref:System.Linq.Enumerable.Reverse%2A> </xref:System.Linq.Enumerable.Skip%2A> </xref:System.Linq.Enumerable.Distinct%2A>  
  
 Quando você estende o <xref:System.Collections.Generic.IEnumerable%601>interface, você pode aplicar seus métodos personalizados para qualquer coleção enumerável.</xref:System.Collections.Generic.IEnumerable%601> Para obter mais informações, consulte [métodos de extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Adicionar um método de agregação  
 Um método de agregação computa um valor único de um conjunto de valores. LINQ fornece vários métodos de agregação, incluindo <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>e <xref:System.Linq.Enumerable.Max%2A>.</xref:System.Linq.Enumerable.Max%2A> </xref:System.Linq.Enumerable.Min%2A> </xref:System.Linq.Enumerable.Average%2A> Você pode criar seu próprio método de agregação, adicionando um método de extensão para o <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601>  
  
 O exemplo de código a seguir mostra como criar um método de extensão chamado `Median` para calcular uma média para uma sequência de números do tipo `double`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module LINQExtension  
  
    ' Extension method for the IEnumerable(of T) interface.   
    ' The method accepts only values of the Double type.  
    <Extension()>   
    Function Median(ByVal source As IEnumerable(Of Double)) As Double  
        If source.Count = 0 Then  
            Throw New InvalidOperationException("Cannot compute median for an empty set.")  
        End If  
  
        Dim sortedSource = From number In source   
                           Order By number  
  
        Dim itemIndex = sortedSource.Count \ 2  
  
        If sortedSource.Count Mod 2 = 0 Then  
            ' Even number of items in list.  
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2  
        Else  
            ' Odd number of items in list.  
            Return sortedSource(itemIndex)  
        End If  
    End Function  
End Module  
```  
  
 Chamar esse método de extensão para qualquer coleção enumerável da mesma maneira que você chamar outros métodos de agregação do <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601>  
  
> [!NOTE]
>  No Visual Basic, você pode usar uma chamada de método ou sintaxe de consulta padrão para o `Aggregate` ou `Group By` cláusula. Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) e [grupo pela cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 O exemplo de código a seguir mostra como usar o `Median` método para uma matriz do tipo `double`.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Um método de agregação para aceitar vários tipos de sobrecarga  
 Você pode sobrecarregar o método de agregação para que ele aceite sequências de vários tipos. A abordagem padrão é criar uma sobrecarga para cada tipo. Outra abordagem é criar uma sobrecarga que se um tipo genérico e convertê-lo em um tipo específico, usando um representante. Você também pode combinar as duas abordagens.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Para criar uma sobrecarga para cada tipo  
 Você pode criar uma sobrecarga específica para cada tipo que você deseja oferecer suporte. O exemplo de código a seguir mostra uma sobrecarga de `Median` método para o `integer` tipo.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Agora você pode chamar o `Median` sobrecargas para ambos `integer` e `double` tipos, conforme mostrado no código a seguir:  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
#### <a name="to-create-a-generic-overload"></a>Para criar uma sobrecarga genérica  
 Você também pode criar uma sobrecarga que aceita uma sequência de objetos genéricos. Essa sobrecarga leva um delegado como parâmetro e usa-o para converter uma sequência de objetos de um tipo genérico a um tipo específico.  
  
 O código a seguir mostra uma sobrecarga de `Median` método que usa o <xref:System.Func%602>Delegar como um parâmetro.</xref:System.Func%602> Esse delegado pega um objeto de tipo genérico T e retorna um objeto do tipo `double`.  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 Agora você pode chamar o `Median` método para uma sequência de objetos de qualquer tipo. Se o tipo não tem sua própria sobrecarga de método, você precisa passar um parâmetro delegado. No Visual Basic, você pode usar uma expressão lambda para essa finalidade. Além disso, se você usar o `Aggregate` ou `Group By` cláusula em vez da chamada de método, você pode passar qualquer valor ou expressão que está no escopo dessa cláusula.  
  
 O exemplo de código a seguir mostra como chamar o `Median` método para uma matriz de inteiros e uma matriz de cadeias de caracteres. Para cadeias de caracteres, a mediana para os comprimentos das cadeias de caracteres na matriz é calculada. O exemplo mostra como passar o <xref:System.Func%602>delegar o parâmetro para o `Median` método para cada caso.</xref:System.Func%602>  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
## <a name="adding-a-method-that-returns-a-collection"></a>Adicionando um método que retorna uma coleção  
 Você pode estender o <xref:System.Collections.Generic.IEnumerable%601>interface com um método de consulta personalizada que retorna uma sequência de valores.</xref:System.Collections.Generic.IEnumerable%601> Nesse caso, o método deve retornar uma coleção do tipo <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601> Esses métodos podem ser usados para aplicar transformações de dados ou filtros para uma sequência de valores.  
  
 O exemplo a seguir mostra como criar um método de extensão chamado `AlternateElements` que retorna todos os outros elementos em uma coleção, começando do primeiro elemento.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Você pode chamar esse método de extensão para qualquer coleção enumerável exatamente como você poderia chamar outros métodos do <xref:System.Collections.Generic.IEnumerable%601>da interface, conforme mostrado no código a seguir:</xref:System.Collections.Generic.IEnumerable%601>  
  
```vb  
Dim strings() As String = {"a", "b", "c", "d", "e"}  
  
Dim query = strings.AlternateElements()  
  
For Each element In query  
    Console.WriteLine(element)  
Next  
  
' This code produces the following output:  
'  
' a  
' c  
' e  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [Métodos de Extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
