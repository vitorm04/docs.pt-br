---
title: "Coleções (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b3c8de3e22075d576f86bcd4eb599946740ebe16
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="collections-visual-basic"></a><span data-ttu-id="f1bf9-102">Coleções (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1bf9-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="f1bf9-103">Para muitos aplicativos, você deseja criar e gerenciar grupos de objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="f1bf9-104">Há duas maneiras para agrupar objetos: criando arrays de objetos e criando coleções de objetos.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="f1bf9-105">As matrizes são mais úteis para criar e trabalhar com um número fixo de objetos fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="f1bf9-106">Para obter informações sobre matrizes, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1bf9-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="f1bf9-107">As coleções fornecem uma maneira mais flexível de trabalhar com grupos de objetos.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="f1bf9-108">Ao contrário de matrizes, o grupo de objetos que você trabalha pode crescer e reduzir dinamicamente conforme as necessidades do aplicativo mudam.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="f1bf9-109">Para algumas coleções, você pode atribuir uma chave para qualquer objeto que você coloque na coleção para que você possa recuperar rapidamente o objeto usando a chave.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="f1bf9-110">Uma coleção é uma classe, portanto você deve declarar uma instância da classe antes de adicionar elementos à coleção.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="f1bf9-111">Se a coleção contém elementos de apenas um tipo de dados, você pode usar uma das classes de <xref:System.Collections.Generic?displayProperty=fullName>namespace.</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f1bf9-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="f1bf9-112">Uma coleção genérica impõe segurança de tipo para que nenhum outro tipo de dados pode ser adicionado a ele.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="f1bf9-113">Quando você recupera um elemento de uma coleção genérica, você não precisa determinar seu tipo de dados ou convertê-lo.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1bf9-114">Para os exemplos neste tópico, incluir [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instruções para o `System.Collections.Generic` e `System.Linq` namespaces.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="f1bf9-115">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="f1bf9-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="f1bf9-116">Usando uma coleção Simple</span><span class="sxs-lookup"><span data-stu-id="f1bf9-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="f1bf9-117">Tipos de coleções</span><span class="sxs-lookup"><span data-stu-id="f1bf9-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="f1bf9-118">Classes de System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="f1bf9-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="f1bf9-119">Classes de System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="f1bf9-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="f1bf9-120">Classes de System. Collections</span><span class="sxs-lookup"><span data-stu-id="f1bf9-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="f1bf9-121">Classe de coleção do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1bf9-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="f1bf9-122">Implementação de uma coleção de pares chave/valor</span><span class="sxs-lookup"><span data-stu-id="f1bf9-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="f1bf9-123">Usando LINQ para acessar uma coleção</span><span class="sxs-lookup"><span data-stu-id="f1bf9-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="f1bf9-124">Classificando uma coleção</span><span class="sxs-lookup"><span data-stu-id="f1bf9-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="f1bf9-125">Definindo uma coleção personalizada</span><span class="sxs-lookup"><span data-stu-id="f1bf9-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="f1bf9-126">Iteradores</span><span class="sxs-lookup"><span data-stu-id="f1bf9-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="f1bf9-127">Usando uma coleção Simple</span><span class="sxs-lookup"><span data-stu-id="f1bf9-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="f1bf9-128">Os exemplos nesta seção usam genérica <xref:System.Collections.Generic.List%601>classe, que permite que você trabalhe com uma lista com rigidez de tipos de objetos.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="f1bf9-129">O exemplo a seguir cria uma lista de cadeias de caracteres e, em seguida, percorre as cadeias de caracteres usando um [para cada uma... Próxima](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
```vb  
' Create a list of strings.  
Dim salmons As New List(Of String)  
salmons.Add("chinook")  
salmons.Add("coho")  
salmons.Add("pink")  
salmons.Add("sockeye")  
  
' Iterate through the list.  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="f1bf9-130">Se o conteúdo de uma coleção forem conhecido antecipadamente, você pode usar um *inicializador de coleção* para inicializar a coleção.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="f1bf9-131">Para obter mais informações, consulte [inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1bf9-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="f1bf9-132">O exemplo a seguir é igual ao exemplo anterior, exceto um inicializador de coleção é usado para adicionar elementos à coleção.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="f1bf9-133">Você pode usar um [para... Próximo](../../../visual-basic/language-reference/statements/for-next-statement.md) instrução em vez de um `For Each` instrução para iterar através de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="f1bf9-134">Você pode fazer isso acessando os elementos da coleção por posição de índice.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="f1bf9-135">O índice dos elementos começa em 0 e termina em menos de 1 a contagem do elemento.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="f1bf9-136">O exemplo a seguir itera através dos elementos de uma coleção usando `For…Next` em vez de `For Each`.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="f1bf9-137">O exemplo a seguir remove um elemento da coleção especificando o objeto a ser removido.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
' Remove an element in the list by specifying  
' the object.  
salmons.Remove("coho")  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook pink sockeye  
```  
  
 <span data-ttu-id="f1bf9-138">O exemplo a seguir remove elementos de uma lista genérica.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="f1bf9-139">Em vez de um `For Each` instrução, um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) instrução que itera em ordem decrescente é usada.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="f1bf9-140">Isso ocorre porque o <xref:System.Collections.Generic.List%601.RemoveAt%2A>método faz com que elementos após um elemento removido para ter um valor de índice mais baixo.</xref:System.Collections.Generic.List%601.RemoveAt%2A></span><span class="sxs-lookup"><span data-stu-id="f1bf9-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
