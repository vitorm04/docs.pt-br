---
title: "Como: adicionar métodos personalizados para consultas LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c94973bf9eae0feb2f7690dcc10e839b6b7c060c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="89287-102">Como: adicionar métodos personalizados para consultas LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89287-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>
<span data-ttu-id="89287-103">Você pode estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando os métodos de extensão à interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="89287-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="89287-104">Por exemplo, além do padrão médio ou máximo de operações, você pode criar um método de agregação personalizado para calcular um único valor de uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="89287-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="89287-105">Você também pode criar um método que funciona como um filtro personalizado ou como uma transformação de dados específicos para uma sequência de valores e que retorna uma nova sequência.</span><span class="sxs-lookup"><span data-stu-id="89287-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="89287-106">Exemplos desses métodos são <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A> e <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="89287-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="89287-107">Ao estender a interface <xref:System.Collections.Generic.IEnumerable%601>, você pode aplicar seus métodos personalizados para qualquer coleção enumerável.</span><span class="sxs-lookup"><span data-stu-id="89287-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="89287-108">Para obter mais informações, consulte [Métodos de extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="89287-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="89287-109">Adicionando um método de agregação</span><span class="sxs-lookup"><span data-stu-id="89287-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="89287-110">Um método de agregação calcula um valor único de um conjunto de valores.</span><span class="sxs-lookup"><span data-stu-id="89287-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="89287-111">O LINQ fornece vários métodos de agregação, incluindo <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A> e <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="89287-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="89287-112">Você pode criar seu próprio método de agregação, adicionando um método de extensão à interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="89287-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="89287-113">O exemplo de código a seguir mostra como criar um método de extensão chamado `Median` para calcular uma mediana de uma sequência de números do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="89287-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
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
  
 <span data-ttu-id="89287-114">Você chama esse método de extensão para qualquer coleção enumerável da mesma maneira que chama outros métodos de agregação da interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="89287-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89287-115">No Visual Basic, você pode usar uma chamada de método ou a sintaxe de consulta padrão para o `Aggregate` ou `Group By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="89287-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="89287-116">Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) e [grupo pela cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="89287-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="89287-117">O exemplo de código a seguir mostra como usar o método `Median` para uma matriz do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="89287-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
```  
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="89287-118">Sobrecarregando um método de agregação para aceitar vários tipos</span><span class="sxs-lookup"><span data-stu-id="89287-118">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="89287-119">Você pode sobrecarregar o método de agregação para que ele aceite sequências de vários tipos.</span><span class="sxs-lookup"><span data-stu-id="89287-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="89287-120">A abordagem padrão é criar uma sobrecarga para cada tipo.</span><span class="sxs-lookup"><span data-stu-id="89287-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="89287-121">Outra abordagem é criar uma sobrecarga que vai pegar um tipo genérico e convertê-lo em um tipo específico, usando um delegado.</span><span class="sxs-lookup"><span data-stu-id="89287-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="89287-122">Você também pode combinar as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="89287-122">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="89287-123">Para criar uma sobrecarga para cada tipo</span><span class="sxs-lookup"><span data-stu-id="89287-123">To create an overload for each type</span></span>  
 <span data-ttu-id="89287-124">Você pode criar uma sobrecarga específica para cada tipo que deseja oferecer suporte.</span><span class="sxs-lookup"><span data-stu-id="89287-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="89287-125">O exemplo de código a seguir mostra uma sobrecarga do método `Median` para o tipo `integer`.</span><span class="sxs-lookup"><span data-stu-id="89287-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 <span data-ttu-id="89287-126">Agora você pode chamar as sobrecargas `Median` para os tipos `integer` e `double`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="89287-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
Dim numbers2() As Integer = {1, 2, 3, 4, 5}  
  
Dim query2 = Aggregate num In numbers2 Into Median()  
  
