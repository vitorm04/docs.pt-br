---
title: "Implementação de um modelo de domínio de microsserviço com .NET Core"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementação de um modelo de domínio de microsserviço com .NET Core"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 26c480a82ad7bb806734decebdfbe5b4a07998e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="c9f3b-104">Implementação de um modelo de domínio de microsserviço com .NET Core</span><span class="sxs-lookup"><span data-stu-id="c9f3b-104">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="c9f3b-105">Na seção anterior, foram explicados os princípios de design fundamental e padrões para criar um modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-105">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="c9f3b-106">Agora é hora de explorar possíveis maneiras de implementar o modelo de domínio usando o .NET Core (C simples\# código) e EF Core.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-106">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="c9f3b-107">Observe que seu modelo de domínio será ser composto apenas de seu código.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-107">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="c9f3b-108">Ele terá apenas a requisitos do modelo EF principal, mas não reais dependências no EF.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-108">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="c9f3b-109">Você não deve ter dependências de disco rígidas ou referências a EF principal ou qualquer outro ORM em seu modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-109">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="c9f3b-110">Estrutura do modelo de domínio em uma biblioteca .NET padrão personalizada</span><span class="sxs-lookup"><span data-stu-id="c9f3b-110">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="c9f3b-111">A organização de pastas usada para o aplicativo de referência eShopOnContainers demonstra o modelo DDD para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-111">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="c9f3b-112">Você pode achar que uma organização de pastas diferente comunica mais claramente as escolhas de design feitas para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-112">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="c9f3b-113">Como você pode ver na Figura 9-10, no modelo de domínio ordenação há duas agregações, a agregação de ordem e a agregação de compradores.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-113">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="c9f3b-114">Cada agregação é um grupo de entidades de domínio e objetos de valor, embora você poderia ter uma agregação composta de uma entidade de domínio único (a raiz de agregação ou entidade raiz) também.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-114">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="c9f3b-115">**Figura 9-10**.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-115">**Figure 9-10**.</span></span> <span data-ttu-id="c9f3b-116">Estrutura de modelo de domínio para o pedido microsserviço em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c9f3b-116">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="c9f3b-117">Além disso, a camada de modelo de domínio inclui os contratos de repositório (interfaces) que são os requisitos de infraestrutura do seu modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-117">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="c9f3b-118">Em outras palavras, essas interfaces express quais repositórios deve implementar a camada de infraestrutura e como.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-118">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="c9f3b-119">É importante que a implementação dos repositórios colocados fora da camada de modelo de domínio, na biblioteca de camada de infraestrutura, para a camada de modelo de domínio não é "contaminação" pela API ou classes de tecnologias de infraestrutura, como o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-119">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="c9f3b-120">Você também pode ver um [SeedWork](https://martinfowler.com/bliki/Seedwork.html) objetos pasta que contém as classes de base personalizadas que você pode usar como base para suas entidades de domínio e o valor, portanto você não tem código redundante na classe de objeto de cada domínio.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-120">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="c9f3b-121">Estruturar agregações em uma biblioteca .NET padrão personalizada</span><span class="sxs-lookup"><span data-stu-id="c9f3b-121">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="c9f3b-122">Uma agregação refere-se a um cluster de objetos de domínio agrupados de acordo com a consistência transacional.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-122">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="c9f3b-123">Esses objetos podem ser instâncias de entidades (um dos quais é o raiz de agregação ou uma entidade raiz) além de qualquer objeto de valor adicional.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-123">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="c9f3b-124">Consistência transacional significa que uma agregação é garantida para ser consistente e atualizado ao final de uma ação de negócios.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-124">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="c9f3b-125">Por exemplo, a agregação de ordem do eShopOnContainers ordenação microsserviço modelo de domínio é composta conforme mostrado na Figura 9-11.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-125">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="c9f3b-126">**Figura 9-11**.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-126">**Figure 9-11**.</span></span> <span data-ttu-id="c9f3b-127">A ordem de agregação na solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c9f3b-127">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="c9f3b-128">Se você abrir qualquer um dos arquivos em uma pasta de agregação, você pode ver como ele está marcado como uma classe base personalizada ou uma interface, como objeto de entidade ou um valor, conforme implementado o [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) pasta.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-128">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="c9f3b-129">Implementação de entidades de domínio como classes POCO</span><span class="sxs-lookup"><span data-stu-id="c9f3b-129">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="c9f3b-130">Você pode implementar um modelo de domínio no .NET criando classes POCO que implementam as entidades de domínio.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-130">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="c9f3b-131">No exemplo a seguir, a classe de ordem é definida como uma entidade e como uma raiz de agregação.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-131">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="c9f3b-132">Porque a classe de ordem deriva da classe base da entidade, ele pode reutilizar o código comuns relacionado a entidades.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-132">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="c9f3b-133">Tenha em mente que essas interfaces e classes base são definidas por você no projeto de modelo de domínio, portanto, é o seu código, não o código de infraestrutura de um ORM como EF.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-133">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 1.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    public int BuyerId { get; private set; }
    public DateTime OrderDate { get; private set; }
    public int StatusId { get; private set; }
    public ICollection<OrderItem> OrderItems { get; private set; }
    public Address ShippingAddress { get; private set; }
    public int PaymentId { get; private set; }
    protected Order() { } //Design constraint needed only by EF Core
    public Order(int buyerId, int paymentId)
    {
        BuyerId = buyerId;
        PaymentId = paymentId;
        StatusId = OrderStatus.InProcess.Id;
        OrderDate = DateTime.UtcNow;
        OrderItems = new List<OrderItem>();
    }

    public void AddOrderItem(productName,
        pictureUrl,
        unitPrice,
        discount,
        units)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...
        OrderItem item = new OrderItem(this.Id, ProductId, productName,
            pictureUrl, unitPrice, discount, units);
  
        OrderItems.Add(item);
    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

<span data-ttu-id="c9f3b-134">É importante observar que isso é implementada como uma classe POCO uma entidade de domínio.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-134">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="c9f3b-135">Ele não tem nenhuma dependência direta do Entity Framework Core ou qualquer outra estrutura de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-135">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="c9f3b-136">Essa implementação é como ele deve ser, apenas C\# código que implementa um modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-136">This implementation is as it should be, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="c9f3b-137">Além disso, a classe é decorada com uma interface denominada IAggregateRoot.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-137">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="c9f3b-138">Essa interface é uma interface vazia, às vezes chamada de um *interface de marcador*, que é usado apenas para indicar que esta classe de entidade também é uma raiz de agregação.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-138">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="c9f3b-139">Uma interface de marcador, às vezes, é considerada como um anti padrão de; No entanto, também é uma maneira simples para marcar uma classe, especialmente quando essa interface pode ser em evolução.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-139">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="c9f3b-140">Um atributo pode ser outra escolha para o marcador, mas é mais rápido ver a classe base (entidades) ao lado da interface do IAggregate em vez de colocar um marcador de atributo de agregação acima da classe.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-140">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="c9f3b-141">É um metter de preferências, de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-141">It is a metter of preferences, in any case.</span></span>

<span data-ttu-id="c9f3b-142">Ter um meio de raiz de agregação que a maioria do código relacionada a consistência e regras de negócio de entidades da agregação devem ser implementadas como métodos na classe de raiz agregada de ordem (por exemplo, AddOrderItem ao adicionar um objeto ItemPedido à agregação) .</span><span class="sxs-lookup"><span data-stu-id="c9f3b-142">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="c9f3b-143">Você não deve criar ou atualizar objetos OrderItems independentemente ou diretamente. a classe AggregateRoot deve manter o controle e a consistência de qualquer operação de atualização com as entidades filhas.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-143">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

<span data-ttu-id="c9f3b-144">Por exemplo, você deverá *não* faça o seguinte de qualquer comando manipulador método ou aplicativo de camada da classe:</span><span class="sxs-lookup"><span data-stu-id="c9f3b-144">For example, you should *not* do the following from any command handler method or application layer class:</span></span>

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

<span data-ttu-id="c9f3b-145">Nesse caso, o método Add é meramente uma operação para adicionar dados, com acesso direto à coleção OrderItems.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-145">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="c9f3b-146">Portanto, a maioria da lógica do domínio, regras ou validações relacionada ao que a operação com as entidades filhas será espalhada pela camada de aplicativo (manipuladores de comandos e controladores de API da Web).</span><span class="sxs-lookup"><span data-stu-id="c9f3b-146">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="c9f3b-147">Se você for uma solução alternativa para a raiz de agregação, a raiz de agregação não pode garantir suas invariáveis, sua validade ou sua consistência.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-147">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="c9f3b-148">Finalmente, você terá código espaguete ou código de script transacional.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-148">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="c9f3b-149">Para seguir padrões DDD, entidades não devem ter setters públicas em qualquer propriedade de entidade.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-149">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="c9f3b-150">Alterações em uma entidade devem ser controlada pelos métodos explícitos com idioma onipresente explícito sobre a alteração que sendo executada na entidade.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-150">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="c9f3b-151">Além disso, coleções dentro da entidade (como os itens do pedido) devem ser propriedades somente leitura (o método AsReadOnly explicado posteriormente).</span><span class="sxs-lookup"><span data-stu-id="c9f3b-151">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="c9f3b-152">Você deve ser capaz de atualizá-lo somente de dentro de métodos da classe raiz agregada ou os métodos de entidade filho.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-152">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="c9f3b-153">Como você pode ver no código para a raiz de agregação de ordem, todos os setters devem ser privada ou, pelo menos, somente leitura externamente, para que qualquer operação de dados da entidade ou entidades seu filho deve ser executada por meio dos métodos na classe de entidade.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-153">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="c9f3b-154">Isso mantém a consistência de forma controlada e orientada a objeto, em vez de implementar o código de script transacional.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-154">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="c9f3b-155">O trecho de código a seguir mostra o modo adequado para a tarefa de adicionar um objeto ItemPedido para a agregação de ordem de código.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-155">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="c9f3b-156">Este trecho de código, a maioria da lógica relacionada à criação de um objeto ItemPedido ou validações serão sob o controle da raiz de agregação de ordem — no método AddOrderItem — especialmente validações e lógica relacionam a outros elementos em conjunto.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-156">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="c9f3b-157">Por exemplo, você pode obter o mesmo item de produto como o resultado de várias chamadas para AddOrderItem.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-157">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="c9f3b-158">Nesse método, você pode examinar os itens de produto e consolidar os mesmos itens de produto em um único objeto ItemPedido com várias unidades.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-158">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="c9f3b-159">Além disso, se há valores de desconto diferente, mas a ID do produto é o mesmo, você provavelmente seria aplicar o desconto mais alto.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-159">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="c9f3b-160">Esse princípio se aplica a qualquer outra lógica do domínio para o objeto ItemPedido.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-160">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="c9f3b-161">Além disso, a nova operação de OrderItem(params) também ser controlada e executada pelo método AddOrderItem da raiz de agregação de ordem.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-161">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="c9f3b-162">Portanto, a maioria da lógica ou validações relacionada ao que a operação (especialmente tudo o que afeta a consistência entre outras entidades filho) será em um único lugar na raiz da agregação.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-162">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="c9f3b-163">Que é a principal finalidade do padrão de raiz de agregação.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-163">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="c9f3b-164">Quando você usar o Entity Framework 1.1, uma entidade DDD pode ser expressada melhor porque um dos novos recursos do Entity Framework Core 1.1 é que ele permite [mapear para os campos](https://docs.microsoft.com/ef/core/modeling/backing-field) além das propriedades.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-164">When you use Entity Framework 1.1, a DDD entity can be better expressed because one of the new features of Entity Framework Core 1.1 is that it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="c9f3b-165">Isso é útil ao proteger as coleções de entidades filho ou objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-165">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="c9f3b-166">Com esse aprimoramento, você pode usar os campos particulares simples em vez de propriedades e você pode implementar qualquer atualização para a coleção de campos em métodos públicos e fornecer acesso somente leitura por meio do método AsReadOnly.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-166">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="c9f3b-167">No DDD para atualizar a entidade por meio de métodos de entidade (ou o construtor) para controlar qualquer invariável e a consistência dos dados, portanto propriedades são definidas somente com um acessador get.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-167">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="c9f3b-168">As propriedades têm o respaldo campos particulares.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-168">The properties are backed by private fields.</span></span> <span data-ttu-id="c9f3b-169">Membros particulares só pode ser acessados de dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-169">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="c9f3b-170">No entanto, exceção lá um: EF Core precisa definir esses campos também.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-170">However, there one exception: EF Core needs to set these fields as well.</span></span>

```csharp
// ENTITY FRAMEWORK CORE 1.1 OR LATER
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    // DDD Patterns comment
    // Using private fields, allowed since EF Core 1.1, is a much better
    // encapsulation aligned with DDD aggregates and domain entities (instead of
    // properties and property collections)
    private bool _someOrderInternalState;
    private DateTime _orderDate;
    public Address Address { get; private set; }
    public Buyer Buyer { get; private set; }
    private int _buyerId;
    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    // DDD patterns comment
    // Using a private collection field is better for DDD aggregate encapsulation.
    // OrderItem objects cannot be added from outside the aggregate root
    // directly to the collection, but only through the
    // OrderAggrergateRoot.AddOrderItem method, which includes behavior.
    private readonly List<OrderItem> _orderItems;
    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();
    // Using List<>.AsReadOnly()
    // This will create a read-only wrapper around the private list so it is
    // protected against external updates. It's much cheaper than .ToList(),
    // because it will not have to copy all items in a new collection.
    // (Just one heap alloc for the wrapper instance)
    // https://msdn.microsoft.com/en-us/library/e78dcd75(v=vs.110).aspx
    public PaymentMethod PaymentMethod { get; private set; }
    private int _paymentMethodId;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.InProcess.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;
    }

    // DDD patterns comment
    // The Order aggregate root method AddOrderitem() should be the only way
    // to add items to the Order object, so that any behavior (discounts, etc.)
    // and validations are controlled by the aggregate root in order to
    // maintain consistency within the whole aggregate.
    public void AddOrderItem(int productId, string productName, decimal unitPrice,
        decimal discount, string pictureUrl, int units = 1)
    {
        // ...
        // Domain rules/logic here for adding OrderItem objects to the order
        // ...
        OrderItem item = new OrderItem(this.Id, productId, productName,
            pictureUrl, unitPrice, discount, units);
        OrderItems.Add(item);
    }

    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="c9f3b-171">Mapeamento de propriedades com apenas obtém acessadores para os campos na tabela de banco de dados</span><span class="sxs-lookup"><span data-stu-id="c9f3b-171">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="c9f3b-172">Mapeamento de propriedades para as colunas da tabela de banco de dados não é a responsabilidade de domínio, mas a parte da camada de infraestrutura e de persistência.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-172">Mapping properties to the database table columns is not a domain responsibility, but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="c9f3b-173">Mencionamos essa aqui apenas para que você está ciente das novas funcionalidades no EF 1.1 relacionadas a como você pode modelar entidades.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-173">We mention this here just so you are aware of the new capabilities in EF 1.1 related to how you can model entities.</span></span> <span data-ttu-id="c9f3b-174">Detalhes adicionais sobre este tópico são explicados na seção de infraestrutura e de persistência.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-174">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="c9f3b-175">Quando você usa EF 1.0, no DbContext você precisa mapear as propriedades que são definidas somente com getters aos campos na tabela de banco de dados reais.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-175">When you use EF 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="c9f3b-176">Isso é feito com o método HasField da classe PropertyBuilder.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-176">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="c9f3b-177">Mapeamento de campos sem propriedades</span><span class="sxs-lookup"><span data-stu-id="c9f3b-177">Mapping fields without properties</span></span>

<span data-ttu-id="c9f3b-178">Com o novo recurso no EF Core 1.1 para mapear colunas para campos, também é possível usar propriedades.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-178">With the new feature in EF Core 1.1 to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="c9f3b-179">Em vez disso, você pode mapear apenas as colunas de uma tabela para campos.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-179">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="c9f3b-180">Um caso de uso comum para isso é campos privados para um estado interno que não precisam ser acessados de fora da entidade.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-180">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="c9f3b-181">Por exemplo, no exemplo de código anterior, o \_someOrderInternalState campo não tem nenhuma propriedade relacionada para um getter ou setter.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-181">For example, in the preceding code example, the \_someOrderInternalState field has no related property for either a setter or getter.</span></span> <span data-ttu-id="c9f3b-182">Esse campo também será calculado dentro de lógica de negócios da ordem e usado em métodos da ordem, mas ele precisa ser mantido no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-182">That field will also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="c9f3b-183">Portanto, no EF 1.1, há uma maneira de mapear um campo sem uma propriedade relacionada a uma coluna no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-183">So, in EF 1.1 there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="c9f3b-184">Isso também é explicado no [camada de infraestrutura](#the-infrastructure-layer) deste guia.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-184">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c9f3b-185">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c9f3b-185">Additional resources</span></span>

-   <span data-ttu-id="c9f3b-186">**Vaughn Vernon. Modelagem de agregações com DDD e Entity Framework.**</span><span class="sxs-lookup"><span data-stu-id="c9f3b-186">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="c9f3b-187">Observe que isso *não* Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="c9f3b-187">Note that this is *not* Entity Framework Core.</span></span>
    [<span data-ttu-id="c9f3b-188">*https://vaughnvernon.co/?p=879*</span><span class="sxs-lookup"><span data-stu-id="c9f3b-188">*https://vaughnvernon.co/?p=879*</span></span>](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="c9f3b-189">**Julie Lerman. Codificação por Design controlado por domínio: dicas para desenvolvedores centrados em dados**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="c9f3b-189">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="c9f3b-190">**Udi Dahan. Como criar totalmente encapsulado modelos de domínio**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="c9f3b-190">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c9f3b-191">[Anterior] (microsserviço-domínio-model.md) [Avançar] (seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="c9f3b-191">[Previous] (microservice-domain-model.md) [Next] (seedwork-domain-model-base-classes-interfaces.md)</span></span>
