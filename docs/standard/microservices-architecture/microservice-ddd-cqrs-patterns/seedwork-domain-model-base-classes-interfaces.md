---
title: Seedwork (classes e interfaces base reutilizáveis para seu modelo de domínio)
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Seedwork (classes e interfaces base reutilizáveis para seu modelo de domínio)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 7098bc1d37ecdf4826c0db6e754ca8df2ed72fe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578047"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="b0cdf-103">Seedwork (classes e interfaces base reutilizáveis para seu modelo de domínio)</span><span class="sxs-lookup"><span data-stu-id="b0cdf-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="b0cdf-104">A pasta de solução contém uma pasta *SeedWork*.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="b0cdf-105">A pasta *SeedWork* contém classes base personalizadas que podem ser usadas como uma base para suas entidades de domínio e objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-105">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="b0cdf-106">Use essas classes base para que você não tenha código redundante na classe de objeto de cada domínio.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-106">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="b0cdf-107">A pasta para esses tipos de classes é chamada *SeedWork* e não algo como *Framework*.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="b0cdf-108">Ela é chamada *SeedWork*, porque a pasta contém apenas um pequeno subconjunto de classes reutilizáveis que realmente não podem ser consideradas uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="b0cdf-109">*Seedwork* é um termo introduzido por [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) e popularizado por [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html), mas você também pode nomear essa pasta Common, SharedKernel, ou semelhantes.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="b0cdf-110">A Figura 9-12 mostra as classes que formam o seedwork do modelo de domínio no microsserviço de ordenação.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-110">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="b0cdf-111">Ele tem algumas classes base personalizadas como Entity, ValueObject e Enumeration, além de algumas interfaces.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="b0cdf-112">Essas interfaces (IRepository e IUnitOfWork) informam a camada de infraestrutura sobre o que precisa ser implementado.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="b0cdf-113">Essas interfaces também são usadas por meio de Injeção de dependência da camada de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="b0cdf-114">**Figura 9-12**.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-114">**Figure 9-12**.</span></span> <span data-ttu-id="b0cdf-115">Um exemplo do conjunto de interfaces e de classes base "seedwork" do modelo de domínio</span><span class="sxs-lookup"><span data-stu-id="b0cdf-115">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="b0cdf-116">Esse é o tipo de reutilização de copiar e colar que muitos desenvolvedores compartilham entre projetos, não uma estrutura formal.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-116">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="b0cdf-117">É possível ter seedworks em qualquer camada ou biblioteca.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-117">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="b0cdf-118">No entanto, se o conjunto de classes e interfaces ficar grande o bastante, crie uma biblioteca de classes individual.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-118">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="b0cdf-119">A classe base Entity personalizada</span><span class="sxs-lookup"><span data-stu-id="b0cdf-119">The custom Entity base class</span></span>

<span data-ttu-id="b0cdf-120">O código a seguir é um exemplo de uma classe base Entity em que é possível inserir o código que pode ser usado da mesma maneira por qualquer entidade de domínio, como a ID da entidade, [operadores de igualdade](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), uma lista de eventos de domínio por entidade, etc.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-120">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), a domain event list per entity, etc.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE (1.1 and later)
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;    
    private List<INotification> _domainEvents;
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

    public List<INotification> DomainEvents => _domainEvents;        
    public void AddDomainEvent(INotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<INotification>();
        _domainEvents.Add(eventItem);
    }
    public void RemoveDomainEvent(INotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
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
                _requestedHashCode = this.Id.GetHashCode() ^ 31; 
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

<span data-ttu-id="b0cdf-121">O código anterior que usa uma lista de eventos de domínio por entidade será explicado nas próximas seções ao abordar eventos de domínio.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-121">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span> 

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="b0cdf-122">Contratos de repositório (interfaces) na camada de modelo de domínio</span><span class="sxs-lookup"><span data-stu-id="b0cdf-122">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="b0cdf-123">Os contratos de repositório são simplesmente interfaces .NET que expressam os requisitos do contrato dos repositórios a serem usados para cada agregação.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-123">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> 

<span data-ttu-id="b0cdf-124">Os repositórios em si, com código do EF Core ou quaisquer outras dependências de infraestrutura e código (LINQ, SQL, etc.), não devem ser implementados no modelo de domínio; os repositórios só deverão implementar as interfaces que você definir.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-124">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span> 

<span data-ttu-id="b0cdf-125">Um padrão relacionado a essa prática (inserir as interfaces de repositório na camada do modelo de domínio) é o padrão Interface separada.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-125">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="b0cdf-126">Como [explicado](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) por Martin Fowler "Use a Interface separada para definir uma interface em um pacote, mas a implemente em outro.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-126">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="b0cdf-127">Dessa forma, um cliente que precisa da dependência com a interface pode não estar completamente ciente da implementação."</span><span class="sxs-lookup"><span data-stu-id="b0cdf-127">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="b0cdf-128">Seguir o padrão Interface separada permite que a camada de aplicativo (nesse caso, o projeto da API Web para o microsserviço) tenha uma dependência nos requisitos definidos no modelo de domínio, mas não uma dependência direta com a camada de infraestrutura/persistência.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-128">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="b0cdf-129">Além disso, é possível usar a Injeção de dependência para isolar a implementação, o que é implementado na camada de infraestrutura/persistência que usam repositórios.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-129">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="b0cdf-130">Por exemplo, o exemplo a seguir com a interface IOrderRepository define quais operações a classe OrderRepository precisará implementar na camada de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-130">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="b0cdf-131">Na implementação atual do aplicativo, o código precisa apenas adicionar ou atualizar ordens no banco de dados, uma vez que as consultas são divididas seguindo a abordagem CQRS simplificada.</span><span class="sxs-lookup"><span data-stu-id="b0cdf-131">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

```csharp
// Defined at IOrderRepository.cs
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
        
    void Update(Order order);

    Task<Order> GetAsync(int orderId);
}

// Defined at IRepository.cs (Part of the Domain Seedwork)
public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a><span data-ttu-id="b0cdf-132">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b0cdf-132">Additional resources</span></span>

-   <span data-ttu-id="b0cdf-133">**Martin Fowler. Interface separada.**
    [*https://www.martinfowler.com/eaaCatalog/separatedInterface.html*](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)</span><span class="sxs-lookup"><span data-stu-id="b0cdf-133">**Martin Fowler. Separated Interface.**
[*https://www.martinfowler.com/eaaCatalog/separatedInterface.html*](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b0cdf-134">[Anterior] (net-core-microservice-domain-model.md) [Próximo] (implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="b0cdf-134">[Previous] (net-core-microservice-domain-model.md) [Next] (implement-value-objects.md)</span></span>
