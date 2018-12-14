---
title: Implementando a camada de aplicativos de microsserviço usando a API Web
description: Arquitetura de Microsserviços do .NET para aplicativos .NET em contêineres | Compreenda a injeção de dependência e os padrões de mediador e seus detalhes de implementação na camada de aplicativo de API Web.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 332829d30f10dde49727c63e9e80a91f24e1123a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151181"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="b1241-103">Implementar a camada de aplicativos de microsserviço usando a API Web</span><span class="sxs-lookup"><span data-stu-id="b1241-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="b1241-104">Usar a injeção de dependência para injetar objetos de infraestrutura em sua camada de aplicativo</span><span class="sxs-lookup"><span data-stu-id="b1241-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="b1241-105">Conforme mencionado anteriormente, a camada de aplicativo pode ser implementada como parte do artefato (assembly) que você está criando, tal como em um projeto de API Web ou um projeto de aplicativo Web do MVC.</span><span class="sxs-lookup"><span data-stu-id="b1241-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="b1241-106">No caso de um microsserviço criado com o ASP.NET Core, a camada de aplicativo geralmente será a biblioteca da API Web.</span><span class="sxs-lookup"><span data-stu-id="b1241-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="b1241-107">Se quiser separar o que é proveniente do ASP.NET Core (a infraestrutura e os controladores) do código personalizado da camada de aplicativo, você também poderá colocar a camada de aplicativo em uma biblioteca de classes separada, mas isso é opcional.</span><span class="sxs-lookup"><span data-stu-id="b1241-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="b1241-108">Por exemplo, o código da camada de aplicativo do microsserviço de ordenação é implementado diretamente como parte do projeto **Ordering.API** (um projeto da API Web ASP.NET Core), como mostrado na Figura 7-23.</span><span class="sxs-lookup"><span data-stu-id="b1241-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

![A exibição do Gerenciador de Soluções do microsserviço Ordering.API, mostrando as subpastas na pasta Aplicativo: Comportamentos, Comandos, DomainEventHandlers, IntegrationEvents, Modelos, Consultas e Validações.](./media/image20.png)

<span data-ttu-id="b1241-110">**Figura 7-23**.</span><span class="sxs-lookup"><span data-stu-id="b1241-110">**Figure 7-23**.</span></span> <span data-ttu-id="b1241-111">A camada de aplicativo no projeto Ordering.API da API Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b1241-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="b1241-112">O ASP.NET Core inclui um [contêiner interno de IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) simples (representado pela interface IServiceProvider) que é compatível com a injeção de construtor por padrão, e o ASP.NET disponibiliza alguns serviços por meio da DI (injeção de dependência).</span><span class="sxs-lookup"><span data-stu-id="b1241-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="b1241-113">O ASP.NET Core usa o termo *serviço* para qualquer um dos tipos que você registra e que serão injetados pela DI.</span><span class="sxs-lookup"><span data-stu-id="b1241-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="b1241-114">Você configura os serviços internos do contêiner no método ConfigureServices na classe Startup do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1241-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="b1241-115">As dependências são implementadas nos serviços que são necessários para um tipo e que você registra no contêiner de IoC.</span><span class="sxs-lookup"><span data-stu-id="b1241-115">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="b1241-116">Normalmente, você deseja injetar dependências que implementam objetos de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="b1241-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="b1241-117">Uma dependência muito comum a ser injetada é um repositório.</span><span class="sxs-lookup"><span data-stu-id="b1241-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="b1241-118">Mas você poderá injetar qualquer outra dependência de infraestrutura que tiver.</span><span class="sxs-lookup"><span data-stu-id="b1241-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="b1241-119">Para implementações mais simples, você injeta diretamente o objeto de padrão da Unidade de Trabalho (o objeto DbContext do EF), porque o DBContext também é a implementação dos objetos de persistência da sua infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="b1241-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="b1241-120">Veja no exemplo a seguir como o .NET Core está injetando os objetos de repositório necessários por meio do construtor.</span><span class="sxs-lookup"><span data-stu-id="b1241-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="b1241-121">A classe é um manipulador de comando, o que será abordado na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="b1241-121">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator, 
                                     IOrderRepository orderRepository, 
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ?? 
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? 
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? 
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic 
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, 
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId, 
                              message.CardNumber, message.CardSecurityNumber, 
                              message.CardHolderName, message.CardExpiration);
            
        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="b1241-122">A classe usa os repositórios injetados para executar a transação e persistir as alterações de estado.</span><span class="sxs-lookup"><span data-stu-id="b1241-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="b1241-123">Não importa se a classe é um manipulador de comandos, um método de controlador da API Web ASP.NET Core ou um [Serviço de aplicativo DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="b1241-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="b1241-124">Em última análise, ela uma classe simples que usa repositórios, entidades de domínio e outras coordenações de aplicativos de forma semelhante a um manipulador de comandos.</span><span class="sxs-lookup"><span data-stu-id="b1241-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="b1241-125">A injeção de dependência funciona da mesma forma para todas as classes mencionadas, como no exemplo que usa a injeção de dependência com base no construtor.</span><span class="sxs-lookup"><span data-stu-id="b1241-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="b1241-126">Registrar tipos e interfaces ou abstrações da implementação de dependência</span><span class="sxs-lookup"><span data-stu-id="b1241-126">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="b1241-127">Antes de usar os objetos injetados por meio de construtores, você precisa saber em que lugar registrar as interfaces e classes que produzem os objetos injetados nas classes do aplicativo por meio da DI.</span><span class="sxs-lookup"><span data-stu-id="b1241-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="b1241-128">(Como na DI baseada no construtor, conforme mostrado anteriormente).</span><span class="sxs-lookup"><span data-stu-id="b1241-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="b1241-129">Usar o contêiner interno de IoC fornecido pelo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b1241-129">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="b1241-130">Ao usar o contêiner interno de IoC fornecido pelo ASP.NET Core, você registra os tipos que deseja injetar no método ConfigureServices no arquivo Startup.cs, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b1241-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

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