```vb  
Dim numbers As New List(Of Integer) From  
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}  
  
' Remove odd numbers.  
For index As Integer = numbers.Count - 1 To 0 Step -1  
    If numbers(index) Mod 2 = 1 Then  
        ' Remove the element by specifying  
        ' the zero-based index in the list.  
        numbers.RemoveAt(index)  
    End If  
Next  
  
' Iterate through the list.  
' A lambda expression is placed in the ForEach method  
' of the List(T) object.  
numbers.ForEach(  
    Sub(number) Console.Write(number & " "))  
' Output: 0 2 4 6 8  
```  
  
 <span data-ttu-id="f1bf9-141">Para o tipo dos elementos no <xref:System.Collections.Generic.List%601>você também pode definir sua própria classe.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="f1bf9-142">No exemplo a seguir, o `Galaxy` classe que é usada pelo <xref:System.Collections.Generic.List%601>é definido no código.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
```vb  
Private Sub IterateThroughList()  
    Dim theGalaxies As New List(Of Galaxy) From  
        {  
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},  
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},  
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},  
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}  
        }  
  
    For Each theGalaxy In theGalaxies  
        With theGalaxy  
            Console.WriteLine(.Name & "  " & .MegaLightYears)  
        End With  
    Next  
  
    ' Output:  
    '  Tadpole  400  
    '  Pinwheel  25  
    '  Milky Way  0  
    '  Andromeda  3  
End Sub  
  
Public Class Galaxy  
    Public Property Name As String  
    Public Property MegaLightYears As Integer  
End Class  
```  
  
<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a><span data-ttu-id="f1bf9-143">Tipos de coleções</span><span class="sxs-lookup"><span data-stu-id="f1bf9-143">Kinds of Collections</span></span>   
 <span data-ttu-id="f1bf9-144">Várias coleções comuns são fornecidas pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="f1bf9-145">Cada tipo de coleção é projetado para uma finalidade específica.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="f1bf9-146">Algumas das classes de coleção comuns são descritas nesta seção:</span><span class="sxs-lookup"><span data-stu-id="f1bf9-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="f1bf9-147">@System.Collections.Genericclasses</span><span class="sxs-lookup"><span data-stu-id="f1bf9-147">@System.Collections.Generic classes</span></span>  
  
-   <span data-ttu-id="f1bf9-148">@System.Collections.Concurrentclasses</span><span class="sxs-lookup"><span data-stu-id="f1bf9-148">@System.Collections.Concurrent classes</span></span>  
  
-   <span data-ttu-id="f1bf9-149">@System.Collectionsclasses</span><span class="sxs-lookup"><span data-stu-id="f1bf9-149">@System.Collections classes</span></span>  
  
