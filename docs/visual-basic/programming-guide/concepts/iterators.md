---
title: Iteradores (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c38609878c10ff3234b5a33ec44d678d24c11d7f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="iterators-visual-basic"></a><span data-ttu-id="aa392-102">Iteradores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa392-102">Iterators (Visual Basic)</span></span>
<span data-ttu-id="aa392-103">Um *iterador* pode ser usado para percorrer coleções, como listas e matrizes.</span><span class="sxs-lookup"><span data-stu-id="aa392-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="aa392-104">Um método iterador ou `get` acessador realiza uma iteração personalizada em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="aa392-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="aa392-105">Usa um método iterador o [gerar](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento por vez.</span><span class="sxs-lookup"><span data-stu-id="aa392-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="aa392-106">Quando um `Yield` instrução for atingida, o local atual no código será lembrado.</span><span class="sxs-lookup"><span data-stu-id="aa392-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="aa392-107">Execução é reiniciada a partir desse local na próxima vez em que a função de iterador é chamada.</span><span class="sxs-lookup"><span data-stu-id="aa392-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="aa392-108">Consumir um iterador no código do cliente usando um [para cada uma... Próxima](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrução, ou usando uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="aa392-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="aa392-109">No exemplo a seguir, a primeira iteração do `For Each` loop faz a execução continue no `SomeNumbers` método iterador até a primeira `Yield` instrução seja atingida.</span><span class="sxs-lookup"><span data-stu-id="aa392-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="aa392-110">Essa iteração retorna um valor de 3, e o local atual no método iterador é mantido.</span><span class="sxs-lookup"><span data-stu-id="aa392-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="aa392-111">Na próxima iteração do loop, a execução no método iterador continuará de onde parou, parando novamente quando ele atinge um `Yield` instrução.</span><span class="sxs-lookup"><span data-stu-id="aa392-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="aa392-112">Essa iteração retorna um valor de 5, e o local atual no método iterador é mantido novamente.</span><span class="sxs-lookup"><span data-stu-id="aa392-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="aa392-113">O loop termina quando o final do método iterador é atingido.</span><span class="sxs-lookup"><span data-stu-id="aa392-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In SomeNumbers()  
        Console.Write(number & " ")  
    Next  
    ' Output: 3 5 8  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function SomeNumbers() As System.Collections.IEnumerable  
    Yield 3  
    Yield 5  
    Yield 8  
End Function  
```  
  
 <span data-ttu-id="aa392-114">O tipo de retorno de um método iterador ou `get` acessador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="aa392-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="aa392-115">Você pode usar um `Exit Function` ou `Return` instrução para finalizar a iteração.</span><span class="sxs-lookup"><span data-stu-id="aa392-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="aa392-116">Uma função de iterador do Visual Basic ou `get` acessador declaração inclui um [iterador](../../../visual-basic/language-reference/modifiers/iterator.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="aa392-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
 <span data-ttu-id="aa392-117">Iteradores foram introduzidos no Visual Basic no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="aa392-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="aa392-118">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="aa392-118">**In this topic**</span></span>  
  
-   [<span data-ttu-id="aa392-119">Iterador simples</span><span class="sxs-lookup"><span data-stu-id="aa392-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
-   [<span data-ttu-id="aa392-120">Criando uma classe de coleção</span><span class="sxs-lookup"><span data-stu-id="aa392-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
-   [<span data-ttu-id="aa392-121">Blocos try</span><span class="sxs-lookup"><span data-stu-id="aa392-121">Try Blocks</span></span>](#BKMK_TryBlocks)  
  
-   [<span data-ttu-id="aa392-122">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="aa392-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)  
  
-   [<span data-ttu-id="aa392-123">Usando iteradores com uma lista genérica</span><span class="sxs-lookup"><span data-stu-id="aa392-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
-   [<span data-ttu-id="aa392-124">Informações de sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa392-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
-   [<span data-ttu-id="aa392-125">Implementação técnica</span><span class="sxs-lookup"><span data-stu-id="aa392-125">Technical Implementation</span></span>](#BKMK_Technical)  
  
-   [<span data-ttu-id="aa392-126">Uso de iteradores</span><span class="sxs-lookup"><span data-stu-id="aa392-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="aa392-127">Para todos os exemplos no tópico exceto o exemplo simples iterador, incluem [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instruções para o `System.Collections` e `System.Collections.Generic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="aa392-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
##  <span data-ttu-id="aa392-128"><a name="BKMK_SimpleIterator"></a>Iterador simples</span><span class="sxs-lookup"><span data-stu-id="aa392-128"><a name="BKMK_SimpleIterator"></a> Simple Iterator</span></span>  
 <span data-ttu-id="aa392-129">O exemplo a seguir tem um único `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="aa392-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="aa392-130">Em `Main`, cada iteração de `For Each` corpo da instrução cria uma chamada para a função do iterador, que passa para o próximo `Yield` instrução.</span><span class="sxs-lookup"><span data-stu-id="aa392-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    ' Output: 6 8 10 12 14 16 18  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As System.Collections.Generic.IEnumerable(Of Integer)  
  
    ' Yield even numbers in the range.  
    For number As Integer = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
##  <span data-ttu-id="aa392-131"><a name="BKMK_CollectionClass"></a>Criando uma classe de coleção</span><span class="sxs-lookup"><span data-stu-id="aa392-131"><a name="BKMK_CollectionClass"></a> Creating a Collection Class</span></span>  
 <span data-ttu-id="aa392-132">No exemplo a seguir, o `DaysOfTheWeek` classe implementa o <xref:System.Collections.IEnumerable>interface, que requer um <xref:System.Collections.IEnumerable.GetEnumerator%2A>método.</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="aa392-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="aa392-133">O compilador chama implicitamente a `GetEnumerator` método, que retorna um <xref:System.Collections.IEnumerator>.</xref:System.Collections.IEnumerator></span><span class="sxs-lookup"><span data-stu-id="aa392-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="aa392-134">O `GetEnumerator` método retorna cada cadeia de caracteres de uma por vez usando o `Yield` instrução e um `Iterator` modificador é na declaração da função.</span><span class="sxs-lookup"><span data-stu-id="aa392-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>  
  
```vb  
Sub Main()  
    Dim days As New DaysOfTheWeek()  
    For Each day As String In days  
        Console.Write(day & " ")  
    Next  
    ' Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey()  
End Sub  
  
Private Class DaysOfTheWeek  
    Implements IEnumerable  
  
    Public days =  
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        ' Yield each day of the week.  
        For i As Integer = 0 To days.Length - 1  
            Yield days(i)  
        Next  
    End Function  
End Class  
```  
  
 <span data-ttu-id="aa392-135">O exemplo a seguir cria um `Zoo` classe que contém uma coleção de animais.</span><span class="sxs-lookup"><span data-stu-id="aa392-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="aa392-136">O `For Each` instrução que faz referência à instância de classe (`theZoo`) chama implicitamente o `GetEnumerator` método.</span><span class="sxs-lookup"><span data-stu-id="aa392-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="aa392-137">O `For Each` instruções que fazem referência a `Birds` e `Mammals` uso de propriedades a `AnimalsForType` chamado o método iterador.</span><span class="sxs-lookup"><span data-stu-id="aa392-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
```vb  
Sub Main()  
    Dim theZoo As New Zoo()  
  
    theZoo.AddMammal("Whale")  
    theZoo.AddMammal("Rhinoceros")  
    theZoo.AddBird("Penguin")  
    theZoo.AddBird("Warbler")  
  
    For Each name As String In theZoo  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros Penguin Warbler  
  
    For Each name As String In theZoo.Birds  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Penguin Warbler  
  
    For Each name As String In theZoo.Mammals  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros  
  
    Console.ReadKey()  
End Sub  
  
Public Class Zoo  
    Implements IEnumerable  
  
    ' Private members.  
    Private animals As New List(Of Animal)  
  
    ' Public methods.  
    Public Sub AddMammal(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})  
    End Sub  
  
    Public Sub AddBird(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})  
    End Sub  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        For Each theAnimal As Animal In animals  
            Yield theAnimal.Name  
        Next  
    End Function  
  
    ' Public members.  
    Public ReadOnly Property Mammals As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Mammal)  
        End Get  
    End Property  
  
    Public ReadOnly Property Birds As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Bird)  
        End Get  
    End Property  
  
    ' Private methods.  
    Private Iterator Function AnimalsForType( _  
    ByVal type As Animal.TypeEnum) As IEnumerable  
        For Each theAnimal As Animal In animals  
            If (theAnimal.Type = type) Then  
                Yield theAnimal.Name  
            End If  
        Next  
    End Function  
  
    ' Private class.  
    Private Class Animal  
        Public Enum TypeEnum  
            Bird  
            Mammal  
        End Enum  
  
        Public Property Name As String  
        Public Property Type As TypeEnum  
    End Class  
