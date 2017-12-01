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
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>Implementação de um modelo de domínio de microsserviço com .NET Core 

Na seção anterior, foram explicados os princípios de design fundamental e padrões para criar um modelo de domínio. Agora é hora de explorar possíveis maneiras de implementar o modelo de domínio usando o .NET Core (C simples\# código) e EF Core. Observe que seu modelo de domínio será ser composto apenas de seu código. Ele terá apenas a requisitos do modelo EF principal, mas não reais dependências no EF. Você não deve ter dependências de disco rígidas ou referências a EF principal ou qualquer outro ORM em seu modelo de domínio.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Estrutura do modelo de domínio em uma biblioteca .NET padrão personalizada

A organização de pastas usada para o aplicativo de referência eShopOnContainers demonstra o modelo DDD para o aplicativo. Você pode achar que uma organização de pastas diferente comunica mais claramente as escolhas de design feitas para o seu aplicativo. Como você pode ver na Figura 9-10, no modelo de domínio ordenação há duas agregações, a agregação de ordem e a agregação de compradores. Cada agregação é um grupo de entidades de domínio e objetos de valor, embora você poderia ter uma agregação composta de uma entidade de domínio único (a raiz de agregação ou entidade raiz) também.

![](./media/image11.png)

**Figura 9-10**. Estrutura de modelo de domínio para o pedido microsserviço em eShopOnContainers

Além disso, a camada de modelo de domínio inclui os contratos de repositório (interfaces) que são os requisitos de infraestrutura do seu modelo de domínio. Em outras palavras, essas interfaces express quais repositórios deve implementar a camada de infraestrutura e como. É importante que a implementação dos repositórios colocados fora da camada de modelo de domínio, na biblioteca de camada de infraestrutura, para a camada de modelo de domínio não é "contaminação" pela API ou classes de tecnologias de infraestrutura, como o Entity Framework.

Você também pode ver um [SeedWork](https://martinfowler.com/bliki/Seedwork.html) objetos pasta que contém as classes de base personalizadas que você pode usar como base para suas entidades de domínio e o valor, portanto você não tem código redundante na classe de objeto de cada domínio.

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>Estruturar agregações em uma biblioteca .NET padrão personalizada

Uma agregação refere-se a um cluster de objetos de domínio agrupados de acordo com a consistência transacional. Esses objetos podem ser instâncias de entidades (um dos quais é o raiz de agregação ou uma entidade raiz) além de qualquer objeto de valor adicional.

Consistência transacional significa que uma agregação é garantida para ser consistente e atualizado ao final de uma ação de negócios. Por exemplo, a agregação de ordem do eShopOnContainers ordenação microsserviço modelo de domínio é composta conforme mostrado na Figura 9-11.

![](./media/image12.png)

**Figura 9-11**. A ordem de agregação na solução do Visual Studio

Se você abrir qualquer um dos arquivos em uma pasta de agregação, você pode ver como ele está marcado como uma classe base personalizada ou uma interface, como objeto de entidade ou um valor, conforme implementado o [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) pasta.

## <a name="implementing-domain-entities-as-poco-classes"></a>Implementação de entidades de domínio como classes POCO

Você pode implementar um modelo de domínio no .NET criando classes POCO que implementam as entidades de domínio. No exemplo a seguir, a classe de ordem é definida como uma entidade e como uma raiz de agregação. Porque a classe de ordem deriva da classe base da entidade, ele pode reutilizar o código comuns relacionado a entidades. Tenha em mente que essas interfaces e classes base são definidas por você no projeto de modelo de domínio, portanto, é o seu código, não o código de infraestrutura de um ORM como EF.

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

É importante observar que isso é implementada como uma classe POCO uma entidade de domínio. Ele não tem nenhuma dependência direta do Entity Framework Core ou qualquer outra estrutura de infraestrutura. Essa implementação é como ele deve ser, apenas C\# código que implementa um modelo de domínio.

Além disso, a classe é decorada com uma interface denominada IAggregateRoot. Essa interface é uma interface vazia, às vezes chamada de um *interface de marcador*, que é usado apenas para indicar que esta classe de entidade também é uma raiz de agregação.

Uma interface de marcador, às vezes, é considerada como um anti padrão de; No entanto, também é uma maneira simples para marcar uma classe, especialmente quando essa interface pode ser em evolução. Um atributo pode ser outra escolha para o marcador, mas é mais rápido ver a classe base (entidades) ao lado da interface do IAggregate em vez de colocar um marcador de atributo de agregação acima da classe. É um metter de preferências, de qualquer forma.

Ter um meio de raiz de agregação que a maioria do código relacionada a consistência e regras de negócio de entidades da agregação devem ser implementadas como métodos na classe de raiz agregada de ordem (por exemplo, AddOrderItem ao adicionar um objeto ItemPedido à agregação) . Você não deve criar ou atualizar objetos OrderItems independentemente ou diretamente. a classe AggregateRoot deve manter o controle e a consistência de qualquer operação de atualização com as entidades filhas.

Por exemplo, você deverá *não* faça o seguinte de qualquer comando manipulador método ou aplicativo de camada da classe:

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

Nesse caso, o método Add é meramente uma operação para adicionar dados, com acesso direto à coleção OrderItems. Portanto, a maioria da lógica do domínio, regras ou validações relacionada ao que a operação com as entidades filhas será espalhada pela camada de aplicativo (manipuladores de comandos e controladores de API da Web).

Se você for uma solução alternativa para a raiz de agregação, a raiz de agregação não pode garantir suas invariáveis, sua validade ou sua consistência. Finalmente, você terá código espaguete ou código de script transacional.

Para seguir padrões DDD, entidades não devem ter setters públicas em qualquer propriedade de entidade. Alterações em uma entidade devem ser controlada pelos métodos explícitos com idioma onipresente explícito sobre a alteração que sendo executada na entidade.

Além disso, coleções dentro da entidade (como os itens do pedido) devem ser propriedades somente leitura (o método AsReadOnly explicado posteriormente). Você deve ser capaz de atualizá-lo somente de dentro de métodos da classe raiz agregada ou os métodos de entidade filho.

Como você pode ver no código para a raiz de agregação de ordem, todos os setters devem ser privada ou, pelo menos, somente leitura externamente, para que qualquer operação de dados da entidade ou entidades seu filho deve ser executada por meio dos métodos na classe de entidade. Isso mantém a consistência de forma controlada e orientada a objeto, em vez de implementar o código de script transacional.

O trecho de código a seguir mostra o modo adequado para a tarefa de adicionar um objeto ItemPedido para a agregação de ordem de código.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

Este trecho de código, a maioria da lógica relacionada à criação de um objeto ItemPedido ou validações serão sob o controle da raiz de agregação de ordem — no método AddOrderItem — especialmente validações e lógica relacionam a outros elementos em conjunto. Por exemplo, você pode obter o mesmo item de produto como o resultado de várias chamadas para AddOrderItem. Nesse método, você pode examinar os itens de produto e consolidar os mesmos itens de produto em um único objeto ItemPedido com várias unidades. Além disso, se há valores de desconto diferente, mas a ID do produto é o mesmo, você provavelmente seria aplicar o desconto mais alto. Esse princípio se aplica a qualquer outra lógica do domínio para o objeto ItemPedido.

Além disso, a nova operação de OrderItem(params) também ser controlada e executada pelo método AddOrderItem da raiz de agregação de ordem. Portanto, a maioria da lógica ou validações relacionada ao que a operação (especialmente tudo o que afeta a consistência entre outras entidades filho) será em um único lugar na raiz da agregação. Que é a principal finalidade do padrão de raiz de agregação.

Quando você usar o Entity Framework 1.1, uma entidade DDD pode ser expressada melhor porque um dos novos recursos do Entity Framework Core 1.1 é que ele permite [mapear para os campos](https://docs.microsoft.com/ef/core/modeling/backing-field) além das propriedades. Isso é útil ao proteger as coleções de entidades filho ou objetos de valor. Com esse aprimoramento, você pode usar os campos particulares simples em vez de propriedades e você pode implementar qualquer atualização para a coleção de campos em métodos públicos e fornecer acesso somente leitura por meio do método AsReadOnly.

No DDD para atualizar a entidade por meio de métodos de entidade (ou o construtor) para controlar qualquer invariável e a consistência dos dados, portanto propriedades são definidas somente com um acessador get. As propriedades têm o respaldo campos particulares. Membros particulares só pode ser acessados de dentro da classe. No entanto, exceção lá um: EF Core precisa definir esses campos também.

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

### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Mapeamento de propriedades com apenas obtém acessadores para os campos na tabela de banco de dados

Mapeamento de propriedades para as colunas da tabela de banco de dados não é a responsabilidade de domínio, mas a parte da camada de infraestrutura e de persistência. Mencionamos essa aqui apenas para que você está ciente das novas funcionalidades no EF 1.1 relacionadas a como você pode modelar entidades. Detalhes adicionais sobre este tópico são explicados na seção de infraestrutura e de persistência.

Quando você usa EF 1.0, no DbContext você precisa mapear as propriedades que são definidas somente com getters aos campos na tabela de banco de dados reais. Isso é feito com o método HasField da classe PropertyBuilder.

### <a name="mapping-fields-without-properties"></a>Mapeamento de campos sem propriedades

Com o novo recurso no EF Core 1.1 para mapear colunas para campos, também é possível usar propriedades. Em vez disso, você pode mapear apenas as colunas de uma tabela para campos. Um caso de uso comum para isso é campos privados para um estado interno que não precisam ser acessados de fora da entidade.

Por exemplo, no exemplo de código anterior, o \_someOrderInternalState campo não tem nenhuma propriedade relacionada para um getter ou setter. Esse campo também será calculado dentro de lógica de negócios da ordem e usado em métodos da ordem, mas ele precisa ser mantido no banco de dados. Portanto, no EF 1.1, há uma maneira de mapear um campo sem uma propriedade relacionada a uma coluna no banco de dados. Isso também é explicado no [camada de infraestrutura](#the-infrastructure-layer) deste guia.

### <a name="additional-resources"></a>Recursos adicionais

-   **Vaughn Vernon. Modelagem de agregações com DDD e Entity Framework.** Observe que isso *não* Entity Framework Core.
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman. Codificação por Design controlado por domínio: dicas para desenvolvedores centrados em dados**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **Udi Dahan. Como criar totalmente encapsulado modelos de domínio**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[Anterior] (microsserviço-domínio-model.md) [Avançar] (seedwork-domain-model-base-classes-interfaces.md)
