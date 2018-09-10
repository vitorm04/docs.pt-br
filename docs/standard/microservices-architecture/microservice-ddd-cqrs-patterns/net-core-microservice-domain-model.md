---
title: Implementando um modelo de domínio de microsserviço com o .NET Core
description: Arquitetura de Microsserviços .NET para aplicativos .NET em contêineres | Implementação de um modelo de domínio de microsserviço com .NET Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: bb11d87cacf5bb6cbc980c879b0c42fae76f6246
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43420921"
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="b02b4-103">Implementando um modelo de domínio de microsserviço com o .NET Core</span><span class="sxs-lookup"><span data-stu-id="b02b4-103">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="b02b4-104">Na seção anterior, foram explicados os princípios de design fundamentais e os padrões para criar um modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="b02b4-104">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="b02b4-105">Agora é hora de explorar possíveis maneiras de implementar o modelo de domínio usando o .NET Core (código C\# simples) e EF Core.</span><span class="sxs-lookup"><span data-stu-id="b02b4-105">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="b02b4-106">Observe que seu modelo de domínio será composto apenas pelo seu código.</span><span class="sxs-lookup"><span data-stu-id="b02b4-106">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="b02b4-107">Ele terá apenas os requisitos do modelo EF Core, mas não reais dependências do EF.</span><span class="sxs-lookup"><span data-stu-id="b02b4-107">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="b02b4-108">Você não deve ter dependências rígidas nem referências ao EF Core ou qualquer outro ORM em seu modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="b02b4-108">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="b02b4-109">Estrutura do modelo de domínio em uma biblioteca .NET Standard personalizada</span><span class="sxs-lookup"><span data-stu-id="b02b4-109">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="b02b4-110">A organização de pastas usada para o aplicativo de referência eShopOnContainers demonstra o modelo DDD para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b02b4-110">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="b02b4-111">Você pode considerar que uma organização de pastas diferente comunica mais claramente as escolhas de design feitas para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b02b4-111">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="b02b4-112">Como você pode ver na Figura 9-10, no modelo de domínio de ordenação, há duas agregações, a agregação de ordem e a agregação de comprador.</span><span class="sxs-lookup"><span data-stu-id="b02b4-112">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="b02b4-113">Cada agregação é um grupo de entidades de domínio e objetos de valor, embora você possa ter uma agregação composta por uma única entidade de domínio (a raiz de agregação ou entidade raiz) também.</span><span class="sxs-lookup"><span data-stu-id="b02b4-113">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="b02b4-114">**Figura 9-10**.</span><span class="sxs-lookup"><span data-stu-id="b02b4-114">**Figure 9-10**.</span></span> <span data-ttu-id="b02b4-115">Estrutura de modelo de domínio para o microsserviço de ordenação em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="b02b4-115">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="b02b4-116">Além disso, a camada de modelo de domínio inclui os contratos de repositório (interfaces) que são os requisitos de infraestrutura do seu modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="b02b4-116">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="b02b4-117">Em outras palavras, essas interfaces expressam quais repositórios a camada de infraestrutura deve implementar e como.</span><span class="sxs-lookup"><span data-stu-id="b02b4-117">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="b02b4-118">É importante que a implementação dos repositórios seja colocada fora da camada de modelo de domínio, na biblioteca de camada de infraestrutura, para que a camada de modelo de domínio não seja "contaminada" pela API ou por classes de tecnologias de infraestrutura, como o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b02b4-118">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="b02b4-119">Você também pode ver uma pasta [SeedWork](https://martinfowler.com/bliki/Seedwork.html) que contém as classes base personalizadas que você pode usar como base para suas entidades de domínio e objetos de valor, portanto, você não tem código redundante em cada classe de objeto de domínio.</span><span class="sxs-lookup"><span data-stu-id="b02b4-119">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="b02b4-120">Estruturando agregações em uma biblioteca .NET Standard personalizada</span><span class="sxs-lookup"><span data-stu-id="b02b4-120">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="b02b4-121">Uma agregação refere-se a um cluster de objetos de domínio agrupados de acordo com a consistência transacional.</span><span class="sxs-lookup"><span data-stu-id="b02b4-121">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="b02b4-122">Esses objetos podem ser instâncias de entidades (uma das quais é a raiz de agregação ou uma entidade raiz) além de qualquer objeto de valor adicional.</span><span class="sxs-lookup"><span data-stu-id="b02b4-122">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="b02b4-123">Consistência transacional significa que uma agregação está garantidamente consistente e atualizada ao final de uma ação de negócios.</span><span class="sxs-lookup"><span data-stu-id="b02b4-123">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="b02b4-124">Por exemplo, a agregação de ordem do modelo de domínio de microsserviços de pedidos eShopOnContainers é composta conforme mostra a Figura 9-11.</span><span class="sxs-lookup"><span data-stu-id="b02b4-124">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="b02b4-125">**Figura 9-11**.</span><span class="sxs-lookup"><span data-stu-id="b02b4-125">**Figure 9-11**.</span></span> <span data-ttu-id="b02b4-126">A agregação de ordem na solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b02b4-126">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="b02b4-127">Se você abrir qualquer um dos arquivos em uma pasta de agregação, verá como ele está marcado como classe base personalizada ou interface, como objeto de entidade ou valor, conforme implementado na pasta [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork).</span><span class="sxs-lookup"><span data-stu-id="b02b4-127">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="b02b4-128">Implementando entidades de domínio como classes POCO</span><span class="sxs-lookup"><span data-stu-id="b02b4-128">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="b02b4-129">Você implementa um modelo de domínio no .NET criando classes POCO que implementam suas entidades de domínio.</span><span class="sxs-lookup"><span data-stu-id="b02b4-129">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="b02b4-130">No exemplo a seguir, a classe Ordem é definida como uma entidade e como uma raiz de agregação.</span><span class="sxs-lookup"><span data-stu-id="b02b4-130">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="b02b4-131">Porque a classe Ordem deriva da classe base da Entidade, ela pode reutilizar o código comum relacionado a entidades.</span><span class="sxs-lookup"><span data-stu-id="b02b4-131">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="b02b4-132">Tenha em mente que essas interfaces e classes base são definidas por você no projeto de modelo de domínio, portanto, é o seu código, não o código de infraestrutura de um ORM, como EF.</span><span class="sxs-lookup"><span data-stu-id="b02b4-132">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 2.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId;

    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    private string _description;
    private int? _paymentMethodId;

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;
  
    public Order(string userId, Address address, int cardTypeId, string cardNumber, string cardSecurityNumber,
            string cardHolderName, DateTime cardExpiration, int? buyerId = null, int? paymentMethodId = null)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.Submitted.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;

        // ...Additional code ...
    }

    public void AddOrderItem(int productId, string productName, 
                            decimal unitPrice, decimal discount, 
                            string pictureUrl, int units = 1)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...

        var orderItem = new OrderItem(productId, productName, unitPrice, discount, pictureUrl, units);
        
        _orderItems.Add(orderItem);
  
    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

