---
title: Coleções (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 60519de1f580bf1cfa4aa067d4a999b20ea8d54d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083118"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="68c80-102">Coleções (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68c80-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="68c80-103">Para muitos aplicativos, você desejará criar e gerenciar grupos de objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="68c80-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="68c80-104">Há duas maneiras de agrupar objetos: criando matrizes de objetos e criando coleções de objetos.</span><span class="sxs-lookup"><span data-stu-id="68c80-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="68c80-105">As matrizes são mais úteis ao criar e trabalhar com um número fixo de objetos fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="68c80-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="68c80-106">Para obter informações sobre matrizes, consulte [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="68c80-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="68c80-107">As coleções fornecem uma maneira mais flexível de trabalhar com grupos de objetos.</span><span class="sxs-lookup"><span data-stu-id="68c80-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="68c80-108">Ao contrário das matrizes, o grupo de objetos com o qual você trabalha pode crescer e reduzir dinamicamente conforme as necessidades do aplicativo são alteradas.</span><span class="sxs-lookup"><span data-stu-id="68c80-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="68c80-109">Para algumas coleções, você pode atribuir uma chave para qualquer objeto que colocar na coleção para que você possa recuperar rapidamente o objeto, usando a chave.</span><span class="sxs-lookup"><span data-stu-id="68c80-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="68c80-110">Uma coleção é uma classe, portanto você deve declarar uma instância da classe antes de adicionar elementos a essa coleção.</span><span class="sxs-lookup"><span data-stu-id="68c80-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="68c80-111">Se a coleção contiver elementos de apenas um tipo de dados, você poderá usar uma das classes no namespace <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="68c80-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="68c80-112">Uma coleção genérica impõe segurança de tipos para que nenhum outro tipo de dados possa ser adicionado a ela.</span><span class="sxs-lookup"><span data-stu-id="68c80-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="68c80-113">Ao recuperar um elemento de uma coleção genérica, você não precisa determinar seu tipo de dados ou convertê-lo.</span><span class="sxs-lookup"><span data-stu-id="68c80-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68c80-114">Para os exemplos neste tópico, inclua [importações](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instruções para o `System.Collections.Generic` e `System.Linq` namespaces.</span><span class="sxs-lookup"><span data-stu-id="68c80-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="68c80-115">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="68c80-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="68c80-116">Usando uma coleção simples</span><span class="sxs-lookup"><span data-stu-id="68c80-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="68c80-117">Tipos de coleções</span><span class="sxs-lookup"><span data-stu-id="68c80-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="68c80-118">Classes System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="68c80-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="68c80-119">Classes System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="68c80-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="68c80-120">Classes System.Collections</span><span class="sxs-lookup"><span data-stu-id="68c80-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="68c80-121">Classe de coleção do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68c80-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="68c80-122">Implementando uma coleção de pares chave-valor</span><span class="sxs-lookup"><span data-stu-id="68c80-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="68c80-123">Usando LINQ para acessar uma coleção</span><span class="sxs-lookup"><span data-stu-id="68c80-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="68c80-124">Classificando uma coleção</span><span class="sxs-lookup"><span data-stu-id="68c80-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="68c80-125">Definindo uma coleção personalizada</span><span class="sxs-lookup"><span data-stu-id="68c80-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="68c80-126">Iteradores</span><span class="sxs-lookup"><span data-stu-id="68c80-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="68c80-127">Usando uma coleção simples</span><span class="sxs-lookup"><span data-stu-id="68c80-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="68c80-128">Os exemplos nesta seção usam a classe genérica <xref:System.Collections.Generic.List%601>, que habilita você a trabalhar com uma lista de objetos fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="68c80-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="68c80-129">O exemplo a seguir cria uma lista de cadeias de caracteres e, em seguida, itera por meio de cadeias de caracteres usando um [para cada um... Próxima](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="68c80-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="68c80-130">Se o conteúdo de uma coleção for conhecido com antecedência, você poderá usar um *inicializador de coleção* para inicializar a coleção.</span><span class="sxs-lookup"><span data-stu-id="68c80-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="68c80-131">Para obter mais informações, consulte [Inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="68c80-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="68c80-132">O exemplo a seguir é igual ao exemplo anterior, exceto que um inicializador de coleção é usado para adicionar elementos à coleção.</span><span class="sxs-lookup"><span data-stu-id="68c80-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="68c80-133">Você pode usar um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) instrução em vez de um `For Each` instrução para iterar por meio de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="68c80-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="68c80-134">Você realiza isso acessando os elementos da coleção pela posição do índice.</span><span class="sxs-lookup"><span data-stu-id="68c80-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="68c80-135">O índice dos elementos começa em 0 e termina na contagem de elementos, menos de 1.</span><span class="sxs-lookup"><span data-stu-id="68c80-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="68c80-136">O exemplo a seguir itera nos elementos de uma coleção usando `For…Next` em vez de `For Each`.</span><span class="sxs-lookup"><span data-stu-id="68c80-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="68c80-137">O exemplo a seguir remove um elemento da coleção, especificando o objeto a ser removido.</span><span class="sxs-lookup"><span data-stu-id="68c80-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="68c80-138">O exemplo a seguir remove elementos de uma lista genérica.</span><span class="sxs-lookup"><span data-stu-id="68c80-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="68c80-139">Em vez de um `For Each` instrução, uma [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) instrução que itera em ordem decrescente é usada.</span><span class="sxs-lookup"><span data-stu-id="68c80-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="68c80-140">Isso é feito porque o método <xref:System.Collections.Generic.List%601.RemoveAt%2A> faz com que os elementos após um elemento removido tenham um valor de índice menor.</span><span class="sxs-lookup"><span data-stu-id="68c80-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="68c80-141">Para o tipo dos elementos na <xref:System.Collections.Generic.List%601>, você também pode definir sua própria classe.</span><span class="sxs-lookup"><span data-stu-id="68c80-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="68c80-142">No exemplo a seguir, a classe `Galaxy` que é usada pela <xref:System.Collections.Generic.List%601> é definida no código.</span><span class="sxs-lookup"><span data-stu-id="68c80-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="68c80-143">Tipos de coleções</span><span class="sxs-lookup"><span data-stu-id="68c80-143">Kinds of Collections</span></span>   
 <span data-ttu-id="68c80-144">Várias coleções comuns são fornecidas pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="68c80-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="68c80-145">Cada tipo de coleção é projetado para uma finalidade específica.</span><span class="sxs-lookup"><span data-stu-id="68c80-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="68c80-146">Algumas das classes de coleção comuns são descritas nesta seção:</span><span class="sxs-lookup"><span data-stu-id="68c80-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="68c80-147">Classes <xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="68c80-147"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="68c80-148">Classes <xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="68c80-148"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="68c80-149">Classes <xref:System.Collections></span><span class="sxs-lookup"><span data-stu-id="68c80-149"><xref:System.Collections> classes</span></span>  
  
-   <span data-ttu-id="68c80-150">Visual Basic `Collection` classe</span><span class="sxs-lookup"><span data-stu-id="68c80-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="68c80-151">Classes System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="68c80-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="68c80-152">Você pode criar uma coleção genérica usando uma das classes no namespace <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="68c80-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="68c80-153">Uma coleção genérica é útil quando cada item na coleção tem o mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="68c80-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="68c80-154">Uma coleção genérica impõe tipagem forte, permitindo que apenas o tipo de dados desejado seja adicionado.</span><span class="sxs-lookup"><span data-stu-id="68c80-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="68c80-155">A tabela a seguir lista algumas das classes frequentemente usadas do namespace <xref:System.Collections.Generic?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="68c80-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="68c80-156">Classe</span><span class="sxs-lookup"><span data-stu-id="68c80-156">Class</span></span>|<span data-ttu-id="68c80-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="68c80-157">Description</span></span>|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="68c80-158">Representa uma coleção de pares chave-valor organizados com base na chave.</span><span class="sxs-lookup"><span data-stu-id="68c80-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="68c80-159">Representa uma lista de objetos que podem ser acessados por índice.</span><span class="sxs-lookup"><span data-stu-id="68c80-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="68c80-160">Fornece métodos para pesquisar, classificar e modificar listas.</span><span class="sxs-lookup"><span data-stu-id="68c80-160">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="68c80-161">Representa uma coleção de objetos PEPS (primeiro a entrar, primeiro a sair).</span><span class="sxs-lookup"><span data-stu-id="68c80-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="68c80-162">Representa uma coleção de pares chave/valor que são classificados por chave com base na implementação de <xref:System.Collections.Generic.IComparer%601> associada.</span><span class="sxs-lookup"><span data-stu-id="68c80-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="68c80-163">Representa uma coleção de objetos UEPS (último a entrar, primeiro a sair).</span><span class="sxs-lookup"><span data-stu-id="68c80-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="68c80-164">Para obter informações adicionais, consulte [Tipos de coleção comumente usados](../../../standard/collections/commonly-used-collection-types.md), [Selecionando uma classe de coleção](../../../standard/collections/selecting-a-collection-class.md) e <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="68c80-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="68c80-165">Classes System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="68c80-165">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="68c80-166">No .NET Framework 4 ou mais recente, as coleções no namespace <xref:System.Collections.Concurrent> fornecem operações thread-safe eficientes para acessar itens da coleção de vários threads.</span><span class="sxs-lookup"><span data-stu-id="68c80-166">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="68c80-167">As classes no namespace <xref:System.Collections.Concurrent> deverão ser usadas em vez dos tipos correspondentes nos namespaces <xref:System.Collections.Generic?displayProperty=nameWithType> e <xref:System.Collections?displayProperty=nameWithType> sempre que vários threads estiverem acessando a coleção simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="68c80-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="68c80-168">Para obter mais informações, veja [Coleções thread-safe](../../../standard/collections/thread-safe/index.md) e <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="68c80-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="68c80-169">Algumas classes incluídas no namespace <xref:System.Collections.Concurrent> são <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601> e <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="68c80-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="68c80-170">Classes System.Collections</span><span class="sxs-lookup"><span data-stu-id="68c80-170">System.Collections Classes</span></span>    
 <span data-ttu-id="68c80-171">As classes no namespace <xref:System.Collections?displayProperty=nameWithType> não armazenam elementos como objetos especificamente tipados, mas como objetos do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="68c80-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="68c80-172">Sempre que possível, você deve usar as coleções genéricas no namespace <xref:System.Collections.Generic?displayProperty=nameWithType> ou no <xref:System.Collections.Concurrent> em vez dos tipos herdados no namespace `System.Collections`.</span><span class="sxs-lookup"><span data-stu-id="68c80-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="68c80-173">A tabela a seguir lista algumas das classes frequentemente usadas no namespace `System.Collections`:</span><span class="sxs-lookup"><span data-stu-id="68c80-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="68c80-174">Classe</span><span class="sxs-lookup"><span data-stu-id="68c80-174">Class</span></span>|<span data-ttu-id="68c80-175">Descrição</span><span class="sxs-lookup"><span data-stu-id="68c80-175">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="68c80-176">Representa uma matriz de objetos cujo tamanho é aumentado dinamicamente conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="68c80-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="68c80-177">Representa uma coleção de pares chave-valor organizados com base no código hash da chave.</span><span class="sxs-lookup"><span data-stu-id="68c80-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="68c80-178">Representa uma coleção de objetos PEPS (primeiro a entrar, primeiro a sair).</span><span class="sxs-lookup"><span data-stu-id="68c80-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="68c80-179">Representa uma coleção de objetos UEPS (último a entrar, primeiro a sair).</span><span class="sxs-lookup"><span data-stu-id="68c80-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="68c80-180">O namespace <xref:System.Collections.Specialized> fornece classes de coleções especializadas e fortemente tipadas, como coleções somente de cadeias de caracteres, bem como de dicionários híbridos e de listas vinculadas.</span><span class="sxs-lookup"><span data-stu-id="68c80-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="68c80-181">Classe de coleção do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68c80-181">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="68c80-182">Você pode usar o Visual Basic <xref:Microsoft.VisualBasic.Collection> de classe para acessar uma coleção de item usando um índice numérico ou um `String` chave.</span><span class="sxs-lookup"><span data-stu-id="68c80-182">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="68c80-183">Você pode adicionar itens a um objeto de coleção com ou sem especificar uma chave.</span><span class="sxs-lookup"><span data-stu-id="68c80-183">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="68c80-184">Se você adicionar um item sem uma chave, você deve usar seu índice numérico para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="68c80-184">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="68c80-185">O Visual Basic `Collection` classe armazena todos os seus elementos como tipo `Object`, portanto, você pode adicionar um item de qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="68c80-185">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="68c80-186">Não há nenhuma garantia em relação a tipos de dados inapropriados sendo adicionados.</span><span class="sxs-lookup"><span data-stu-id="68c80-186">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="68c80-187">Quando você usa o Visual Basic `Collection` classe, o primeiro item em uma coleção tem um índice de 1.</span><span class="sxs-lookup"><span data-stu-id="68c80-187">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="68c80-188">Isso é diferente das classes de coleção do .NET Framework, para o qual o índice inicial é 0.</span><span class="sxs-lookup"><span data-stu-id="68c80-188">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="68c80-189">Sempre que possível, você deve usar as coleções genéricas na <xref:System.Collections.Generic?displayProperty=nameWithType> namespace ou o <xref:System.Collections.Concurrent> namespace, em vez do Visual Basic `Collection` classe.</span><span class="sxs-lookup"><span data-stu-id="68c80-189">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="68c80-190">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="68c80-190">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="68c80-191">Implementando uma coleção de pares chave-valor</span><span class="sxs-lookup"><span data-stu-id="68c80-191">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="68c80-192">A coleção genérica <xref:System.Collections.Generic.Dictionary%602> permite que você acesse elementos em uma coleção usando a chave de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="68c80-192">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="68c80-193">Cada adição ao dicionário consiste em um valor e a respectiva chave associada.</span><span class="sxs-lookup"><span data-stu-id="68c80-193">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="68c80-194">A recuperação de um valor usando sua chave é rápida, porque a classe `Dictionary` é implementada como uma tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="68c80-194">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="68c80-195">O exemplo a seguir cria uma coleção `Dictionary` e itera no dicionário usando uma instrução `For Each`.</span><span class="sxs-lookup"><span data-stu-id="68c80-195">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
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
  
 <span data-ttu-id="68c80-196">Para, em vez disso, usar um inicializador de coleção para criar a coleção `Dictionary`, você pode substituir os métodos `BuildDictionary` e `AddToDictionary` pelo seguinte método.</span><span class="sxs-lookup"><span data-stu-id="68c80-196">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="68c80-197">O exemplo a seguir usa o método <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> e a propriedade <xref:System.Collections.Generic.Dictionary%602.Item%2A> de `Dictionary` para localizar rapidamente um item por chave.</span><span class="sxs-lookup"><span data-stu-id="68c80-197">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="68c80-198">O `Item` propriedade permite que você acesse um item em de `elements` coleção usando o `elements(symbol)` código no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="68c80-198">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
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
  
 <span data-ttu-id="68c80-199">O exemplo a seguir usa o método <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> para localizar rapidamente um item por chave.</span><span class="sxs-lookup"><span data-stu-id="68c80-199">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="68c80-200">Usando LINQ para acessar uma coleção</span><span class="sxs-lookup"><span data-stu-id="68c80-200">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="68c80-201">A LINQ (consulta integrada à linguagem) pode ser usada para acessar coleções.</span><span class="sxs-lookup"><span data-stu-id="68c80-201">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="68c80-202">As consultas LINQ fornecem recursos de filtragem, classificação e agrupamento.</span><span class="sxs-lookup"><span data-stu-id="68c80-202">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="68c80-203">Para obter mais informações, consulte [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="68c80-203">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="68c80-204">O exemplo a seguir executa uma consulta LINQ em uma `List` genérica.</span><span class="sxs-lookup"><span data-stu-id="68c80-204">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="68c80-205">A consulta LINQ retorna uma coleção diferente que contém os resultados.</span><span class="sxs-lookup"><span data-stu-id="68c80-205">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="68c80-206">Classificando uma coleção</span><span class="sxs-lookup"><span data-stu-id="68c80-206">Sorting a Collection</span></span>  
 <span data-ttu-id="68c80-207">O exemplo a seguir ilustra um procedimento para a classificação de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="68c80-207">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="68c80-208">O exemplo classifica instâncias da classe `Car` que estão armazenados em uma <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="68c80-208">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="68c80-209">A classe `Car` implementa a interface <xref:System.IComparable%601>, que requer que o método <xref:System.IComparable%601.CompareTo%2A> seja implementado.</span><span class="sxs-lookup"><span data-stu-id="68c80-209">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="68c80-210">Cada chamada ao método <xref:System.IComparable%601.CompareTo%2A> faz uma comparação única que é usada para classificação.</span><span class="sxs-lookup"><span data-stu-id="68c80-210">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="68c80-211">Os códigos escritos pelo usuário no método `CompareTo` retornam um valor para cada comparação do objeto atual com outro objeto.</span><span class="sxs-lookup"><span data-stu-id="68c80-211">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="68c80-212">O valor retornado será menor que zero se o objeto atual for menor que o outro objeto, maior que zero se o objeto atual for maior que o outro objeto e zero, se eles forem iguais.</span><span class="sxs-lookup"><span data-stu-id="68c80-212">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="68c80-213">Isso permite que você defina no código os critérios para maior que, menor que e igual.</span><span class="sxs-lookup"><span data-stu-id="68c80-213">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="68c80-214">No método `ListCars`, a instrução `cars.Sort()` classifica a lista.</span><span class="sxs-lookup"><span data-stu-id="68c80-214">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="68c80-215">Essa chamada para o método <xref:System.Collections.Generic.List%601.Sort%2A> da <xref:System.Collections.Generic.List%601> faz com que o método `CompareTo` seja chamado automaticamente para os objetos `Car` na `List`.</span><span class="sxs-lookup"><span data-stu-id="68c80-215">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="68c80-216">Definindo uma coleção personalizada</span><span class="sxs-lookup"><span data-stu-id="68c80-216">Defining a Custom Collection</span></span>  
 <span data-ttu-id="68c80-217">Você pode definir uma coleção implementando a interface <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="68c80-217">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="68c80-218">Para obter mais informações, consulte [enumerando uma coleção](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span><span class="sxs-lookup"><span data-stu-id="68c80-218">For additional information, see [Enumerating a Collection](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="68c80-219">Embora seja possível definir uma coleção personalizada, é melhor usar as coleções que estão incluídas no .NET Framework, que estão descritas em [Tipos de coleções](#kinds-of-collections) anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="68c80-219">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="68c80-220">O exemplo a seguir define uma classe de coleção personalizada chamada `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="68c80-220">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="68c80-221">Essa classe implementa a interface <xref:System.Collections.IEnumerable>, que requer que o método <xref:System.Collections.IEnumerable.GetEnumerator%2A> seja implementado.</span><span class="sxs-lookup"><span data-stu-id="68c80-221">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="68c80-222">O método `GetEnumerator` retorna uma instância da classe `ColorEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="68c80-222">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="68c80-223">`ColorEnumerator` implementa a interface <xref:System.Collections.IEnumerator>, que requer que a propriedade <xref:System.Collections.IEnumerator.Current%2A>, o método <xref:System.Collections.IEnumerator.MoveNext%2A> e o método <xref:System.Collections.IEnumerator.Reset%2A> sejam implementados.</span><span class="sxs-lookup"><span data-stu-id="68c80-223">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="68c80-224">Iterators</span><span class="sxs-lookup"><span data-stu-id="68c80-224">Iterators</span></span>  
 <span data-ttu-id="68c80-225">Um *iterador* é usado para realizar uma iteração personalizada em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="68c80-225">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="68c80-226">Um iterador pode ser um método ou um acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="68c80-226">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="68c80-227">Um iterador usa uma [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento da coleção um por vez.</span><span class="sxs-lookup"><span data-stu-id="68c80-227">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="68c80-228">Você chama um iterador usando uma [para cada um... Próxima](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="68c80-228">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="68c80-229">Cada iteração do loop `For Each` chama o iterador.</span><span class="sxs-lookup"><span data-stu-id="68c80-229">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="68c80-230">Quando uma instrução `Yield` é alcançada no iterador, uma expressão é retornada e o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="68c80-230">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="68c80-231">A execução será reiniciada desse local na próxima vez que o iterador for chamado.</span><span class="sxs-lookup"><span data-stu-id="68c80-231">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="68c80-232">Para obter mais informações, consulte [iteradores (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="68c80-232">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="68c80-233">O exemplo a seguir usa um método iterador.</span><span class="sxs-lookup"><span data-stu-id="68c80-233">The following example uses an iterator method.</span></span> <span data-ttu-id="68c80-234">O método iterador tem uma `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="68c80-234">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="68c80-235">No método `ListEvenNumbers`, cada iteração do corpo da instrução `For Each` cria uma chamada ao método iterador, que avança para a próxima instrução `Yield`.</span><span class="sxs-lookup"><span data-stu-id="68c80-235">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68c80-236">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68c80-236">See also</span></span>

- [<span data-ttu-id="68c80-237">Inicializadores de Coleção</span><span class="sxs-lookup"><span data-stu-id="68c80-237">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
- [<span data-ttu-id="68c80-238">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68c80-238">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)  
- [<span data-ttu-id="68c80-239">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="68c80-239">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
- [<span data-ttu-id="68c80-240">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68c80-240">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="68c80-241">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="68c80-241">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
- [<span data-ttu-id="68c80-242">Coleções e Estruturas de Dados</span><span class="sxs-lookup"><span data-stu-id="68c80-242">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
- [<span data-ttu-id="68c80-243">Criando e manipulando coleções</span><span class="sxs-lookup"><span data-stu-id="68c80-243">Creating and Manipulating Collections</span></span>](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
- [<span data-ttu-id="68c80-244">Selecionando uma Classe de Coleção</span><span class="sxs-lookup"><span data-stu-id="68c80-244">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
- [<span data-ttu-id="68c80-245">Comparações e Classificações Dentro de Coleções</span><span class="sxs-lookup"><span data-stu-id="68c80-245">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
- [<span data-ttu-id="68c80-246">Quando Usar Coleções Genéricas</span><span class="sxs-lookup"><span data-stu-id="68c80-246">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
