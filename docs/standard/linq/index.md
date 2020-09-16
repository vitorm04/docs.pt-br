---
title: Visão geral do LINQ – .NET
description: O LINQ (consulta integrada à linguagem) fornece recursos de consulta de nível de linguagem e uma API de função de ordem superior para C# e Visual Basic, que permite escrever código expressivo de expressiva.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.openlocfilehash: 65370a2bd21e2474af4cb070bb8d82a167f10070
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554990"
---
# <a name="linq-overview"></a><span data-ttu-id="5db36-103">Visão geral da consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="5db36-103">LINQ overview</span></span>

<span data-ttu-id="5db36-104">O LINQ (consulta integrada à linguagem) fornece recursos de consulta de nível de linguagem e uma API de [função de ordem superior](https://en.wikipedia.org/wiki/Higher-order_function) para C# e Visual Basic, que permite escrever código expressivo de expressiva.</span><span class="sxs-lookup"><span data-stu-id="5db36-104">Language-Integrated Query (LINQ) provides language-level querying capabilities, and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic, that enable you to write expressive declarative code.</span></span>

## <a name="language-level-query-syntax"></a><span data-ttu-id="5db36-105">Sintaxe de consulta de nível de linguagem</span><span class="sxs-lookup"><span data-stu-id="5db36-105">Language-level query syntax</span></span>

<span data-ttu-id="5db36-106">Esta é a sintaxe de consulta no nível de linguagem:</span><span class="sxs-lookup"><span data-stu-id="5db36-106">This is the language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

```vb
Dim linqExperts = From p in programmers
                  Where p.IsNewToLINQ
                  Select New LINQExpert(p)
```

<span data-ttu-id="5db36-107">Este é o mesmo exemplo usando a `IEnumerable<T>` API:</span><span class="sxs-lookup"><span data-stu-id="5db36-107">This is the same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="5db36-108">O LINQ é expressivo</span><span class="sxs-lookup"><span data-stu-id="5db36-108">LINQ is expressive</span></span>

<span data-ttu-id="5db36-109">Imagine que você tem uma lista de animais de estimação, mas deseja convertê-la em um dicionário em que você pode acessar um animal de estimação diretamente por seu valor `RFID`.</span><span class="sxs-lookup"><span data-stu-id="5db36-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="5db36-110">Este é o código imperativo tradicional:</span><span class="sxs-lookup"><span data-stu-id="5db36-110">This is traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

```vb
Dim petLookup = New Dictionary(Of Integer, Pet)()

For Each pet in pets
    petLookup.Add(pet.RFID, pet)
Next
```

<span data-ttu-id="5db36-111">A intenção por trás do código não é criar um novo `Dictionary<int, Pet>` e adicionar a ele por meio de um loop, é converter uma lista existente em um dicionário!</span><span class="sxs-lookup"><span data-stu-id="5db36-111">The intention behind the code isn't to create a new `Dictionary<int, Pet>` and add to it via a loop, it's to convert an existing list into a dictionary!</span></span> <span data-ttu-id="5db36-112">O LINQ preserva a intenção, enquanto que o código imperativo não.</span><span class="sxs-lookup"><span data-stu-id="5db36-112">LINQ preserves the intention whereas the imperative code doesn't.</span></span>

<span data-ttu-id="5db36-113">Esta é a expressão LINQ equivalente:</span><span class="sxs-lookup"><span data-stu-id="5db36-113">This is the equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="5db36-114">O código usando a LINQ é importante porque ele nivela a área de atuação entre a intenção e o código ao raciocinar como um programador.</span><span class="sxs-lookup"><span data-stu-id="5db36-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="5db36-115">Outro bônus é a brevidade do código.</span><span class="sxs-lookup"><span data-stu-id="5db36-115">Another bonus is code brevity.</span></span> <span data-ttu-id="5db36-116">Imagine reduzir grandes partes de uma base de código em 1/3 como feito acima.</span><span class="sxs-lookup"><span data-stu-id="5db36-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="5db36-117">Ótima coisa, certo?</span><span class="sxs-lookup"><span data-stu-id="5db36-117">Sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="5db36-118">Provedores de LINQ simplificam o acesso a dados</span><span class="sxs-lookup"><span data-stu-id="5db36-118">LINQ providers simplify data access</span></span>

<span data-ttu-id="5db36-119">Para uma parte significativa do software fora do lugar, tudo se destaca em lidar com os dados de alguma fonte (bancos de dado, JSON, XML e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="5db36-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, and so on).</span></span> <span data-ttu-id="5db36-120">Geralmente isso envolve aprender uma nova API para cada fonte de dados, o que pode ser inconveniente.</span><span class="sxs-lookup"><span data-stu-id="5db36-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="5db36-121">O LINQ simplifica isso, abstraindo elementos comuns de acesso a dados em uma sintaxe de consulta que tem a mesma aparência, independentemente da fonte de dados escolhida.</span><span class="sxs-lookup"><span data-stu-id="5db36-121">LINQ simplifies this by abstracting common elements of data access into a query syntax that looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="5db36-122">Isso localiza todos os elementos XML com um valor de atributo específico:</span><span class="sxs-lookup"><span data-stu-id="5db36-122">This finds all XML elements with a specific attribute value:</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

```vb
Public Shared Function FindAllElementsWithAttribute(documentRoot As XElement, elementName As String,
                                           attributeName As String, value As String) As IEnumerable(Of XElement)
    Return From el In documentRoot.Elements(elementName)
           Where el.Element(attributeName).ToString() = value
           Select el
End Function
```

<span data-ttu-id="5db36-123">Escrever código para atravessar manualmente o documento XML para realizar essa tarefa seria muito mais desafiador.</span><span class="sxs-lookup"><span data-stu-id="5db36-123">Writing code to manually traverse the XML document to do this task would be far more challenging.</span></span>

<span data-ttu-id="5db36-124">Interagir com XML não é a única coisa que você pode fazer com provedores LINQ.</span><span class="sxs-lookup"><span data-stu-id="5db36-124">Interacting with XML isn't the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="5db36-125">O [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) é um ORM (Mapeador de Objeto Relacional) de funções bastante básicas para um banco de dados MSSQL.</span><span class="sxs-lookup"><span data-stu-id="5db36-125">[Linq to SQL](../../framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="5db36-126">A biblioteca [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) fornece uma passagem do documento JSON eficiente por meio da LINQ.</span><span class="sxs-lookup"><span data-stu-id="5db36-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="5db36-127">Além disso, se não houver uma biblioteca que faça o que você precisa, você também poderá [escrever seu próprio provedor de LINQ](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span><span class="sxs-lookup"><span data-stu-id="5db36-127">Furthermore, if there isn't a library that does what you need, you can also [write your own LINQ Provider](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="reasons-to-use-the-query-syntax"></a><span data-ttu-id="5db36-128">Motivos para usar a sintaxe de consulta</span><span class="sxs-lookup"><span data-stu-id="5db36-128">Reasons to use the query syntax</span></span>

<span data-ttu-id="5db36-129">Por que usar a sintaxe de consulta?</span><span class="sxs-lookup"><span data-stu-id="5db36-129">Why use query syntax?</span></span> <span data-ttu-id="5db36-130">Essa é uma pergunta que muitas vezes surge.</span><span class="sxs-lookup"><span data-stu-id="5db36-130">This is a question that often comes up.</span></span> <span data-ttu-id="5db36-131">Afinal, o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="5db36-131">After all, the following code:</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="5db36-132">é muito mais conciso que isso:</span><span class="sxs-lookup"><span data-stu-id="5db36-132">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

```vb
Dim filteredItems = From item In myItems
                    Where item.Foo
                    Select item
```

<span data-ttu-id="5db36-133">Não é a sintaxe da API apenas uma maneira mais concisa de fazer a sintaxe de consulta?</span><span class="sxs-lookup"><span data-stu-id="5db36-133">Isn't the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="5db36-134">Não.</span><span class="sxs-lookup"><span data-stu-id="5db36-134">No.</span></span> <span data-ttu-id="5db36-135">A sintaxe de consulta permite o uso da cláusula **let**, que permite que você introduza e associe uma variável no escopo da expressão, usando-a em partes subsequentes da expressão.</span><span class="sxs-lookup"><span data-stu-id="5db36-135">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="5db36-136">A reprodução do mesmo código apenas com a sintaxe da API pode ser feita, mas provavelmente levará a um código difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="5db36-136">Reproducing the same code with only the API syntax can be done, but will most likely lead to code that's hard to read.</span></span>

<span data-ttu-id="5db36-137">Portanto, isso levanta a questão, **você deve usar apenas a sintaxe de consulta?**</span><span class="sxs-lookup"><span data-stu-id="5db36-137">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="5db36-138">A resposta para essa pergunta será **Sim** se:</span><span class="sxs-lookup"><span data-stu-id="5db36-138">The answer to this question is **yes** if:</span></span>

- <span data-ttu-id="5db36-139">A codebase existente já usa a sintaxe de consulta.</span><span class="sxs-lookup"><span data-stu-id="5db36-139">Your existing codebase already uses the query syntax.</span></span>
- <span data-ttu-id="5db36-140">Você precisa de escopo de variáveis em suas consultas devido à complexidade.</span><span class="sxs-lookup"><span data-stu-id="5db36-140">You need to scope variables within your queries because of complexity.</span></span>
- <span data-ttu-id="5db36-141">Você prefere a sintaxe de consulta e não vai distrair da base de código.</span><span class="sxs-lookup"><span data-stu-id="5db36-141">You prefer the query syntax and it won't distract from your codebase.</span></span>

<span data-ttu-id="5db36-142">A resposta para essa pergunta será **não** se...</span><span class="sxs-lookup"><span data-stu-id="5db36-142">The answer to this question is **no** if...</span></span>

- <span data-ttu-id="5db36-143">Sua base de código já usar a sintaxe de API</span><span class="sxs-lookup"><span data-stu-id="5db36-143">Your existing codebase already uses the API syntax</span></span>
- <span data-ttu-id="5db36-144">Você não precisar definir o escopo de variáveis em suas consultas</span><span class="sxs-lookup"><span data-stu-id="5db36-144">You have no need to scope variables within your queries</span></span>
- <span data-ttu-id="5db36-145">Você prefere a sintaxe da API e não vai distrair da base de código</span><span class="sxs-lookup"><span data-stu-id="5db36-145">You prefer the API syntax and it won't distract from your codebase</span></span>

## <a name="essential-linq"></a><span data-ttu-id="5db36-146">LINQ essencial</span><span class="sxs-lookup"><span data-stu-id="5db36-146">Essential LINQ</span></span>

<span data-ttu-id="5db36-147">Para obter uma lista realmente abrangente de amostras de LINQ, visite [101 LINQ Samples ](/samples/dotnet/try-samples/101-linq-samples/) (101 exemplos da LINQ).</span><span class="sxs-lookup"><span data-stu-id="5db36-147">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](/samples/dotnet/try-samples/101-linq-samples/).</span></span>

<span data-ttu-id="5db36-148">Os exemplos a seguir são uma demonstração rápida de algumas das partes essenciais do LINQ.</span><span class="sxs-lookup"><span data-stu-id="5db36-148">The following examples are a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="5db36-149">Isso não é tão abrangente, pois o LINQ fornece mais funcionalidade do que o que é demonstrado aqui.</span><span class="sxs-lookup"><span data-stu-id="5db36-149">This is in no way comprehensive, as LINQ provides more functionality than what is showcased here.</span></span>

### <a name="the-bread-and-butter---where-select-and-aggregate"></a><span data-ttu-id="5db36-150">O pão e pelos- `Where` , `Select` e `Aggregate`</span><span class="sxs-lookup"><span data-stu-id="5db36-150">The bread and butter - `Where`, `Select`, and `Aggregate`</span></span>

```csharp
// Filtering a list.
var germanShepherds = dogs.Where(dog => dog.Breed == DogBreed.GermanShepherd);

// Using the query syntax.
var queryGermanShepherds = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepherd
                          select dog;

// Mapping a list from type A to type B.
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax.
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings.
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

```vb
' Filtering a list.
Dim germanShepherds = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepherd)

' Using the query syntax.
Dim queryGermanShepherds = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepherd
                          Select dog

' Mapping a list from type A to type B.
Dim cats = dogs.Select(Function(dog) dog.TurnIntoACat())

' Using the query syntax.
Dim queryCats = From dog In dogs
                Select dog.TurnIntoACat()

' Summing the lengths of a set of strings.
Dim seed As Integer = 0
Dim sumOfStrings As Integer = strings.Aggregate(seed, Function(s1, s2) s1.Length + s2.Length)
```

### <a name="flattening-a-list-of-lists"></a><span data-ttu-id="5db36-151">Nivelar uma lista de listas</span><span class="sxs-lookup"><span data-stu-id="5db36-151">Flattening a list of lists</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

### <a name="union-between-two-sets-with-custom-comparator"></a><span data-ttu-id="5db36-152">União entre dois conjuntos (com comparador personalizado)</span><span class="sxs-lookup"><span data-stu-id="5db36-152">Union between two sets (with custom comparator)</span></span>

```csharp
public class DogHairLengthComparer : IEqualityComparer<Dog>
{
    public bool Equals(Dog a, Dog b)
    {
        if (a == null && b == null)
        {
            return true;
        }
        else if ((a == null && b != null) ||
                 (a != null && b == null))
        {
            return false;
        }
        else
        {
            return a.HairLengthType == b.HairLengthType;
        }
    }

    public int GetHashCode(Dog d)
    {
        // Default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}
...

// Gets all the short-haired dogs between two different kennels.
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());

```

```vb
Public Class DogHairLengthComparer
  Inherits IEqualityComparer(Of Dog)

  Public Function Equals(a As Dog,b As Dog) As Boolean
      If a Is Nothing AndAlso b Is Nothing Then
          Return True
      ElseIf (a Is Nothing AndAlso b IsNot Nothing) OrElse (a IsNot Nothing AndAlso b Is Nothing) Then
          Return False
      Else
          Return a.HairLengthType = b.HairLengthType
      End If
  End Function

  Public Function GetHashCode(d As Dog) As Integer
      ' Default hashcode is enough here, as these are simple objects.
      Return d.GetHashCode()
  End Function
End Class

...

' Gets all the short-haired dogs between two different kennels.
Dim allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, New DogHairLengthComparer())
```

### <a name="intersection-between-two-sets"></a><span data-ttu-id="5db36-153">Interseção entre dois conjuntos</span><span class="sxs-lookup"><span data-stu-id="5db36-153">Intersection between two sets</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

```vb
' Gets the volunteers who spend share time with two humane societies.
Dim volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     New VolunteerTimeComparer())
```

### <a name="ordering"></a><span data-ttu-id="5db36-154">Ordenando</span><span class="sxs-lookup"><span data-stu-id="5db36-154">Ordering</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

```vb
' Get driving directions, ordering by if it's toll-free before estimated driving time.
Dim results = DirectionsProcessor.GetDirections(start, end).
                OrderBy(Function(direction) direction.HasNoTolls).
                ThenBy(Function(direction) direction.EstimatedTime)
