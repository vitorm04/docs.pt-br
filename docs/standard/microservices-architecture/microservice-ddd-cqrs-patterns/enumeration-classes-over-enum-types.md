---
title: Usando classes Enumeration em vez de tipos enum
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Usando classes Enumeration em vez de tipos enum
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: f1b88d160d6532c2a768684b55cd236417699322
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467845"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="0de02-103">Usando classes Enumeration em vez de tipos enum</span><span class="sxs-lookup"><span data-stu-id="0de02-103">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="0de02-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (ou *tipos enum*) são um wrapper de idioma fino em torno de um tipo integral.</span><span class="sxs-lookup"><span data-stu-id="0de02-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="0de02-105">Talvez convenha limitar seu uso para quando você estiver armazenando um valor de um conjunto fechado de valores.</span><span class="sxs-lookup"><span data-stu-id="0de02-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="0de02-106">A classificação com base em tamanhos (pequeno, médio ou grande) é um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="0de02-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="0de02-107">Usar enumerações para fluxo de controle ou abstrações mais robustas pode ser um [code smell](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="0de02-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="0de02-108">Esse tipo de uso leva a um código frágil com muitas instruções de fluxo de controle que verificam os valores da enumeração.</span><span class="sxs-lookup"><span data-stu-id="0de02-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="0de02-109">Em vez disso, é possível criar classes Enumeration que habilitam todos os recursos avançados de uma linguagem orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="0de02-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="0de02-110">No entanto, isso não é um tópico crítico e, em muitos casos, para simplificar, ainda será possível usar [tipos enum](../../../../docs/csharp/language-reference/keywords/enum.md) regulares se você preferir.</span><span class="sxs-lookup"><span data-stu-id="0de02-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="0de02-111">Implementando uma classe base Enumeration</span><span class="sxs-lookup"><span data-stu-id="0de02-111">Implementing an Enumeration base class</span></span>

<span data-ttu-id="0de02-112">O microsserviço de ordenação em eShopOnContainers fornece uma implementação de exemplo de classe base Enumeration, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0de02-112">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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
    
    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | BindingFlags.Static | BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
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

<span data-ttu-id="0de02-113">É possível usar essa classe como um tipo em qualquer entidade ou objeto de valor, como para a seguinte classe Enumeration CardType:</span><span class="sxs-lookup"><span data-stu-id="0de02-113">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

```csharp
public abstract class CardType : Enumeration
{
    public static CardType Amex = new AmexCardType();
    public static CardType Visa = new VisaCardType();
    public static CardType MasterCard = new MasterCardType();

    protected CardType(int id, string name)
        : base(id, name)
    {
    }

    private class AmexCardType : CardType
    {
        public AmexCardType(): base(1, "Amex")
        { }
    }
    
    private class VisaCardType : CardType
    {
        public VisaCardType(): base(2, "Visa")
        { }
    }
    
    private class MasterCardType : CardType
    {
        public MasterCardType(): base(3, "MasterCard")
        { }
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="0de02-114">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0de02-114">Additional resources</span></span>

-   <span data-ttu-id="0de02-115">**Enums são nocivos — atualização**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="0de02-115">**Enum’s are evil—update**
[*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="0de02-116">**Daniel Hardman. Como os Enums espalham doenças — e como curá-las**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="0de02-116">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="0de02-117">**Jimmy Bogard. Classes de enumeração**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="0de02-117">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="0de02-118">**Steve Smith. Alternativas de Enum em C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="0de02-118">**Steve Smith. Enum Alternatives in C#**
[*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="0de02-119">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="0de02-119">**Enumeration.cs.**</span></span> <span data-ttu-id="0de02-120">Classe base de enumeração no eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="0de02-120">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="0de02-121">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="0de02-121">**CardType.cs**.</span></span> <span data-ttu-id="0de02-122">Exemplo de classe de enumeração em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0de02-122">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="0de02-123">[Anterior](implement-value-objects.md)
[Próximo](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="0de02-123">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
