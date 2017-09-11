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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 166eb731d41e009c374ba55f929eed302793ecd0
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="5126f-102">Como: adicionar métodos personalizados para consultas LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5126f-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>
<span data-ttu-id="5126f-103">Você pode estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando métodos de extensão para o <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5126f-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="5126f-104">Por exemplo, além do padrão médio ou máximo de operações, você pode criar um método de agregação personalizado para calcular um valor único de uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="5126f-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="5126f-105">Você também pode criar um método que funciona como um filtro personalizado ou uma transformação de dados específicos para uma sequência de valores e retorna uma nova sequência.</span><span class="sxs-lookup"><span data-stu-id="5126f-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="5126f-106">São exemplos de tais métodos <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>e <xref:System.Linq.Enumerable.Reverse%2A>.</xref:System.Linq.Enumerable.Reverse%2A> </xref:System.Linq.Enumerable.Skip%2A> </xref:System.Linq.Enumerable.Distinct%2A></span><span class="sxs-lookup"><span data-stu-id="5126f-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="5126f-107">Quando você estende o <xref:System.Collections.Generic.IEnumerable%601>interface, você pode aplicar seus métodos personalizados para qualquer coleção enumerável.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5126f-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="5126f-108">Para obter mais informações, consulte [métodos de extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="5126f-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="5126f-109">Adicionar um método de agregação</span><span class="sxs-lookup"><span data-stu-id="5126f-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="5126f-110">Um método de agregação computa um valor único de um conjunto de valores.</span><span class="sxs-lookup"><span data-stu-id="5126f-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="5126f-111">LINQ fornece vários métodos de agregação, incluindo <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>e <xref:System.Linq.Enumerable.Max%2A>.</xref:System.Linq.Enumerable.Max%2A> </xref:System.Linq.Enumerable.Min%2A> </xref:System.Linq.Enumerable.Average%2A></span><span class="sxs-lookup"><span data-stu-id="5126f-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="5126f-112">Você pode criar seu próprio método de agregação, adicionando um método de extensão para o <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5126f-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="5126f-113">O exemplo de código a seguir mostra como criar um método de extensão chamado `Median` para calcular uma média para uma sequência de números do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="5126f-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
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
  
 <span data-ttu-id="5126f-114">Chamar esse método de extensão para qualquer coleção enumerável da mesma maneira que você chamar outros métodos de agregação do <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5126f-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5126f-115">No Visual Basic, você pode usar uma chamada de método ou sintaxe de consulta padrão para o `Aggregate` ou `Group By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="5126f-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="5126f-116">Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) e [grupo pela cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5126f-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="5126f-117">O exemplo de código a seguir mostra como usar o `Median` método para uma matriz do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="5126f-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
<span data-ttu-id="5126f-118"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="5126f-118"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="5126f-119"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="5126f-119"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="5126f-120">Um método de agregação para aceitar vários tipos de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="5126f-120">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="5126f-121">Você pode sobrecarregar o método de agregação para que ele aceite sequências de vários tipos.</span><span class="sxs-lookup"><span data-stu-id="5126f-121">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="5126f-122">A abordagem padrão é criar uma sobrecarga para cada tipo.</span><span class="sxs-lookup"><span data-stu-id="5126f-122">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="5126f-123">Outra abordagem é criar uma sobrecarga que se um tipo genérico e convertê-lo em um tipo específico, usando um representante.</span><span class="sxs-lookup"><span data-stu-id="5126f-123">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="5126f-124">Você também pode combinar as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="5126f-124">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="5126f-125">Para criar uma sobrecarga para cada tipo</span><span class="sxs-lookup"><span data-stu-id="5126f-125">To create an overload for each type</span></span>  
 <span data-ttu-id="5126f-126">Você pode criar uma sobrecarga específica para cada tipo que você deseja oferecer suporte.</span><span class="sxs-lookup"><span data-stu-id="5126f-126">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="5126f-127">O exemplo de código a seguir mostra uma sobrecarga de `Median` método para o `integer` tipo.</span><span class="sxs-lookup"><span data-stu-id="5126f-127">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
<span data-ttu-id="5126f-128"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="5126f-128"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="5126f-129">Agora você pode chamar o `Median` sobrecargas para ambos `integer` e `double` tipos, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="5126f-129">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
<span data-ttu-id="5126f-130"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="5126f-130"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="5126f-131"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="5126f-131"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="5126f-132"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="5126f-132"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="5126f-133">Para criar uma sobrecarga genérica</span><span class="sxs-lookup"><span data-stu-id="5126f-133">To create a generic overload</span></span>  
 <span data-ttu-id="5126f-134">Você também pode criar uma sobrecarga que aceita uma sequência de objetos genéricos.</span><span class="sxs-lookup"><span data-stu-id="5126f-134">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="5126f-135">Essa sobrecarga leva um delegado como parâmetro e usa-o para converter uma sequência de objetos de um tipo genérico a um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="5126f-135">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="5126f-136">O código a seguir mostra uma sobrecarga de `Median` método que usa o <xref:System.Func%602>Delegar como um parâmetro.</xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="5126f-136">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="5126f-137">Esse delegado pega um objeto de tipo genérico T e retorna um objeto do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="5126f-137">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 <span data-ttu-id="5126f-138">Agora você pode chamar o `Median` método para uma sequência de objetos de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="5126f-138">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="5126f-139">Se o tipo não tem sua própria sobrecarga de método, você precisa passar um parâmetro delegado.</span><span class="sxs-lookup"><span data-stu-id="5126f-139">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="5126f-140">No Visual Basic, você pode usar uma expressão lambda para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="5126f-140">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="5126f-141">Além disso, se você usar o `Aggregate` ou `Group By` cláusula em vez da chamada de método, você pode passar qualquer valor ou expressão que está no escopo dessa cláusula.</span><span class="sxs-lookup"><span data-stu-id="5126f-141">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="5126f-142">O exemplo de código a seguir mostra como chamar o `Median` método para uma matriz de inteiros e uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5126f-142">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="5126f-143">Para cadeias de caracteres, a mediana para os comprimentos das cadeias de caracteres na matriz é calculada.</span><span class="sxs-lookup"><span data-stu-id="5126f-143">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="5126f-144">O exemplo mostra como passar o <xref:System.Func%602>delegar o parâmetro para o `Median` método para cada caso.</xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="5126f-144">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
<span data-ttu-id="5126f-145"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="5126f-145"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="5126f-146">Adicionando um método que retorna uma coleção</span><span class="sxs-lookup"><span data-stu-id="5126f-146">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="5126f-147">Você pode estender o <xref:System.Collections.Generic.IEnumerable%601>interface com um método de consulta personalizada que retorna uma sequência de valores.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5126f-147">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="5126f-148">Nesse caso, o método deve retornar uma coleção do tipo <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5126f-148">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="5126f-149">Esses métodos podem ser usados para aplicar transformações de dados ou filtros para uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="5126f-149">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="5126f-150">O exemplo a seguir mostra como criar um método de extensão chamado `AlternateElements` que retorna todos os outros elementos em uma coleção, começando do primeiro elemento.</span><span class="sxs-lookup"><span data-stu-id="5126f-150">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
<span data-ttu-id="5126f-151"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="5126f-151"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="5126f-152">Você pode chamar esse método de extensão para qualquer coleção enumerável exatamente como você poderia chamar outros métodos do <xref:System.Collections.Generic.IEnumerable%601>da interface, conforme mostrado no código a seguir:</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5126f-152">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5126f-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5126f-153">See Also</span></span>  
 <span data-ttu-id="5126f-154"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5126f-154"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="5126f-155"> [Métodos de Extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="5126f-155"> [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span></span>