<span data-ttu-id="b02b4-133">É importante observar que essa é uma entidade de domínio implementada como uma classe POCO.</span><span class="sxs-lookup"><span data-stu-id="b02b4-133">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="b02b4-134">Ela não tem nenhuma dependência direta do Entity Framework Core nem qualquer outra estrutura de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="b02b4-134">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="b02b4-135">Essa implementação é como deve ser em DDD, apenas código C\# implementando um modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="b02b4-135">This implementation is as it should be in DDD, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="b02b4-136">Além disso, a classe é decorada com uma interface denominada IAggregateRoot.</span><span class="sxs-lookup"><span data-stu-id="b02b4-136">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="b02b4-137">Essa interface é uma interface vazia, às vezes chamada de uma *interface de marcador*, que é usada apenas para indicar que essa classe de entidade também é uma raiz de agregação.</span><span class="sxs-lookup"><span data-stu-id="b02b4-137">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="b02b4-138">Uma interface de marcador às vezes é considerada como um antipadrão; no entanto, também é uma maneira simples de marcar uma classe, especialmente quando essa interface pode estar em evolução.</span><span class="sxs-lookup"><span data-stu-id="b02b4-138">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="b02b4-139">Um atributo pode ser outra escolha para o marcador, mas é mais rápido ver a classe base (Entity) ao lado da interface IAggregate, em vez de colocar um marcador de atributo Aggregate acima da classe.</span><span class="sxs-lookup"><span data-stu-id="b02b4-139">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="b02b4-140">É uma questão de preferências, de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="b02b4-140">It is a matter of preferences, in any case.</span></span>

