---
title: Usando classes Enumeration em vez de tipos enum
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Saiba como você pode usar classes de enumeração, em vez de enumerações, como uma maneira de resolver algumas limitações dessa última.
ms.date: 10/08/2018
ms.openlocfilehash: 6752adb28b1bd0982c66fa2d021b04b999447c6e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337689"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="1d1a0-103">Usar classes de enumeração em vez de tipos enumerados</span><span class="sxs-lookup"><span data-stu-id="1d1a0-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="1d1a0-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (ou *tipos enum*) são um wrapper de idioma fino em torno de um tipo integral.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="1d1a0-105">Talvez convenha limitar seu uso para quando você estiver armazenando um valor de um conjunto fechado de valores.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="1d1a0-106">A classificação com base em tamanhos (pequeno, médio ou grande) é um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="1d1a0-107">Usar enumerações para fluxo de controle ou abstrações mais robustas pode ser um [code smell](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="1d1a0-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="1d1a0-108">Esse tipo de uso leva a um código frágil com muitas instruções de fluxo de controle que verificam os valores da enumeração.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="1d1a0-109">Em vez disso, é possível criar classes Enumeration que habilitam todos os recursos avançados de uma linguagem orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="1d1a0-110">No entanto, isso não é um tópico crítico e, em muitos casos, para simplificar, ainda será possível usar [tipos enum](../../../csharp/language-reference/builtin-types/enum.md) regulares se você preferir.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="1d1a0-111">De qualquer forma, o uso de classes de enumeração está mais está relacionado a conceitos relacionados a negócios.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="1d1a0-112">Implementar uma classe base de enumeração</span><span class="sxs-lookup"><span data-stu-id="1d1a0-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="1d1a0-113">O microsserviço de ordenação em eShopOnContainers fornece uma implementação de exemplo de classe base Enumeration, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1d1a0-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public |
                                         BindingFlags.Static |
                                         BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;

        if (otherValue == null)
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);

    // Other utility methods ...
}
```

<span data-ttu-id="1d1a0-114">Use essa classe como um tipo em qualquer entidade ou objeto de valor, como para a seguinte classe `CardType`: `Enumeration`:</span><span class="sxs-lookup"><span data-stu-id="1d1a0-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="1d1a0-115">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1d1a0-115">Additional resources</span></span>

- <span data-ttu-id="1d1a0-116">**Enumerações são nocivas – atualização** </span><span class="sxs-lookup"><span data-stu-id="1d1a0-116">**Enum’s are evil—update** </span></span>\
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- <span data-ttu-id="1d1a0-117">**Daniel Hardman. Como as enums difundem a doença – e como remediar** </span><span class="sxs-lookup"><span data-stu-id="1d1a0-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** </span></span>\
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- <span data-ttu-id="1d1a0-118">**Jimmy Bogard. Classes de enumeração** </span><span class="sxs-lookup"><span data-stu-id="1d1a0-118">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="1d1a0-119">**Steve Smith. Enumerar alternativas C# no** </span><span class="sxs-lookup"><span data-stu-id="1d1a0-119">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="1d1a0-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="1d1a0-120">**Enumeration.cs.**</span></span> <span data-ttu-id="1d1a0-121">Classe base de enumeração em eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="1d1a0-121">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="1d1a0-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-122">**CardType.cs**.</span></span> <span data-ttu-id="1d1a0-123">Exemplo de classe de enumeração em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="1d1a0-124">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-124">**SmartEnum**.</span></span> <span data-ttu-id="1d1a0-125">Ardalis – Classes para ajudar a produzir enumerações fortemente tipadas mais inteligentes no .NET.</span><span class="sxs-lookup"><span data-stu-id="1d1a0-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="1d1a0-126">[Anterior](implement-value-objects.md)
>[Próximo](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="1d1a0-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
