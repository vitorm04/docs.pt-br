---
title: LINQ (Consulta Integrada à Linguagem)
description: Saiba como a LINQ fornece funcionalidades de consulta no nível da linguagem e uma API para C# e VB como uma maneira de escrever um código expressivo e declarativo.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 4e6e361666b6b6ae36b7d4bf02af55a379c8e16e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999789"
---
# <a name="linq-language-integrated-query"></a>LINQ (Consulta Integrada à Linguagem)

## <a name="what-is-it"></a>O que é?

A LINQ fornece funcionalidades de consulta no nível da linguagem e uma API de [função de ordem superior](https://en.wikipedia.org/wiki/Higher-order_function) para C# e VB como uma maneira de escrever um código expressivo e declarativo.

Sintaxe de consulta de nível de linguagem:

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

Mesmo exemplo usando a API `IEnumerable<T>`:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a>A LINQ é expressiva

Imagine que você tem uma lista de animais de estimação, mas deseja convertê-la em um dicionário em que você pode acessar um animal de estimação diretamente por seu valor `RFID`.

Código imperativo tradicional:

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

A intenção por trás do código não é criar um novo `Dictionary<int, Pet>` e adicionar a ele por meio de um loop, é converter uma lista existente em um dicionário. A LINQ preserva a intenção enquanto o código imperativo não.

Expressão LINQ equivalente:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

O código usando a LINQ é importante porque ele nivela a área de atuação entre a intenção e o código ao raciocinar como um programador. Outro bônus é a brevidade do código. Imagine reduzir grandes partes de uma base de código em 1/3 como feito acima. Excelente, certo?

## <a name="linq-providers-simplify-data-access"></a>Provedores LINQ simplificam o acesso a dados

Para uma parte significativa do software em uso, tudo gira em torno de lidar com os dados de alguma origem (bancos de dados, JSON, XML etc.). Geralmente isso envolve aprender uma nova API para cada fonte de dados, o que pode ser inconveniente. A LINQ simplifica isso abstraindo os elementos comuns de acesso a dados em uma sintaxe de consulta que tem a mesma aparência, independentemente da fonte de dados escolhida.

Considere o seguinte: localizar todos os elementos XML com um valor de atributo específico.

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

Escrever o código para percorrer manualmente o documento XML para realizar essa tarefa seria muito mais desafiador.

Interagir com o XML não é a única coisa que você pode fazer com provedores LINQ. O [LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) é um ORM (Mapeador de Objeto Relacional) de funções bastante básicas para um banco de dados MSSQL. A biblioteca [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) fornece uma passagem do documento JSON eficiente por meio da LINQ. Além disso, se não existir uma biblioteca que faça o que você precisa, também é possível [escrever seu próprio provedor LINQ](https://msdn.microsoft.com/library/Bb546158.aspx).

## <a name="why-use-the-query-syntax"></a>Por que usar a sintaxe de consulta?

Essa é uma pergunta que surge bastante. Afinal, isso

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

é muito mais conciso que isso:

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

A sintaxe da API não é apenas uma maneira mais concisa de fazer a sintaxe de consulta?

Nº A sintaxe de consulta permite o uso da cláusula **let**, que permite que você introduza e associe uma variável no escopo da expressão, usando-a em partes subsequentes da expressão. É possível reproduzir o mesmo código com apenas a sintaxe da API, mas mais provavelmente levará a um código que é difícil de ler.

Portanto, isso levanta a questão, **você deve usar apenas a sintaxe de consulta?**

A resposta para essa pergunta será **sim** se...

*   Sua base de código já usar a sintaxe de consulta
*   Você precisar definir o escopo de variáveis em suas consultas devido à complexidade
*   Você preferir a sintaxe de consulta e ela não for distraí-lo da base de código

A resposta para essa pergunta será **não** se...

*   Sua base de código já usar a sintaxe de API
*   Você não precisar definir o escopo de variáveis em suas consultas
*   Você preferir a sintaxe de API e ela não for distraí-lo da base de código

## <a name="essential-samples"></a>Exemplos essenciais

Para obter uma lista realmente abrangente de amostras de LINQ, visite [101 LINQ Samples ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b) (101 exemplos da LINQ).

A seguir está uma rápida demonstração de algumas das partes essenciais da LINQ. De nenhuma forma isso é abrangente, uma vez que a LINQ fornece significativamente mais funcionalidades do que o que é apresentado aqui.

*   O básico: `Where`, `Select` e `Aggregate`:

```csharp
// Filtering a list
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

*   Nivelar uma lista de listas:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   União entre dois conjuntos (com o comparador personalizado):

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
        // default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

*   Interseção entre dois conjuntos:

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   Ordenar:

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   Por fim, um exemplo mais avançado: determinar se os valores das propriedades de duas instâncias do mesmo tipo são iguais (emprestados e modificados [dessa postagem do StackOverflow](http://stackoverflow.com/a/844855)):

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

## <a name="plinq"></a>PLINQ

PLINQ, ou LINQ Paralela, é um mecanismo de execução paralelo para expressões de LINQ. Em outras palavras, expressões regulares de LINQ podem ser paralelizadas trivialmente em qualquer número de threads. Isso é feito por meio de uma chamada para `AsParallel()` precedendo a expressão.

Considere o seguinte:

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

Esse código particionará `facebookUsers` entre threads do sistema conforme necessário, somará o total de semelhantes em cada thread em paralelo, somará os resultados calculados por cada thread e projetará esse resultado em uma bela cadeia de caracteres.

Na forma de diagrama:

![Diagrama da PLINQ](./media/using-linq/plinq-diagram.png)

Trabalhos vinculados à CPU paralelizáveis que podem ser facilmente expressos por meio da LINQ (em outras palavras, que são funções puras e não têm efeitos colaterais) são ótimos candidatos para PLINQ. Para trabalhos que _têm_ um efeito colateral, considere usar a [Biblioteca de paralelismo de tarefas](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Recursos adicionais:

*   [101 exemplos do LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   [LINQPad](https://www.linqpad.net/), um mecanismo de consulta de banco de dados e ambiente de playground para C#/F#/VB
*   [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), um livro eletrônico para aprender como o LINQ to Objects é implementado