<span data-ttu-id="b02b4-141">Ter um meio de raiz de agregação significa que a maioria do código relacionado à consistência e a regras de negócio das entidades da agregação deve ser implementada como métodos na classe raiz agregada de Ordem (por exemplo, AddOrderItem ao adicionar um objeto OrderItem à agregação).</span><span class="sxs-lookup"><span data-stu-id="b02b4-141">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="b02b4-142">Você não deve criar nem atualizar objetos OrderItems de modo independente ou direto; a classe AggregateRoot deve manter o controle e a consistência de qualquer operação de atualização com relação às suas entidades filho.</span><span class="sxs-lookup"><span data-stu-id="b02b4-142">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

## <a name="encapsulating-data-in-the-domain-entities"></a><span data-ttu-id="b02b4-143">Encapsulando dados nas Entidades de Domínio</span><span class="sxs-lookup"><span data-stu-id="b02b4-143">Encapsulating data in the Domain Entities</span></span>

<span data-ttu-id="b02b4-144">Um problema comum em modelos de entidade é que eles expõem propriedades de navegação da coleção como tipos de lista publicamente acessíveis.</span><span class="sxs-lookup"><span data-stu-id="b02b4-144">A common problem in entity models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="b02b4-145">Isso permite que qualquer desenvolvedor do colaborador manipule o conteúdo desses tipos de coleção, o que pode ignorar importantes regras de negócio relacionadas à coleção, possivelmente deixando o objeto em um estado inválido.</span><span class="sxs-lookup"><span data-stu-id="b02b4-145">This allows any collaborator developer to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="b02b4-146">A solução para isso é expor o acesso somente leitura a coleções relacionadas e fornecer explicitamente métodos que definem maneiras como os clientes podem manipulá-los.</span><span class="sxs-lookup"><span data-stu-id="b02b4-146">The solution to this is to expose read-only access to related collections and explicitly provide methods that define ways in which clients can manipulate them.</span></span>

<span data-ttu-id="b02b4-147">No código anterior, observe que muitos atributos são somente leitura ou privados e só são atualizáveis pelos métodos de classe, assim, qualquer atualização leva em conta invariáveis de domínio de negócio da conta e lógica especificada dentro do método de classe.</span><span class="sxs-lookup"><span data-stu-id="b02b4-147">In the previous code, note that many attributes are read-only or private and are only updatable by the class methods, so any update takes into account business domain invariants and logic specified within the class methods.</span></span>

<span data-ttu-id="b02b4-148">Por exemplo, após os padrões DDD, você *não* deve fazer o seguinte de nenhum método de manipulador de comando ou classe de camada de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b02b4-148">For example, following DDD patterns, you should *not* do the following from any command handler method or application layer class:</span></span>

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

