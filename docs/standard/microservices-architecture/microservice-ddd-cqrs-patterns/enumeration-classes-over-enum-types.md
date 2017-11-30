---
title: "Usando classes de enumeração em vez de tipos de enumeração"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Usando classes de enumeração em vez de tipos de enumeração"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1745198720fd12a9d26aab2d2afb2c5dd6b6b49d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>Usando classes de enumeração em vez de tipos de enumeração

[Enumerações](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*enums* abreviada) são um wrapper de idioma fino em torno de um tipo integral. Você talvez queira limitar seu uso para quando você estiver armazenando um valor de um conjunto fechado de valores. Classificação com base em gênero (por exemplo, masculino, feminino, desconhecido) ou tamanhos (S, M, L, XL) são bons exemplos. Usar enums de fluxo de controle ou abstrações mais robustas pode ser um [código cheiro](http://deviq.com/code-smells/). Esse tipo de uso levará ao código frágil com muitas instruções de fluxo de controle verificar valores de enum.

Em vez disso, você pode criar classes de enumeração que permitem que todos os recursos avançados de uma linguagem orientada a objeto. No entanto, isso não é um problema crítico e, em muitos casos, para simplificar, você ainda pode usar enums normal se você preferir.

## <a name="implementing-enumeration-classes"></a>Implementando classes de enumeração

O ordenação microsserviço em eShopOnContainers fornece uma implementação de classe base de enumeração de exemplo, conforme mostrado no exemplo a seguir:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }
    public int Id { get; private set; }

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

Você pode usar essa classe como um tipo em qualquer objeto de entidade ou um valor para a seguinte classe de enumeração CardType.

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

## <a name="additional-resources"></a>Recursos adicionais

-   **Enum é nocivo — atualizar**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **Daniel Hardman. Como os Enums se espalham doença — E a cura-**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard. Classes de enumeração**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith. Alternativas de enum no c#**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs.** Classe de enumeração em eShopOnContainers base [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**. Exemplo de classe de enumeração em eShopOnContainers.
    [*https://GitHub.com/dotnet/eShopOnContainers/blob/Master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[Anterior] (implementar-valor-objects.md) [Avançar] (domínio-modelo-camada-validations.md)
