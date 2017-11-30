---
title: "Implementando a camada de aplicativo de microsserviço usando a API da Web"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementando a camada de aplicativo de microsserviço usando a API da Web"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="f7ff6-104">Implementando a camada de aplicativo de microsserviço usando a API da Web</span><span class="sxs-lookup"><span data-stu-id="f7ff6-104">Implementing the microservice application layer using the Web API</span></span>

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="f7ff6-105">Usando a injeção de dependência para injetar objetos de infraestrutura em sua camada de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f7ff6-105">Using Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="f7ff6-106">Conforme mencionado anteriormente, a camada de aplicativo pode ser implementada como parte do artefato que você está criando, tal como em um projeto de API da Web ou um projeto de aplicativo web MVC.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-106">As mentioned previously, the application layer can be implemented as part of the artifact you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="f7ff6-107">No caso de um microsserviço criado com o ASP.NET Core, a camada de aplicativo geralmente será a sua biblioteca de API da Web.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-107">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="f7ff6-108">Se você quiser separar quais são as novidades do ASP.NET Core (sua infraestrutura e os controladores) do seu código da camada de aplicativo personalizado, você também pode colocar sua camada de aplicativo em uma biblioteca de classe separada, mas que é opcional.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-108">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="f7ff6-109">Por exemplo, o código da camada de aplicativo de microsserviço a ordenação diretamente é implementado como parte do **Ordering.API** projeto (um projeto de API da Web do ASP.NET Core), como mostrado na Figura 9 19.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-109">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 9-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="f7ff6-110">**Figura 9-19**.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-110">**Figure 9-19**.</span></span> <span data-ttu-id="f7ff6-111">A camada de aplicativo no projeto de API da Web do Ordering.API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f7ff6-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="f7ff6-112">ASP.NET Core inclui um simples [contêiner interno de IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (representado pela interface IServiceProvider) que dá suporte a injeção de construtor por padrão, e ASP.NET disponibiliza por meio de DI determinados serviços.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="f7ff6-113">ASP.NET Core usa o termo *service* para qualquer um dos tipos que serão injetados pelo DI registrar.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="f7ff6-114">Configure os serviços do contêiner interno no método ConfigureServices na classe de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="f7ff6-115">As dependências são implementadas nos serviços de que precisa de um tipo.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-115">Your dependencies are implemented in the services that a type needs.</span></span>

<span data-ttu-id="f7ff6-116">Normalmente, você deseja injetar dependências que implementam os objetos de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="f7ff6-117">Uma dependência muito comum para injetar é um repositório.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="f7ff6-118">Mas você pode injetar qualquer outra dependência de infraestrutura que você pode ter.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="f7ff6-119">Para implementações mais simples, você poderia inserir diretamente o objeto de padrão de unidade de trabalho (o objeto EF DbContext), porque o DBContext também é a implementação de seus objetos de persistência de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="f7ff6-120">No exemplo a seguir, você pode ver como o .NET Core está injetando os objetos de repositório necessárias por meio do construtor.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="f7ff6-121">A classe é um manipulador de comando, o que abordaremos na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-121">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

<span data-ttu-id="f7ff6-122">A classe usa os repositórios injetados para executar a transação e manter as alterações de estado.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="f7ff6-123">Não importa se a classe é um manipulador de comandos, um método de controlador de API da Web do ASP.NET Core, ou uma [o serviço de aplicativo DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="f7ff6-124">Por fim, é uma classe simples que usa os repositórios, entidades de domínio e a coordenação de outros aplicativos de forma semelhante a um manipulador de comandos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="f7ff6-125">Injeção de dependência funciona da mesma forma para todas as classes mencionadas, como no exemplo usando a injeção de dependência com base no construtor.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="f7ff6-126">Registrando tipos de implementação de dependência e interfaces ou abstrações</span><span class="sxs-lookup"><span data-stu-id="f7ff6-126">Registering the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="f7ff6-127">Antes de usar os objetos injetados por meio de construtores, você precisa saber onde se registrar as interfaces e classes que geram os objetos injetados suas classes de aplicativo por meio de injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="f7ff6-128">(Como DI baseado no construtor, conforme mostrado anteriormente.)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="f7ff6-129">Usando o contêiner IoC interno fornecido pelo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f7ff6-129">Using the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="f7ff6-130">Quando você usa o contêiner IoC interno fornecido pelo ASP.NET Core, você pode registrar os tipos que você deseja inserir no método ConfigureServices no arquivo Startup.cs, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="f7ff6-131">O padrão mais comum quando registrar tipos em um contêiner IoC é registrar um par de tipos — uma interface e sua classe de implementação relacionada.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="f7ff6-132">Em seguida, quando você solicitar um objeto de contêiner IoC por meio de nenhum construtor, você solicitar um objeto de um determinado tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="f7ff6-133">Por exemplo, no exemplo anterior, a última linha indica que, quando qualquer um dos seus construtores tem uma dependência no IMyCustomRepository (interface ou abstração), o contêiner IoC será injetar uma instância da implementação MyCustomSQLServerRepository classe.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="f7ff6-134">Usando a biblioteca de Scrutor para registro automático de tipos</span><span class="sxs-lookup"><span data-stu-id="f7ff6-134">Using the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="f7ff6-135">Ao usar a DI no núcleo do .NET, você talvez queira ser capaz de verificar um assembly e registrar automaticamente seus tipos por convenção.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="f7ff6-136">Este recurso não está disponível atualmente no núcleo do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="f7ff6-137">No entanto, você pode usar o [Scrutor](https://github.com/khellang/Scrutor) biblioteca para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="f7ff6-138">Essa abordagem é conveniente quando você tem dúzias de tipos que precisam ser registrados em seu contêiner IoC.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f7ff6-139">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f7ff6-139">Additional resources</span></span>

-   <span data-ttu-id="f7ff6-140">**Matthew rei. Registrando serviços Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-140">**Matthew King. Registering services with Scrutor**
[*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span></span>

<!-- -->

-   <span data-ttu-id="f7ff6-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="f7ff6-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="f7ff6-142">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-142">GitHub repo.</span></span>
    [<span data-ttu-id="f7ff6-143">*https://GitHub.com/khellang/Scrutor*</span><span class="sxs-lookup"><span data-stu-id="f7ff6-143">*https://github.com/khellang/Scrutor*</span></span>](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a><span data-ttu-id="f7ff6-144">Usando Autofac como um contêiner IoC</span><span class="sxs-lookup"><span data-stu-id="f7ff6-144">Using Autofac as an IoC container</span></span>

<span data-ttu-id="f7ff6-145">Você também pode usar contêineres de IoC adicionais e conectá-los no pipeline do ASP.NET Core, como o ordenação microsserviço em eShopOnContainers, que usa [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="f7ff6-146">Ao usar Autofac normalmente registrar tipos por meio de módulos, que permitem dividir os tipos de registro entre vários arquivos, dependendo de onde seus tipos são, exatamente como você pode ter os tipos de aplicativos distribuídos em várias bibliotecas de classe.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="f7ff6-147">Por exemplo, o seguinte é o [módulo de aplicativo Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) para o [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projeto com os tipos que você pode inserir.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule
    :Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="f7ff6-148">O processo de registro e os conceitos são muito semelhantes à forma como você pode registrar tipos com o contêiner de iOS interno do ASP.NET Core, mas a sintaxe ao usar Autofac é um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core iOS container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="f7ff6-149">No código de exemplo, a abstração IOrderRepository é registrada junto com a classe de implementação OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="f7ff6-150">Isso significa que sempre que um construtor está declarando uma dependência por meio de abstração IOrderRepository ou interface, o contêiner IoC será injetar uma instância da classe OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="f7ff6-151">O tipo de escopo de instância determina como uma instância é compartilhada entre as solicitações para o mesmo serviço ou dependência.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="f7ff6-152">Quando uma solicitação é feita em uma dependência, o contêiner IoC pode retornar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

-   <span data-ttu-id="f7ff6-153">Uma única instância por escopo de tempo de vida (conhecido no contêiner do ASP.NET Core IoC como *escopo*).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

-   <span data-ttu-id="f7ff6-154">Uma nova instância por dependência (conhecido no contêiner do ASP.NET Core IoC como *transitório*).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

-   <span data-ttu-id="f7ff6-155">Uma única instância compartilhada entre todos os objetos usando o contêiner IoC (conhecido no contêiner do ASP.NET Core IoC como *singleton*).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f7ff6-156">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f7ff6-156">Additional resources</span></span>

-   <span data-ttu-id="f7ff6-157">**Introdução a injeção de dependência no núcleo do ASP.NET**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-157">**Introduction to Dependency Injection in ASP.NET Core**
[*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span></span>

-   <span data-ttu-id="f7ff6-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="f7ff6-158">**Autofac.**</span></span> <span data-ttu-id="f7ff6-159">Documentação oficial.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-159">Official documentation.</span></span>
    [<span data-ttu-id="f7ff6-160">*http://docs.autofac.org/en/Latest/*</span><span class="sxs-lookup"><span data-stu-id="f7ff6-160">*http://docs.autofac.org/en/latest/*</span></span>](http://docs.autofac.org/en/latest/)

-   <span data-ttu-id="f7ff6-161">**Cesar de la Torre. Comparando os tempos de vida do serviço de contêiner de ASP.NET Core IoC com escopos de instância de contêiner IoC Autofac**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IoC-Service-Life-Times-and-autofac-IoC-Instance-Scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-161">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="implementing-the-command-and-command-handler-patterns"></a><span data-ttu-id="f7ff6-162">Implementar os padrões de comando e o manipulador de comandos</span><span class="sxs-lookup"><span data-stu-id="f7ff6-162">Implementing the Command and Command Handler patterns</span></span>

<span data-ttu-id="f7ff6-163">No exemplo DI pelo construtor mostrado na seção anterior, o contêiner IoC foi injetando repositórios por meio de um construtor em uma classe.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="f7ff6-164">Mas exatamente onde foram eles injetado?</span><span class="sxs-lookup"><span data-stu-id="f7ff6-164">But exactly where were they injected?</span></span> <span data-ttu-id="f7ff6-165">Em uma API simples da Web (por exemplo, o catálogo de microsserviço em eShopOnContainers), colocá-los no nível de controladores MVC, em um construtor de controlador.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers level, in a controller constructor.</span></span> <span data-ttu-id="f7ff6-166">No entanto, no código inicial desta seção (o [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) classe do serviço de Ordering.API no eShopOnContainers), a injeção de dependências é feita por meio do construtor de um comando específico manipulador.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="f7ff6-167">Vamos explicar o que um manipulador de comando é e por que você deseja usá-lo.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="f7ff6-168">O padrão de comando intrinsecamente está relacionado ao padrão CQRS apresentada neste guia.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="f7ff6-169">CQRS tem dois lados.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-169">CQRS has two sides.</span></span> <span data-ttu-id="f7ff6-170">A primeira área é consultas, usando consultas simplificadas com o [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, o que foi explicado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="f7ff6-171">A segunda área é comandos, que são o ponto de partida para transações e o canal de entrada de fora do serviço.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="f7ff6-172">Conforme mostrado na Figura 9-20, o padrão é baseado em aceitar comandos do lado do cliente, processá-las com base nas regras do modelo de domínio e, por fim, manter os estados com transações.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-172">As shown in Figure 9-20, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![](./media/image21.png)

<span data-ttu-id="f7ff6-173">**Figura 9-20**.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-173">**Figure 9-20**.</span></span> <span data-ttu-id="f7ff6-174">Exibição de alto nível dos comandos ou "lado transacional" em um padrão CQRS</span><span class="sxs-lookup"><span data-stu-id="f7ff6-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="f7ff6-175">A classe de comando</span><span class="sxs-lookup"><span data-stu-id="f7ff6-175">The command class</span></span>

<span data-ttu-id="f7ff6-176">Um comando é uma solicitação para o sistema executar uma ação que altera o estado do sistema.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="f7ff6-177">Comandos são obrigatório e devem ser processados apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="f7ff6-178">Como os comandos são obrigações, geralmente são nomeados com um verbo disposto obrigatório (por exemplo, "criar" ou "atualização") e elas podem incluir o tipo de agregação, como CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="f7ff6-179">Ao contrário de um evento, um comando não é um fato do passado; ele é apenas uma solicitação e, portanto, pode ser recusado.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="f7ff6-180">Comandos podem ser obtidos de interface do usuário como resultado de um usuário que inicia uma solicitação ou de um Gerenciador de processo quando o Gerenciador de processo é direcionar uma agregação para executar uma ação.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="f7ff6-181">Uma característica importante de um comando é que ele deve ser processado apenas uma vez por um único destinatário.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="f7ff6-182">Isso ocorre porque um comando é uma ação única ou uma transação que você deseja executar no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="f7ff6-183">Por exemplo, o mesmo comando de criação de ordem não deve ser processado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="f7ff6-184">Isso é uma importante diferença entre os comandos e eventos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="f7ff6-185">Eventos podem ser processados várias vezes, porque muitos sistemas ou microservices pode estar interessado no evento.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="f7ff6-186">Além disso, é importante que um comando seja processada apenas uma vez caso o comando não é idempotente.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="f7ff6-187">Um comando é idempotente, se ele pode ser executado várias vezes sem alterar o resultado, devido à natureza do comando ou por causa da forma que o sistema manipula o comando.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="f7ff6-188">Ele é uma boa prática fazer seus comandos e atualiza idempotente quando faz sentido em regras de negócios do seu domínio e invariáveis.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="f7ff6-189">Por exemplo, para usar o mesmo exemplo, se por algum motivo (lógica de repetição, hackers, etc.) o mesmo comando CreateOrder atingir seu sistema várias vezes, você deve ser capaz de identificá-lo e certifique-se de que você não crie vários pedidos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="f7ff6-190">Para fazer isso, você precisa anexar algum tipo de identidade nas operações de e para identificar se o comando ou a atualização já foi processada.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="f7ff6-191">Enviar um comando para um único destinatário; um comando não publicar.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="f7ff6-192">A publicação é para eventos de integração que o estado de um fato — que algo aconteceu e pode ser interessantes para receptores de evento.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-192">Publishing is for integration events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="f7ff6-193">No caso de eventos, o publicador tem sem preocupações sobre quais destinatários obterem o evento ou o que eles fazem-lo.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="f7ff6-194">Mas os eventos de integração são outra história já introduzida nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-194">But integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="f7ff6-195">Um comando é implementado com uma classe que contém campos de dados ou coleções com todas as informações necessárias para executar esse comando.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="f7ff6-196">Um comando é um tipo especial de dados transferidos objeto (DTO), que é usado especificamente para solicitar alterações ou transações.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="f7ff6-197">O próprio comando baseia-se exatamente as informações necessárias para processar o comando e nada mais.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="f7ff6-198">O exemplo a seguir mostra a classe CreateOrderCommand simplificada.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="f7ff6-199">Este é um comando imutável que é usado no ordenação microsserviço em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;

    [DataMember]
    public string City { get; private set; }

    [DataMember]
    public string Street { get; private set; }

    [DataMember]
    public string State { get; private set; }

    [DataMember]
    public string Country { get; private set; }

    [DataMember]
    public string ZipCode { get; private set; }

    [DataMember]
    public string CardNumber { get; private set; }

    [DataMember]
    public string CardHolderName { get; private set; }

    [DataMember]
    public DateTime CardExpiration { get; private set; }

    [DataMember]
    public string CardSecurityNumber { get; private set; }

    [DataMember]
    public int CardTypeId { get; private set; }

    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="f7ff6-200">Basicamente, a classe de comando contém todos os dados que você precisa para realizar uma transação comercial, usando os objetos de modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="f7ff6-201">Assim, os comandos são simplesmente estruturas de dados que contêm dados somente leitura e nenhum comportamento.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="f7ff6-202">Nome do comando indica sua finalidade.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="f7ff6-203">Em vários idiomas, como C\#, comandos são representados como classes, mas eles não são true classes no sentido real orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-203">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="f7ff6-204">Como uma característica adicional, comandos são imutáveis, porque o uso esperado é que eles são processados diretamente pelo modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="f7ff6-205">Eles não precisam alterar durante seu ciclo de vida projetado.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="f7ff6-206">Em um C\# classe imutabilidade pode ser obtida por não haver qualquer setters ou outros métodos que alteram o estado interno.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-206">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="f7ff6-207">Por exemplo, a classe de comando para a criação de um pedido é provavelmente semelhante em termos de dados na ordem em que você deseja criar, mas você não tenha os mesmos atributos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-207">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="f7ff6-208">Por exemplo, CreateOrderCommand não tem uma ID de ordem, porque a ordem ainda não foi criada.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-208">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="f7ff6-209">Muitas classes de comando podem ser simples, exigindo somente alguns campos sobre algum estado que precisa ser alterado.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-209">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="f7ff6-210">Isso seria o caso se você estiver alterando apenas o status de um pedido de "processo" para "pago" ou "enviados" usando um comando semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-210">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="f7ff6-211">Alguns desenvolvedores fazem seus objetos de interface do usuário de solicitação separados de DTOs seu comando, mas que é apenas uma questão de preferência.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-211">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="f7ff6-212">É uma separação entediante não muito valor agregado, e os objetos são quase exatamente da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-212">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="f7ff6-213">Por exemplo, no eShopOnContainers, os comandos vêm diretamente do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-213">For instance, in eShopOnContainers, the commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="f7ff6-214">A classe do manipulador de comando</span><span class="sxs-lookup"><span data-stu-id="f7ff6-214">The Command Handler class</span></span>

<span data-ttu-id="f7ff6-215">Você deve implementar uma classe de manipulador de comando específicas para cada comando.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-215">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="f7ff6-216">Isso é como funciona o padrão e é onde você usará o objeto de comando, os objetos de domínio e os objetos de repositório de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-216">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="f7ff6-217">O manipulador de comandos na verdade é a essência da camada de aplicativo em termos de CQRS e DDD.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-217">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="f7ff6-218">No entanto, toda a lógica do domínio deve estar contida em classes de domínio — as raízes de agregação (entidades raiz), dentro de entidades filho, ou [dos serviços de domínio](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), mas não dentro do manipulador de comando, que é uma classe do aplicativo camada.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-218">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="f7ff6-219">Um manipulador de comandos recebe um comando e obtém um resultado de agregação que é usada.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-219">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="f7ff6-220">O resultado deve ser a execução bem-sucedida do comando ou uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-220">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="f7ff6-221">No caso de uma exceção, o estado do sistema deve ser inalterado.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-221">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="f7ff6-222">O manipulador de comandos geralmente executa as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-222">The command handler usually takes the following steps:</span></span>

-   <span data-ttu-id="f7ff6-223">Ele recebe o objeto de comando, como um DTO (da [mediador](https://en.wikipedia.org/wiki/Mediator_pattern) ou outro objeto de infraestrutura).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-223">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

-   <span data-ttu-id="f7ff6-224">Ele valida que o comando é válido (se não validado pelo mediador).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-224">It validates that the command is valid (if not validated by the mediator).</span></span>

-   <span data-ttu-id="f7ff6-225">Ele cria a instância de raiz de agregação que é o destino do comando atual.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-225">It instantiates the aggregate root instance that is the target of the current command.</span></span>

-   <span data-ttu-id="f7ff6-226">Ele executa o método na instância de raiz de agregação, obtendo os dados necessários do comando.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-226">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

-   <span data-ttu-id="f7ff6-227">Persistir o estado novo da agregação para seu banco de dados relacionado.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-227">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="f7ff6-228">Esta última operação é a transação atual.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-228">This last operation is the actual transaction.</span></span>

<span data-ttu-id="f7ff6-229">Normalmente, um manipulador de comandos lida com uma única agregação orientada por sua raiz de agregação (entidade de raiz).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-229">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="f7ff6-230">Se várias agregações devem ser afetadas pela recepção de um único comando, você pode usar eventos de domínio para propagar estados ou ações em várias agregações</span><span class="sxs-lookup"><span data-stu-id="f7ff6-230">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates</span></span>

<span data-ttu-id="f7ff6-231">O ponto importante aqui é que, quando um comando está sendo processado, toda a lógica do domínio deve estar dentro do modelo de domínio (agregações), totalmente encapsulado e está pronto para teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-231">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="f7ff6-232">O manipulador de comando apenas atua como uma maneira de obter o modelo de domínio do banco de dados e a etapa final, para informar a camada de infraestrutura (repositórios) para manter as alterações quando o modelo é alterado.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-232">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="f7ff6-233">A vantagem dessa abordagem é que você pode refatorar a lógica do domínio em um modelo de domínio isolado, totalmente encapsulado, ricos e comportamentais sem alterar o código do aplicativo ou as camadas de infraestrutura, que são o nível de detalhes técnicos (manipuladores de comandos, API da Web, repositórios, etc.).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-233">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="f7ff6-234">Quando manipuladores de comandos complexos, com muita lógica, que pode ser um cheiro de código.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-234">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="f7ff6-235">Examiná-los e, se você encontrar a lógica do domínio, refatorar o código para mover esse comportamento de domínio para os métodos dos objetos de domínio (agregação raiz e filho entidade).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-235">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="f7ff6-236">Como um exemplo de uma classe de manipulador de comando, o código a seguir mostra a mesma classe CreateOrderCommandHandler que você viu no início deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-236">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="f7ff6-237">Nesse caso destacamos o identificador de método e as operações com o domínio objetos modelo agrega.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-237">In this case we have highlighted the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

<span data-ttu-id="f7ff6-238">Estas são as etapas adicionais que deve ser seguidas por um manipulador de comandos:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-238">These are additional steps a command handler should take:</span></span>

-   <span data-ttu-id="f7ff6-239">Use dados do comando para operar com métodos e o comportamento da raiz de agregação.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-239">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

-   <span data-ttu-id="f7ff6-240">Internamente dentro dos objetos de domínio, gere eventos de domínio enquanto a transação é executada, mas isso é transparente de um ponto de vista do comando manipulador.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-240">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

-   <span data-ttu-id="f7ff6-241">Se o resultado da operação de agregação for bem-sucedida, e depois que a transação for concluída, aumente o manipulador de comando de eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-241">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events command handler.</span></span> <span data-ttu-id="f7ff6-242">(Eles podem também ser gerados por classes de infraestrutura como repositórios.)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-242">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f7ff6-243">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f7ff6-243">Additional resources</span></span>

-   <span data-ttu-id="f7ff6-244">**Mark Seemann. Em limites, os aplicativos são orientados a objeto não**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, orientado a ApplicationsareNotObject /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-244">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented**
[*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span></span>

-   <span data-ttu-id="f7ff6-245">**Comandos e eventos**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-245">**Commands and events**
[*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span></span>

-   <span data-ttu-id="f7ff6-246">**O que faz um manipulador de comando? ** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-246">**What does a command handler do?**
[*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span></span>

-   <span data-ttu-id="f7ff6-247">**Jimmy Bogard. Padrões de comando do domínio – manipuladores**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-247">**Jimmy Bogard. Domain Command Patterns – Handlers**
[*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span></span>

-   <span data-ttu-id="f7ff6-248">**Jimmy Bogard. Padrões de comando do domínio – validação**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-248">**Jimmy Bogard. Domain Command Patterns – Validation**
[*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span></span>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="f7ff6-249">O pipeline de processo do comando: como acionar um manipulador de comandos</span><span class="sxs-lookup"><span data-stu-id="f7ff6-249">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="f7ff6-250">A próxima pergunta é como chamar um manipulador de comandos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-250">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="f7ff6-251">Manualmente, você pode chamá-lo em cada controlador do ASP.NET Core relacionado.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-251">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="f7ff6-252">No entanto, o que abordagem seria muito acoplados e não é ideal.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-252">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="f7ff6-253">As outras duas opções principais, que são as opções recomendadas, são:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-253">The other two main options, which are the recommended options, are:</span></span>

-   <span data-ttu-id="f7ff6-254">Por meio de um artefato de padrão de mediador na memória.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-254">Through an in-memory Mediator pattern artifact.</span></span>

-   <span data-ttu-id="f7ff6-255">Com uma fila de mensagens assíncronas, entre os controladores e manipuladores.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-255">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="f7ff6-256">Usando o padrão de mediador (na memória) no pipeline de comando</span><span class="sxs-lookup"><span data-stu-id="f7ff6-256">Using the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="f7ff6-257">Conforme mostrado na Figura 9-21, uma abordagem CQRS você usa um mediador inteligente, semelhante a um barramento de memória, que é inteligente para redirecionar para o manipulador de comando correta com base no tipo de comando ou DTO sendo recebidas.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-257">As shown in Figure 9-21, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="f7ff6-258">As setas pretas único entre componentes representam as dependências entre objetos (em muitos casos, inseridos por meio de DI) com suas interações relacionadas.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-258">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![](./media/image22.png)

<span data-ttu-id="f7ff6-259">**Figura 9-21**.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-259">**Figure 9-21**.</span></span> <span data-ttu-id="f7ff6-260">Usando o padrão de mediador no processo em um único microsserviço CQRS</span><span class="sxs-lookup"><span data-stu-id="f7ff6-260">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="f7ff6-261">O motivo pelo qual usando o padrão de mediador faz sentido é se em aplicativos da empresa, as solicitações de processamento podem ficar complicadas.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-261">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="f7ff6-262">Você deseja adicionar um número aberto de resolvem preocupações com segurança, validações, auditoria e registro em log.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-262">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="f7ff6-263">Nesses casos, você pode confiar em um pipeline mediador (consulte [padrão mediador](https://en.wikipedia.org/wiki/Mediator_pattern)) para fornecer um meio para esses comportamentos extras ou resolvem preocupações.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-263">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="f7ff6-264">Um mediador é um objeto que encapsula o "como" desse processo: coordena com base no estado de execução, a maneira como um manipulador de comandos é chamado ou a carga que você fornecer para o manipulador.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-264">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="f7ff6-265">Com um componente mediador você pode aplicar resolvem preocupações de forma centralizada e transparente aplicando decoradores (ou [pipeline comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) desde mediador v3).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-265">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since Mediator v3).</span></span> <span data-ttu-id="f7ff6-266">(Para obter mais informações, consulte o [padrão de decorador](https://en.wikipedia.org/wiki/Decorator_pattern).)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-266">(For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).)</span></span>

<span data-ttu-id="f7ff6-267">Os decoradores e comportamentos são semelhantes às [programação orientada a aspecto (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)somente aplicado a um pipeline de processo específico gerenciado pelo componente mediador.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-267">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="f7ff6-268">Aspectos AOP que implementam resolvem preocupações são aplicados com base em *weavers aspecto* injetado em tempo de compilação ou com base em interceptação de chamada de objeto.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-268">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="f7ff6-269">Ambas as abordagens AOP típicas, às vezes, são chamadas para funcionar "como"mágica, porque ele não é fácil ver como AOP faz seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-269">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="f7ff6-270">Ao lidar com problemas sérios ou bugs, AOP pode ser difícil de depurar.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-270">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="f7ff6-271">Por outro lado, esses decoradores/comportamentos são explícita e aplicadas apenas no contexto do mediador, modo de depuração é muito mais fácil e previsível.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-271">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="f7ff6-272">Por exemplo, no eShopOnContainers ordenação microsserviço, implementamos dois decoradores de exemplo, um [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) classe e um [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) classe.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-272">For example, in the eShopOnContainers ordering microservice, we implemented two sample decorators, a [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class and a [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class.</span></span> <span data-ttu-id="f7ff6-273">Implementação do decorador é explicada na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-273">The decorator’s implementation is explained in the next section.</span></span> <span data-ttu-id="f7ff6-274">Observe que, em uma versão futura, eShopOnContainers migrará para [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) e mover para [comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) em vez de usar os decoradores.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-274">Note that in a future version, eShopOnContainers will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="f7ff6-275">Usando filas de mensagens (fora de processo) no pipeline do comando</span><span class="sxs-lookup"><span data-stu-id="f7ff6-275">Using message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="f7ff6-276">Outra opção é usar mensagens assíncronas com base em agentes ou filas de mensagens, conforme mostrado na Figura 9-22.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-276">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 9-22.</span></span> <span data-ttu-id="f7ff6-277">Essa opção também pode ser combinada com o componente mediador antes do manipulador de comandos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-277">That option could also be combined with the mediator component right before the command handler.</span></span>

![](./media/image23.png)

<span data-ttu-id="f7ff6-278">**Figura 9-22**.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-278">**Figure 9-22**.</span></span> <span data-ttu-id="f7ff6-279">Usando filas de mensagens (fora de processo e de comunicação entre processos) com comandos CQRS</span><span class="sxs-lookup"><span data-stu-id="f7ff6-279">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="f7ff6-280">Usar mensagens de filas para aceitar que os comandos podem mais complicam o pipeline do comando, porque você provavelmente precisará dividir o pipeline em dois processos conectados por meio da fila de mensagens externas.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-280">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="f7ff6-281">Ainda assim, ele deve ser usado se você precisa ter melhor escalabilidade e desempenho com base no sistema de mensagens assíncronas.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-281">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="f7ff6-282">Considere a possibilidade de que no caso de Figura 9-22, o controlador apenas envia a mensagem de comando na fila e retorna.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-282">Consider that in the case of Figure 9-22, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="f7ff6-283">Em seguida, o manipulador de comandos processa as mensagens em seu próprio ritmo.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-283">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="f7ff6-284">Isto é um grande benefício de filas — a fila de mensagens pode agir como um buffer em casos quando hyper escalabilidade é necessária, como para qualquer cenário com um alto volume de dados de entrada ou de ações.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-284">That is a great benefit of queues—the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="f7ff6-285">No entanto, devido à natureza assíncrona de filas de mensagens, você precisa descobrir como se comunicar com o aplicativo cliente sobre o êxito ou falha do processo do comando.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-285">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="f7ff6-286">Como regra, você nunca deve usar comandos de "disparar e esquecer".</span><span class="sxs-lookup"><span data-stu-id="f7ff6-286">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="f7ff6-287">Todos os aplicativos de negócios precisa saber se um comando foi processado com êxito, ou pelo menos validado e aceitos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-287">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="f7ff6-288">Portanto, ser capaz de responder ao cliente após a validação de uma mensagem de comando que foi enviada para uma fila assíncrona adiciona complexidade ao seu sistema, em comparação com um processo no processo de comando que retorna o resultado da operação depois de executar a transação.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-288">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="f7ff6-289">Uso de filas, talvez seja necessário retornar o resultado do processo de comando por meio de outras mensagens de resultado da operação, que exigirá a comunicação personalizada e componentes adicionais no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-289">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="f7ff6-290">Além disso, async comandos são unidirecionais, que, em muitos casos, pode não ser necessário, como explicado no seguinte troca interessante entre Burtsev Alexey e Greg Young em um [conversa on-line](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="f7ff6-290">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

<span data-ttu-id="f7ff6-291">\[Burtsev Alexey\] localizar muitos códigos de onde as pessoas usam o tratamento de comando assíncrono ou comando unidirecional de mensagens sem nenhuma razão para isso (eles não estão fazendo alguma operação longa, eles não estão executando o código de async externo, que não ultrapassem mesmo aplicativo limite usando o barramento de mensagem).</span><span class="sxs-lookup"><span data-stu-id="f7ff6-291">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="f7ff6-292">Por que introduzem essa complexidade desnecessária?</span><span class="sxs-lookup"><span data-stu-id="f7ff6-292">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="f7ff6-293">E, na verdade, não tiver visto um exemplo de código CQRS com bloqueio de manipuladores de comando até o momento, embora ele funcionará bem na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-293">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>

<span data-ttu-id="f7ff6-294">\[Greg Young\] \[... \] um comando assíncrono não existe; ela é realmente outro evento.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-294">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="f7ff6-295">Se deve aceitar o que você envie-me e gerar um evento se eu não concordo, ele não está mais você informando a fazer algo.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-295">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something.</span></span> <span data-ttu-id="f7ff6-296">É você informando que algo foi feito.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-296">It's you telling me something has been done.</span></span> <span data-ttu-id="f7ff6-297">Isso parece uma pequena diferença inicialmente, mas ele tem várias implicações.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-297">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="f7ff6-298">Comandos assíncronos aumentam significativamente a complexidade de um sistema, porque não há nenhuma maneira simple de indicam falhas.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-298">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="f7ff6-299">Portanto, comandos assíncronos não são recomendados diferente de quando os requisitos de dimensionamento são necessários ou, em casos especiais ao comunicar-se a microservices interna por meio de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-299">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="f7ff6-300">Nesses casos, você deve criar um sistema de emissão de relatórios e recuperação separado para falhas.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-300">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="f7ff6-301">Na versão inicial do eShopOnContainers, decidimos usar processamento de comando síncrono, iniciado a partir de solicitações HTTP e orientadas por padrão o mediador.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-301">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="f7ff6-302">Que permite retornar o êxito ou falha do processo, como em facilmente o [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementação.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-302">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="f7ff6-303">Em qualquer caso, isso deve ser uma decisão com base nos requisitos de negócios do aplicativo ou do microsserviço.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-303">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="f7ff6-304">Implementando o pipeline de comando de processo com um padrão de mediador (MediatR)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-304">Implementing the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="f7ff6-305">Como um exemplo de implementação, este guia propõe usando o pipeline em processo baseado no padrão de mediador para inclusão de comando de unidade e roteamento, na memória, os manipuladores de comando correta.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-305">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and routing them, in memory, to the right command handlers.</span></span> <span data-ttu-id="f7ff6-306">O guia também propõe aplicando decoradores ou [comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) para separar resolvem preocupações.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-306">The guide also proposes applying decorators or [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="f7ff6-307">Para a implementação no núcleo do .NET, há várias bibliotecas de código-fonte disponíveis que implementam o padrão de mediador.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-307">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="f7ff6-308">A biblioteca usada neste guia é o [MediatR](https://github.com/jbogard/MediatR) biblioteca de código-fonte aberto (criado pelo Jimmy Bogard), mas você pode usar outra abordagem.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-308">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="f7ff6-309">MediatR é uma biblioteca de pequena e simple que permite que você processe mensagens na memória como um comando, aplicando decoradores ou comportamentos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-309">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="f7ff6-310">Usando o padrão de mediador ajuda a reduzir o acoplamento e isolar as preocupações do trabalho solicitado, ao conectar-se automaticamente para o manipulador que executa esse trabalho — nesse caso, para manipuladores de comando.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-310">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="f7ff6-311">Outra boa razão para usar o padrão de mediador foi explicada por Jimmy Bogard ao revisar este guia:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-311">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

<span data-ttu-id="f7ff6-312">Acho que pode ser vale a pena mencionar teste aqui – fornece uma janela consistente adequada para o comportamento do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-312">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="f7ff6-313">Na solicitação, em resposta. Descobrimos que aspecto bastante valioso no prédio consistentemente se comportando testes.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-313">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="f7ff6-314">Primeiro, vamos dar uma olhada no código do controlador quando você realmente usa o objeto mediador.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-314">First, let us take a look to the controller code where you actually would use the mediator object.</span></span> <span data-ttu-id="f7ff6-315">Se você não estava usando o objeto mediador, você precisa inserir todas as dependências para esse controlador, como um objeto do agente de log e outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-315">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="f7ff6-316">Portanto, o construtor seria muito complicado.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-316">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="f7ff6-317">Por outro lado, se você usar o objeto mediador, o construtor do controlador pode ser muito mais simples, com apenas algumas dependências em vez de muitas dependências que seria necessário se você tivesse um por operação abrangentes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-317">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies that you would have if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

<span data-ttu-id="f7ff6-318">Você pode ver o mediador fornece um construtor de controlador Web API lean e limpo.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-318">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="f7ff6-319">Além disso, dentro do método do controlador, o código para enviar um comando para o objeto mediador é quase uma linha:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-319">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

<span data-ttu-id="f7ff6-320">Para MediatR estar ciente das suas classes de manipulador de comando, é necessário registrar as classes de mediador e as classes de manipulador de comando em seu contêiner IoC.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-320">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="f7ff6-321">Por padrão, MediatR usa Autofac como o contêiner IoC, mas você também pode usar o contêiner do ASP.NET Core IoC interno ou qualquer outro contêiner MediatR com suporte.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-321">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="f7ff6-322">O código a seguir mostra como registrar comandos e tipos do mediador ao usar módulos de Autofac.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-322">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

<span data-ttu-id="f7ff6-323">Como cada manipulador de comando implementa a interface com genérico IAsyncRequestHandler&lt;T&gt; e, em seguida, inspeciona o RegisteredAssemblyTypes do objeto, o manipulador é capaz de relacionar cada comando com seu manipulador de comando, porque que relação é declarada na classe CommandHandler, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-323">Because each command handler implements the interface with generic IAsyncRequestHandler&lt;T&gt; and then inspects the RegisteredAssemblyTypes object, the handler is able to relate each command with its command handler, because that relationship is stated in the CommandHandler class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="f7ff6-324">Este é o código que se correlaciona comandos com manipuladores de comandos.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-324">This is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="f7ff6-325">O manipulador é apenas uma classe simples, mas ele herda de RequestHandler&lt;T&gt;, e MediatR torna-se de que ele será invocado com a carga correta.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-325">The handler is just a simple class, but it inherits from RequestHandler&lt;T&gt;, and MediatR makes sure it gets invoked with the correct payload.</span></span>

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a><span data-ttu-id="f7ff6-326">Aplicando resolvem preocupações durante o processamento de comandos com os padrões mediador e decorador</span><span class="sxs-lookup"><span data-stu-id="f7ff6-326">Applying cross-cutting concerns when processing commands with the Mediator and Decorator patterns</span></span>

<span data-ttu-id="f7ff6-327">Há algo mais: conseguir aplicar resolvem preocupações pipeline mediador.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-327">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="f7ff6-328">Você também pode ver no final do código do módulo de registro Autofac como ele está registrando um decorador de tipo, especificamente, uma classe LogDecorator personalizada.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-328">You can also see at the end of the Autofac registration module code how it is registering a decorator type, specifically, a custom LogDecorator class.</span></span>

<span data-ttu-id="f7ff6-329">Novamente, observe que uma versão futura do eShopOnContainers ele migrará para [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) e mover para [comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) em vez de usar os decoradores.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-329">Again, note that a future version of eShopOnContainers it will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

<span data-ttu-id="f7ff6-330">Que [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) classe pode ser implementada como o código a seguir, que registra informações sobre o manipulador de comando que está sendo executado e se ela foi bem-sucedida ou não.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-330">That [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

<span data-ttu-id="f7ff6-331">Basta implementar essa classe decorador e decorando pipeline com ele, todos os comandos processados por meio de MediatR fizerem logon informações sobre a execução.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-331">Just by implementing this decorator class and by decorating the pipeline with it, all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="f7ff6-332">O eShopOnContainers ordenação microsserviço também se aplica a um segundo decorador para validações básicas, o [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) classe depende do [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteca, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-332">The eShopOnContainers ordering microservice also applies a second decorator for basic validations, the [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

<span data-ttu-id="f7ff6-333">Em seguida, com base no [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteca, criamos a validação para os dados passados com CreateOrderCommand, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f7ff6-333">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}
```

<span data-ttu-id="f7ff6-334">Você pode criar validações adicionais.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-334">You could create additional validations.</span></span> <span data-ttu-id="f7ff6-335">Isso é uma maneira muito claro e elegante para implementar seu validações de comando.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-335">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="f7ff6-336">De maneira semelhante, você pode implementar outros decoradores para aspectos adicionais ou resolvem preocupações que você deseja aplicar aos comandos ao lidar com eles.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-336">In a similar way, you could implement other decorators for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f7ff6-337">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f7ff6-337">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="f7ff6-338">O padrão de mediador</span><span class="sxs-lookup"><span data-stu-id="f7ff6-338">The mediator pattern</span></span>

-   <span data-ttu-id="f7ff6-339">**Padrão de mediador**
    [*https://en.wikipedia.org/wiki/Mediator\_padrão*](https://en.wikipedia.org/wiki/Mediator_pattern)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-339">**Mediator pattern**
[*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)</span></span>

##### <a name="the-decorator-pattern"></a><span data-ttu-id="f7ff6-340">O padrão de decorador</span><span class="sxs-lookup"><span data-stu-id="f7ff6-340">The decorator pattern</span></span>

-   <span data-ttu-id="f7ff6-341">**Padrão de decorador**
    [*https://en.wikipedia.org/wiki/Decorator\_padrão*](https://en.wikipedia.org/wiki/Decorator_pattern)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-341">**Decorator pattern**
[*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)</span></span>

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="f7ff6-342">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-342">MediatR (Jimmy Bogard)</span></span>

-   <span data-ttu-id="f7ff6-343">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="f7ff6-343">**MediatR.**</span></span> <span data-ttu-id="f7ff6-344">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-344">GitHub repo.</span></span>
    [<span data-ttu-id="f7ff6-345">*https://GitHub.com/jbogard/MediatR*</span><span class="sxs-lookup"><span data-stu-id="f7ff6-345">*https://github.com/jbogard/MediatR*</span></span>](https://github.com/jbogard/MediatR)

-   <span data-ttu-id="f7ff6-346">**CQRS com MediatR e AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-346">**CQRS with MediatR and AutoMapper**
[*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span></span>

-   <span data-ttu-id="f7ff6-347">**Coloque os controladores em uma dieta: postagens e comandos. ** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-347">**Put your controllers on a diet: POSTs and commands.**
[*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span></span>

-   <span data-ttu-id="f7ff6-348">**Lidar com resolvem preocupações com um pipeline mediador**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-348">**Tackling cross-cutting concerns with a mediator pipeline**
[*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span></span>

-   <span data-ttu-id="f7ff6-349">**CQRS e REST: a correspondência perfeita**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-349">**CQRS and REST: the perfect match**
[*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span></span>

-   <span data-ttu-id="f7ff6-350">**Exemplos de Pipeline de MediatR**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-350">**MediatR Pipeline Examples**
[*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span></span>

-   <span data-ttu-id="f7ff6-351">**Acessórios de teste de fatia vertical para MediatR e ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*</span><span class="sxs-lookup"><span data-stu-id="f7ff6-351">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core**
*<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span></span>

-   <span data-ttu-id="f7ff6-352">**Extensões MediatR Microsoft para injeção de dependência liberado**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-352">**MediatR Extensions for Microsoft Dependency Injection Released**
[*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span></span>

##### <a name="fluent-validation"></a><span data-ttu-id="f7ff6-353">Validação fluente</span><span class="sxs-lookup"><span data-stu-id="f7ff6-353">Fluent validation</span></span>

-   <span data-ttu-id="f7ff6-354">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="f7ff6-354">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="f7ff6-355">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="f7ff6-355">GitHub repo.</span></span>
    [<span data-ttu-id="f7ff6-356">*https://GitHub.com/JeremySkinner/FluentValidation*</span><span class="sxs-lookup"><span data-stu-id="f7ff6-356">*https://github.com/JeremySkinner/FluentValidation*</span></span>](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
<span data-ttu-id="f7ff6-357">[Anterior] (microservice-application-layer-web-api-design.md) [Avançar] (... /Implement-resilient-Applications/Index.MD)</span><span class="sxs-lookup"><span data-stu-id="f7ff6-357">[Previous] (microservice-application-layer-web-api-design.md) [Next] (../implement-resilient-applications/index.md)</span></span>
