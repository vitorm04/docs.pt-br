---
title: LINQ (Consulta Integrada à Linguagem)
description: Saiba como a LINQ fornece funcionalidades de consulta no nível da linguagem e uma API para C# e VB como uma maneira de escrever um código expressivo e declarativo.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 2e4b23b7bf197c9984c53b2f4cc2acaa61731d38
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238625"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="8d917-103">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="8d917-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="8d917-104">O que é?</span><span class="sxs-lookup"><span data-stu-id="8d917-104">What is it?</span></span>

<span data-ttu-id="8d917-105">A LINQ fornece funcionalidades de consulta no nível da linguagem e uma API de [função de ordem superior](https://en.wikipedia.org/wiki/Higher-order_function) para C# e VB como uma maneira de escrever um código expressivo e declarativo.</span><span class="sxs-lookup"><span data-stu-id="8d917-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="8d917-106">Sintaxe de consulta de nível de linguagem:</span><span class="sxs-lookup"><span data-stu-id="8d917-106">Language-level query syntax:</span></span>

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

<span data-ttu-id="8d917-107">Mesmo exemplo usando a API `IEnumerable<T>`:</span><span class="sxs-lookup"><span data-stu-id="8d917-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="8d917-108">A LINQ é expressiva</span><span class="sxs-lookup"><span data-stu-id="8d917-108">LINQ is Expressive</span></span>

<span data-ttu-id="8d917-109">Imagine que você tem uma lista de animais de estimação, mas deseja convertê-la em um dicionário em que você pode acessar um animal de estimação diretamente por seu valor `RFID`.</span><span class="sxs-lookup"><span data-stu-id="8d917-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="8d917-110">Código imperativo tradicional:</span><span class="sxs-lookup"><span data-stu-id="8d917-110">Traditional imperative code:</span></span>

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

<span data-ttu-id="8d917-111">A intenção por trás do código não é criar um novo `Dictionary<int, Pet>` e adicionar a ele por meio de um loop, é converter uma lista existente em um dicionário.</span><span class="sxs-lookup"><span data-stu-id="8d917-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="8d917-112">A LINQ preserva a intenção enquanto o código imperativo não.</span><span class="sxs-lookup"><span data-stu-id="8d917-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="8d917-113">Expressão LINQ equivalente:</span><span class="sxs-lookup"><span data-stu-id="8d917-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="8d917-114">O código usando a LINQ é importante porque ele nivela a área de atuação entre a intenção e o código ao raciocinar como um programador.</span><span class="sxs-lookup"><span data-stu-id="8d917-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="8d917-115">Outro bônus é a brevidade do código.</span><span class="sxs-lookup"><span data-stu-id="8d917-115">Another bonus is code brevity.</span></span> <span data-ttu-id="8d917-116">Imagine reduzir grandes partes de uma base de código em 1/3 como feito acima.</span><span class="sxs-lookup"><span data-stu-id="8d917-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="8d917-117">Excelente, certo?</span><span class="sxs-lookup"><span data-stu-id="8d917-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="8d917-118">Provedores LINQ simplificam o acesso a dados</span><span class="sxs-lookup"><span data-stu-id="8d917-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="8d917-119">Para uma parte significativa do software em uso, tudo gira em torno de lidar com os dados de alguma origem (bancos de dados, JSON, XML etc.).</span><span class="sxs-lookup"><span data-stu-id="8d917-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="8d917-120">Geralmente isso envolve aprender uma nova API para cada fonte de dados, o que pode ser inconveniente.</span><span class="sxs-lookup"><span data-stu-id="8d917-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="8d917-121">A LINQ simplifica isso abstraindo os elementos comuns de acesso a dados em uma sintaxe de consulta que tem a mesma aparência, independentemente da fonte de dados escolhida.</span><span class="sxs-lookup"><span data-stu-id="8d917-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="8d917-122">Considere o seguinte: localizar todos os elementos XML com um valor de atributo específico.</span><span class="sxs-lookup"><span data-stu-id="8d917-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

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

<span data-ttu-id="8d917-123">Escrever o código para percorrer manualmente o documento XML para realizar essa tarefa seria muito mais desafiador.</span><span class="sxs-lookup"><span data-stu-id="8d917-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="8d917-124">Interagir com o XML não é a única coisa que você pode fazer com provedores LINQ.</span><span class="sxs-lookup"><span data-stu-id="8d917-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="8d917-125">O [LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) é um ORM (Mapeador de Objeto Relacional) de funções bastante básicas para um banco de dados MSSQL.</span><span class="sxs-lookup"><span data-stu-id="8d917-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="8d917-126">A biblioteca [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) fornece uma passagem do documento JSON eficiente por meio da LINQ.</span><span class="sxs-lookup"><span data-stu-id="8d917-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="8d917-127">Além disso, se não existir uma biblioteca que faça o que você precisa, também é possível [escrever seu próprio provedor LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="8d917-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="8d917-128">Por que usar a sintaxe de consulta?</span><span class="sxs-lookup"><span data-stu-id="8d917-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="8d917-129">Essa é uma pergunta que surge bastante.</span><span class="sxs-lookup"><span data-stu-id="8d917-129">This is a question which often comes up.</span></span> <span data-ttu-id="8d917-130">Afinal, isso</span><span class="sxs-lookup"><span data-stu-id="8d917-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="8d917-131">é muito mais conciso que isso:</span><span class="sxs-lookup"><span data-stu-id="8d917-131">is a lot more concise than this:</span></span>

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

<span data-ttu-id="8d917-132">A sintaxe da API não é apenas uma maneira mais concisa de fazer a sintaxe de consulta?</span><span class="sxs-lookup"><span data-stu-id="8d917-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="8d917-133">Nº</span><span class="sxs-lookup"><span data-stu-id="8d917-133">No.</span></span> <span data-ttu-id="8d917-134">A sintaxe de consulta permite o uso da cláusula **let**, que permite que você introduza e associe uma variável no escopo da expressão, usando-a em partes subsequentes da expressão.</span><span class="sxs-lookup"><span data-stu-id="8d917-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="8d917-135">É possível reproduzir o mesmo código com apenas a sintaxe da API, mas mais provavelmente levará a um código que é difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="8d917-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="8d917-136">Portanto, isso levanta a questão, **você deve usar apenas a sintaxe de consulta?**</span><span class="sxs-lookup"><span data-stu-id="8d917-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="8d917-137">A resposta para essa pergunta será **sim** se...</span><span class="sxs-lookup"><span data-stu-id="8d917-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="8d917-138">Sua base de código já usar a sintaxe de consulta</span><span class="sxs-lookup"><span data-stu-id="8d917-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="8d917-139">Você precisar definir o escopo de variáveis em suas consultas devido à complexidade</span><span class="sxs-lookup"><span data-stu-id="8d917-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="8d917-140">Você preferir a sintaxe de consulta e ela não for distraí-lo da base de código</span><span class="sxs-lookup"><span data-stu-id="8d917-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="8d917-141">A resposta para essa pergunta será **não** se...</span><span class="sxs-lookup"><span data-stu-id="8d917-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="8d917-142">Sua base de código já usar a sintaxe de API</span><span class="sxs-lookup"><span data-stu-id="8d917-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="8d917-143">Você não precisar definir o escopo de variáveis em suas consultas</span><span class="sxs-lookup"><span data-stu-id="8d917-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="8d917-144">Você preferir a sintaxe de API e ela não for distraí-lo da base de código</span><span class="sxs-lookup"><span data-stu-id="8d917-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="8d917-145">Exemplos essenciais</span><span class="sxs-lookup"><span data-stu-id="8d917-145">Essential Samples</span></span>

<span data-ttu-id="8d917-146">Para obter uma lista realmente abrangente de amostras de LINQ, visite [101 LINQ Samples ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b) (101 exemplos da LINQ).</span><span class="sxs-lookup"><span data-stu-id="8d917-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="8d917-147">A seguir está uma rápida demonstração de algumas das partes essenciais da LINQ.</span><span class="sxs-lookup"><span data-stu-id="8d917-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="8d917-148">De nenhuma forma isso é abrangente, uma vez que a LINQ fornece significativamente mais funcionalidades do que o que é apresentado aqui.</span><span class="sxs-lookup"><span data-stu-id="8d917-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="8d917-149">O básico: `Where`, `Select` e `Aggregate`:</span><span class="sxs-lookup"><span data-stu-id="8d917-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list.
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax.
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
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
Dim germanShepards = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepard)

' Using the query syntax.
Dim queryGermanShepards = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepard
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

* <span data-ttu-id="8d917-150">Nivelar uma lista de listas:</span><span class="sxs-lookup"><span data-stu-id="8d917-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* <span data-ttu-id="8d917-151">União entre dois conjuntos (com o comparador personalizado):</span><span class="sxs-lookup"><span data-stu-id="8d917-151">Union between two sets (with custom comparator):</span></span>

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

* <span data-ttu-id="8d917-152">Interseção entre dois conjuntos:</span><span class="sxs-lookup"><span data-stu-id="8d917-152">Intersection between two sets:</span></span>

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

* <span data-ttu-id="8d917-153">Ordenar:</span><span class="sxs-lookup"><span data-stu-id="8d917-153">Ordering:</span></span>

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

* <span data-ttu-id="8d917-154">Por fim, um exemplo mais avançado: determinar se os valores das propriedades de duas instâncias do mesmo tipo são iguais (emprestados e modificados [dessa postagem do StackOverflow](https://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="8d917-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

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

## <a name="plinq"></a><span data-ttu-id="8d917-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="8d917-155">PLINQ</span></span>

<span data-ttu-id="8d917-156">PLINQ, ou LINQ Paralela, é um mecanismo de execução paralelo para expressões de LINQ.</span><span class="sxs-lookup"><span data-stu-id="8d917-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="8d917-157">Em outras palavras, expressões regulares de LINQ podem ser paralelizadas trivialmente em qualquer número de threads.</span><span class="sxs-lookup"><span data-stu-id="8d917-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="8d917-158">Isso é feito por meio de uma chamada para `AsParallel()` precedendo a expressão.</span><span class="sxs-lookup"><span data-stu-id="8d917-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="8d917-159">Considere o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8d917-159">Consider the following:</span></span>

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

<span data-ttu-id="8d917-160">Esse código particionará `facebookUsers` entre threads do sistema conforme necessário, somará o total de semelhantes em cada thread em paralelo, somará os resultados calculados por cada thread e projetará esse resultado em uma bela cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8d917-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="8d917-161">Na forma de diagrama:</span><span class="sxs-lookup"><span data-stu-id="8d917-161">In diagram form:</span></span>

![Diagrama da PLINQ](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="8d917-163">Trabalhos vinculados à CPU paralelizáveis que podem ser facilmente expressos por meio da LINQ (em outras palavras, que são funções puras e não têm efeitos colaterais) são ótimos candidatos para PLINQ.</span><span class="sxs-lookup"><span data-stu-id="8d917-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="8d917-164">Para trabalhos que _têm_ um efeito colateral, considere usar a [Biblioteca de paralelismo de tarefas](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="8d917-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="8d917-165">Recursos adicionais:</span><span class="sxs-lookup"><span data-stu-id="8d917-165">Further Resources:</span></span>

* [<span data-ttu-id="8d917-166">101 exemplos do LINQ</span><span class="sxs-lookup"><span data-stu-id="8d917-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* <span data-ttu-id="8d917-167">[LINQPad](https://www.linqpad.net/), um mecanismo de consulta de banco de dados e ambiente de playground para C#/F#/VB</span><span class="sxs-lookup"><span data-stu-id="8d917-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
* <span data-ttu-id="8d917-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), um livro eletrônico para aprender como o LINQ to Objects é implementado</span><span class="sxs-lookup"><span data-stu-id="8d917-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
