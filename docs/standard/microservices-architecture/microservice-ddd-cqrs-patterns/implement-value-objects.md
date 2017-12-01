---
title: Implementando os objetos de valor
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementando os objetos de valor"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c20bc80d2ddb864a3a0172beb211974426a278a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-value-objects"></a>Implementando os objetos de valor

Conforme discutido nas seções anteriores sobre entidades e agregações, a identidade é fundamental para entidades. No entanto, há muitos objetos e itens de dados em um sistema que não exigem uma identidade e controle de alterações, como objetos de valor.

Um objeto de valor pode fazer referência a outras entidades. Por exemplo, em um aplicativo que gera uma rota que descreve como obter de um ponto para outro, essa rota deve ser um objeto de valor. Seria um instantâneo de pontos em uma rota específica, mas essa rota sugerida não teria uma identidade, embora internamente ele pode fazer referência a entidades, como cidade, Road, etc.

Figura 9 a 13 mostra o objeto de valor de endereço dentro do agregado de ordem.

![](./media/image14.png)

**Figura 9 a 13**. Objeto de valor dentro do agregado de ordem de endereço

Conforme mostrado na Figura 9 a 13, uma entidade geralmente é composta de vários atributos. Por exemplo, ordem pode ser modelada como uma entidade com uma identidade e internamente composto de um conjunto de atributos como OrderId, OrderDate, OrderItems, etc. Mas o endereço, que é simplesmente um valor complexo composto por país, rua, cidade, etc. devem ser modeladas e tratado como um objeto de valor.

## <a name="important-characteristics-of-value-objects"></a>Características importantes de objetos de valor

Há dois principais características para objetos de valor:

-   Eles não possuem identidade.

-   Eles são imutáveis.

A primeira característica já foi discutida. A imutabilidade é um requisito importante. Os valores de um objeto de valor devem ser imutáveis depois que o objeto é criado. Portanto, quando o objeto for construído, você deve fornecer os valores necessários, mas você não deve permitir a alteração durante o tempo de vida do objeto.

Objetos de valor permitem que você execute certas truques para desempenho, graças a sua natureza imutável. Isso é especialmente verdadeiro em sistemas em que podem haver milhares de valor de instâncias de objetos, muitos dos quais têm os mesmos valores. Sua natureza imutável permite que eles sejam reutilizados; eles podem ser objetos intercambiáveis, desde que seus valores são os mesmos e eles não possuem identidade. Esse tipo de otimização, às vezes, pode fazer uma diferença entre o software que é executado lentamente e software com bom desempenho. Obviamente, todos esses casos dependem do ambiente do aplicativo e o contexto de implantação.

## <a name="value-object-implementation-in-c"></a>Implementação de objeto de valor em C\#

Em termos de implementação, você pode ter uma classe base de objeto de valor que tem métodos de utilitário básico como igualdade com base na comparação entre todos os atributos (como um objeto de valor não deve ser baseado em identidade) e outras características fundamentais. O exemplo a seguir mostra uma classe base do objeto valor usada no ordenação microsserviço de eShopOnContainers.

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }
    // Other utilility methods
}
```

Você pode usar essa classe durante a implementação do seu objeto de valor real, assim como acontece com o objeto de valor de endereço mostrado no exemplo a seguir:

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address(string street, string city, string state,
        string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a>Ocultar a característica de identidade usando EF principais para manter os objetos de valor

Uma limitação quando usar EF principal estiver na sua versão atual (EF Core 1.1) não é possível usar [tipos complexos](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) conforme definido no EF 6. x. Portanto, você deve armazenar o objeto de valor como uma entidade EF. No entanto, você pode ocultar sua ID para esclarecer que a identidade não é importante no modelo que o objeto de valor faz parte do. Ocultar a ID é usando a ID como uma propriedade de sombra. Desde que a configuração para ocultar a ID do modelo é configurada no nível de infraestrutura, ele será transparente para o seu modelo de domínio e sua implementação de infra-estrutura foi alterado no futuro.

Em eShopOnContainers, a ID oculta necessária para a infraestrutura principal de EF é implementada da seguinte maneira no nível de DbContext, usando a API fluente o projeto de infra-estrutura.

```csharp
// Fluent API within the OrderingContext:DbContext in the
// Ordering.Infrastructure project

void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

Portanto, a ID é ocultada do ponto de vista do domínio modelo e no futuro, a infraestrutura de objeto de valor também pode ser implementada como um tipo complexo ou outra maneira.

## <a name="additional-resources"></a>Recursos adicionais

-   **Martin Fowler. Padrão de ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Eric Evans. Design controlado por domínio: Lidar com a complexidade do Centro de Software.** (Livro; inclui uma discussão sobre objetos de valor) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon. Implementando um Design controlado por domínio.** (Livro; inclui uma discussão sobre objetos de valor) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Propriedades de sombra**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Tipos complexos e/ou objetos de valor**. Discussão no repositório GitHub de núcleo EF (guia de problemas) [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs.** Classe de objeto de valor base no eShopOnContainers.
    [*https://GitHub.com/dotnet/eShopOnContainers/blob/Master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **Classe de endereço.** Classe de objeto de valor de exemplo no eShopOnContainers.
    [*https://GitHub.com/dotnet/eShopOnContainers/blob/Master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
[Anterior] (seedwork-domain-model-base-classes-interfaces.md) [Avançar] (enumeração-classes-over-enum-types.md)