```

### <a name="equality-of-instance-properties"></a><span data-ttu-id="5db36-155">Igualdade de propriedades de instância</span><span class="sxs-lookup"><span data-stu-id="5db36-155">Equality of instance properties</span></span>

<span data-ttu-id="5db36-156">Por fim, um exemplo mais avançado: determinar se os valores das propriedades de duas instâncias do mesmo tipo são iguais (emprestados e modificados [dessa postagem do StackOverflow](https://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="5db36-156">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self == null || to == null)
    {
        return self == to;
    }

    // Selects the properties which have unequal values into a sequence of those properties.
    var unequalProperties = from property in typeof(T).GetProperties(BindingFlags.Public | BindingFlags.Instance)
                            where !ignore.Contains(property.Name)
                            let selfValue = property.GetValue(self, null)
                            let toValue = property.GetValue(to, null)
                            where !Equals(selfValue, toValue)
                            select property;
    return !unequalProperties.Any();
}
```

```vb
<System.Runtime.CompilerServices.Extension()>
Public Function PublicInstancePropertiesEqual(Of T As Class)(self As T, [to] As T, ParamArray ignore As String()) As Boolean
    If self Is Nothing OrElse [to] Is Nothing Then
        Return self Is [to]
    End If

    ' Selects the properties which have unequal values into a sequence of those properties.
    Dim unequalProperties = From [property] In GetType(T).GetProperties(BindingFlags.Public Or BindingFlags.Instance)
                            Where Not ignore.Contains([property].Name)
                            Let selfValue = [property].GetValue(self, Nothing)
                            Let toValue = [property].GetValue([to], Nothing)
                            Where Not Equals(selfValue, toValue) Select [property]
    Return Not unequalProperties.Any()
End Function
```

