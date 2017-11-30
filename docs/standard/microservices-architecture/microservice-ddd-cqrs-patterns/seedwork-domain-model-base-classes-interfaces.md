---
title: "Seedwork (reutilizáveis classes e interfaces base para o seu modelo de domínio)"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Seedwork (reutilizáveis classes e interfaces base para o seu modelo de domínio)"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 17602d94ea167997389a77f0d2358326258a8219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (reutilizáveis classes e interfaces base para o seu modelo de domínio)

A pasta de solução contém um *SeedWork* pasta. O *SeedWork* pasta contém classes base personalizadas que você pode usar como base para suas entidades de domínio e os objetos de valor. Use essas classes base para que você não tem código redundante na classe de objeto de cada domínio. A pasta para esses tipos de classes é chamada *SeedWork* e não algo como *Framework*. Ele é chamado *SeedWork* porque a pasta contém apenas um pequeno subconjunto de classes reutilizáveis que realmente não pode ser considerada uma estrutura. *Seedwork* é um termo introduzido por [difusões de Michael](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) e popularizada por [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) , mas você também pode nomear essa pasta comum, SharedKernel, ou semelhantes.

Figura 9-12 mostra as classes que formam o seedwork do modelo de domínio em microsserviço a ordenação. Ele tem algumas classes de base personalizadas como entidade, ValueObject e a enumeração, além de algumas interfaces. Essas interfaces (IRepository e IUnitOfWork) informam a camada de infraestrutura sobre o que precisa ser implementado. Essas interfaces também são usadas por meio de injeção de dependência de camada de aplicativo.

![](./media/image13.PNG)

**Figura 9-12**. Um exemplo de conjunto de interfaces e classes base do modelo de domínio "seedwork"

Esse é o tipo da reutilização de copiar e colar que muitos desenvolvedores compartilham entre projetos, não uma estrutura formal. Você pode ter seedworks em qualquer camada ou na biblioteca. No entanto, se o conjunto de classes e interfaces obtém suficientemente grande, convém criar uma biblioteca de classe individual.

## <a name="the-custom-entity-base-class"></a>A classe base de entidade personalizada

O código a seguir é um exemplo de uma classe base da entidade em que você pode colocar o código que pode ser usado da mesma forma, qualquer entidade de domínio, como a ID de entidade, [operadores de igualdade](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), etc.

```csharp
// ENTITY FRAMEWORK CORE 1.1
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;

    public virtual int Id
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }
  
    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() \^ 31;
            // XOR for random distribution. See:
            // http://blogs.msdn.com/b/ericlippert/archive/2011/02/28/guidelines-and-rules-for-gethashcode.aspx
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }

    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null)) ? true : false;
        else
            return left.Equals(right);
    }

    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Contratos de repositório (interfaces) na camada de modelo de domínio

Contratos de repositório são simplesmente interfaces .NET que expressa os requisitos do contrato dos repositórios a ser usado para cada agregação. Os repositórios, com código EF principal ou quaisquer outras dependências de infra-estrutura e código, não devem ser implementados no modelo de domínio. os repositórios só devem implementar as interfaces que você definir.

Um padrão relacionado a essa prática (colocando as interfaces do repositório na camada de modelo de domínio) é o padrão de Interface separada. Como [explicado](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) por Martin Fowler "Interface separados de usar para definir uma interface em um pacote, mas implementá-la em outro. Dessa forma um cliente que precisa de dependência para a interface pode ser completamente ciente da implementação."

Seguindo o padrão de Interface separada permite que a camada de aplicativo (nesse caso, o projeto de API da Web para o microsserviço) têm uma dependência nos requisitos definidos no modelo de domínio, mas não uma dependência direta para a infraestrutura/persistência camada. Além disso, você pode usar a injeção de dependência para isolar a implementação, o que é implementada na infraestrutura / camada de persistência usando repositórios.

Por exemplo, o exemplo a seguir com a interface IOrderRepository define as operações que a classe OrderRepository precisará implementar na camada de infraestrutura. Na implementação atual do aplicativo, o código precisa apenas adicionar a ordem para o banco de dados, desde que as consultas são divisão seguinte que abordagem CQS e atualizações para pedidos não são implementadas.

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
}

public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a>Recursos adicionais

-   **Martin Fowler. Interface separada. ** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)


>[!div class="step-by-step"]
[Anterior] (net-core-microsserviço-domínio-model.md) [Avançar] (implementar-valor-objects.md)