End Class  
```  
  
##  <span data-ttu-id="aa392-138"><a name="BKMK_TryBlocks"></a>Blocos try</span><span class="sxs-lookup"><span data-stu-id="aa392-138"><a name="BKMK_TryBlocks"></a> Try Blocks</span></span>  
 <span data-ttu-id="aa392-139">Visual Basic permite uma `Yield` instrução no `Try` bloco de um [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aa392-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="aa392-140">A `Try` bloco tem uma `Yield` instrução pode ter `Catch` blocos e pode ter um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="aa392-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="aa392-141">O exemplo a seguir inclui `Try`, `Catch`, e `Finally` blocos em uma função de iterador.</span><span class="sxs-lookup"><span data-stu-id="aa392-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="aa392-142">O `Finally` bloco na função iterador é executado antes do `For Each` termina de iteração.</span><span class="sxs-lookup"><span data-stu-id="aa392-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In Test()  
        Console.WriteLine(number)  
    Next  
    Console.WriteLine("For Each is done.")  
  
    ' Output:  
    '  3  
    '  4  
    '  Something happened. Yields are done.  
    '  Finally is called.  
    '  For Each is done.  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function Test() As IEnumerable(Of Integer)  
    Try  
        Yield 3  
        Yield 4  
        Throw New Exception("Something happened. Yields are done.")  
        Yield 5  
        Yield 6  
    Catch ex As Exception  
        Console.WriteLine(ex.Message)  
    Finally  
        Console.WriteLine("Finally is called.")  
    End Try  
End Function  
```  
  
 <span data-ttu-id="aa392-143">A `Yield` instrução não pode estar dentro de uma `Catch` bloco ou uma `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="aa392-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="aa392-144">Se o `For Each` corpo (em vez do método iterador) gera uma exceção, uma `Catch` bloco na função iterador não é executado, mas um `Finally` bloco na função iterador é executado.</span><span class="sxs-lookup"><span data-stu-id="aa392-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="aa392-145">Um `Catch` bloco dentro de uma função de iterador captura somente exceções que ocorrem dentro da função de iterador.</span><span class="sxs-lookup"><span data-stu-id="aa392-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
##  <span data-ttu-id="aa392-146"><a name="BKMK_AnonymousMethods"></a>Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="aa392-146"><a name="BKMK_AnonymousMethods"></a> Anonymous Methods</span></span>  
 <span data-ttu-id="aa392-147">No Visual Basic, uma função anônima pode ser uma função de iterador.</span><span class="sxs-lookup"><span data-stu-id="aa392-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="aa392-148">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="aa392-148">The following example illustrates this.</span></span>  
  
```vb  
Dim iterateSequence = Iterator Function() _  
                      As IEnumerable(Of Integer)  
                          Yield 1  
                          Yield 2  
                      End Function  
  