-   <span data-ttu-id="f1bf9-150">Visual Basic `Collection` classe</span><span class="sxs-lookup"><span data-stu-id="f1bf9-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="f1bf9-151">Classes de System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="f1bf9-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="f1bf9-152">Você pode criar uma coleção genérica, usando uma das classes de <xref:System.Collections.Generic>namespace.</xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="f1bf9-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="f1bf9-153">Uma coleção genérica é útil quando cada item na coleção tem os mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="f1bf9-154">Uma coleção genérica impõe tipagem forte, permitindo que apenas os dados desejados tipo a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="f1bf9-155">A tabela a seguir lista algumas das classes usadas com frequência da <xref:System.Collections.Generic?displayProperty=fullName>namespace:</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f1bf9-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="f1bf9-156">Classe</span><span class="sxs-lookup"><span data-stu-id="f1bf9-156">Class</span></span>|<span data-ttu-id="f1bf9-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1bf9-157">Description</span></span>|  
|---|---|  
|<span data-ttu-id="f1bf9-158"><xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="f1bf9-158"><xref:System.Collections.Generic.Dictionary%602></span></span>|<span data-ttu-id="f1bf9-159">Representa uma coleção de pares chave/valor que são organizados com base na chave.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-159">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<span data-ttu-id="f1bf9-160"><xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-160"><xref:System.Collections.Generic.List%601></span></span>|<span data-ttu-id="f1bf9-161">Representa uma lista de objetos que podem ser acessados pelo índice.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-161">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="f1bf9-162">Fornece métodos para pesquisar, classificar e modificar listas.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-162">Provides methods to search, sort, and modify lists.</span></span>|  
|<span data-ttu-id="f1bf9-163"><xref:System.Collections.Generic.Queue%601></xref:System.Collections.Generic.Queue%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-163"><xref:System.Collections.Generic.Queue%601></span></span>|<span data-ttu-id="f1bf9-164">Representa o primeiro a entrar, primeiro a sair (PEPS) coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-164">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<span data-ttu-id="f1bf9-165"><xref:System.Collections.Generic.SortedList%602></xref:System.Collections.Generic.SortedList%602></span><span class="sxs-lookup"><span data-stu-id="f1bf9-165"><xref:System.Collections.Generic.SortedList%602></span></span>|<span data-ttu-id="f1bf9-166">Representa uma coleção de pares chave/valor que são classificadas por chave com base em associado <xref:System.Collections.Generic.IComparer%601>implementação.</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-166">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<span data-ttu-id="f1bf9-167"><xref:System.Collections.Generic.Stack%601></xref:System.Collections.Generic.Stack%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-167"><xref:System.Collections.Generic.Stack%601></span></span>|<span data-ttu-id="f1bf9-168">Representa um último a entrar, primeiro a sair (UEPS) coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-168">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="f1bf9-169">Para obter informações adicionais, consulte [comumente usados tipos de coleção](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55), [selecionando uma classe de coleção](../../../standard/collections/selecting-a-collection-class.md)e <xref:System.Collections.Generic?displayProperty=fullName>.</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f1bf9-169">For additional information, see [Commonly Used Collection Types](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=fullName>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="f1bf9-170">Classes de System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="f1bf9-170">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="f1bf9-171">No .NET Framework 4 ou mais recente, as coleções de <xref:System.Collections.Concurrent>namespace fornecem operações thread-safe eficientes para acessar itens de coleção de vários threads.</xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="f1bf9-171">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="f1bf9-172">As classes de <xref:System.Collections.Concurrent>namespace deve ser usado em vez dos tipos correspondentes no <xref:System.Collections.Generic?displayProperty=fullName>e <xref:System.Collections?displayProperty=fullName>namespaces sempre que vários threads estão acessando a coleção simultaneamente.</xref:System.Collections?displayProperty=fullName> </xref:System.Collections.Generic?displayProperty=fullName> </xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="f1bf9-172">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=fullName> and <xref:System.Collections?displayProperty=fullName> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="f1bf9-173">Para obter mais informações, consulte [coleção Thread-Safe](../../../standard/collections/threadsafe/index.md) e <xref:System.Collections.Concurrent>.</xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="f1bf9-173">For more information, see [Thread-Safe Collections](../../../standard/collections/threadsafe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="f1bf9-174">Algumas classes incluídas no <xref:System.Collections.Concurrent>namespace são <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>e <xref:System.Collections.Concurrent.ConcurrentStack%601>.</xref:System.Collections.Concurrent.ConcurrentStack%601> </xref:System.Collections.Concurrent.ConcurrentQueue%601> </xref:System.Collections.Concurrent.ConcurrentDictionary%602> </xref:System.Collections.Concurrent.BlockingCollection%601> </xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="f1bf9-174">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="f1bf9-175">Classes de System. Collections</span><span class="sxs-lookup"><span data-stu-id="f1bf9-175">System.Collections Classes</span></span>    
 <span data-ttu-id="f1bf9-176">As classes de <xref:System.Collections?displayProperty=fullName>namespace não armazenam elementos como especificamente objetos tipados, mas como objetos do tipo `Object`.</xref:System.Collections?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f1bf9-176">The classes in the <xref:System.Collections?displayProperty=fullName> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="f1bf9-177">Sempre que possível, você deve usar as coleções genéricas no <xref:System.Collections.Generic?displayProperty=fullName>namespace ou o <xref:System.Collections.Concurrent>namespace em vez dos tipos herdados no `System.Collections` namespace.</xref:System.Collections.Concurrent> </xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f1bf9-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=fullName> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="f1bf9-178">A tabela a seguir lista algumas das classes usadas no `System.Collections` namespace:</span><span class="sxs-lookup"><span data-stu-id="f1bf9-178">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="f1bf9-179">Classe</span><span class="sxs-lookup"><span data-stu-id="f1bf9-179">Class</span></span>|<span data-ttu-id="f1bf9-180">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1bf9-180">Description</span></span>|  
|---|---|  
|<span data-ttu-id="f1bf9-181"><xref:System.Collections.ArrayList></xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="f1bf9-181"><xref:System.Collections.ArrayList></span></span>|<span data-ttu-id="f1bf9-182">Representa uma matriz de objetos cujo tamanho é aumentado dinamicamente conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-182">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<span data-ttu-id="f1bf9-183"><xref:System.Collections.Hashtable></xref:System.Collections.Hashtable></span><span class="sxs-lookup"><span data-stu-id="f1bf9-183"><xref:System.Collections.Hashtable></span></span>|<span data-ttu-id="f1bf9-184">Representa uma coleção de pares chave-valor organizados com base no código hash da chave.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-184">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<span data-ttu-id="f1bf9-185"><xref:System.Collections.Queue></xref:System.Collections.Queue></span><span class="sxs-lookup"><span data-stu-id="f1bf9-185"><xref:System.Collections.Queue></span></span>|<span data-ttu-id="f1bf9-186">Representa o primeiro a entrar, primeiro a sair (PEPS) coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-186">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<span data-ttu-id="f1bf9-187"><xref:System.Collections.Stack></xref:System.Collections.Stack></span><span class="sxs-lookup"><span data-stu-id="f1bf9-187"><xref:System.Collections.Stack></span></span>|<span data-ttu-id="f1bf9-188">Representa um último a entrar, primeiro a sair (UEPS) coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-188">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="f1bf9-189">O <xref:System.Collections.Specialized>namespace fornece classes de coleções especializadas e fortemente tipadas, como coleções de sequência apenas e listas vinculadas e dicionários híbridos.</xref:System.Collections.Specialized></span><span class="sxs-lookup"><span data-stu-id="f1bf9-189">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="f1bf9-190">Classe de coleção do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1bf9-190">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="f1bf9-191">Você pode usar o Visual Basic <xref:Microsoft.VisualBasic.Collection>classe para acessar uma coleção de itens, usando qualquer um índice numérico ou um `String` chave.</xref:Microsoft.VisualBasic.Collection></span><span class="sxs-lookup"><span data-stu-id="f1bf9-191">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="f1bf9-192">Você pode adicionar itens a um objeto de coleção com ou sem especificar uma chave.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-192">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="f1bf9-193">Se você adicionar um item sem uma chave, você deve usar seu índice numérico para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-193">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="f1bf9-194">O Visual Basic `Collection` classe armazena todos seus elementos com o tipo `Object`, portanto, você pode adicionar um item de qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-194">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="f1bf9-195">Não há nenhuma segurança contra tipos de dados inapropriados sendo adicionados.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-195">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="f1bf9-196">Quando você usa o Visual Basic `Collection` classe, o primeiro item em uma coleção tem um índice de 1.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-196">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="f1bf9-197">Isso é diferente de classes de coleção do .NET Framework, para que o índice inicial é 0.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-197">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="f1bf9-198">Sempre que possível, você deve usar as coleções genéricas no <xref:System.Collections.Generic?displayProperty=fullName>namespace ou o <xref:System.Collections.Concurrent>namespace em vez do Visual Basic `Collection` classe</xref:System.Collections.Concurrent> </xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f1bf9-198">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=fullName> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="f1bf9-199">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Collection>.</xref:Microsoft.VisualBasic.Collection></span><span class="sxs-lookup"><span data-stu-id="f1bf9-199">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="f1bf9-200">Implementação de uma coleção de pares chave/valor</span><span class="sxs-lookup"><span data-stu-id="f1bf9-200">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="f1bf9-201">O <xref:System.Collections.Generic.Dictionary%602>coleção genérica permite que você acesse a elementos em uma coleção usando a chave de cada elemento.</xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="f1bf9-201">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="f1bf9-202">Cada adição ao dicionário consiste em um valor e a chave associada.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-202">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="f1bf9-203">Recuperar um valor usando sua chave é rápido, porque o `Dictionary` classe é implementada como uma tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-203">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="f1bf9-204">O exemplo a seguir cria um `Dictionary` coleta e itera pelo dicionário usando um `For Each` instrução.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-204">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
```vb  
Private Sub IterateThroughDictionary()  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    For Each kvp As KeyValuePair(Of String, Element) In elements  
        Dim theElement As Element = kvp.Value  
  
        Console.WriteLine("key: " & kvp.Key)  
        With theElement  
            Console.WriteLine("values: " & .Symbol & " " &  
                .Name & " " & .AtomicNumber)  
        End With  
    Next  
End Sub  
  
Private Function BuildDictionary() As Dictionary(Of String, Element)  
    Dim elements As New Dictionary(Of String, Element)  
  
    AddToDictionary(elements, "K", "Potassium", 19)  
    AddToDictionary(elements, "Ca", "Calcium", 20)  
    AddToDictionary(elements, "Sc", "Scandium", 21)  
    AddToDictionary(elements, "Ti", "Titanium", 22)  
  
    Return elements  
End Function  
  
Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),  
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)  
    Dim theElement As New Element  
  
    theElement.Symbol = symbol  
    theElement.Name = name  
    theElement.AtomicNumber = atomicNumber  
  
    elements.Add(Key:=theElement.Symbol, value:=theElement)  
End Sub  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <span data-ttu-id="f1bf9-205">Em vez disso, usar um inicializador de coleção para criar o `Dictionary` coleção, você pode substituir o `BuildDictionary` e `AddToDictionary` métodos com o seguinte método.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-205">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
```vb  
Private Function BuildDictionary2() As Dictionary(Of String, Element)  
    Return New Dictionary(Of String, Element) From  
        {  
            {"K", New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {"Ca", New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {"Sc", New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {"Ti", New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
```  
  
 <span data-ttu-id="f1bf9-206">O exemplo a seguir usa o <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>método e o <xref:System.Collections.Generic.Dictionary%602.Item%2A>propriedade `Dictionary` para localizar rapidamente um item por chave.</xref:System.Collections.Generic.Dictionary%602.Item%2A> </xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A></span><span class="sxs-lookup"><span data-stu-id="f1bf9-206">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="f1bf9-207">O `Item` propriedade permite que você acesse um item de `elements` coleção usando o `elements(symbol)` código no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-207">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
```vb  
Private Sub FindInDictionary(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    If elements.ContainsKey(symbol) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Dim theElement = elements(symbol)  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
 <span data-ttu-id="f1bf9-208">O exemplo a seguir usará o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>método localizar rapidamente um item por chave.</xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A></span><span class="sxs-lookup"><span data-stu-id="f1bf9-208">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
```vb  
Private Sub FindInDictionary2(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    Dim theElement As Element = Nothing  
    If elements.TryGetValue(symbol, theElement) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
<a name="BKMK_LINQ"></a> 
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="f1bf9-209">Usando LINQ para acessar uma coleção</span><span class="sxs-lookup"><span data-stu-id="f1bf9-209">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="f1bf9-210">LINQ (consulta integrada à linguagem) pode ser usado para acessar coleções.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-210">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="f1bf9-211">Consultas LINQ fornecem filtragem, classificação e agrupamento de recursos.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-211">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="f1bf9-212">Para obter mais informações, consulte [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="f1bf9-212">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="f1bf9-213">O exemplo a seguir executa uma consulta LINQ em um genérico `List`.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-213">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="f1bf9-214">A consulta LINQ retorna uma coleção diferente que contém os resultados.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-214">The LINQ query returns a different collection that contains the results.</span></span>  
  
```vb  
Private Sub ShowLINQ()  
    Dim elements As List(Of Element) = BuildList()  
  
    ' LINQ Query.  
    Dim subset = From theElement In elements  
                  Where theElement.AtomicNumber < 22  
                  Order By theElement.Name  
  
    For Each theElement In subset  
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)  
    Next  
  
    ' Output:  
    '  Calcium 20  
    '  Potassium 19  
    '  Scandium 21  
End Sub  
  
Private Function BuildList() As List(Of Element)  
    Return New List(Of Element) From  
        {  
            {New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <a name="BKMK_Sorting"></a> 
## <a name="sorting-a-collection"></a><span data-ttu-id="f1bf9-215">Classificando uma coleção</span><span class="sxs-lookup"><span data-stu-id="f1bf9-215">Sorting a Collection</span></span>  
 <span data-ttu-id="f1bf9-216">O exemplo a seguir ilustra um procedimento para uma coleção de classificação.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-216">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="f1bf9-217">O exemplo classifica instâncias de `Car` classe são armazenados em <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-217">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f1bf9-218">O `Car` classe implementa o <xref:System.IComparable%601>interface, que requer que o <xref:System.IComparable%601.CompareTo%2A>método ser implementado.</xref:System.IComparable%601.CompareTo%2A> </xref:System.IComparable%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-218">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="f1bf9-219">Cada chamada para o <xref:System.IComparable%601.CompareTo%2A>método faz uma comparação única que é usada para classificação.</xref:System.IComparable%601.CompareTo%2A></span><span class="sxs-lookup"><span data-stu-id="f1bf9-219">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="f1bf9-220">Códigos escritos pelo usuário no `CompareTo` método retorna um valor para cada comparação do objeto atual com outro objeto.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-220">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="f1bf9-221">O valor retornado é menor que zero se o objeto atual é menor do que o outro objeto maior do que zero se o objeto atual é maior do que o outro objeto e zero se eles forem iguais.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-221">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="f1bf9-222">Isso permite que você defina no código os critérios para maior que, menor que e igual.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-222">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="f1bf9-223">No `ListCars` método, o `cars.Sort()` instrução classifica a lista.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-223">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="f1bf9-224">Essa chamada para o <xref:System.Collections.Generic.List%601.Sort%2A>método o <xref:System.Collections.Generic.List%601>faz com que o `CompareTo` método a ser chamado automaticamente para o `Car` objetos no `List`.</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A></span><span class="sxs-lookup"><span data-stu-id="f1bf9-224">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
```vb  
Public Sub ListCars()  
  
    ' Create some new cars.  
    Dim cars As New List(Of Car) From  
    {  
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},  
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},  
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},  
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},  
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},  
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},  
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}  
    }  
  
    ' Sort the cars by color alphabetically, and then by speed  
    ' in descending order.  
    cars.Sort()  
  
    ' View all of the cars.  
    For Each thisCar As Car In cars  
        Console.Write(thisCar.Color.PadRight(5) & " ")  
        Console.Write(thisCar.Speed.ToString & " ")  
        Console.Write(thisCar.Name)  
        Console.WriteLine()  
    Next  
  
    ' Output:  
    '  blue  50 car4  
    '  blue  30 car5  
    '  blue  20 car1  
    '  green 50 car7  
    '  green 10 car3  
    '  red   60 car6  
    '  red   50 car2  
End Sub  
  
Public Class Car  
    Implements IComparable(Of Car)  
  
    Public Property Name As String  
    Public Property Speed As Integer  
    Public Property Color As String  
  
    Public Function CompareTo(ByVal other As Car) As Integer _  
        Implements System.IComparable(Of Car).CompareTo  
        ' A call to this method makes a single comparison that is  
        ' used for sorting.  
  
        ' Determine the relative order of the objects being compared.  
        ' Sort by color alphabetically, and then by speed in  
        ' descending order.  
  
        ' Compare the colors.  
        Dim compare As Integer  
        compare = String.Compare(Me.Color, other.Color, True)  
  
        ' If the colors are the same, compare the speeds.  
        If compare = 0 Then  
            compare = Me.Speed.CompareTo(other.Speed)  
  
            ' Use descending order for speed.  
            compare = -compare  
        End If  
  
        Return compare  
    End Function  
End Class  
```  
  
<a name="BKMK_CustomCollection"></a> 
## <a name="defining-a-custom-collection"></a><span data-ttu-id="f1bf9-225">Definindo uma coleção personalizada</span><span class="sxs-lookup"><span data-stu-id="f1bf9-225">Defining a Custom Collection</span></span>  
 <span data-ttu-id="f1bf9-226">Você pode definir uma coleção Implementando a <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Collections.IEnumerable>interface.</xref:System.Collections.IEnumerable> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="f1bf9-226">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="f1bf9-227">Para obter informações adicionais, consulte [enumerando uma coleção](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).</span><span class="sxs-lookup"><span data-stu-id="f1bf9-227">For additional information, see [Enumerating a Collection](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="f1bf9-228">Embora seja possível definir uma coleção personalizada, é melhor usar as coleções que estão incluídas no .NET Framework, que são descritos em [tipos de coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-228">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) earlier in this topic.</span></span>  
  
 <span data-ttu-id="f1bf9-229">O exemplo a seguir define uma classe de coleção personalizada chamada `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-229">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="f1bf9-230">Essa classe implementa o <xref:System.Collections.IEnumerable>interface, que requer que o <xref:System.Collections.IEnumerable.GetEnumerator%2A>método ser implementado.</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="f1bf9-230">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="f1bf9-231">O `GetEnumerator` método retorna uma instância da `ColorEnumerator` classe.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-231">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="f1bf9-232">`ColorEnumerator`implementa o <xref:System.Collections.IEnumerator>interface, que requer que o <xref:System.Collections.IEnumerator.Current%2A>propriedade <xref:System.Collections.IEnumerator.MoveNext%2A>método, e <xref:System.Collections.IEnumerator.Reset%2A>método ser implementado.</xref:System.Collections.IEnumerator.Reset%2A> </xref:System.Collections.IEnumerator.MoveNext%2A> </xref:System.Collections.IEnumerator.Current%2A> </xref:System.Collections.IEnumerator></span><span class="sxs-lookup"><span data-stu-id="f1bf9-232">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
```vb  
Public Sub ListColors()  
    Dim colors As New AllColors()  
  
    For Each theColor As Color In colors  
        Console.Write(theColor.Name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: red blue green  
End Sub  
  
' Collection class.  
Public Class AllColors  
    Implements System.Collections.IEnumerable  
  
    Private _colors() As Color =  
    {  
        New Color With {.Name = "red"},  
        New Color With {.Name = "blue"},  
        New Color With {.Name = "green"}  
    }  
  
    Public Function GetEnumerator() As System.Collections.IEnumerator _  
        Implements System.Collections.IEnumerable.GetEnumerator  
  
        Return New ColorEnumerator(_colors)  
  
        ' Instead of creating a custom enumerator, you could  
        ' use the GetEnumerator of the array.  
        'Return _colors.GetEnumerator  
    End Function  
  
    ' Custom enumerator.  
    Private Class ColorEnumerator  
        Implements System.Collections.IEnumerator  
  
        Private _colors() As Color  
        Private _position As Integer = -1  
  
        Public Sub New(ByVal colors() As Color)  
            _colors = colors  
        End Sub  
  
        Public ReadOnly Property Current() As Object _  
            Implements System.Collections.IEnumerator.Current  
            Get  
                Return _colors(_position)  
            End Get  
        End Property  
  
        Public Function MoveNext() As Boolean _  
            Implements System.Collections.IEnumerator.MoveNext  
            _position += 1  
            Return (_position < _colors.Length)  
        End Function  
  
        Public Sub Reset() Implements System.Collections.IEnumerator.Reset  
            _position = -1  
        End Sub  
    End Class  
End Class  
  
' Element class.  
Public Class Color  
    Public Property Name As String  
End Class  
```  
  
<a name="BKMK_Iterators"></a>
##  <a name="iterators"></a><span data-ttu-id="f1bf9-233">Iteradores</span><span class="sxs-lookup"><span data-stu-id="f1bf9-233">Iterators</span></span>  
 <span data-ttu-id="f1bf9-234">Um *iterador* é usado para executar uma iteração personalizada em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-234">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="f1bf9-235">Um iterador pode ser um método ou um `get` acessador.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-235">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="f1bf9-236">Um iterador usa um [gerar](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento da coleção um por vez.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-236">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="f1bf9-237">Chamar um iterador usando um [para cada uma... Próxima](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-237">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="f1bf9-238">Cada iteração de `For Each` loop chama o iterador.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-238">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="f1bf9-239">Quando um `Yield` instrução for atingida no iterador, uma expressão é retornada e o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-239">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="f1bf9-240">Execução é reiniciada a partir desse local na próxima vez que o iterador é chamado.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-240">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="f1bf9-241">Para obter mais informações, consulte [iteradores (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="f1bf9-241">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="f1bf9-242">O exemplo a seguir usa um método iterador.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-242">The following example uses an iterator method.</span></span> <span data-ttu-id="f1bf9-243">O método iterador tem um `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-243">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="f1bf9-244">No `ListEvenNumbers` cada iteração de um método, o `For Each` corpo da instrução cria uma chamada para o método iterador, que passa para o próximo `Yield` instrução.</span><span class="sxs-lookup"><span data-stu-id="f1bf9-244">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
```vb  
Public Sub ListEvenNumbers()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    Console.WriteLine()  
    ' Output: 6 8 10 12 14 16 18  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As IEnumerable(Of Integer)  
  
' Yield even numbers in the range.  
    For number = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1bf9-245">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1bf9-245">See Also</span></span>  
 <span data-ttu-id="f1bf9-246">[Inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1bf9-246">[Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span></span>  
<span data-ttu-id="f1bf9-247"> [Conceitos de programação (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1bf9-247"> [Programming Concepts (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="f1bf9-248"> [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f1bf9-248"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="f1bf9-249"> [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="f1bf9-249"> [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="f1bf9-250"> [LINQ paralelo (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455) </span><span class="sxs-lookup"><span data-stu-id="f1bf9-250"> [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455) </span></span>  
<span data-ttu-id="f1bf9-251"> [Coleções e estruturas de dados](../../../standard/collections/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1bf9-251"> [Collections and Data Structures](../../../standard/collections/index.md) </span></span>  
<span data-ttu-id="f1bf9-252"> [Criando e manipulando coleções](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069) </span><span class="sxs-lookup"><span data-stu-id="f1bf9-252"> [Creating and Manipulating Collections](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069) </span></span>  
<span data-ttu-id="f1bf9-253"> [Selecionando uma classe de coleção](../../../standard/collections/selecting-a-collection-class.md) </span><span class="sxs-lookup"><span data-stu-id="f1bf9-253"> [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md) </span></span>  
<span data-ttu-id="f1bf9-254"> [Comparações e ordenações dentro de coleções](../../../standard/collections/comparisons-and-sorts-within-collections.md) </span><span class="sxs-lookup"><span data-stu-id="f1bf9-254"> [Comparisons and Sorts Within Collections](../../../standard/collections/comparisons-and-sorts-within-collections.md) </span></span>  
<span data-ttu-id="f1bf9-255"> [Quando Usar Coleções Genéricas](../../../standard/collections/when-to-use-generic-collections.md)</span><span class="sxs-lookup"><span data-stu-id="f1bf9-255"> [When to Use Generic Collections](../../../standard/collections/when-to-use-generic-collections.md)</span></span>
