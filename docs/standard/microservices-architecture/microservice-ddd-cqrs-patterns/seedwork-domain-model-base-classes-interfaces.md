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
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="136cd-104">Seedwork (reutilizáveis classes e interfaces base para o seu modelo de domínio)</span><span class="sxs-lookup"><span data-stu-id="136cd-104">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="136cd-105">A pasta de solução contém um *SeedWork* pasta.</span><span class="sxs-lookup"><span data-stu-id="136cd-105">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="136cd-106">O *SeedWork* pasta contém classes base personalizadas que você pode usar como base para suas entidades de domínio e os objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="136cd-106">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="136cd-107">Use essas classes base para que você não tem código redundante na classe de objeto de cada domínio.</span><span class="sxs-lookup"><span data-stu-id="136cd-107">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="136cd-108">A pasta para esses tipos de classes é chamada *SeedWork* e não algo como *Framework*.</span><span class="sxs-lookup"><span data-stu-id="136cd-108">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="136cd-109">Ele é chamado *SeedWork* porque a pasta contém apenas um pequeno subconjunto de classes reutilizáveis que realmente não pode ser considerada uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="136cd-109">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="136cd-110">*Seedwork* é um termo introduzido por [difusões de Michael](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) e popularizada por [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) , mas você também pode nomear essa pasta comum, SharedKernel, ou semelhantes.</span><span class="sxs-lookup"><span data-stu-id="136cd-110">*Seedwork* is a term introduced by [Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="136cd-111">Figura 9-12 mostra as classes que formam o seedwork do modelo de domínio em microsserviço a ordenação.</span><span class="sxs-lookup"><span data-stu-id="136cd-111">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="136cd-112">Ele tem algumas classes de base personalizadas como entidade, ValueObject e a enumeração, além de algumas interfaces.</span><span class="sxs-lookup"><span data-stu-id="136cd-112">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="136cd-113">Essas interfaces (IRepository e IUnitOfWork) informam a camada de infraestrutura sobre o que precisa ser implementado.</span><span class="sxs-lookup"><span data-stu-id="136cd-113">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="136cd-114">Essas interfaces também são usadas por meio de injeção de dependência de camada de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="136cd-114">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="136cd-115">**Figura 9-12**.</span><span class="sxs-lookup"><span data-stu-id="136cd-115">**Figure 9-12**.</span></span> <span data-ttu-id="136cd-116">Um exemplo de conjunto de interfaces e classes base do modelo de domínio "seedwork"</span><span class="sxs-lookup"><span data-stu-id="136cd-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="136cd-117">Esse é o tipo da reutilização de copiar e colar que muitos desenvolvedores compartilham entre projetos, não uma estrutura formal.</span><span class="sxs-lookup"><span data-stu-id="136cd-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="136cd-118">Você pode ter seedworks em qualquer camada ou na biblioteca.</span><span class="sxs-lookup"><span data-stu-id="136cd-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="136cd-119">No entanto, se o conjunto de classes e interfaces obtém suficientemente grande, convém criar uma biblioteca de classe individual.</span><span class="sxs-lookup"><span data-stu-id="136cd-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="136cd-120">A classe base de entidade personalizada</span><span class="sxs-lookup"><span data-stu-id="136cd-120">The custom Entity base class</span></span>

<span data-ttu-id="136cd-121">O código a seguir é um exemplo de uma classe base da entidade em que você pode colocar o código que pode ser usado da mesma forma, qualquer entidade de domínio, como a ID de entidade, [operadores de igualdade](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), etc.</span><span class="sxs-lookup"><span data-stu-id="136cd-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), etc.</span></span>

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

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="136cd-122">Contratos de repositório (interfaces) na camada de modelo de domínio</span><span class="sxs-lookup"><span data-stu-id="136cd-122">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="136cd-123">Contratos de repositório são simplesmente interfaces .NET que expressa os requisitos do contrato dos repositórios a ser usado para cada agregação.</span><span class="sxs-lookup"><span data-stu-id="136cd-123">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> <span data-ttu-id="136cd-124">Os repositórios, com código EF principal ou quaisquer outras dependências de infra-estrutura e código, não devem ser implementados no modelo de domínio. os repositórios só devem implementar as interfaces que você definir.</span><span class="sxs-lookup"><span data-stu-id="136cd-124">The repositories themselves, with EF Core code or any other infrastructure dependencies and code, must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span>

<span data-ttu-id="136cd-125">Um padrão relacionado a essa prática (colocando as interfaces do repositório na camada de modelo de domínio) é o padrão de Interface separada.</span><span class="sxs-lookup"><span data-stu-id="136cd-125">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="136cd-126">Como [explicado](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) por Martin Fowler "Interface separados de usar para definir uma interface em um pacote, mas implementá-la em outro.</span><span class="sxs-lookup"><span data-stu-id="136cd-126">As [explained](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="136cd-127">Dessa forma um cliente que precisa de dependência para a interface pode ser completamente ciente da implementação."</span><span class="sxs-lookup"><span data-stu-id="136cd-127">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="136cd-128">Seguindo o padrão de Interface separada permite que a camada de aplicativo (nesse caso, o projeto de API da Web para o microsserviço) têm uma dependência nos requisitos definidos no modelo de domínio, mas não uma dependência direta para a infraestrutura/persistência camada.</span><span class="sxs-lookup"><span data-stu-id="136cd-128">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="136cd-129">Além disso, você pode usar a injeção de dependência para isolar a implementação, o que é implementada na infraestrutura / camada de persistência usando repositórios.</span><span class="sxs-lookup"><span data-stu-id="136cd-129">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="136cd-130">Por exemplo, o exemplo a seguir com a interface IOrderRepository define as operações que a classe OrderRepository precisará implementar na camada de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="136cd-130">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="136cd-131">Na implementação atual do aplicativo, o código precisa apenas adicionar a ordem para o banco de dados, desde que as consultas são divisão seguinte que abordagem CQS e atualizações para pedidos não são implementadas.</span><span class="sxs-lookup"><span data-stu-id="136cd-131">In the current implementation of the application, the code just needs to add the order to the database, since queries are split following the CQS approach, and updates to orders are not implemented.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="136cd-132">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="136cd-132">Additional resources</span></span>

-   <span data-ttu-id="136cd-133">**Martin Fowler. Interface separada. ** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span><span class="sxs-lookup"><span data-stu-id="136cd-133">**Martin Fowler. Separated Interface.**
[*http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="136cd-134">[Anterior] (net-core-microsserviço-domínio-model.md) [Avançar] (implementar-valor-objects.md)</span><span class="sxs-lookup"><span data-stu-id="136cd-134">[Previous] (net-core-microservice-domain-model.md) [Next] (implement-value-objects.md)</span></span>