For Each number As Integer In iterateSequence()  
    Console.Write(number & " ")  
Next  
' Output: 1 2  
Console.ReadKey()  
```  
  
 <span data-ttu-id="aa392-149">O exemplo a seguir tem um método iterador não valida os argumentos.</span><span class="sxs-lookup"><span data-stu-id="aa392-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="aa392-150">O método retorna o resultado de um iterador anônimo que descreve os elementos da coleção.</span><span class="sxs-lookup"><span data-stu-id="aa392-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In GetSequence(5, 10)  
        Console.Write(number & " ")  
    Next  
    ' Output: 5 6 7 8 9 10  
    Console.ReadKey()  
End Sub  
  
Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _  
As IEnumerable  
    ' Validate the arguments.  
    If low < 1 Then  
        Throw New ArgumentException("low is too low")  
    End If  
    If high > 140 Then  
        Throw New ArgumentException("high is too high")  
    End If  
  
    ' Return an anonymous iterator function.  
    Dim iterateSequence = Iterator Function() As IEnumerable  
                              For index = low To high  
                                  Yield index  
                              Next  
                          End Function  
    Return iterateSequence()  
End Function  
```  
  
 <span data-ttu-id="aa392-151">Se a validação estiver dentro da função de iterador, a validação não pode ser executada antes do início da primeira iteração do `For Each` corpo.</span><span class="sxs-lookup"><span data-stu-id="aa392-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>  
  
