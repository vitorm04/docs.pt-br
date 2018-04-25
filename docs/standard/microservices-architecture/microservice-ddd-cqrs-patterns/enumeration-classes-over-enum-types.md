---
title: Usando classes Enumeration em vez de tipos enum
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Usando classes Enumeration em vez de tipos enum
keywords: Docker, Microsserviços, ASP.NET, Contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9df8dc3373930d38bf9f53e9c3a9e986156d3d89
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="6fb79-104">Usando classes Enumeration em vez de tipos enum</span><span class="sxs-lookup"><span data-stu-id="6fb79-104">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="6fb79-105">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (ou *tipos enum*) são um wrapper de idioma fino em torno de um tipo integral.</span><span class="sxs-lookup"><span data-stu-id="6fb79-105">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="6fb79-106">Talvez convenha limitar seu uso para quando você estiver armazenando um valor de um conjunto fechado de valores.</span><span class="sxs-lookup"><span data-stu-id="6fb79-106">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="6fb79-107">Classificação baseada em gênero (por exemplo, masculino, feminino, desconhecido) ou tamanhos (pequeno, médio, grande) são bons exemplos.</span><span class="sxs-lookup"><span data-stu-id="6fb79-107">Classification based on gender (for example, male, female, unknown) or sizes (small, medium, large) are good examples.</span></span> <span data-ttu-id="6fb79-108">Usar enumerações para fluxo de controle ou abstrações mais robustas pode ser um [code smell](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="6fb79-108">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="6fb79-109">Esse tipo de uso leva a um código frágil com muitas instruções de fluxo de controle que verificam os valores da enumeração.</span><span class="sxs-lookup"><span data-stu-id="6fb79-109">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="6fb79-110">Em vez disso, é possível criar classes Enumeration que habilitam todos os recursos avançados de uma linguagem orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="6fb79-110">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="6fb79-111">No entanto, isso não é um tópico crítico e, em muitos casos, para simplificar, ainda será possível usar [tipos enum](../../../../docs/csharp/language-reference/keywords/enum.md) regulares se você preferir.</span><span class="sxs-lookup"><span data-stu-id="6fb79-111">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="6fb79-112">Implementando uma classe base Enumeration</span><span class="sxs-lookup"><span data-stu-id="6fb79-112">Implementing an Enumeration base class</span></span>

<span data-ttu-id="6fb79-113">O microsserviço de ordenação em eShopOnContainers fornece uma implementação de exemplo de classe base Enumeration, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6fb79-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; }
    public int Id { get; }

    protected Enumeration()
    {
    }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString()
    {
        return Name;
    }

    public static IEnumerable<T> GetAll<T>() where T : Enumeration, new()
    {
        var type = typeof(T);
        var fields = type.GetTypeInfo().GetFields(BindingFlags.Public |
            BindingFlags.Static |
            BindingFlags.DeclaredOnly);
        foreach (var info in fields)
        {
            var instance = new T();
            var locatedValue = info.GetValue(instance) as T;
            if (locatedValue != null)
            {
                yield return locatedValue;
            }
        }
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;
        if (otherValue == null)
        {
            return false;
        }
        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);
        return typeMatches && valueMatches;
    }

    public int CompareTo(object other)
    {
        return Id.CompareTo(((Enumeration)other).Id);
    }

    // Other utility methods ...
}
```

<span data-ttu-id="6fb79-114">É possível usar essa classe como um tipo em qualquer entidade ou objeto de valor, como para a seguinte classe Enumeration CardType:</span><span class="sxs-lookup"><span data-stu-id="6fb79-114">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    protected CardType() { }

    public CardType(int id, string name)
        : base(id, name)
    {
    }

    public static IEnumerable<CardType> List()
    {
        return new[] { Amex, Visa, MasterCard };
    }
    // Other util methods
}
```

## <a name="additional-resources"></a><span data-ttu-id="6fb79-115">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="6fb79-115">Additional resources</span></span>

-   <span data-ttu-id="6fb79-116">**Enums são nocivos — atualização**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="6fb79-116">**Enum’s are evil—update**
[*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="6fb79-117">**Daniel Hardman. Como os Enums espalham doenças — e como curá-las**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="6fb79-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="6fb79-118">**Jimmy Bogard. Classes de enumeração**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="6fb79-118">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="6fb79-119">**Steve Smith. Alternativas de Enum em C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="6fb79-119">**Steve Smith. Enum Alternatives in C#**
[*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="6fb79-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="6fb79-120">**Enumeration.cs.**</span></span> <span data-ttu-id="6fb79-121">Classe base de enumeração no eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="6fb79-121">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="6fb79-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="6fb79-122">**CardType.cs**.</span></span> <span data-ttu-id="6fb79-123">Exemplo de classe de enumeração em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6fb79-123">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="6fb79-124">[Anterior] (implement-value-objects.md) [Próximo] (domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="6fb79-124">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
