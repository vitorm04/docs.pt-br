---
title: Iteradores (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: ecc48ad5bbddc82457a8d6cc8e60ee419fb593fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="d5aed-102">Iteradores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5aed-102">Iterators (Visual Basic)</span></span>
<span data-ttu-id="d5aed-103">Um *iterador* pode ser usado para percorrer coleções, como listas e matrizes.</span><span class="sxs-lookup"><span data-stu-id="d5aed-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="d5aed-104">Um método iterador ou um acessador `get` realiza uma iteração personalizada em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="d5aed-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="d5aed-105">Usa um método iterador o [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento de uma por vez.</span><span class="sxs-lookup"><span data-stu-id="d5aed-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="d5aed-106">Quando uma instrução `Yield` for atingida, o local atual no código será lembrado.</span><span class="sxs-lookup"><span data-stu-id="d5aed-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="d5aed-107">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="d5aed-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="d5aed-108">Consumir um iterador no código do cliente usando um [para cada um... Próxima](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrução, ou usando uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="d5aed-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="d5aed-109">No exemplo a seguir, a primeira iteração do loop `For Each` faz a execução continue no método iterador `SomeNumbers` até que a primeira instrução `Yield` seja alcançada.</span><span class="sxs-lookup"><span data-stu-id="d5aed-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="d5aed-110">Essa iteração retorna um valor de 3 e o local atual no método iterador é mantido.</span><span class="sxs-lookup"><span data-stu-id="d5aed-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="d5aed-111">Na próxima iteração do loop, a execução no método iterador continuará de onde parou, parando novamente quando alcançar uma instrução `Yield`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="d5aed-112">Essa iteração retorna um valor de 5 e o local atual no método iterador é mantido novamente.</span><span class="sxs-lookup"><span data-stu-id="d5aed-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="d5aed-113">O loop terminará quando o final do método iterador for alcançado.</span><span class="sxs-lookup"><span data-stu-id="d5aed-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
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
  
 <span data-ttu-id="d5aed-114">O tipo de retorno de um método iterador ou acessador `get` pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="d5aed-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="d5aed-115">Você pode usar um `Exit Function` ou `Return` instrução para finalizar a iteração.</span><span class="sxs-lookup"><span data-stu-id="d5aed-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="d5aed-116">Uma função de iterador do Visual Basic ou `get` acessador declaração inclui um [iterador](../../../visual-basic/language-reference/modifiers/iterator.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="d5aed-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
 <span data-ttu-id="d5aed-117">Iteradores foram introduzidos no Visual Basic no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="d5aed-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="d5aed-118">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="d5aed-118">**In this topic**</span></span>  
  
-   [<span data-ttu-id="d5aed-119">Iterador simples</span><span class="sxs-lookup"><span data-stu-id="d5aed-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
-   [<span data-ttu-id="d5aed-120">Criando uma classe de coleção</span><span class="sxs-lookup"><span data-stu-id="d5aed-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
-   [<span data-ttu-id="d5aed-121">Blocos try</span><span class="sxs-lookup"><span data-stu-id="d5aed-121">Try Blocks</span></span>](#BKMK_TryBlocks)  
  
-   [<span data-ttu-id="d5aed-122">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="d5aed-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)  
  
-   [<span data-ttu-id="d5aed-123">Usando iteradores com uma lista genérica</span><span class="sxs-lookup"><span data-stu-id="d5aed-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
-   [<span data-ttu-id="d5aed-124">Informações de sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5aed-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
-   [<span data-ttu-id="d5aed-125">Implementação técnica</span><span class="sxs-lookup"><span data-stu-id="d5aed-125">Technical Implementation</span></span>](#BKMK_Technical)  
  
-   [<span data-ttu-id="d5aed-126">Uso de iteradores</span><span class="sxs-lookup"><span data-stu-id="d5aed-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="d5aed-127">Para obter todos os exemplos do tópico, exceto o exemplo simples iterador, incluir [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instruções para o `System.Collections` e `System.Collections.Generic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="d5aed-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
##  <a name="BKMK_SimpleIterator"></a> <span data-ttu-id="d5aed-128">Iterador simples</span><span class="sxs-lookup"><span data-stu-id="d5aed-128">Simple Iterator</span></span>  
 <span data-ttu-id="d5aed-129">O exemplo a seguir tem um único `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="d5aed-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="d5aed-130">Em `Main`, cada iteração do corpo da instrução `For Each` cria uma chamada à função iteradora, que avança para a próxima instrução `Yield`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
##  <a name="BKMK_CollectionClass"></a> <span data-ttu-id="d5aed-131">Criando uma classe de coleção</span><span class="sxs-lookup"><span data-stu-id="d5aed-131">Creating a Collection Class</span></span>  
 <span data-ttu-id="d5aed-132">No exemplo a seguir, a classe `DaysOfTheWeek` implementa a interface <xref:System.Collections.IEnumerable>, que requer um método <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5aed-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="d5aed-133">O compilador chama implicitamente o método `GetEnumerator`, que retorna um <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="d5aed-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="d5aed-134">O `GetEnumerator` método retorna cada cadeia de caracteres de um cada vez usando o `Yield` instrução e um `Iterator` modificador é na declaração da função.</span><span class="sxs-lookup"><span data-stu-id="d5aed-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>  
  
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
  
 <span data-ttu-id="d5aed-135">O exemplo a seguir cria uma classe `Zoo` que contém uma coleção de animais.</span><span class="sxs-lookup"><span data-stu-id="d5aed-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="d5aed-136">A instrução `For Each`, que faz referência à instância de classe (`theZoo`), chama implicitamente o método `GetEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="d5aed-137">As instruções `For Each`, que fazem referência às propriedades `Birds` e `Mammals`, usam o método iterador nomeado `AnimalsForType`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
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
  
##  <a name="BKMK_TryBlocks"></a> <span data-ttu-id="d5aed-138">Blocos try</span><span class="sxs-lookup"><span data-stu-id="d5aed-138">Try Blocks</span></span>  
 <span data-ttu-id="d5aed-139">Visual Basic permite um `Yield` instrução o `Try` block de um [tente... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5aed-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="d5aed-140">Um `Try` bloco tem um `Yield` instrução pode ter `Catch` bloqueia e pode ter um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="d5aed-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="d5aed-141">O exemplo a seguir inclui `Try`, `Catch`, e `Finally` blocos em uma função de iterador.</span><span class="sxs-lookup"><span data-stu-id="d5aed-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="d5aed-142">O `Finally` bloco na função de iterador é executado antes do `For Each` termina de iteração.</span><span class="sxs-lookup"><span data-stu-id="d5aed-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>  
  
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
  
 <span data-ttu-id="d5aed-143">Um `Yield` instrução não pode estar dentro de um `Catch` blocos ou um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="d5aed-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="d5aed-144">Se o `For Each` corpo (em vez do método de iterador) gera uma exceção, uma `Catch` bloco na função iterador não é executado, mas um `Finally` bloco na função de iterador é executado.</span><span class="sxs-lookup"><span data-stu-id="d5aed-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="d5aed-145">Um `Catch` blocos dentro de uma função iterator captura somente exceções que ocorrem dentro da função de iterador.</span><span class="sxs-lookup"><span data-stu-id="d5aed-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
##  <a name="BKMK_AnonymousMethods"></a> <span data-ttu-id="d5aed-146">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="d5aed-146">Anonymous Methods</span></span>  
 <span data-ttu-id="d5aed-147">No Visual Basic, uma função anônima pode ser uma função de iterador.</span><span class="sxs-lookup"><span data-stu-id="d5aed-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="d5aed-148">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="d5aed-148">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="d5aed-149">O exemplo a seguir tem um método iterador não valida os argumentos.</span><span class="sxs-lookup"><span data-stu-id="d5aed-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="d5aed-150">O método retorna o resultado de um iterador anônimo que descreve os elementos da coleção.</span><span class="sxs-lookup"><span data-stu-id="d5aed-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>  
  
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
  
 <span data-ttu-id="d5aed-151">Se a validação está dentro da função de iterador, a validação não pode ser executada até o início da primeira iteração do `For Each` corpo.</span><span class="sxs-lookup"><span data-stu-id="d5aed-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>  
  
##  <a name="BKMK_GenericList"></a> <span data-ttu-id="d5aed-152">Usando iteradores com uma lista genérica</span><span class="sxs-lookup"><span data-stu-id="d5aed-152">Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="d5aed-153">No exemplo a seguir, a classe `Stack(Of T)` genérica implementa a interface genérica <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d5aed-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="d5aed-154">O método `Push` atribui valores a uma matriz do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="d5aed-155">O método <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> retorna os valores da matriz usando a instrução `Yield`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>  
  
 <span data-ttu-id="d5aed-156">Além do método <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> genérico, o método <xref:System.Collections.IEnumerable.GetEnumerator%2A> não genérico também deve ser implementado.</span><span class="sxs-lookup"><span data-stu-id="d5aed-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="d5aed-157">Isso ocorre porque <xref:System.Collections.Generic.IEnumerable%601> herda de <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="d5aed-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="d5aed-158">A implementação não genérica adia a implementação genérica.</span><span class="sxs-lookup"><span data-stu-id="d5aed-158">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="d5aed-159">O exemplo usa iteradores nomeados para dar suporte a várias maneiras de iterar na mesma coleção de dados.</span><span class="sxs-lookup"><span data-stu-id="d5aed-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="d5aed-160">Esses iteradores nomeados são as propriedades `TopToBottom` e `BottomToTop` e o método `TopN`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="d5aed-161">O `BottomToTop` declaração de propriedade inclui o `Iterator` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d5aed-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>  
  
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
  
##  <a name="BKMK_SyntaxInformation"></a> <span data-ttu-id="d5aed-162">Informações de sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5aed-162">Syntax Information</span></span>  
 <span data-ttu-id="d5aed-163">Um iterador pode ocorrer como um método ou como um acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="d5aed-164">Um iterador não pode ocorrer em um evento, um construtor de instância, um construtor estático ou um destruidor estático.</span><span class="sxs-lookup"><span data-stu-id="d5aed-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="d5aed-165">Deve existir uma conversão implícita do tipo de expressão na instrução `Yield`, para o tipo de retorno do iterador.</span><span class="sxs-lookup"><span data-stu-id="d5aed-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="d5aed-166">No Visual Basic, um método iterador não pode conter qualquer `ByRef` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d5aed-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="d5aed-167">No Visual Basic, "Yield" não é uma palavra reservada e tem um significado especial somente quando ele é usado em uma `Iterator` método ou `get` acessador.</span><span class="sxs-lookup"><span data-stu-id="d5aed-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>  
  
##  <a name="BKMK_Technical"></a> <span data-ttu-id="d5aed-168">Implementação técnica</span><span class="sxs-lookup"><span data-stu-id="d5aed-168">Technical Implementation</span></span>  
 <span data-ttu-id="d5aed-169">Embora você escreva um iterador como um método, o compilador o traduz em uma classe aninhada que é, na verdade, uma máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="d5aed-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="d5aed-170">Essa classe mantém o controle da posição do iterador enquanto o loop `For Each...Next` no código cliente continuar.</span><span class="sxs-lookup"><span data-stu-id="d5aed-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="d5aed-171">Para ver o que o compilador faz, você pode usar a ferramenta Ildasm.exe para exibir o código Microsoft Intermediate Language que é gerado para um método iterador.</span><span class="sxs-lookup"><span data-stu-id="d5aed-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="d5aed-172">Quando você criar um iterador para um [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md), não é necessário que implementar todo <xref:System.Collections.IEnumerator> interface.</span><span class="sxs-lookup"><span data-stu-id="d5aed-172">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="d5aed-173">Quando o compilador detecta o iterador, ele gera automaticamente os métodos `Current`, `MoveNext` e `Dispose` da interface <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="d5aed-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="d5aed-174">A cada iteração sucessiva do loop `For Each…Next` (ou a chamada direta ao `IEnumerator.MoveNext`), o próximo corpo de código do iterador continua, depois da instrução `Yield` anterior.</span><span class="sxs-lookup"><span data-stu-id="d5aed-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="d5aed-175">Em seguida, ele continuará até a próxima `Yield` instrução até o final do corpo do iterador é atingido, ou até que um `Exit Function` ou `Return` instrução for encontrada.</span><span class="sxs-lookup"><span data-stu-id="d5aed-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>  
  
 <span data-ttu-id="d5aed-176">Iteradores não dão suporte a <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="d5aed-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5aed-177">Para iterar novamente desde o início, você deve obter um novo iterador.</span><span class="sxs-lookup"><span data-stu-id="d5aed-177">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="d5aed-178">Para obter informações adicionais, consulte o [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d5aed-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>  
  
##  <a name="BKMK_UseOfIterators"></a> <span data-ttu-id="d5aed-179">Uso de iteradores</span><span class="sxs-lookup"><span data-stu-id="d5aed-179">Use of Iterators</span></span>  
 <span data-ttu-id="d5aed-180">Os iteradores permitem que você mantenha a simplicidade de um loop `For Each` quando for necessário usar um código complexo para preencher uma sequência de lista.</span><span class="sxs-lookup"><span data-stu-id="d5aed-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="d5aed-181">Isso pode ser útil quando você quiser fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5aed-181">This can be useful when you want to do the following:</span></span>  
  
-   <span data-ttu-id="d5aed-182">Modificar a sequência de lista após a primeira iteração de loop `For Each`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>  
  
-   <span data-ttu-id="d5aed-183">Evitar o carregamento completo de uma grande lista antes da primeira iteração de um loop `For Each`.</span><span class="sxs-lookup"><span data-stu-id="d5aed-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="d5aed-184">Um exemplo é uma busca paginada para carregar um lote de linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="d5aed-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="d5aed-185">Outro exemplo é o método <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>, que implementa os iteradores dentro do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5aed-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
-   <span data-ttu-id="d5aed-186">Encapsular a criação da lista no iterador.</span><span class="sxs-lookup"><span data-stu-id="d5aed-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="d5aed-187">No método iterador, você pode criar a lista e, em seguida, gerar cada resultado em um loop.</span><span class="sxs-lookup"><span data-stu-id="d5aed-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5aed-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5aed-188">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="d5aed-189">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="d5aed-189">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="d5aed-190">Instrução Yield</span><span class="sxs-lookup"><span data-stu-id="d5aed-190">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)  
 [<span data-ttu-id="d5aed-191">Iterador</span><span class="sxs-lookup"><span data-stu-id="d5aed-191">Iterator</span></span>](../../../visual-basic/language-reference/modifiers/iterator.md)