## <a name="plinq"></a><span data-ttu-id="5db36-157">PLINQ</span><span class="sxs-lookup"><span data-stu-id="5db36-157">PLINQ</span></span>

<span data-ttu-id="5db36-158">PLINQ, ou LINQ Paralela, é um mecanismo de execução paralelo para expressões de LINQ.</span><span class="sxs-lookup"><span data-stu-id="5db36-158">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="5db36-159">Em outras palavras, expressões regulares de LINQ podem ser paralelizadas trivialmente em qualquer número de threads.</span><span class="sxs-lookup"><span data-stu-id="5db36-159">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="5db36-160">Isso é feito por meio de uma chamada para `AsParallel()` precedendo a expressão.</span><span class="sxs-lookup"><span data-stu-id="5db36-160">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="5db36-161">Considere o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5db36-161">Consider the following:</span></span>

```csharp
public static string GetAllFacebookUserLikesMessage(IEnumerable<FacebookUser> facebookUsers)
{
    var seed = default(UInt64);

    Func<UInt64, UInt64, UInt64> threadAccumulator = (t1, t2) => t1 + t2;
    Func<UInt64, UInt64, UInt64> threadResultAccumulator = (t1, t2) => t1 + t2;
    Func<Uint64, string> resultSelector = total => $"Facebook has {total} likes!";

    return facebookUsers.AsParallel()
                        .Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector);
}
```