Console.WriteLine("Integer: Median = " & query2)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
' Integer: Median = 3  
```  
  
 
#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="89287-127">Para criar uma sobrecarga genérica</span><span class="sxs-lookup"><span data-stu-id="89287-127">To create a generic overload</span></span>  
 <span data-ttu-id="89287-128">Você também pode criar uma sobrecarga que aceita uma sequência de objetos genéricos.</span><span class="sxs-lookup"><span data-stu-id="89287-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="89287-129">Essa sobrecarga recebe um delegado como parâmetro e usa-o para converter uma sequência de objetos de um tipo genérico em um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="89287-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="89287-130">O código a seguir mostra uma sobrecarga do método `Median` que recebe o delegado <xref:System.Func%602> como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="89287-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="89287-131">Esse delegado recebe um objeto de tipo genérico T e retorna um objeto do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="89287-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 <span data-ttu-id="89287-132">Agora você pode chamar o método `Median` para uma sequência de objetos de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="89287-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="89287-133">Se o tipo não tem sua própria sobrecarga de método, você precisa passar um parâmetro delegado.</span><span class="sxs-lookup"><span data-stu-id="89287-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="89287-134">No Visual Basic, você pode usar uma expressão lambda para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="89287-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="89287-135">Além disso, se você usar o `Aggregate` ou `Group By` cláusula em vez da chamada do método, você pode transmitir qualquer valor ou expressão que está no escopo dessa cláusula.</span><span class="sxs-lookup"><span data-stu-id="89287-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="89287-136">O exemplo de código a seguir mostra como chamar o método `Median` para uma matriz de inteiros e para uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="89287-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="89287-137">Será calculada a mediana dos comprimentos das cadeias de caracteres na matriz.</span><span class="sxs-lookup"><span data-stu-id="89287-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="89287-138">O exemplo também mostra como passar o parâmetro delegado <xref:System.Func%602> ao método `Median` para cada caso.</span><span class="sxs-lookup"><span data-stu-id="89287-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
```vb  
Dim numbers3() As Integer = {1, 2, 3, 4, 5}  
  
' You can use num as a parameter for the Median method   
' so that the compiler will implicitly convert its value to double.  
' If there is no implicit conversion, the compiler will  
' display an error message.  
  
Dim query3 = Aggregate num In numbers3 Into Median(num)  
  
Console.WriteLine("Integer: Median = " & query3)  
  
Dim numbers4() As String = {"one", "two", "three", "four", "five"}  
  
' With the generic overload, you can also use numeric properties of objects.  
  
Dim query4 = Aggregate str In numbers4 Into Median(str.Length)  
  
Console.WriteLine("String: Median = " & query4)  
  
' This code produces the following output:  
'  
' Integer: Median = 3  
' String: Median = 4  
```  
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="89287-139">Adicionando um método que retorna uma coleção</span><span class="sxs-lookup"><span data-stu-id="89287-139">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="89287-140">Você pode estender a interface <xref:System.Collections.Generic.IEnumerable%601> com um método de consulta personalizada que retorna uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="89287-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="89287-141">Nesse caso, o método deve retornar uma coleção do tipo <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="89287-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="89287-142">Esses métodos podem ser usados para aplicar transformações de dados ou filtros a uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="89287-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="89287-143">O exemplo a seguir mostra como criar um método de extensão chamado `AlternateElements` que retorna todos os outros elementos em uma coleção, começando pelo primeiro elemento.</span><span class="sxs-lookup"><span data-stu-id="89287-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
```vb  
' Extension method for the IEnumerable(of T) interface.   
' The method returns every other element of a sequence.  
  
<Extension()>   
Function AlternateElements(Of T)(  
    ByVal source As IEnumerable(Of T)  
    ) As IEnumerable(Of T)  
  
    Dim list As New List(Of T)  
    Dim i = 0  
    For Each element In source  
        If (i Mod 2 = 0) Then  
            list.Add(element)  
        End If  
        i = i + 1  
    Next  
    Return list  
End Function  
```  
 <span data-ttu-id="89287-144">Você pode chamar esse método de extensão para qualquer coleção enumerável exatamente como chamaria outros métodos da interface <xref:System.Collections.Generic.IEnumerable%601>, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="89287-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89287-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89287-145">See Also</span></span>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="89287-146">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="89287-146">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
