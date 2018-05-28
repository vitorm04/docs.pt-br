---
title: Coleções (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 7400d4eee4df99cb1e255e428f83028fddf481f4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
---
# <a name="collections-c"></a><span data-ttu-id="bb31d-102">Coleções (C#)</span><span class="sxs-lookup"><span data-stu-id="bb31d-102">Collections (C#)</span></span>
<span data-ttu-id="bb31d-103">Para muitos aplicativos, você desejará criar e gerenciar grupos de objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="bb31d-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="bb31d-104">Há duas maneiras de agrupar objetos: criando matrizes de objetos e criando coleções de objetos.</span><span class="sxs-lookup"><span data-stu-id="bb31d-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="bb31d-105">As matrizes são mais úteis ao criar e trabalhar com um número fixo de objetos fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="bb31d-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="bb31d-106">Para obter informações sobre matrizes, consulte [Matrizes](../../../csharp/programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="bb31d-106">For information about arrays, see [Arrays](../../../csharp/programming-guide/arrays/index.md).</span></span>  
  
 <span data-ttu-id="bb31d-107">As coleções fornecem uma maneira mais flexível de trabalhar com grupos de objetos.</span><span class="sxs-lookup"><span data-stu-id="bb31d-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="bb31d-108">Ao contrário das matrizes, o grupo de objetos com o qual você trabalha pode crescer e reduzir dinamicamente conforme as necessidades do aplicativo são alteradas.</span><span class="sxs-lookup"><span data-stu-id="bb31d-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="bb31d-109">Para algumas coleções, você pode atribuir uma chave para qualquer objeto que colocar na coleção para que você possa recuperar rapidamente o objeto, usando a chave.</span><span class="sxs-lookup"><span data-stu-id="bb31d-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="bb31d-110">Uma coleção é uma classe, portanto você deve declarar uma instância da classe antes de adicionar elementos a essa coleção.</span><span class="sxs-lookup"><span data-stu-id="bb31d-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="bb31d-111">Se a coleção contiver elementos de apenas um tipo de dados, você poderá usar uma das classes no namespace <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb31d-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="bb31d-112">Uma coleção genérica impõe segurança de tipos para que nenhum outro tipo de dados possa ser adicionado a ela.</span><span class="sxs-lookup"><span data-stu-id="bb31d-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="bb31d-113">Ao recuperar um elemento de uma coleção genérica, você não precisa determinar seu tipo de dados ou convertê-lo.</span><span class="sxs-lookup"><span data-stu-id="bb31d-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb31d-114">Para os exemplos neste tópico, inclua diretivas [using](../../../csharp/language-reference/keywords/using-directive.md) para os namespaces `System.Collections.Generic` e `System.Linq`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-114">For the examples in this topic, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="bb31d-115">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="bb31d-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="bb31d-116">Usando uma coleção simples</span><span class="sxs-lookup"><span data-stu-id="bb31d-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="bb31d-117">Tipos de coleções</span><span class="sxs-lookup"><span data-stu-id="bb31d-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="bb31d-118">Classes System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="bb31d-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="bb31d-119">Classes System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="bb31d-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="bb31d-120">Classes System.Collections</span><span class="sxs-lookup"><span data-stu-id="bb31d-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
-   [<span data-ttu-id="bb31d-121">Implementando uma coleção de pares chave-valor</span><span class="sxs-lookup"><span data-stu-id="bb31d-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="bb31d-122">Usando LINQ para acessar uma coleção</span><span class="sxs-lookup"><span data-stu-id="bb31d-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="bb31d-123">Classificando uma coleção</span><span class="sxs-lookup"><span data-stu-id="bb31d-123">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="bb31d-124">Definindo uma coleção personalizada</span><span class="sxs-lookup"><span data-stu-id="bb31d-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="bb31d-125">Iteradores</span><span class="sxs-lookup"><span data-stu-id="bb31d-125">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="bb31d-126">Usando uma coleção simples</span><span class="sxs-lookup"><span data-stu-id="bb31d-126">Using a Simple Collection</span></span>  
 <span data-ttu-id="bb31d-127">Os exemplos nesta seção usam a classe genérica <xref:System.Collections.Generic.List%601>, que habilita você a trabalhar com uma lista de objetos fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="bb31d-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="bb31d-128">O exemplo a seguir cria uma lista de cadeias de caracteres e, em seguida, itera nas cadeias de caracteres usando uma instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="bb31d-128">The following example creates a list of strings and then iterates through the strings by using a or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
```csharp  
// Create a list of strings.  
var salmons = new List<string>();  
salmons.Add("chinook");  
salmons.Add("coho");  
salmons.Add("pink");  
salmons.Add("sockeye");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="bb31d-129">Se o conteúdo de uma coleção for conhecido com antecedência, você poderá usar um *inicializador de coleção* para inicializar a coleção.</span><span class="sxs-lookup"><span data-stu-id="bb31d-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="bb31d-130">Para obter mais informações, consulte [Inicializadores de coleção e objeto](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="bb31d-130">For more information, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
 <span data-ttu-id="bb31d-131">O exemplo a seguir é igual ao exemplo anterior, exceto que um inicializador de coleção é usado para adicionar elementos à coleção.</span><span class="sxs-lookup"><span data-stu-id="bb31d-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="bb31d-132">Você pode usar uma instrução [for](../../../csharp/language-reference/keywords/for.md) em vez de uma instrução `foreach` para iterar em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="bb31d-132">You can use a [for](../../../csharp/language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="bb31d-133">Você realiza isso acessando os elementos da coleção pela posição do índice.</span><span class="sxs-lookup"><span data-stu-id="bb31d-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="bb31d-134">O índice dos elementos começa em 0 e termina na contagem de elementos, menos de 1.</span><span class="sxs-lookup"><span data-stu-id="bb31d-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="bb31d-135">O exemplo a seguir itera nos elementos de uma coleção usando `for` em vez de `foreach`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
for (var index = 0; index < salmons.Count; index++)  
{  
    Console.Write(salmons[index] + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="bb31d-136">O exemplo a seguir remove um elemento da coleção, especificando o objeto a ser removido.</span><span class="sxs-lookup"><span data-stu-id="bb31d-136">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Remove an element from the list by specifying  
// the object.  
salmons.Remove("coho");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook pink sockeye  
```  
  
 <span data-ttu-id="bb31d-137">O exemplo a seguir remove elementos de uma lista genérica.</span><span class="sxs-lookup"><span data-stu-id="bb31d-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="bb31d-138">Em vez de uma instrução `foreach`, é usada uma instrução [for](../../../csharp/language-reference/keywords/for.md) que itera em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="bb31d-138">Instead of a `foreach` statement, a [for](../../../csharp/language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="bb31d-139">Isso é feito porque o método <xref:System.Collections.Generic.List%601.RemoveAt%2A> faz com que os elementos após um elemento removido tenham um valor de índice menor.</span><span class="sxs-lookup"><span data-stu-id="bb31d-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
```csharp  
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
// Remove odd numbers.  
for (var index = numbers.Count - 1; index >= 0; index--)  
{  
    if (numbers[index] % 2 == 1)  
    {  
        // Remove the element by specifying  
        // the zero-based index in the list.  
        numbers.RemoveAt(index);  
    }  
}  
  
// Iterate through the list.  
// A lambda expression is placed in the ForEach method  
// of the List(T) object.  
numbers.ForEach(  
    number => Console.Write(number + " "));  
// Output: 0 2 4 6 8  
```  
  
 <span data-ttu-id="bb31d-140">Para o tipo dos elementos na <xref:System.Collections.Generic.List%601>, você também pode definir sua própria classe.</span><span class="sxs-lookup"><span data-stu-id="bb31d-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="bb31d-141">No exemplo a seguir, a classe `Galaxy` que é usada pela <xref:System.Collections.Generic.List%601> é definida no código.</span><span class="sxs-lookup"><span data-stu-id="bb31d-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
```csharp  
private static void IterateThroughList()  
{  
    var theGalaxies = new List<Galaxy>  
        {  
            new Galaxy() { Name="Tadpole", MegaLightYears=400},  
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},  
            new Galaxy() { Name="Milky Way", MegaLightYears=0},  
            new Galaxy() { Name="Andromeda", MegaLightYears=3}  
        };  
  
    foreach (Galaxy theGalaxy in theGalaxies)  
    {  
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);  
    }  
  
    // Output:  
    //  Tadpole  400  
    //  Pinwheel  25  
    //  Milky Way  0  
    //  Andromeda  3  
}  
  
public class Galaxy  
{  
    public string Name { get; set; }  
    public int MegaLightYears { get; set; }  
}  
```  

<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a><span data-ttu-id="bb31d-142">Tipos de coleções</span><span class="sxs-lookup"><span data-stu-id="bb31d-142">Kinds of Collections</span></span> 
 <span data-ttu-id="bb31d-143">Várias coleções comuns são fornecidas pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb31d-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="bb31d-144">Cada tipo de coleção é projetado para uma finalidade específica.</span><span class="sxs-lookup"><span data-stu-id="bb31d-144">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="bb31d-145">Algumas das classes de coleção comuns são descritas nesta seção:</span><span class="sxs-lookup"><span data-stu-id="bb31d-145">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="bb31d-146">Classes <xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="bb31d-146"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="bb31d-147">Classes <xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="bb31d-147"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="bb31d-148">Classes <xref:System.Collections></span><span class="sxs-lookup"><span data-stu-id="bb31d-148"><xref:System.Collections> classes</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="bb31d-149">Classes System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="bb31d-149">System.Collections.Generic Classes</span></span>  
 <span data-ttu-id="bb31d-150">Você pode criar uma coleção genérica usando uma das classes no namespace <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="bb31d-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="bb31d-151">Uma coleção genérica é útil quando cada item na coleção tem o mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="bb31d-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="bb31d-152">Uma coleção genérica impõe tipagem forte, permitindo que apenas o tipo de dados desejado seja adicionado.</span><span class="sxs-lookup"><span data-stu-id="bb31d-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="bb31d-153">A tabela a seguir lista algumas das classes frequentemente usadas do namespace <xref:System.Collections.Generic?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="bb31d-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  

|<span data-ttu-id="bb31d-154">Classe</span><span class="sxs-lookup"><span data-stu-id="bb31d-154">Class</span></span>|<span data-ttu-id="bb31d-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb31d-155">Description</span></span>| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="bb31d-156">Representa uma coleção de pares chave-valor organizados com base na chave.</span><span class="sxs-lookup"><span data-stu-id="bb31d-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="bb31d-157">Representa uma lista de objetos que podem ser acessados por índice.</span><span class="sxs-lookup"><span data-stu-id="bb31d-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="bb31d-158">Fornece métodos para pesquisar, classificar e modificar listas.</span><span class="sxs-lookup"><span data-stu-id="bb31d-158">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="bb31d-159">Representa uma coleção de objetos PEPS (primeiro a entrar, primeiro a sair).</span><span class="sxs-lookup"><span data-stu-id="bb31d-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="bb31d-160">Representa uma coleção de pares chave/valor que são classificados por chave com base na implementação de <xref:System.Collections.Generic.IComparer%601> associada.</span><span class="sxs-lookup"><span data-stu-id="bb31d-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="bb31d-161">Representa uma coleção de objetos UEPS (último a entrar, primeiro a sair).</span><span class="sxs-lookup"><span data-stu-id="bb31d-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="bb31d-162">Para obter informações adicionais, consulte [Tipos de coleção comumente usados](../../../standard/collections/commonly-used-collection-types.md), [Selecionando uma classe de coleção](../../../standard/collections/selecting-a-collection-class.md) e <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="bb31d-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="bb31d-163">Classes System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="bb31d-163">System.Collections.Concurrent Classes</span></span>  
 <span data-ttu-id="bb31d-164">No .NET Framework 4 ou mais recente, as coleções no namespace <xref:System.Collections.Concurrent> fornecem operações thread-safe eficientes para acessar itens da coleção de vários threads.</span><span class="sxs-lookup"><span data-stu-id="bb31d-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="bb31d-165">As classes no namespace <xref:System.Collections.Concurrent> deverão ser usadas em vez dos tipos correspondentes nos namespaces <xref:System.Collections.Generic?displayProperty=nameWithType> e <xref:System.Collections?displayProperty=nameWithType> sempre que vários threads estiverem acessando a coleção simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="bb31d-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="bb31d-166">Para obter mais informações, veja [Coleções thread-safe](../../../standard/collections/thread-safe/index.md) e <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="bb31d-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="bb31d-167">Algumas classes incluídas no namespace <xref:System.Collections.Concurrent> são <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601> e <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="bb31d-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="bb31d-168">Classes System.Collections</span><span class="sxs-lookup"><span data-stu-id="bb31d-168">System.Collections Classes</span></span>  
 <span data-ttu-id="bb31d-169">As classes no namespace <xref:System.Collections?displayProperty=nameWithType> não armazenam elementos como objetos especificamente tipados, mas como objetos do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="bb31d-170">Sempre que possível, você deve usar as coleções genéricas no namespace <xref:System.Collections.Generic?displayProperty=nameWithType> ou no <xref:System.Collections.Concurrent> em vez dos tipos herdados no namespace `System.Collections`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="bb31d-171">A tabela a seguir lista algumas das classes frequentemente usadas no namespace `System.Collections`:</span><span class="sxs-lookup"><span data-stu-id="bb31d-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="bb31d-172">Classe</span><span class="sxs-lookup"><span data-stu-id="bb31d-172">Class</span></span>|<span data-ttu-id="bb31d-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb31d-173">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="bb31d-174">Representa uma matriz de objetos cujo tamanho é aumentado dinamicamente conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="bb31d-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="bb31d-175">Representa uma coleção de pares chave-valor organizados com base no código hash da chave.</span><span class="sxs-lookup"><span data-stu-id="bb31d-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="bb31d-176">Representa uma coleção de objetos PEPS (primeiro a entrar, primeiro a sair).</span><span class="sxs-lookup"><span data-stu-id="bb31d-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="bb31d-177">Representa uma coleção de objetos UEPS (último a entrar, primeiro a sair).</span><span class="sxs-lookup"><span data-stu-id="bb31d-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="bb31d-178">O namespace <xref:System.Collections.Specialized> fornece classes de coleções especializadas e fortemente tipadas, como coleções somente de cadeias de caracteres, bem como de dicionários híbridos e de listas vinculadas.</span><span class="sxs-lookup"><span data-stu-id="bb31d-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="bb31d-179">Implementando uma coleção de pares chave-valor</span><span class="sxs-lookup"><span data-stu-id="bb31d-179">Implementing a Collection of Key/Value Pairs</span></span>  
 <span data-ttu-id="bb31d-180">A coleção genérica <xref:System.Collections.Generic.Dictionary%602> permite que você acesse elementos em uma coleção usando a chave de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="bb31d-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="bb31d-181">Cada adição ao dicionário consiste em um valor e a respectiva chave associada.</span><span class="sxs-lookup"><span data-stu-id="bb31d-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="bb31d-182">A recuperação de um valor usando sua chave é rápida, porque a classe `Dictionary` é implementada como uma tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="bb31d-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="bb31d-183">O exemplo a seguir cria uma coleção `Dictionary` e itera no dicionário usando uma instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>  
  
```csharp  
private static void IterateThruDictionary()  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    foreach (KeyValuePair<string, Element> kvp in elements)  
    {  
        Element theElement = kvp.Value;  
  
        Console.WriteLine("key: " + kvp.Key);  
        Console.WriteLine("values: " + theElement.Symbol + " " +  
            theElement.Name + " " + theElement.AtomicNumber);  
    }  
}  
  
private static Dictionary<string, Element> BuildDictionary()  
{  
    var elements = new Dictionary<string, Element>();  
  
    AddToDictionary(elements, "K", "Potassium", 19);  
    AddToDictionary(elements, "Ca", "Calcium", 20);  
    AddToDictionary(elements, "Sc", "Scandium", 21);  
    AddToDictionary(elements, "Ti", "Titanium", 22);  
  
    return elements;  
}  
  
private static void AddToDictionary(Dictionary<string, Element> elements,  
    string symbol, string name, int atomicNumber)  
{  
    Element theElement = new Element();  
  
    theElement.Symbol = symbol;  
    theElement.Name = name;  
    theElement.AtomicNumber = atomicNumber;  
  
    elements.Add(key: theElement.Symbol, value: theElement);  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  
  
 <span data-ttu-id="bb31d-184">Para, em vez disso, usar um inicializador de coleção para criar a coleção `Dictionary`, você pode substituir os métodos `BuildDictionary` e `AddToDictionary` pelo seguinte método.</span><span class="sxs-lookup"><span data-stu-id="bb31d-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
```csharp  
private static Dictionary<string, Element> BuildDictionary2()  
{  
    return new Dictionary<string, Element>  
    {  
        {"K",  
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        {"Ca",  
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        {"Sc",  
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        {"Ti",  
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
```  
  
 <span data-ttu-id="bb31d-185">O exemplo a seguir usa o método <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> e a propriedade <xref:System.Collections.Generic.Dictionary%602.Item%2A> de `Dictionary` para localizar rapidamente um item por chave.</span><span class="sxs-lookup"><span data-stu-id="bb31d-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="bb31d-186">A propriedade `Item` permite que você acesse um item na coleção `elements` usando o `elements[symbol]` no C#.</span><span class="sxs-lookup"><span data-stu-id="bb31d-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>  
  
```csharp  
private static void FindInDictionary(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    if (elements.ContainsKey(symbol) == false)  
    {  
        Console.WriteLine(symbol + " not found");  
    }  
    else  
    {  
        Element theElement = elements[symbol];  
        Console.WriteLine("found: " + theElement.Name);  
    }  
}  
```  
  
 <span data-ttu-id="bb31d-187">O exemplo a seguir usa o método <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> para localizar rapidamente um item por chave.</span><span class="sxs-lookup"><span data-stu-id="bb31d-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
```csharp  
private static void FindInDictionary2(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    Element theElement = null;  
    if (elements.TryGetValue(symbol, out theElement) == false)  
        Console.WriteLine(symbol + " not found");  
    else  
        Console.WriteLine("found: " + theElement.Name);  
}  
```  

<a name="BKMK_LINQ"></a>
## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="bb31d-188">Usando LINQ para acessar uma coleção</span><span class="sxs-lookup"><span data-stu-id="bb31d-188">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="bb31d-189">A LINQ (consulta integrada à linguagem) pode ser usada para acessar coleções.</span><span class="sxs-lookup"><span data-stu-id="bb31d-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="bb31d-190">As consultas LINQ fornecem recursos de filtragem, classificação e agrupamento.</span><span class="sxs-lookup"><span data-stu-id="bb31d-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="bb31d-191">Para obter mais informações, consulte [Introdução à LINQ em C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="bb31d-191">For more information, see  [Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="bb31d-192">O exemplo a seguir executa uma consulta LINQ em uma `List` genérica.</span><span class="sxs-lookup"><span data-stu-id="bb31d-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="bb31d-193">A consulta LINQ retorna uma coleção diferente que contém os resultados.</span><span class="sxs-lookup"><span data-stu-id="bb31d-193">The LINQ query returns a different collection that contains the results.</span></span>  
  
```csharp  
private static void ShowLINQ()  
{  
    List<Element> elements = BuildList();  
  
    // LINQ Query.  
    var subset = from theElement in elements  
                 where theElement.AtomicNumber < 22  
                 orderby theElement.Name  
                 select theElement;  
  
    foreach (Element theElement in subset)  
    {  
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);  
    }  
  
    // Output:  
    //  Calcium 20  
    //  Potassium 19  
    //  Scandium 21  
}  
  
private static List<Element> BuildList()  
{  
    return new List<Element>  
    {  
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  

<a name="BKMK_Sorting"></a>
## <a name="sorting-a-collection"></a><span data-ttu-id="bb31d-194">Classificando uma coleção</span><span class="sxs-lookup"><span data-stu-id="bb31d-194">Sorting a Collection</span></span>  
 <span data-ttu-id="bb31d-195">O exemplo a seguir ilustra um procedimento para a classificação de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="bb31d-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="bb31d-196">O exemplo classifica instâncias da classe `Car` que estão armazenados em uma <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="bb31d-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="bb31d-197">A classe `Car` implementa a interface <xref:System.IComparable%601>, que requer que o método <xref:System.IComparable%601.CompareTo%2A> seja implementado.</span><span class="sxs-lookup"><span data-stu-id="bb31d-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="bb31d-198">Cada chamada ao método <xref:System.IComparable%601.CompareTo%2A> faz uma comparação única que é usada para classificação.</span><span class="sxs-lookup"><span data-stu-id="bb31d-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="bb31d-199">Os códigos escritos pelo usuário no método `CompareTo` retornam um valor para cada comparação do objeto atual com outro objeto.</span><span class="sxs-lookup"><span data-stu-id="bb31d-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="bb31d-200">O valor retornado será menor que zero se o objeto atual for menor que o outro objeto, maior que zero se o objeto atual for maior que o outro objeto e zero, se eles forem iguais.</span><span class="sxs-lookup"><span data-stu-id="bb31d-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="bb31d-201">Isso permite que você defina no código os critérios para maior que, menor que e igual.</span><span class="sxs-lookup"><span data-stu-id="bb31d-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="bb31d-202">No método `ListCars`, a instrução `cars.Sort()` classifica a lista.</span><span class="sxs-lookup"><span data-stu-id="bb31d-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="bb31d-203">Essa chamada para o método <xref:System.Collections.Generic.List%601.Sort%2A> da <xref:System.Collections.Generic.List%601> faz com que o método `CompareTo` seja chamado automaticamente para os objetos `Car` na `List`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
```csharp  
private static void ListCars()  
{  
    var cars = new List<Car>  
    {  
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},  
        { new Car() { Name = "car2", Color = "red", Speed = 50}},  
        { new Car() { Name = "car3", Color = "green", Speed = 10}},  
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},  
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},  
        { new Car() { Name = "car6", Color = "red", Speed = 60}},  
        { new Car() { Name = "car7", Color = "green", Speed = 50}}  
    };  
  
    // Sort the cars by color alphabetically, and then by speed  
    // in descending order.  
    cars.Sort();  
  
    // View all of the cars.  
    foreach (Car thisCar in cars)  
    {  
        Console.Write(thisCar.Color.PadRight(5) + " ");  
        Console.Write(thisCar.Speed.ToString() + " ");  
        Console.Write(thisCar.Name);  
        Console.WriteLine();  
    }  
  
    // Output:  
    //  blue  50 car4  
    //  blue  30 car5  
    //  blue  20 car1  
    //  green 50 car7  
    //  green 10 car3  
    //  red   60 car6  
    //  red   50 car2  
}  
  
public class Car : IComparable<Car>  
{  
    public string Name { get; set; }  
    public int Speed { get; set; }  
    public string Color { get; set; }  
  
    public int CompareTo(Car other)  
    {  
        // A call to this method makes a single comparison that is  
        // used for sorting.  
  
        // Determine the relative order of the objects being compared.  
        // Sort by color alphabetically, and then by speed in  
        // descending order.  
  
        // Compare the colors.  
        int compare;  
        compare = String.Compare(this.Color, other.Color, true);  
  
        // If the colors are the same, compare the speeds.  
        if (compare == 0)  
        {  
            compare = this.Speed.CompareTo(other.Speed);  
  
            // Use descending order for speed.  
            compare = -compare;  
        }  
  
        return compare;  
    }  
}  
```  
  
<a name="BKMK_CustomCollection"></a>
## <a name="defining-a-custom-collection"></a><span data-ttu-id="bb31d-204">Definindo uma coleção personalizada</span><span class="sxs-lookup"><span data-stu-id="bb31d-204">Defining a Custom Collection</span></span>  
 <span data-ttu-id="bb31d-205">Você pode definir uma coleção implementando a interface <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="bb31d-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>  
  
 <span data-ttu-id="bb31d-206">Embora seja possível definir uma coleção personalizada, é melhor usar as coleções que estão incluídas no .NET Framework, que estão descritas em [Tipos de coleções](#BKMK_KindsOfCollections) anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="bb31d-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="bb31d-207">O exemplo a seguir define uma classe de coleção personalizada chamada `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="bb31d-208">Essa classe implementa a interface <xref:System.Collections.IEnumerable>, que requer que o método <xref:System.Collections.IEnumerable.GetEnumerator%2A> seja implementado.</span><span class="sxs-lookup"><span data-stu-id="bb31d-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="bb31d-209">O método `GetEnumerator` retorna uma instância da classe `ColorEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="bb31d-210">`ColorEnumerator` implementa a interface <xref:System.Collections.IEnumerator>, que requer que a propriedade <xref:System.Collections.IEnumerator.Current%2A>, o método <xref:System.Collections.IEnumerator.MoveNext%2A> e o método <xref:System.Collections.IEnumerator.Reset%2A> sejam implementados.</span><span class="sxs-lookup"><span data-stu-id="bb31d-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
```csharp  
private static void ListColors()  
{  
    var colors = new AllColors();  
  
    foreach (Color theColor in colors)  
    {  
        Console.Write(theColor.Name + " ");  
    }  
    Console.WriteLine();  
    // Output: red blue green  
}  
  
// Collection class.  
public class AllColors : System.Collections.IEnumerable  
{  
    Color[] _colors =  
    {  
        new Color() { Name = "red" },  
        new Color() { Name = "blue" },  
        new Color() { Name = "green" }  
    };  
  
    public System.Collections.IEnumerator GetEnumerator()  
    {  
        return new ColorEnumerator(_colors);  
  
        // Instead of creating a custom enumerator, you could  
        // use the GetEnumerator of the array.  
        //return _colors.GetEnumerator();  
    }  
  
    // Custom enumerator.  
    private class ColorEnumerator : System.Collections.IEnumerator  
    {  
        private Color[] _colors;  
        private int _position = -1;  
  
        public ColorEnumerator(Color[] colors)  
        {  
            _colors = colors;  
        }  
  
        object System.Collections.IEnumerator.Current  
        {  
            get  
            {  
                return _colors[_position];  
            }  
        }  
  
        bool System.Collections.IEnumerator.MoveNext()  
        {  
            _position++;  
            return (_position < _colors.Length);  
        }  
  
        void System.Collections.IEnumerator.Reset()  
        {  
            _position = -1;  
        }  
    }  
}  
  
// Element class.  
public class Color  
{  
    public string Name { get; set; }  
}  
```  

<a name="BKMK_Iterators"></a> 
##  <a name="iterators"></a><span data-ttu-id="bb31d-211">Iterators</span><span class="sxs-lookup"><span data-stu-id="bb31d-211">Iterators</span></span>  
 <span data-ttu-id="bb31d-212">Um *iterador* é usado para realizar uma iteração personalizada em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="bb31d-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="bb31d-213">Um iterador pode ser um método ou um acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="bb31d-214">Um iterador usa uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) para retornar um elemento da coleção por vez.</span><span class="sxs-lookup"><span data-stu-id="bb31d-214">An iterator uses a [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="bb31d-215">Você chama um iterador usando uma instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="bb31d-215">You call an iterator by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="bb31d-216">Cada iteração do loop `foreach` chama o iterador.</span><span class="sxs-lookup"><span data-stu-id="bb31d-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="bb31d-217">Quando uma instrução `yield return` é alcançada no iterador, uma expressão é retornada e o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="bb31d-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="bb31d-218">A execução será reiniciada desse local na próxima vez que o iterador for chamado.</span><span class="sxs-lookup"><span data-stu-id="bb31d-218">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="bb31d-219">Para obter mais informações, consulte [Iteradores (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="bb31d-219">For more information, see [Iterators (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="bb31d-220">O exemplo a seguir usa um método iterador.</span><span class="sxs-lookup"><span data-stu-id="bb31d-220">The following example uses an iterator method.</span></span> <span data-ttu-id="bb31d-221">O método iterador tem uma instrução `yield return` que está dentro de um loop [for](../../../csharp/language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="bb31d-221">The iterator method has a `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="bb31d-222">No método `ListEvenNumbers`, cada iteração do corpo da instrução `foreach` cria uma chamada ao método iterador, que avança para a próxima instrução `yield return`.</span><span class="sxs-lookup"><span data-stu-id="bb31d-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>  
  
```csharp  
private static void ListEvenNumbers()  
{  
    foreach (int number in EvenSequence(5, 18))  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    Console.WriteLine();  
    // Output: 6 8 10 12 14 16 18  
}  
  
private static IEnumerable<int> EvenSequence(  
    int firstNumber, int lastNumber)  
{  
    // Yield even numbers in the range.  
    for (var number = firstNumber; number <= lastNumber; number++)  
    {  
        if (number % 2 == 0)  
        {  
            yield return number;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb31d-223">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb31d-223">See Also</span></span>  
 [<span data-ttu-id="bb31d-224">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="bb31d-224">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="bb31d-225">Conceitos de programação (C#)</span><span class="sxs-lookup"><span data-stu-id="bb31d-225">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)  
 [<span data-ttu-id="bb31d-226">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="bb31d-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="bb31d-227">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="bb31d-227">LINQ to Objects (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="bb31d-228">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="bb31d-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="bb31d-229">Coleções e Estruturas de Dados</span><span class="sxs-lookup"><span data-stu-id="bb31d-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="bb31d-230">Criando e manipulando coleções</span><span class="sxs-lookup"><span data-stu-id="bb31d-230">Creating and Manipulating Collections</span></span>](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [<span data-ttu-id="bb31d-231">Selecionando uma Classe de Coleção</span><span class="sxs-lookup"><span data-stu-id="bb31d-231">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
 [<span data-ttu-id="bb31d-232">Comparações e Classificações Dentro de Coleções</span><span class="sxs-lookup"><span data-stu-id="bb31d-232">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [<span data-ttu-id="bb31d-233">Quando Usar Coleções Genéricas</span><span class="sxs-lookup"><span data-stu-id="bb31d-233">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)  