<span data-ttu-id="b02b4-149">Neste caso, o método Add é meramente uma operação para adicionar dados, com acesso direto à coleção OrderItems.</span><span class="sxs-lookup"><span data-stu-id="b02b4-149">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="b02b4-150">Portanto, a maioria da lógica, das regras ou das validações de domínio relacionada àquela operação com as entidades filho será espalhada pela camada de aplicativo (manipuladores de comandos e controladores de API da Web).</span><span class="sxs-lookup"><span data-stu-id="b02b4-150">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="b02b4-151">Se você usar uma solução alternativa para a raiz de agregação, a raiz de agregação não assegurará suas invariáveis, sua validade nem sua consistência.</span><span class="sxs-lookup"><span data-stu-id="b02b4-151">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="b02b4-152">Por fim, você terá código espaguete ou código de script transacional.</span><span class="sxs-lookup"><span data-stu-id="b02b4-152">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="b02b4-153">Para seguir padrões DDD, as entidades não devem ter setters públicos em nenhuma propriedade de entidade.</span><span class="sxs-lookup"><span data-stu-id="b02b4-153">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="b02b4-154">Alterações em uma entidade devem ser controladas pelos métodos explícitos com linguagem ubíqua explícita sobre a alteração que estão sendo executadas na entidade.</span><span class="sxs-lookup"><span data-stu-id="b02b4-154">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="b02b4-155">Além disso, coleções na entidade (como os itens do pedido) devem ser propriedades somente leitura (o método AsReadOnly explicado posteriormente).</span><span class="sxs-lookup"><span data-stu-id="b02b4-155">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="b02b4-156">Você deve ser capaz de atualizá-lo somente de dentro de métodos da classe raiz agregada ou de métodos de entidade filho.</span><span class="sxs-lookup"><span data-stu-id="b02b4-156">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="b02b4-157">Como você pode ver no código para a raiz de agregação de ordem, todos os setters devem ser privados ou, pelo menos, somente leitura externamente, de modo que qualquer operação contra os dados da entidade ou entidades seu filho deve ser executada por meio dos métodos na classe de entidade.</span><span class="sxs-lookup"><span data-stu-id="b02b4-157">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="b02b4-158">Isso mantém a consistência de maneira controlada e orientada a objeto, em vez de implementar o código de script transacional.</span><span class="sxs-lookup"><span data-stu-id="b02b4-158">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="b02b4-159">O trecho de código a seguir mostra a maneira adequada de codificar a tarefa de adicionar um objeto OrderItem para a agregação de ordem de código.</span><span class="sxs-lookup"><span data-stu-id="b02b4-159">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="b02b4-160">Neste trecho de código, a maioria das validações ou da lógica relacionada à criação de um objeto OrderItem estará sob o controle da raiz de agregação de Ordem (no método AddOrderItem), especialmente validações e lógica relacionadas a outros elementos no agregado.</span><span class="sxs-lookup"><span data-stu-id="b02b4-160">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="b02b4-161">Por exemplo, você pode obter o mesmo item de produto como resultado de várias chamadas para AddOrderItem.</span><span class="sxs-lookup"><span data-stu-id="b02b4-161">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="b02b4-162">Nesse método, você pode examinar os itens de produto e consolidar os mesmos itens de produto em um único objeto OrderItem com várias unidades.</span><span class="sxs-lookup"><span data-stu-id="b02b4-162">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="b02b4-163">Além disso, se houver valores de desconto diferentes, mas a ID do produto (product ID) for a mesma, você provavelmente aplicará o desconto maior.</span><span class="sxs-lookup"><span data-stu-id="b02b4-163">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="b02b4-164">Esse princípio se aplica a qualquer outra lógica do domínio para o objeto OrderItem.</span><span class="sxs-lookup"><span data-stu-id="b02b4-164">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="b02b4-165">Além disso, a nova operação OrderItem(params) também será controlada e executada pelo método AddOrderItem da raiz de agregação de Ordem.</span><span class="sxs-lookup"><span data-stu-id="b02b4-165">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="b02b4-166">Portanto, a maioria da lógica ou das validações relacionadas àquela operação (especialmente tudo o que afeta a consistência entre outras entidades filho) estará em um único lugar na raiz da agregação.</span><span class="sxs-lookup"><span data-stu-id="b02b4-166">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="b02b4-167">Esta é a principal finalidade do padrão de raiz de agregação.</span><span class="sxs-lookup"><span data-stu-id="b02b4-167">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="b02b4-168">Quando você usar o Entity Framework Core 1.1 ou posterior, uma entidade DDD pode ser melhor expressada porque ela permite [mapear para os campos](https://docs.microsoft.com/ef/core/modeling/backing-field) além das propriedades.</span><span class="sxs-lookup"><span data-stu-id="b02b4-168">When you use Entity Framework Core 1.1 or later, a DDD entity can be better expressed because it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="b02b4-169">Isso é útil ao proteger as coleções de entidades filho ou objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="b02b4-169">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="b02b4-170">Com esse aprimoramento, você pode usar os campos privados, em vez das propriedades, e pode implementar qualquer atualização à coleção de campo nos métodos públicos e fornecer acesso somente leitura por meio do método AsReadOnly.</span><span class="sxs-lookup"><span data-stu-id="b02b4-170">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="b02b4-171">No DDD, você deseja atualizar a entidade somente por meio de métodos na entidade (ou no construtor) para controlar qualquer invariável e a consistência dos dados, portanto, as propriedades são definidas somente com um acessador get.</span><span class="sxs-lookup"><span data-stu-id="b02b4-171">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="b02b4-172">As propriedades têm o respaldo de campos privados.</span><span class="sxs-lookup"><span data-stu-id="b02b4-172">The properties are backed by private fields.</span></span> <span data-ttu-id="b02b4-173">Membros privados só pode ser acessados de dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="b02b4-173">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="b02b4-174">No entanto, há uma exceção: o EF Core precisa definir esses campos também.</span><span class="sxs-lookup"><span data-stu-id="b02b4-174">However, there one exception: EF Core needs to set these fields as well.</span></span>


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="b02b4-175">Mapeamento de propriedades com apenas acessadores get para os campos na tabela de banco de dados</span><span class="sxs-lookup"><span data-stu-id="b02b4-175">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="b02b4-176">Mapeamento de propriedades para colunas de tabela do banco de dados não é uma responsabilidade do domínio, mas parte da camada de infraestrutura e persistência.</span><span class="sxs-lookup"><span data-stu-id="b02b4-176">Mapping properties to database table columns is not a domain responsibility but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="b02b4-177">Mencionamos isso aqui apenas para que você esteja ciente das novas funcionalidades no EF Core 1.1 ou posterior relacionadas a como você pode modelar entidades.</span><span class="sxs-lookup"><span data-stu-id="b02b4-177">We mention this here just so you are aware of the new capabilities in EF Core 1.1 or later related to how you can model entities.</span></span> <span data-ttu-id="b02b4-178">Detalhes adicionais sobre este tópico são explicados na seção de infraestrutura e persistência.</span><span class="sxs-lookup"><span data-stu-id="b02b4-178">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="b02b4-179">Quando você usa EF Core 1.0, no DbContext, precisa mapear as propriedades definidas somente com getters para os campos reais na tabela de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b02b4-179">When you use EF Core 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="b02b4-180">Isso é feito com o método HasField da classe PropertyBuilder.</span><span class="sxs-lookup"><span data-stu-id="b02b4-180">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="b02b4-181">Mapeamento de campos sem propriedades</span><span class="sxs-lookup"><span data-stu-id="b02b4-181">Mapping fields without properties</span></span>

<span data-ttu-id="b02b4-182">Com o recurso no EF Core 1.1 ou posterior para mapear colunas para campos, também é possível não usar propriedades.</span><span class="sxs-lookup"><span data-stu-id="b02b4-182">With the feature in EF Core 1.1 or later to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="b02b4-183">Em vez disso, você pode apenas mapear as colunas de uma tabela para campos.</span><span class="sxs-lookup"><span data-stu-id="b02b4-183">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="b02b4-184">Um caso de uso comum para isso são campos privados para um estado interno que não precisam ser acessados de fora da entidade.</span><span class="sxs-lookup"><span data-stu-id="b02b4-184">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="b02b4-185">Por exemplo, no exemplo de código anterior, OrderAggregate, há vários campos privados, como o campo `_paymentMethodId`, que não têm nenhuma propriedade relacionada para um setter ou um getter.</span><span class="sxs-lookup"><span data-stu-id="b02b4-185">For example, in the preceding OrderAggregate code example, there are several private fields, like the  `_paymentMethodId` field, that have no related property for either a setter or getter.</span></span> <span data-ttu-id="b02b4-186">Esse campo também poderia ser calculado dentro da lógica de negócios da ordem e usado em métodos da ordem, mas precisa ser mantido no banco de dados também.</span><span class="sxs-lookup"><span data-stu-id="b02b4-186">That field could also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="b02b4-187">Assim, no EF Core (desde a v1.1), existe uma maneira de mapear um campo sem uma propriedade relacionada a uma coluna no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b02b4-187">So in EF Core (since v1.1) there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="b02b4-188">Isso também é explicado na seção [Camada de infraestrutura](#the-infrastructure-layer) deste guia.</span><span class="sxs-lookup"><span data-stu-id="b02b4-188">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b02b4-189">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b02b4-189">Additional resources</span></span>

-   <span data-ttu-id="b02b4-190">**Vaughn Vernon. Modelagem de agregações com DDD e Entity Framework.**</span><span class="sxs-lookup"><span data-stu-id="b02b4-190">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="b02b4-191">Observe que este *não* é um Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="b02b4-191">Note that this is *not* Entity Framework Core.</span></span>
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="b02b4-192">**Julie Lerman. Codificação para o Design Controlado por Domínio: dicas para desenvolvedores centrados em dados**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="b02b4-192">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="b02b4-193">**Udi Dahan. Como criar modelos de domínio totalmente encapsulados**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="b02b4-193">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b02b4-194">[Anterior](microservice-domain-model.md)
[Próximo](seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="b02b4-194">[Previous](microservice-domain-model.md)
[Next](seedwork-domain-model-base-classes-interfaces.md)</span></span>