##  <span data-ttu-id="aa392-152"><a name="BKMK_GenericList"></a>Usando iteradores com uma lista genérica</span><span class="sxs-lookup"><span data-stu-id="aa392-152"><a name="BKMK_GenericList"></a> Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="aa392-153">No exemplo a seguir, o `Stack(Of T)` classe genérica implementa o <xref:System.Collections.Generic.IEnumerable%601>interface genérica.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="aa392-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="aa392-154">O `Push` método atribui valores a uma matriz do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="aa392-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="aa392-155">O <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>método retorna os valores da matriz usando o `Yield` instrução.</xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="aa392-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>  
  
 <span data-ttu-id="aa392-156">Além de genérica <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>método, não genérico <xref:System.Collections.IEnumerable.GetEnumerator%2A>método também deve ser implementado.</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="aa392-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="aa392-157">Isso ocorre porque <xref:System.Collections.Generic.IEnumerable%601>herda de <xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="aa392-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="aa392-158">A implementação não genérico adia a implementação genérica.</span><span class="sxs-lookup"><span data-stu-id="aa392-158">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="aa392-159">O exemplo usa os iteradores nomeados para dar suporte a várias maneiras de iterar a mesma coleção de dados.</span><span class="sxs-lookup"><span data-stu-id="aa392-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="aa392-160">Esses iteradores de chamada são os `TopToBottom` e `BottomToTop` propriedades e o `TopN` método.</span><span class="sxs-lookup"><span data-stu-id="aa392-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="aa392-161">O `BottomToTop` declaração de propriedade inclui o `Iterator` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="aa392-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>  
  
```vb  
Sub Main()  
    Dim theStack As New Stack(Of Integer)  
  
    ' Add items to the stack.  
    For number As Integer = 0 To 9  
        theStack.Push(number)  
    Next  
  
    ' Retrieve items from the stack.  
    ' For Each is allowed because theStack implements  
    ' IEnumerable(Of Integer).  
    For Each number As Integer In theStack  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    ' For Each is allowed, because theStack.TopToBottom  
    ' returns IEnumerable(Of Integer).  
    For Each number As Integer In theStack.TopToBottom  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    For Each number As Integer In theStack.BottomToTop  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 0 1 2 3 4 5 6 7 8 9   
  
    For Each number As Integer In theStack.TopN(7)  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey()  
End Sub  
  
Public Class Stack(Of T)  
    Implements IEnumerable(Of T)  
  
    Private values As T() = New T(99) {}  
    Private top As Integer = 0  
  
    Public Sub Push(ByVal t As T)  
        values(top) = t  
        top = top + 1  
    End Sub  
  
    Public Function Pop() As T  
        top = top - 1  
        Return values(top)  
    End Function  
  
    ' This function implements the GetEnumerator method. It allows  
    ' an instance of the class to be used in a For Each statement.  
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _  
        Implements IEnumerable(Of T).GetEnumerator  
  
        For index As Integer = top - 1 To 0 Step -1  
            Yield values(index)  
        Next  
    End Function  
  
    Public Iterator Function GetEnumerator1() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        Yield GetEnumerator()  
    End Function  
  
    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)  
        Get  
            Return Me  
        End Get  
    End Property  
  
    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)  
        Get  
            For index As Integer = 0 To top - 1  
                Yield values(index)  
            Next  
        End Get  
    End Property  
  
    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _  
        As IEnumerable(Of T)  
  
        ' Return less than itemsFromTop if necessary.  
        Dim startIndex As Integer =  
            If(itemsFromTop >= top, 0, top - itemsFromTop)  
  
        For index As Integer = top - 1 To startIndex Step -1  
            Yield values(index)  
        Next  
    End Function  
End Class  
  
```  
  
##  <span data-ttu-id="aa392-162"><a name="BKMK_SyntaxInformation"></a>Informações de sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa392-162"><a name="BKMK_SyntaxInformation"></a> Syntax Information</span></span>  
 <span data-ttu-id="aa392-163">Um iterador pode ocorrer como um método ou `get` acessador.</span><span class="sxs-lookup"><span data-stu-id="aa392-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="aa392-164">Um iterador não pode ocorrer em um evento, construtor de instância, construtor estático ou destruidor static.</span><span class="sxs-lookup"><span data-stu-id="aa392-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="aa392-165">Deve existir uma conversão implícita do tipo de expressão no `Yield` instrução para o tipo de retorno do iterador.</span><span class="sxs-lookup"><span data-stu-id="aa392-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="aa392-166">No Visual Basic, um iterador não pode ter nenhum `ByRef` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="aa392-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="aa392-167">No Visual Basic, "Yield" não é uma palavra reservada e tem um significado especial somente quando ela é usada em uma `Iterator` método ou `get` acessador.</span><span class="sxs-lookup"><span data-stu-id="aa392-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>  
  
