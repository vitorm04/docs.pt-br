---
title: Usando classes Enumeration em vez de tipos enum
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Saiba como você pode usar classes de enumeração, em vez de enumerações, como uma maneira de resolver algumas limitações dessa última.
ms.date: 10/08/2018
ms.openlocfilehash: fb2cbcd744f29c70a86e6f3300721934192eb752
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847174"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="4bd55-103">Usar classes de enumeração em vez de tipos enumerados</span><span class="sxs-lookup"><span data-stu-id="4bd55-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="4bd55-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (ou *tipos enum*) são um wrapper de idioma fino em torno de um tipo integral.</span><span class="sxs-lookup"><span data-stu-id="4bd55-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="4bd55-105">Talvez convenha limitar seu uso para quando você estiver armazenando um valor de um conjunto fechado de valores.</span><span class="sxs-lookup"><span data-stu-id="4bd55-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="4bd55-106">A classificação com base em tamanhos (pequeno, médio ou grande) é um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="4bd55-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="4bd55-107">Usar enumerações para fluxo de controle ou abstrações mais robustas pode ser um [code smell](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="4bd55-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="4bd55-108">Esse tipo de uso leva a um código frágil com muitas instruções de fluxo de controle que verificam os valores da enumeração.</span><span class="sxs-lookup"><span data-stu-id="4bd55-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="4bd55-109">Em vez disso, é possível criar classes Enumeration que habilitam todos os recursos avançados de uma linguagem orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="4bd55-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="4bd55-110">No entanto, isso não é um tópico crítico e, em muitos casos, para simplificar, ainda será possível usar [tipos enum](../../../csharp/language-reference/builtin-types/enum.md) regulares se você preferir.</span><span class="sxs-lookup"><span data-stu-id="4bd55-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="4bd55-111">De qualquer forma, o uso de classes de enumeração está mais está relacionado a conceitos relacionados a negócios.</span><span class="sxs-lookup"><span data-stu-id="4bd55-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="4bd55-112">Implementar uma classe base de enumeração</span><span class="sxs-lookup"><span data-stu-id="4bd55-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="4bd55-113">O microsserviço de ordenação em eShopOnContainers fornece uma implementação de exemplo de classe base Enumeration, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4bd55-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="4bd55-114">Use essa classe como um tipo em qualquer entidade ou objeto de valor, como para a seguinte classe `CardType`: `Enumeration`:</span><span class="sxs-lookup"><span data-stu-id="4bd55-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static readonly CardType Amex = new CardType(1, "Amex");
    public static readonly CardType Visa = new CardType(2, "Visa");
    public static readonly CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="4bd55-115">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="4bd55-115">Additional resources</span></span>

- <span data-ttu-id="4bd55-116">**Jimmy Bogard. Aulas de enumeração** </span><span class="sxs-lookup"><span data-stu-id="4bd55-116">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="4bd55-117">**Steve Smith. Alternativas enum em C #** </span><span class="sxs-lookup"><span data-stu-id="4bd55-117">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="4bd55-118">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="4bd55-118">**Enumeration.cs.**</span></span> <span data-ttu-id="4bd55-119">Classe base de enumeração em eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="4bd55-119">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="4bd55-120">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="4bd55-120">**CardType.cs**.</span></span> <span data-ttu-id="4bd55-121">Exemplo de classe de enumeração em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="4bd55-121">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="4bd55-122">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="4bd55-122">**SmartEnum**.</span></span> <span data-ttu-id="4bd55-123">Ardalis – Classes para ajudar a produzir enumerações fortemente tipadas mais inteligentes no .NET.</span><span class="sxs-lookup"><span data-stu-id="4bd55-123">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="4bd55-124">[Próximo](implement-value-objects.md)
>[anterior](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="4bd55-124">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