```vb
Public Shared GetAllFacebookUserLikesMessage(facebookUsers As IEnumerable(Of FacebookUser)) As String
{
    Dim seed As UInt64 = 0

    Dim threadAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim threadResultAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim resultSelector As Func(Of Uint64, string) = Function(total) $"Facebook has {total} likes!"

    Return facebookUsers.AsParallel().
                        Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector)
}
```

<span data-ttu-id="5db36-162">Esse código particionará `facebookUsers` entre threads do sistema conforme necessário, somará o total de semelhantes em cada thread em paralelo, somará os resultados calculados por cada thread e projetará esse resultado em uma bela cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5db36-162">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="5db36-163">Na forma de diagrama:</span><span class="sxs-lookup"><span data-stu-id="5db36-163">In diagram form:</span></span>

![Diagrama da PLINQ](media/index/plinq-diagram.png)

<span data-ttu-id="5db36-165">Paralelizáveis trabalhos associados à CPU que podem ser facilmente expressos via LINQ (em outras palavras, são funções puras e não têm efeitos colaterais) são um excelente candidato para PLINQ.</span><span class="sxs-lookup"><span data-stu-id="5db36-165">Parallelizable CPU-bound jobs that can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="5db36-166">Para trabalhos que _têm um_ efeito colateral, considere o uso da [biblioteca de tarefas paralelas](../parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="5db36-166">For jobs that _do_ have a side effect, consider using the [Task Parallel Library](../parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="more-resources"></a><span data-ttu-id="5db36-167">Mais recursos</span><span class="sxs-lookup"><span data-stu-id="5db36-167">More resources</span></span>

* [<span data-ttu-id="5db36-168">101 exemplos do LINQ</span><span class="sxs-lookup"><span data-stu-id="5db36-168">101 LINQ Samples</span></span>](/samples/dotnet/try-samples/101-linq-samples/)
* <span data-ttu-id="5db36-169">[LINQPad](https://www.linqpad.net/), um ambiente playground e mecanismo de consulta de banco de dados para C#/F #/Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5db36-169">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="5db36-170">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), um livro eletrônico para aprender como o LINQ to Objects é implementado</span><span class="sxs-lookup"><span data-stu-id="5db36-170">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