<span data-ttu-id="b1241-131">O padrão mais comum ao registrar tipos em um contêiner de IoC é registrar um par de tipos: uma interface e a respectiva classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="b1241-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="b1241-132">Então, quando solicita um objeto do contêiner de IoC por meio de nenhum construtor, você solicita um objeto de um determinado tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="b1241-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="b1241-133">Assim, como visto no exemplo anterior, a última linha indica que, quando qualquer um dos seus construtores tiver uma dependência em IMyCustomRepository (interface ou abstração), o contêiner de IoC injetará uma instância da classe de implementação MyCustomSQLServerRepository.</span><span class="sxs-lookup"><span data-stu-id="b1241-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="b1241-134">Usar a biblioteca Scrutor para registro automático de tipos</span><span class="sxs-lookup"><span data-stu-id="b1241-134">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="b1241-135">Ao usar a DI no .NET Core, talvez seja interessante verificar um assembly e registrar automaticamente seus tipos por convenção.</span><span class="sxs-lookup"><span data-stu-id="b1241-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="b1241-136">Este recurso não está disponível atualmente no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1241-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="b1241-137">No entanto, você pode usar a biblioteca [Scrutor](https://github.com/khellang/Scrutor) para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b1241-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="b1241-138">Essa abordagem é conveniente quando você tem muitos tipos que precisam ser registrados no contêiner de IoC.</span><span class="sxs-lookup"><span data-stu-id="b1241-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b1241-139">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b1241-139">Additional resources</span></span>

- <span data-ttu-id="b1241-140">**Matthew King. Registrando serviços com o Scrutor** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-140">**Matthew King. Registering services with Scrutor** \\</span></span>
  [*https://www.mking.net/blog/registering-services-with-scrutor*](https://www.mking.net/blog/registering-services-with-scrutor)

- <span data-ttu-id="b1241-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="b1241-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="b1241-142">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b1241-142">GitHub repo.</span></span> \
  [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="b1241-143">Usar o Autofac como um contêiner de IoC</span><span class="sxs-lookup"><span data-stu-id="b1241-143">Use Autofac as an IoC container</span></span>

<span data-ttu-id="b1241-144">Você também pode usar mais contêineres de IoC e conectá-los no pipeline do ASP.NET Core, como no microsserviço de ordenação em eShopOnContainers, que usa o [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="b1241-144">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="b1241-145">Ao usar Autofac, você normalmente registra os tipos por meio de módulos, que permitem dividir os tipos de registro entre vários arquivos, dependendo do local em que seus tipos estão, assim como os tipos de aplicativos podem ser distribuídos entre várias bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="b1241-145">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="b1241-146">Por exemplo, a seguir está o [módulo de aplicativo do Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) para o projeto de [API Web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) com os tipos que você pode injetar.</span><span class="sxs-lookup"><span data-stu-id="b1241-146">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
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

<span data-ttu-id="b1241-147">O Autofac também tem um recurso para [digitalizar assemblies e registrar tipos pelas convenções de nome](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span><span class="sxs-lookup"><span data-stu-id="b1241-147">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="b1241-148">O processo e os conceitos de registro são muito semelhantes à forma pela qual você registra tipos com o contêiner de IoC interno do ASP.NET Core, mas a sintaxe, ao usar Autofac, é um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="b1241-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="b1241-149">No código de exemplo, a abstração IOrderRepository é registrada juntamente com a classe de implementação OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="b1241-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="b1241-150">Isso significa que, sempre que um construtor estiver declarando uma dependência por meio da abstração ou interface IOrderRepository, o contêiner de IoC injetará uma instância da classe OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="b1241-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="b1241-151">O tipo de escopo da instância determina como uma instância é compartilhada entre as solicitações para o mesmo serviço ou dependência.</span><span class="sxs-lookup"><span data-stu-id="b1241-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="b1241-152">Quando uma solicitação é feita a uma dependência, o contêiner de IoC pode retornar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b1241-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="b1241-153">Uma única instância por escopo de tempo de vida (conhecida no contêiner de IoC do ASP.NET Core como *com escopo*).</span><span class="sxs-lookup"><span data-stu-id="b1241-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="b1241-154">Uma nova instância por dependência (conhecida no contêiner de IoC do ASP.NET Core como *transitória*).</span><span class="sxs-lookup"><span data-stu-id="b1241-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="b1241-155">Uma única instância compartilhada entre todos os objetos que usam o contêiner de IoC (conhecida no contêiner de IoC do ASP.NET Core como *singleton*).</span><span class="sxs-lookup"><span data-stu-id="b1241-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b1241-156">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b1241-156">Additional resources</span></span>

- <span data-ttu-id="b1241-157">**Introdução à injeção de dependência no ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-157">**Introduction to Dependency Injection in ASP.NET Core** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="b1241-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="b1241-158">**Autofac.**</span></span> <span data-ttu-id="b1241-159">Documentação oficial.</span><span class="sxs-lookup"><span data-stu-id="b1241-159">Official documentation.</span></span> \
  [*http://docs.autofac.org/en/latest/*](http://docs.autofac.org/en/latest/)

- <span data-ttu-id="b1241-160">**Comparando os tempos de vida do serviço de contêiner de IoC do ASP.NET Core com os escopos de instância de contêiner de IoC do Autofac – Cesar de la Torre.**</span><span class="sxs-lookup"><span data-stu-id="b1241-160">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="b1241-161">Implementar os padrões de Comando e Manipulador de Comandos</span><span class="sxs-lookup"><span data-stu-id="b1241-161">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="b1241-162">No exemplo de DI por meio de construtor, mostrado na seção anterior, o contêiner de IoC injetou repositórios por meio de um construtor em uma classe.</span><span class="sxs-lookup"><span data-stu-id="b1241-162">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="b1241-163">Mas em que local eles foram exatamente injetados?</span><span class="sxs-lookup"><span data-stu-id="b1241-163">But exactly where were they injected?</span></span> <span data-ttu-id="b1241-164">Em uma API Web simples (por exemplo, o microsserviço de catálogo em eShopOnContainers), eles são injetados no nível de controladores do MVC, em um construtor de controlador, como parte do pipeline de solicitação do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1241-164">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers’ level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="b1241-165">Entretanto, no código inicial desta seção (a classe [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) do serviço Ordering.API em eShopOnContainers), a injeção de dependências é feita por meio do construtor de um manipulador comandos específico.</span><span class="sxs-lookup"><span data-stu-id="b1241-165">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="b1241-166">Vamos explicar o que é um manipulador de comandos e por que você o usaria.</span><span class="sxs-lookup"><span data-stu-id="b1241-166">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="b1241-167">O padrão Command é intrinsecamente relacionado ao padrão CQRS, apresentado anteriormente neste guia.</span><span class="sxs-lookup"><span data-stu-id="b1241-167">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="b1241-168">O CQRS tem dois lados.</span><span class="sxs-lookup"><span data-stu-id="b1241-168">CQRS has two sides.</span></span> <span data-ttu-id="b1241-169">A primeira área é a de consultas, usando consultas simplificadas com o micro ORM [Dapper](https://github.com/StackExchange/dapper-dot-net), explicado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b1241-169">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="b1241-170">A segunda área é a de comandos, os quais são o ponto de partida para transações e o canal de entrada do serviço.</span><span class="sxs-lookup"><span data-stu-id="b1241-170">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="b1241-171">Conforme mostrado na Figura 7-24, o padrão é baseado em aceitar comandos do lado do cliente, processá-los com base nas regras do modelo de domínio e, por fim, persistir os estados com as transações.</span><span class="sxs-lookup"><span data-stu-id="b1241-171">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![O modo de exibição de alto nível do lado das gravações em CQRS: o aplicativo de interface do usuário envia um comando por meio da API que é um CommandHandler, que depende do modelo de domínio e da infraestrutura para atualizar o banco de dados.](./media/image21.png)

<span data-ttu-id="b1241-173">**Figura 7-24**.</span><span class="sxs-lookup"><span data-stu-id="b1241-173">**Figure 7-24**.</span></span> <span data-ttu-id="b1241-174">Exibição de alto nível dos comandos ou do "lado transacional" em um padrão CQRS</span><span class="sxs-lookup"><span data-stu-id="b1241-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="b1241-175">A classe de comando</span><span class="sxs-lookup"><span data-stu-id="b1241-175">The command class</span></span>

<span data-ttu-id="b1241-176">Um comando é uma solicitação ao sistema para executar uma ação que altera o estado do sistema.</span><span class="sxs-lookup"><span data-stu-id="b1241-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="b1241-177">Os comandos são imperativos e devem ser processados apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="b1241-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="b1241-178">Como são imperativos, os comandos geralmente são nomeados com um verbo no modo imperativo, por exemplo, "criar" ou "atualizar", e eles podem incluir o tipo de agregação, como CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="b1241-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="b1241-179">Ao contrário de um evento, um comando não é um fato do passado; ele é apenas uma solicitação e, portanto, pode ser recusado.</span><span class="sxs-lookup"><span data-stu-id="b1241-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="b1241-180">Os comandos podem se originar na interface do usuário, como resultado do início de uma solicitação por um usuário ou de um gerenciador de processos, quando ele está instruindo uma agregação a executar uma ação.</span><span class="sxs-lookup"><span data-stu-id="b1241-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="b1241-181">Uma característica importante de um comando é que ele deve ser processado apenas uma vez por um único destinatário.</span><span class="sxs-lookup"><span data-stu-id="b1241-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="b1241-182">Isso porque um comando é uma ação ou transação única que você deseja executar no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1241-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="b1241-183">Por exemplo, o mesmo comando de criação de pedido não deve ser processado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="b1241-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="b1241-184">Essa é uma importante diferença entre comandos e eventos.</span><span class="sxs-lookup"><span data-stu-id="b1241-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="b1241-185">Os eventos podem ser processados várias vezes, porque muitos sistemas ou microsserviços podem estar interessados no evento.</span><span class="sxs-lookup"><span data-stu-id="b1241-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="b1241-186">Além disso, é importante que um comando seja processado apenas uma vez, caso ele não seja idempotente.</span><span class="sxs-lookup"><span data-stu-id="b1241-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="b1241-187">Um comando será idempotente se ele puder ser executado várias vezes sem alterar o resultado, devido à natureza do comando ou por causa da forma como o sistema manipula o comando.</span><span class="sxs-lookup"><span data-stu-id="b1241-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="b1241-188">Uma boa prática é tornar os comandos e atualizações idempotentes, quando isso for adequado às regras de negócios e invariáveis do seu domínio.</span><span class="sxs-lookup"><span data-stu-id="b1241-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="b1241-189">Assim, para usar o mesmo exemplo, se por algum motivo (lógica de repetição, hackers, etc.) o mesmo comando CreateOrder chegar até seu sistema diversas vezes, você deverá ser capaz de identificá-lo e ter a certeza de não criar vários pedidos.</span><span class="sxs-lookup"><span data-stu-id="b1241-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="b1241-190">Para fazer isso, você precisa anexar algum tipo de identidade nas operações e identificar se o comando ou a atualização já foi processada.</span><span class="sxs-lookup"><span data-stu-id="b1241-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="b1241-191">Você envia um comando a um único destinatário; você não publica um comando.</span><span class="sxs-lookup"><span data-stu-id="b1241-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="b1241-192">A publicação serve para eventos que declaram um fato, ou seja, que algo aconteceu e pode ser interessante para destinatários de eventos.</span><span class="sxs-lookup"><span data-stu-id="b1241-192">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="b1241-193">No caso de eventos, o publicador não tem preocupações sobre quais destinatários recebem o evento ou o que eles fazem com isso.</span><span class="sxs-lookup"><span data-stu-id="b1241-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="b1241-194">No entanto, os eventos de domínio ou de integração são outra história, já apresentada nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="b1241-194">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="b1241-195">Um comando é implementado com uma classe que contém campos de dados ou coleções com todas as informações necessárias para executar esse comando.</span><span class="sxs-lookup"><span data-stu-id="b1241-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="b1241-196">Um comando é um tipo especial de DTO (Objeto de Transferência de Dados), usado especificamente para solicitar alterações ou transações.</span><span class="sxs-lookup"><span data-stu-id="b1241-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="b1241-197">O próprio comando baseia-se estritamente nas informações necessárias para processar o comando e nada mais.</span><span class="sxs-lookup"><span data-stu-id="b1241-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="b1241-198">O exemplo a seguir mostra a classe CreateOrderCommand simplificada.</span><span class="sxs-lookup"><span data-stu-id="b1241-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="b1241-199">Este é um comando imutável que é usado no microsserviço de ordenação em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b1241-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/library/bb383979.aspx
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

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
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

<span data-ttu-id="b1241-200">Basicamente, a classe de comando contém todos os dados necessários para realizar uma transação comercial, usando os objetos do modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="b1241-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="b1241-201">Assim, os comandos são simplesmente estruturas de dados que contêm dados somente leitura e nenhum comportamento.</span><span class="sxs-lookup"><span data-stu-id="b1241-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="b1241-202">O nome do comando indica sua finalidade.</span><span class="sxs-lookup"><span data-stu-id="b1241-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="b1241-203">Em várias linguagens, como C\#, os comandos são representados como classes, mas eles não são verdadeiramente classes, no real sentido de orientado a objeto.</span><span class="sxs-lookup"><span data-stu-id="b1241-203">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="b1241-204">Como uma característica adicional, os comandos são imutáveis, porque o uso esperado é que eles sejam processados diretamente pelo modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="b1241-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="b1241-205">Eles não precisam ser alterados durante o tempo de vida projetado.</span><span class="sxs-lookup"><span data-stu-id="b1241-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="b1241-206">Em uma classe de C\#, a imutabilidade pode ser obtida por não haver nenhum setter nem outros métodos que alterem o estado interno.</span><span class="sxs-lookup"><span data-stu-id="b1241-206">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="b1241-207">Lembre-se de que se você pretende ou espera que os comandos passem por um processo de serialização/desserialização, as propriedades devem ter um setter privado e o atributo `[DataMemeber]` (ou `[JsonProperty]`), caso contrário, o desserializador não consegue reconstruir o objeto no destino com os valores necessários.</span><span class="sxs-lookup"><span data-stu-id="b1241-207">Bear in mind that if you intend or expect commands will be going through a serializing/deserializing process, the properties must have private setter, and the `[DataMemeber]` (or `[JsonProperty]`) attribute, otherwise the deserializer will not be able to reconstruct the object at destination with the required values.</span></span>

<span data-ttu-id="b1241-208">Por exemplo, a classe de comando para a criação de um pedido é, provavelmente, semelhante em relação aos dados para o pedido que você deseja criar, mas é provável que você não precise dos mesmos atributos.</span><span class="sxs-lookup"><span data-stu-id="b1241-208">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="b1241-209">Por exemplo, a CreateOrderCommand não tem uma ID de pedido, porque o pedido ainda não foi criado.</span><span class="sxs-lookup"><span data-stu-id="b1241-209">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="b1241-210">Muitas classes de comando podem ser simples, exigindo apenas alguns campos de algum estado que tenha que ser alterado.</span><span class="sxs-lookup"><span data-stu-id="b1241-210">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="b1241-211">Esse seria o caso se você estivesse apenas alterando o status de um pedido de "em processo" para "pago" ou "enviado", usando um comando semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="b1241-211">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

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

<span data-ttu-id="b1241-212">Alguns desenvolvedores criam os objetos de solicitação da interface do usuário separados dos DTOs do comando, mas essa é apenas uma questão de preferência.</span><span class="sxs-lookup"><span data-stu-id="b1241-212">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="b1241-213">É uma separação entediante que não agrega muito valor, e os objetos são quase exatamente da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="b1241-213">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="b1241-214">Por exemplo, em eShopOnContainers, alguns comandos vêm diretamente do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="b1241-214">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="b1241-215">A classe Manipuladora de Comandos</span><span class="sxs-lookup"><span data-stu-id="b1241-215">The Command Handler class</span></span>

<span data-ttu-id="b1241-216">Você deve implementar uma classe manipuladora de comandos específica para cada comando.</span><span class="sxs-lookup"><span data-stu-id="b1241-216">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="b1241-217">É assim que o padrão funciona e é o local em que você usará o objeto de comando, os objetos de domínio e os objetos de repositório da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="b1241-217">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="b1241-218">O manipulador de comandos é, na verdade, a essência da camada de aplicativo em termos de CQRS e DDD.</span><span class="sxs-lookup"><span data-stu-id="b1241-218">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="b1241-219">No entanto, toda a lógica do domínio deve estar contida nas classes de domínio — nas raízes de agregação (entidades raiz), nas entidades filho ou nos [serviços de domínio](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), mas não no manipulador de comandos, que é uma classe da camada de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1241-219">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="b1241-220">A classe de manipulador de comando oferece um forte ponto de partida no caminho para alcançar o SRP (Princípio de Responsabilidade Único) mencionado em uma seção anterior.</span><span class="sxs-lookup"><span data-stu-id="b1241-220">The command handler class offers a strong stepping stone in the way to achieve the Single Resposibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="b1241-221">Um manipulador de comandos recebe um comando e obtém um resultado da agregação que é usada.</span><span class="sxs-lookup"><span data-stu-id="b1241-221">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="b1241-222">O resultado deverá ser a execução bem-sucedida do comando ou uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b1241-222">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="b1241-223">No caso de uma exceção, o estado do sistema deve permanecer inalterado.</span><span class="sxs-lookup"><span data-stu-id="b1241-223">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="b1241-224">O manipulador de comandos geralmente realiza as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="b1241-224">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="b1241-225">Ele recebe o objeto de comando, como um DTO (do [mediador](https://en.wikipedia.org/wiki/Mediator_pattern) ou de outro objeto da infraestrutura).</span><span class="sxs-lookup"><span data-stu-id="b1241-225">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="b1241-226">Ele verifica se o comando é válido (se não tiver sido validado pelo mediador).</span><span class="sxs-lookup"><span data-stu-id="b1241-226">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="b1241-227">Ele cria a instância da raiz de agregação que é o destino do comando atual.</span><span class="sxs-lookup"><span data-stu-id="b1241-227">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="b1241-228">Ele executa o método na instância raiz da agregação, obtendo os dados necessários do comando.</span><span class="sxs-lookup"><span data-stu-id="b1241-228">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="b1241-229">Ele persiste o novo estado da agregação no respectivo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b1241-229">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="b1241-230">Esta última operação é, verdadeiramente, a transação.</span><span class="sxs-lookup"><span data-stu-id="b1241-230">This last operation is the actual transaction.</span></span>

<span data-ttu-id="b1241-231">Normalmente, um manipulador de comandos lida com uma única agregação orientada por sua raiz de agregação (entidade de raiz).</span><span class="sxs-lookup"><span data-stu-id="b1241-231">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="b1241-232">Se várias agregações devem ser afetadas pela recepção de um único comando, você pode usar eventos de domínio para propagar estados ou ações entre várias agregações.</span><span class="sxs-lookup"><span data-stu-id="b1241-232">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="b1241-233">O ponto importante aqui é que, quando um comando está sendo processado, toda a lógica do domínio deve estar dentro do modelo de domínio (as agregações), totalmente encapsulada e pronta para o teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="b1241-233">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="b1241-234">O manipulador de comandos atua apenas como uma maneira de obter o modelo de domínio do banco de dados e como a etapa final, para informar à camada de infraestrutura (aos repositórios) para persistir as alterações quando o modelo for alterado.</span><span class="sxs-lookup"><span data-stu-id="b1241-234">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="b1241-235">A vantagem dessa abordagem é que você pode refatorar a lógica do domínio em um modelo de domínio isolado, totalmente encapsulado, avançado e comportamental sem alterar o código do aplicativo ou as camadas de infraestrutura, que fazem parte do nível de detalhes técnicos (manipuladores de comandos, API Web, repositórios, etc.).</span><span class="sxs-lookup"><span data-stu-id="b1241-235">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="b1241-236">Quando manipuladores de comandos se tornam complexos, com muita lógica, começam a ficar parecidos com código.</span><span class="sxs-lookup"><span data-stu-id="b1241-236">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="b1241-237">Examine-os e, se você encontrar lógica de domínio, refatore o código para mover esse comportamento de domínio para os métodos dos objetos de domínio (a raiz de agregação e a entidade filho).</span><span class="sxs-lookup"><span data-stu-id="b1241-237">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="b1241-238">Como um exemplo de uma classe manipuladora de comandos, o código a seguir mostra a mesma classe CreateOrderCommandHandler que você viu no início deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="b1241-238">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="b1241-239">Nesse caso, queremos realçar o método Handle e as operações com os objetos/agregações do modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="b1241-239">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator, 
                                     IOrderRepository orderRepository, 
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ?? 
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? 
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? 
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic 
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, 
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId, 
                              message.CardNumber, message.CardSecurityNumber, 
                              message.CardHolderName, message.CardExpiration);
            
        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="b1241-240">Aqui estão etapas adicionais que um manipulador de comandos deve realizar:</span><span class="sxs-lookup"><span data-stu-id="b1241-240">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="b1241-241">Usar os dados do comando para operar com os métodos e o comportamento da raiz de agregação.</span><span class="sxs-lookup"><span data-stu-id="b1241-241">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

- <span data-ttu-id="b1241-242">Internamente, dentro dos objetos de domínio, acionar eventos de domínio enquanto a transação é executada, mas isso é transparente do ponto de vista de um manipulador comandos.</span><span class="sxs-lookup"><span data-stu-id="b1241-242">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="b1241-243">Se o resultado da operação de agregação for bem-sucedido e depois que a transação for concluída, acione eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="b1241-243">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="b1241-244">(Eles também podem ser acionados por classes de infraestrutura como repositórios).</span><span class="sxs-lookup"><span data-stu-id="b1241-244">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b1241-245">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b1241-245">Additional resources</span></span>

- <span data-ttu-id="b1241-246">**Mark Seemann. Nos limites, os aplicativos não são orientados a objeto** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-246">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** \\</span></span>
  [<span data-ttu-id="b1241-247">*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*</span><span class="sxs-lookup"><span data-stu-id="b1241-247">*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*</span></span>](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

- <span data-ttu-id="b1241-248">**Comandos e eventos** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-248">**Commands and events** \\</span></span>
  [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

- <span data-ttu-id="b1241-249">**O que faz um manipulador de comandos?**</span><span class="sxs-lookup"><span data-stu-id="b1241-249">**What does a command handler do?**</span></span> \
  [*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

- <span data-ttu-id="b1241-250">**Jimmy Bogard. Padrões de comando do domínio – manipuladores** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-250">**Jimmy Bogard. Domain Command Patterns – Handlers** \\</span></span>
  [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

- <span data-ttu-id="b1241-251">**Jimmy Bogard. Padrões de comando do domínio – validação** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-251">**Jimmy Bogard. Domain Command Patterns – Validation** \\</span></span>
  [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="b1241-252">O pipeline de processo Comando: como disparar um manipulador de comandos</span><span class="sxs-lookup"><span data-stu-id="b1241-252">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="b1241-253">A próxima pergunta é como invocar um manipulador de comandos.</span><span class="sxs-lookup"><span data-stu-id="b1241-253">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="b1241-254">Você poderia chamá-lo manualmente em cada controlador do ASP.NET Core relacionado.</span><span class="sxs-lookup"><span data-stu-id="b1241-254">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="b1241-255">No entanto, essa abordagem seria muito acoplada e não seria o ideal.</span><span class="sxs-lookup"><span data-stu-id="b1241-255">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="b1241-256">As outras duas opções principais, que são as opções recomendadas, são:</span><span class="sxs-lookup"><span data-stu-id="b1241-256">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="b1241-257">Por meio de um artefato de padrão Mediador na memória.</span><span class="sxs-lookup"><span data-stu-id="b1241-257">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="b1241-258">Com uma fila de mensagens assíncronas, entre os controladores e manipuladores.</span><span class="sxs-lookup"><span data-stu-id="b1241-258">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="b1241-259">Usar o padrão Mediador (na memória) no pipeline de comando</span><span class="sxs-lookup"><span data-stu-id="b1241-259">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="b1241-260">Conforme mostrado na Figura 7-25, em uma abordagem CQRS você usa um mediador, semelhante a um barramento na memória, que é inteligente o suficiente para redirecionar para o manipulador de comandos correto com base no tipo de comando ou DTO que está sendo recebido.</span><span class="sxs-lookup"><span data-stu-id="b1241-260">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="b1241-261">As setas pretas simples entre componentes representam as dependências entre objetos (em muitos casos, injetadas por meio da DI) com as respectivas interações.</span><span class="sxs-lookup"><span data-stu-id="b1241-261">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Aumentando o zoom da imagem anterior: o controlador do ASP.NET Core envia o comando ao pipeline de comando do MediatR, de forma que ele chega ao manipulador adequado.](./media/image22.png)

<span data-ttu-id="b1241-263">**Figura 7-25**.</span><span class="sxs-lookup"><span data-stu-id="b1241-263">**Figure 7-25**.</span></span> <span data-ttu-id="b1241-264">Usando o padrão Mediador no processo em um único microsserviço CQRS</span><span class="sxs-lookup"><span data-stu-id="b1241-264">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="b1241-265">O motivo pelo qual o uso do padrão Mediador faz sentido é porque, em aplicativos empresariais, as solicitações de processamento podem ficar complicadas.</span><span class="sxs-lookup"><span data-stu-id="b1241-265">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="b1241-266">Você almeja adicionar um número indefinido de interesses transversais como registro em log, validações, auditoria e segurança.</span><span class="sxs-lookup"><span data-stu-id="b1241-266">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="b1241-267">Nesses casos, você pode confiar em um pipeline mediador (veja [Padrão mediador](https://en.wikipedia.org/wiki/Mediator_pattern)) para oferecer um meio para esses comportamentos adicionais ou interesses transversais.</span><span class="sxs-lookup"><span data-stu-id="b1241-267">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="b1241-268">Um mediador é um objeto que encapsula o "como" desse processo: ele coordena a execução com base no estado, a maneira como um manipulador de comandos é invocado ou o conteúdo que você fornece para o manipulador.</span><span class="sxs-lookup"><span data-stu-id="b1241-268">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="b1241-269">Com um componente mediador, você pode aplicar interesses transversais de uma forma centralizada e transparente, por meio da aplicação de decoradores (ou [comportamentos de pipeline](https://github.com/jbogard/MediatR/wiki/Behaviors) como [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="b1241-269">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="b1241-270">Para obter mais informações, consulte o [Padrão decorador](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="b1241-270">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="b1241-271">Os decoradores e comportamentos são semelhantes à [AOP (Programação orientada a aspectos)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), aplicada somente a um pipeline de processo específico gerenciado pelo componente mediador.</span><span class="sxs-lookup"><span data-stu-id="b1241-271">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="b1241-272">Os aspectos na AOP, que implementam interesses transversais, são aplicados com base em *construtores de aspecto* injetados em tempo de compilação ou com base na interceptação da chamada de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1241-272">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="b1241-273">Às vezes, essas duas abordagens de AOP típicas parecem funcionar "como mágica", porque não é fácil entender como a AOP faz seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="b1241-273">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="b1241-274">Ao lidar com problemas sérios ou bugs, pode ser difícil depurar a AOP.</span><span class="sxs-lookup"><span data-stu-id="b1241-274">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="b1241-275">Por outro lado, esses decoradores/comportamentos são explícitos e aplicados apenas no contexto do mediador, assim, a depuração fica muito mais fácil e previsível.</span><span class="sxs-lookup"><span data-stu-id="b1241-275">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="b1241-276">Por exemplo, no microsserviço de pedidos eShopOnContainers, implementamos dois comportamentos de exemplo, uma classe [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) e uma classe [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs).</span><span class="sxs-lookup"><span data-stu-id="b1241-276">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="b1241-277">A implementação dos comportamentos será explicada na próxima seção, mostrando como a eShopOnContainers usa [comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0).</span><span class="sxs-lookup"><span data-stu-id="b1241-277">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="b1241-278">Usar filas de mensagens (fora do processo) no pipeline do comando</span><span class="sxs-lookup"><span data-stu-id="b1241-278">Use message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="b1241-279">Outra opção é usar mensagens assíncronas com base em agentes ou filas de mensagens, conforme mostrado na Figura 7-26.</span><span class="sxs-lookup"><span data-stu-id="b1241-279">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="b1241-280">Essa opção também pode ser combinada com o componente mediador imediatamente antes do manipulador de comandos.</span><span class="sxs-lookup"><span data-stu-id="b1241-280">That option could also be combined with the mediator component right before the command handler.</span></span>

![O pipeline do comando também pode ser tratado por uma fila de mensagens de alta disponibilidade para entregar os comandos ao manipulador adequado.](./media/image23.png)

<span data-ttu-id="b1241-282">**Figura 7-26**.</span><span class="sxs-lookup"><span data-stu-id="b1241-282">**Figure 7-26**.</span></span> <span data-ttu-id="b1241-283">Usando filas de mensagens (comunicação fora do processo e entre processos) com comandos CQRS</span><span class="sxs-lookup"><span data-stu-id="b1241-283">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="b1241-284">O uso de filas de mensagens para aceitar os comandos pode complicar ainda mais o pipeline do comando, porque você provavelmente precisará dividir o pipeline em dois processos conectados por meio da fila de mensagens externas.</span><span class="sxs-lookup"><span data-stu-id="b1241-284">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="b1241-285">Ainda assim, isso deve ser usado se você precisa ter melhor escalabilidade e desempenho com base no sistema de mensagens assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b1241-285">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="b1241-286">Considere que, no caso da Figura 7-26, o controlador apenas posta a mensagem de comando na fila e retorna.</span><span class="sxs-lookup"><span data-stu-id="b1241-286">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="b1241-287">Em seguida, o manipulador de comandos processa as mensagens em seu próprio ritmo.</span><span class="sxs-lookup"><span data-stu-id="b1241-287">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="b1241-288">Esse é um grande benefício das filas: a fila de mensagens pode agir como um buffer nos casos em que a hiperescalabilidade é necessária, como para estoques ou qualquer outro cenário com um alto volume de dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="b1241-288">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="b1241-289">No entanto, devido à natureza assíncrona das filas de mensagens, você precisa descobrir como se comunicar com o aplicativo cliente em relação ao êxito ou falha do processo do comando.</span><span class="sxs-lookup"><span data-stu-id="b1241-289">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="b1241-290">Como regra, você nunca deve usar comandos do tipo "disparar e esquecer".</span><span class="sxs-lookup"><span data-stu-id="b1241-290">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="b1241-291">Todos os aplicativos de negócios precisam saber se um comando foi processado com êxito ou, pelo menos, validado e aceito.</span><span class="sxs-lookup"><span data-stu-id="b1241-291">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="b1241-292">Portanto, a capacidade de responder ao cliente após a validação de uma mensagem de comando que foi enviada para uma fila assíncrona adiciona complexidade ao seu sistema, em comparação com um processo de comando em processo, que retorna o resultado da operação depois de executar a transação.</span><span class="sxs-lookup"><span data-stu-id="b1241-292">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="b1241-293">Ao usar filas, talvez seja necessário retornar o resultado do processo do comando por meio de outras mensagens de resultado da operação, o que exigirá comunicação personalizada e componentes adicionais em seu sistema.</span><span class="sxs-lookup"><span data-stu-id="b1241-293">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="b1241-294">Além disso, os comandos assíncronos são unidirecionais, o que, em muitos casos, pode não ser necessário, conforme explicado na seguinte discussão interessante entre Burtsev Alexey e Greg Young em uma [conversa online](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="b1241-294">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="b1241-295">\[Burtsev Alexey\] Eu encontro muito código nos locais em que as pessoas usam a manipulação de comando assíncrono ou sistemas de mensagens de comando unidirecional sem nenhuma razão para isso (eles não estão fazendo nenhuma operação longa, nem executando código assíncrono externo, nem mesmo ultrapassando o limite do aplicativo para usar o barramento de mensagem).</span><span class="sxs-lookup"><span data-stu-id="b1241-295">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="b1241-296">Por que eles introduzem essa complexidade desnecessária?</span><span class="sxs-lookup"><span data-stu-id="b1241-296">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="b1241-297">E, na verdade, eu não vi nenhum exemplo de código CQRS com manipuladores de comando de bloqueio até o momento, embora isso funcionaria muito bem na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="b1241-297">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="b1241-298">\[Greg Young\] \[...\] um comando assíncrono não existe; ele é, na verdade, outro evento.</span><span class="sxs-lookup"><span data-stu-id="b1241-298">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="b1241-299">Se eu precisar aceitar o que você me envia e acionar um evento se não concordar, já não será mais você me dizendo para fazer algo, \[ou seja, não se tratará de um comando\].</span><span class="sxs-lookup"><span data-stu-id="b1241-299">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it’s not a command\].</span></span> <span data-ttu-id="b1241-300">É você me informando que algo foi feito.</span><span class="sxs-lookup"><span data-stu-id="b1241-300">It's you telling me something has been done.</span></span> <span data-ttu-id="b1241-301">Parece que essa é apenas uma pequena diferença inicialmente, mas isso tem várias implicações.</span><span class="sxs-lookup"><span data-stu-id="b1241-301">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="b1241-302">Os comandos assíncronos aumentam significativamente a complexidade de um sistema, porque não há nenhuma maneira simples de indicar falhas.</span><span class="sxs-lookup"><span data-stu-id="b1241-302">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="b1241-303">Portanto, os comandos assíncronos não são recomendados a não ser quando há requisitos de dimensionamento ou em casos especiais, ao comunicar os microsserviços internos por meio do sistema de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b1241-303">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="b1241-304">Nesses casos, você deve projetar um sistema de relatórios e de recuperação separado para falhas.</span><span class="sxs-lookup"><span data-stu-id="b1241-304">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="b1241-305">Na versão inicial do eShopOnContainers, decidimos usar processamento de comando síncrono, iniciado com solicitações HTTP e orientado pelo padrão Mediador.</span><span class="sxs-lookup"><span data-stu-id="b1241-305">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="b1241-306">Isso permite retornar o êxito ou a falha do processo com facilidade, como na implementação de [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="b1241-306">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="b1241-307">Em todo caso, essa deve ser uma decisão baseada nos requisitos de negócio do aplicativo ou do microsserviço.</span><span class="sxs-lookup"><span data-stu-id="b1241-307">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="b1241-308">Implementar o pipeline de processo de comando com um padrão mediador (MediatR)</span><span class="sxs-lookup"><span data-stu-id="b1241-308">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="b1241-309">Como uma implementação de exemplo, este guia propõe o uso do pipeline em processo baseado no padrão Mediador para orientar a ingestão de comando e rotear comandos, na memória, para os manipuladores de comando corretos.</span><span class="sxs-lookup"><span data-stu-id="b1241-309">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="b1241-310">O guia também propõe a aplicação de [comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) para separar interesses transversais.</span><span class="sxs-lookup"><span data-stu-id="b1241-310">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="b1241-311">Para a implementação no .NET Core, há várias bibliotecas de software livre disponíveis que implementam o padrão Mediador.</span><span class="sxs-lookup"><span data-stu-id="b1241-311">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="b1241-312">A biblioteca usada neste guia é a [MediatR](https://github.com/jbogard/MediatR), biblioteca de software livre criada por Jimmy Bogard, mas você pode usar outra abordagem.</span><span class="sxs-lookup"><span data-stu-id="b1241-312">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="b1241-313">A MediatR é uma biblioteca pequena e simples que permite que você processe mensagens na memória como um comando, aplicando, ao mesmo tempo, decoradores ou comportamentos.</span><span class="sxs-lookup"><span data-stu-id="b1241-313">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="b1241-314">O uso do padrão Mediador ajuda a reduzir o acoplamento e isolar as preocupações com o trabalho solicitado, ao conectar-se automaticamente com manipulador que executa esse trabalho — nesse caso, os manipuladores de comando.</span><span class="sxs-lookup"><span data-stu-id="b1241-314">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="b1241-315">Outra boa razão para usar o padrão Mediador foi explicada por Jimmy Bogard durante a revisão desse guia:</span><span class="sxs-lookup"><span data-stu-id="b1241-315">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="b1241-316">Acho que vale a pena mencionar testes aqui – eles oferecem uma janela consistente e adequada sobre o comportamento do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="b1241-316">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="b1241-317">Solicitação entra, resposta sai. Descobrimos que esse aspecto é bastante valioso na construção de testes de comportamentos consistentes.</span><span class="sxs-lookup"><span data-stu-id="b1241-317">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="b1241-318">Primeiro, vamos dar uma olhada em um controlador de WebAPI de exemplo no local em que você usaria o objeto mediador.</span><span class="sxs-lookup"><span data-stu-id="b1241-318">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="b1241-319">Se não estivesse usando o objeto mediador, você teria que injetar todas as dependências desse controlador, como um objeto do agente e outras coisas.</span><span class="sxs-lookup"><span data-stu-id="b1241-319">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="b1241-320">Portanto, o construtor ficaria muito complicado.</span><span class="sxs-lookup"><span data-stu-id="b1241-320">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="b1241-321">Por outro lado, se você usasse o objeto mediador, o construtor do controlador poderia ser muito mais simples, com apenas algumas dependências em vez de muitas dependências, se você tivesse um por operação transversal, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b1241-321">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator, 
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

<span data-ttu-id="b1241-322">Veja que o mediador fornece um construtor de controlador da API Web simples e eficiente.</span><span class="sxs-lookup"><span data-stu-id="b1241-322">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="b1241-323">Além disso, dentro dos métodos do controlador, o código para enviar um comando para o objeto mediador tem quase uma linha:</span><span class="sxs-lookup"><span data-stu-id="b1241-323">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost] 
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand 
                                                               runOperationCommand) 
{
    var commandResult = await _mediator.SendAsync(runOperationCommand); 

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a><span data-ttu-id="b1241-324">Implementar comandos idempotentes</span><span class="sxs-lookup"><span data-stu-id="b1241-324">Implement idempotent Commands</span></span>

<span data-ttu-id="b1241-325">Em **eShopOnContainers**, um exemplo mais avançado que o que foi visto está enviando um objeto CreateOrderCommand do microsserviço de pedidos.</span><span class="sxs-lookup"><span data-stu-id="b1241-325">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="b1241-326">Mas, como o processo empresarial de Pedidos é um pouco mais complexo e, em nosso caso, ele realmente tem início no microsserviço Carrinho de compras, essa ação de enviar o objeto CreateOrderCommand é executada em um manipulador de eventos de integração chamado >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) em vez de um simples controlador de API Web chamado no aplicativo cliente, como no exemplo anterior, que era mais simples.</span><span class="sxs-lookup"><span data-stu-id="b1241-326">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="b1241-327">Mesmo assim, a ação de enviar o Comando para o MediatR é bem semelhante, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b1241-327">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,     
                                                eventMsg.UserId, eventMsg.City, 
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber, 
                                                eventMsg.CardHolderName, 
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,  
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand, 
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="b1241-328">No entanto, neste caso também é um pouco mais avançado porque estamos implementando comandos idempotentes.</span><span class="sxs-lookup"><span data-stu-id="b1241-328">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="b1241-329">O processo CreateOrderCommand deve ser idempotente, portanto, se a mesma mensagem vier duplicada pela rede, independentemente do motivo, como repetições, a mesma ordem de negócios será processada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="b1241-329">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="b1241-330">Isso é implementado pelo encapsulamento do comando empresarial (CreateOrderCommand, neste caso), inserindo-o em um IdentifiedCommand genérico que é controlado por uma ID de cada mensagem que chega por meio da rede e que deve ser idempotente.</span><span class="sxs-lookup"><span data-stu-id="b1241-330">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="b1241-331">Veja no código abaixo que o IdentifiedCommand não passa de um DTO com uma ID, além do objeto do comando de negócios encapsulado.</span><span class="sxs-lookup"><span data-stu-id="b1241-331">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="b1241-332">Então, o CommandHandler do IdentifiedCommand chamado [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) vai basicamente verificar se a ID que está chegando como parte da mensagem já existe em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="b1241-332">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="b1241-333">Se ela já existir, aquele comando não será processado novamente, comportando-se como um comando idempotente.</span><span class="sxs-lookup"><span data-stu-id="b1241-333">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="b1241-334">Esse código de infraestrutura é executado pela chamada de método `_requestManager.ExistAsync` abaixo.</span><span class="sxs-lookup"><span data-stu-id="b1241-334">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> : 
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator, 
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embeded business command to mediator 
            // so it runs its related CommandHandler 
            var result = await _mediator.Send(message.Command);
                
            return result;
        }
    }
}
```

<span data-ttu-id="b1241-335">Como o IdentifiedCommand age como o envelope de um comando de negócios, quando o comando de negócios tiver que ser processado, por não ter uma ID repetida, ele obterá esse comando de negócios interno e o enviará novamente para o Mediador, como na última parte do código mostrado acima ao executar `_mediator.Send(message.Command)`, do [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="b1241-335">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="b1241-336">Ao fazer isso, ele vinculará e executará o manipulador do comando empresarial, o [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs), nesse caso, que está executando transações no banco de dados de Pedidos, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b1241-336">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator, 
                                     IOrderRepository orderRepository, 
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ?? 
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? 
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? 
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,  
                              message.CardNumber, message.CardSecurityNumber, 
                              message.CardHolderName, message.CardExpiration);
            
        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="b1241-337">Registrar os tipos usados pelo MediatR</span><span class="sxs-lookup"><span data-stu-id="b1241-337">Register the types used by MediatR</span></span>

<span data-ttu-id="b1241-338">Para que o MediatR tome ciência de suas classes de manipulador de comando, é necessário registrar as classes de mediador e as classes de manipulador de comandos em seu contêiner de IoC.</span><span class="sxs-lookup"><span data-stu-id="b1241-338">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="b1241-339">Por padrão, o MediatR usa o Autofac como contêiner de IoC, mas você também pode usar o contêiner de IoC interno do ASP.NET Core ou qualquer outro contêiner compatível com o MediatR.</span><span class="sxs-lookup"><span data-stu-id="b1241-339">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="b1241-340">O código a seguir mostra como registrar comandos e tipos do Mediador ao usar módulos de Autofac.</span><span class="sxs-lookup"><span data-stu-id="b1241-340">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="b1241-341">É aqui que a "mágica acontece" com o MediatR.</span><span class="sxs-lookup"><span data-stu-id="b1241-341">This is where “the magic happens” with MediatR.</span></span>

<span data-ttu-id="b1241-342">Como cada manipulador de comando implementa a interface `IAsyncRequestHandler<T>` genérica, durante o registro de assemblies, o código registra todos os tipos marcados como `IAsyncRequestHandler` com `RegisteredAssemblyTypes`, relacionando, ao mesmo tempo, os `CommandHandlers` com seus respectivos `Commands`, graças a relação declarada na classe `CommandHandler`, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b1241-342">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="b1241-343">Esse é o código que correlaciona comandos com manipuladores de comandos.</span><span class="sxs-lookup"><span data-stu-id="b1241-343">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="b1241-344">O manipulador é apenas uma classe simples, mas ele herda de `RequestHandler<T>`, em que T é o tipo de comando, enquanto o MediatR garante que ele seja invocado com o conteúdo correto.</span><span class="sxs-lookup"><span data-stu-id="b1241-344">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="b1241-345">Aplicar questões abrangentes ao processar comandos com os Comportamentos no MediatR</span><span class="sxs-lookup"><span data-stu-id="b1241-345">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="b1241-346">Há mais um assunto para discutir: a capacidade de aplicar interesses transversais ao pipeline mediador.</span><span class="sxs-lookup"><span data-stu-id="b1241-346">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="b1241-347">Você também pode ver, no final do código do módulo de registro do Autofac, como ele registra um tipo de comportamento, especificamente uma classe LoggingBehavior personalizada e uma classe ValidatorBehavior.</span><span class="sxs-lookup"><span data-stu-id="b1241-347">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="b1241-348">Mas você também pode adicionar outros comportamentos personalizados.</span><span class="sxs-lookup"><span data-stu-id="b1241-348">But you could add other custom behaviors, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...        
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="b1241-349">Essa classe [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs), que registra informações sobre o manipulador de comando que está sendo executado e se ele foi bem-sucedido ou não, pode ser implementada como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b1241-349">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse> 
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="b1241-350">Basta implementar essa classe de comportamento e registrar o pipeline com ela (no MediatorModule acima) e todos os comandos processados por meio do MediatR registrarão em log as informações sobre a execução.</span><span class="sxs-lookup"><span data-stu-id="b1241-350">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="b1241-351">O microsserviço de pedidos eShopOnContainers também aplica um segundo comportamento para validações básicas, a classe [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs), que depende da biblioteca [FluentValidation](https://github.com/JeremySkinner/FluentValidation), conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b1241-351">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse> 
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="b1241-352">O comportamento aqui é gerar uma exceção se a validação falhar, mas também é possível retornar um objeto de resultado. Esse objeto contém o resultado do comando se ele é bem-sucedido ou, caso contrário, as mensagens de validação.</span><span class="sxs-lookup"><span data-stu-id="b1241-352">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn’t.</span></span> <span data-ttu-id="b1241-353">Isso provavelmente tornaria mais fácil exibir os resultados da validação para o usuário.</span><span class="sxs-lookup"><span data-stu-id="b1241-353">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="b1241-354">Assim, com base na biblioteca [FluentValidation](https://github.com/JeremySkinner/FluentValidation), criamos a validação para os dados passados com CreateOrderCommand, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b1241-354">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

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
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date"); 
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3); 
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found"); 
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

<span data-ttu-id="b1241-355">Você pode criar validações adicionais.</span><span class="sxs-lookup"><span data-stu-id="b1241-355">You could create additional validations.</span></span> <span data-ttu-id="b1241-356">Essa é uma maneira muito eficiente e elegante de se implementar validações de comando.</span><span class="sxs-lookup"><span data-stu-id="b1241-356">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="b1241-357">De maneira semelhante, você pode implementar outros comportamentos para aspectos adicionais ou interesses transversais que você deseja aplicar aos comandos ao manipulá-los.</span><span class="sxs-lookup"><span data-stu-id="b1241-357">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b1241-358">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b1241-358">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="b1241-359">O padrão mediador</span><span class="sxs-lookup"><span data-stu-id="b1241-359">The mediator pattern</span></span>

- <span data-ttu-id="b1241-360">**Padrão de mediador** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-360">**Mediator pattern** \\</span></span>
  [*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="b1241-361">O padrão decorador</span><span class="sxs-lookup"><span data-stu-id="b1241-361">The decorator pattern</span></span>

- <span data-ttu-id="b1241-362">**Padrão de decorador** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-362">**Decorator pattern** \\</span></span>
  [*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="b1241-363">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="b1241-363">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="b1241-364">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="b1241-364">**MediatR.**</span></span> <span data-ttu-id="b1241-365">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b1241-365">GitHub repo.</span></span> \
  [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

- <span data-ttu-id="b1241-366">**CQRS com MediatR e AutoMapper** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-366">**CQRS with MediatR and AutoMapper** \\</span></span>
  [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

- <span data-ttu-id="b1241-367">**Coloque os controladores de dieta: POSTs e comandos.**</span><span class="sxs-lookup"><span data-stu-id="b1241-367">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  [*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

- <span data-ttu-id="b1241-368">**Lidando com preocupações paralelas com um pipeline de mediadores** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-368">**Tackling cross-cutting concerns with a mediator pipeline** \\</span></span>
  [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

- <span data-ttu-id="b1241-369">**CQRS e REST: o par perfeito** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-369">**CQRS and REST: the perfect match** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

- <span data-ttu-id="b1241-370">**Exemplos de pipeline de MediatR** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-370">**MediatR Pipeline Examples** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

- <span data-ttu-id="b1241-371">**Acessórios de teste de fatia vertical para MediatR e ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-371">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/*](https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/)

- <span data-ttu-id="b1241-372">**Extensões de MediatR para injeção de dependência da Microsoft** \\</span><span class="sxs-lookup"><span data-stu-id="b1241-372">**MediatR Extensions for Microsoft Dependency Injection Released** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a><span data-ttu-id="b1241-373">Validação fluente</span><span class="sxs-lookup"><span data-stu-id="b1241-373">Fluent validation</span></span>

- <span data-ttu-id="b1241-374">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="b1241-374">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="b1241-375">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b1241-375">GitHub repo.</span></span> \
  [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
><span data-ttu-id="b1241-376">[Anterior](microservice-application-layer-web-api-design.md)
>[Próximo](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="b1241-376">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>