##  <span data-ttu-id="aa392-168"><a name="BKMK_Technical"></a>Implementação técnica</span><span class="sxs-lookup"><span data-stu-id="aa392-168"><a name="BKMK_Technical"></a> Technical Implementation</span></span>  
 <span data-ttu-id="aa392-169">Embora escrever um iterador como um método, o compilador converte em uma classe aninhada isto é, na verdade, uma máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="aa392-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="aa392-170">Essa classe mantém controle sobre a posição do iterador como tempo o `For Each...Next` continua loop no código do cliente.</span><span class="sxs-lookup"><span data-stu-id="aa392-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="aa392-171">Para ver o que o compilador faz, você pode usar a ferramenta Ildasm.exe para exibir o código Microsoft intermediate language que é gerado para um método iterador.</span><span class="sxs-lookup"><span data-stu-id="aa392-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="aa392-172">Quando você cria um iterador para um [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md), você não precisa implementar todo <xref:System.Collections.IEnumerator>interface.</xref:System.Collections.IEnumerator></span><span class="sxs-lookup"><span data-stu-id="aa392-172">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="aa392-173">Quando o compilador detecta o iterador, ela gera automaticamente o `Current`, `MoveNext`, e `Dispose` métodos de <xref:System.Collections.IEnumerator>ou <xref:System.Collections.Generic.IEnumerator%601>interface.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator></span><span class="sxs-lookup"><span data-stu-id="aa392-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="aa392-174">Em cada iteração sucessiva de `For Each…Next` loop (ou a chamada direta para `IEnumerator.MoveNext`), o corpo de código do iterador próxima continua após anterior `Yield` instrução.</span><span class="sxs-lookup"><span data-stu-id="aa392-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="aa392-175">Em seguida, ele continuará até a próxima `Yield` instrução até o final do corpo do iterador for atingido, ou até que uma `Exit Function` ou `Return` declaração é encontrada.</span><span class="sxs-lookup"><span data-stu-id="aa392-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>  
  
 <span data-ttu-id="aa392-176">Iteradores não oferecem suporte a <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName>método.</xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="aa392-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="aa392-177">Para iterar novamente desde o início, você deve obter um iterador de novo.</span><span class="sxs-lookup"><span data-stu-id="aa392-177">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="aa392-178">Para obter informações adicionais, consulte o [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification.md).</span><span class="sxs-lookup"><span data-stu-id="aa392-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md).</span></span>  
  
##  <span data-ttu-id="aa392-179"><a name="BKMK_UseOfIterators"></a>Uso de iteradores</span><span class="sxs-lookup"><span data-stu-id="aa392-179"><a name="BKMK_UseOfIterators"></a> Use of Iterators</span></span>  
 <span data-ttu-id="aa392-180">Iteradores que você possa manter a simplicidade de um `For Each` loop quando precisar usar código complexo para preencher uma sequência de lista.</span><span class="sxs-lookup"><span data-stu-id="aa392-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="aa392-181">Isso pode ser útil quando você deseja fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="aa392-181">This can be useful when you want to do the following:</span></span>  
  
-   <span data-ttu-id="aa392-182">Modificar a sequência de lista após a primeira `For Each` iteração de loop.</span><span class="sxs-lookup"><span data-stu-id="aa392-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>  
  
-   <span data-ttu-id="aa392-183">Evite o carregamento totalmente uma grande lista antes da primeira iteração de um `For Each` loop.</span><span class="sxs-lookup"><span data-stu-id="aa392-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="aa392-184">Um exemplo é uma busca paginada para carregar um lote de linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="aa392-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="aa392-185">Outro exemplo é o <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>método, que implementa os iteradores dentro do .NET Framework.</xref:System.IO.DirectoryInfo.EnumerateFiles%2A></span><span class="sxs-lookup"><span data-stu-id="aa392-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
-   <span data-ttu-id="aa392-186">Encapsule a criação da lista no iterador.</span><span class="sxs-lookup"><span data-stu-id="aa392-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="aa392-187">No método iterador, você pode criar a lista e, em seguida, gerar cada resultado em um loop.</span><span class="sxs-lookup"><span data-stu-id="aa392-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa392-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa392-188">See Also</span></span>  
 <span data-ttu-id="aa392-189"><xref:System.Collections.Generic></xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="aa392-189"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="aa392-190"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="aa392-190"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="aa392-191"> [Para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="aa392-191"> [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="aa392-192"> [Instrução yield](../../../visual-basic/language-reference/statements/yield-statement.md) </span><span class="sxs-lookup"><span data-stu-id="aa392-192"> [Yield Statement](../../../visual-basic/language-reference/statements/yield-statement.md) </span></span>  
<span data-ttu-id="aa392-193"> [Iterador](../../../visual-basic/language-reference/modifiers/iterator.md)</span><span class="sxs-lookup"><span data-stu-id="aa392-193"> [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)</span></span>
