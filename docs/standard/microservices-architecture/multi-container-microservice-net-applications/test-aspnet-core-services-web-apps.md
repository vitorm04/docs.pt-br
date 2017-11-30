---
title: "Teste os serviços principais do ASP.NET e aplicativos web"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Teste os serviços principais do ASP.NET e aplicativos web"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f756a679befee676db2bf6d402fd7e34b1621b9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="df560-104">Teste os serviços principais do ASP.NET e aplicativos web</span><span class="sxs-lookup"><span data-stu-id="df560-104">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="df560-105">Os controladores são uma parte central de qualquer serviço de API do ASP.NET Core e o aplicativo Web do ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="df560-105">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="df560-106">Como tal, você deve ter confiança que se comportam conforme o esperado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df560-106">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="df560-107">Testes automatizados podem fornecer essa confiança e podem detectar erros antes que elas atinjam a produção.</span><span class="sxs-lookup"><span data-stu-id="df560-107">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="df560-108">Você precisa testar como o controlador se comporta com base nas entradas válidas ou inválidas e respostas de controlador com base no resultado da operação de negócios que ele executa um teste.</span><span class="sxs-lookup"><span data-stu-id="df560-108">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="df560-109">No entanto, você deve ter esses tipos de teste sua microservices:</span><span class="sxs-lookup"><span data-stu-id="df560-109">However, you should have these types of tests your microservices:</span></span>

-   <span data-ttu-id="df560-110">Testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="df560-110">Unit tests.</span></span> <span data-ttu-id="df560-111">Eles garantem que os componentes individuais do aplicativo funcionam como esperado.</span><span class="sxs-lookup"><span data-stu-id="df560-111">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="df560-112">Asserções testar a API do componente.</span><span class="sxs-lookup"><span data-stu-id="df560-112">Assertions test the component API.</span></span>

-   <span data-ttu-id="df560-113">Testes de integração.</span><span class="sxs-lookup"><span data-stu-id="df560-113">Integration tests.</span></span> <span data-ttu-id="df560-114">Eles garantem que as interações do componente funcionam como esperado em artefatos externos, como bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="df560-114">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="df560-115">Asserções podem testar a API do componente, interface do usuário ou os efeitos colaterais de ações, como e/s de banco de dados, log, etc.</span><span class="sxs-lookup"><span data-stu-id="df560-115">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="df560-116">Testes funcionais para cada microsserviço.</span><span class="sxs-lookup"><span data-stu-id="df560-116">Functional tests for each microservice.</span></span> <span data-ttu-id="df560-117">Eles garantem que o aplicativo funciona conforme o esperado da perspectiva do usuário.</span><span class="sxs-lookup"><span data-stu-id="df560-117">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="df560-118">Testes de serviço.</span><span class="sxs-lookup"><span data-stu-id="df560-118">Service tests.</span></span> <span data-ttu-id="df560-119">Eles garantem que os casos de uso do serviço de ponta a ponta, incluindo testes de vários serviços ao mesmo tempo, são testados.</span><span class="sxs-lookup"><span data-stu-id="df560-119">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="df560-120">Para esse tipo de teste, você precisa preparar o ambiente primeiro.</span><span class="sxs-lookup"><span data-stu-id="df560-120">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="df560-121">Nesse caso, isso significa que iniciar os serviços (por exemplo, usando o docker-compor backup).</span><span class="sxs-lookup"><span data-stu-id="df560-121">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="df560-122">Implementação de testes de unidade para APIs de Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="df560-122">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="df560-123">Testes de unidade envolve uma parte de um aplicativo de teste em isolamento de sua infraestrutura e as dependências.</span><span class="sxs-lookup"><span data-stu-id="df560-123">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="df560-124">Quando a lógica do controlador, somente o conteúdo de uma única ação de teste de unidade você ou método é testado, não o comportamento de suas dependências ou a própria estrutura.</span><span class="sxs-lookup"><span data-stu-id="df560-124">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="df560-125">Testes de unidade não detectam problemas na interação entre componentes, que é o objetivo do teste de integração.</span><span class="sxs-lookup"><span data-stu-id="df560-125">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="df560-126">Como você unidade suas ações do controlador de teste, verifique se que você se concentrar apenas em seus comportamentos.</span><span class="sxs-lookup"><span data-stu-id="df560-126">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="df560-127">Um teste de unidade do controlador evita coisas como filtros, roteamento ou associação de modelo.</span><span class="sxs-lookup"><span data-stu-id="df560-127">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="df560-128">Como eles se concentrar no teste apenas uma coisa, testes de unidade geralmente são simples de escrever e rápido executar.</span><span class="sxs-lookup"><span data-stu-id="df560-128">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="df560-129">Um conjunto bem escrito de testes de unidade pode ser executado com frequência sem muita sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="df560-129">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="df560-130">Testes de unidade são implementados com base nas estruturas de teste como xUnit.net, MSTest, Moq ou NUnit.</span><span class="sxs-lookup"><span data-stu-id="df560-130">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="df560-131">Para o aplicativo de exemplo eShopOnContainers, estamos usando XUnit.</span><span class="sxs-lookup"><span data-stu-id="df560-131">For the eShopOnContainers sample application, we are using XUnit.</span></span>

<span data-ttu-id="df560-132">Quando você grava um teste de unidade para um controlador de API da Web, você instanciar a classe do controlador diretamente usando a nova palavra-chave C\#, de modo que o teste será executado mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="df560-132">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="df560-133">O exemplo a seguir mostra como fazer isso ao usar [XUnit](https://xunit.github.io/) como a estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="df560-133">The following example shows how to do this when using [XUnit](https://xunit.github.io/) as the Test framework.</span></span>

```csharp
[Fact]
public void Add_new_Order_raises_new_event()
{
    // Arrange
    var street = " FakeStreet ";
    var city = "FakeCity";
    // Other variables omitted for brevity ...
    // Act
    var fakeOrder = new Order(new Address(street, city, state, country, zipcode),
        cardTypeId, cardNumber,
        cardSecurityNumber, cardHolderName,
        cardExpiration);
    // Assert
    Assert.Equal(fakeOrder.DomainEvents.Count, expectedResult);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="df560-134">Implementação de integração e testes funcionais para cada microsserviço</span><span class="sxs-lookup"><span data-stu-id="df560-134">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="df560-135">Conforme observado, testes de integração e testes funcionais têm metas e objetivos diferentes.</span><span class="sxs-lookup"><span data-stu-id="df560-135">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="df560-136">No entanto, a maneira como você implementa ambos ao testar controladores do ASP.NET Core é semelhante, portanto nesta seção, nos concentraremos em testes de integração.</span><span class="sxs-lookup"><span data-stu-id="df560-136">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="df560-137">Testes de integração, você garante que componentes de um aplicativo funcionam corretamente quando montado.</span><span class="sxs-lookup"><span data-stu-id="df560-137">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="df560-138">ASP.NET Core dá suporte a teste de integração usando estruturas de teste de unidade e um host da web internos de teste que pode ser usado para tratar as solicitações sem sobrecarga de rede.</span><span class="sxs-lookup"><span data-stu-id="df560-138">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="df560-139">Ao contrário de testes de unidade, testes de integração com frequência envolvem preocupações de infraestrutura de aplicativo, como um banco de dados, sistema de arquivos, recursos de rede, ou web solicitações e respostas.</span><span class="sxs-lookup"><span data-stu-id="df560-139">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="df560-140">Testes de unidade usam fakes ou simular objetos no lugar essas preocupações.</span><span class="sxs-lookup"><span data-stu-id="df560-140">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="df560-141">Mas a finalidade de testes de integração confirmar se o sistema funciona conforme esperado com esses sistemas, forma para testes de integração não usar fakes ou simular objetos.</span><span class="sxs-lookup"><span data-stu-id="df560-141">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="df560-142">Em vez disso, você pode incluir a infraestrutura, como a invocação de acesso ou o serviço de banco de dados de outros serviços.</span><span class="sxs-lookup"><span data-stu-id="df560-142">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="df560-143">Porque o exercitam de testes de integração maior de segmentos de código que testes de unidade e testes de integração se basear em elementos de infraestrutura, eles tendem a ser ordens de magnitude menor do que testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="df560-143">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="df560-144">Portanto, é uma boa ideia limitar quantos testes de integração, gravar e executar.</span><span class="sxs-lookup"><span data-stu-id="df560-144">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="df560-145">ASP.NET Core inclui um teste interno host da web que pode ser usado para tratar as solicitações HTTP sem sobrecarga de rede, que significa que você pode executar esses testes mais rapidamente ao usar um host da web real.</span><span class="sxs-lookup"><span data-stu-id="df560-145">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="df560-146">O host de teste da web está disponível em um componente do NuGet como Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="df560-146">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="df560-147">Ele pode ser adicionado a projetos de teste de integração e aplicativos usados para hospedar o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="df560-147">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="df560-148">Como você pode ver no código a seguir, quando você cria testes de integração para o ASP.NET Core controladores, você pode instanciar os controladores por meio do host de teste.</span><span class="sxs-lookup"><span data-stu-id="df560-148">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="df560-149">Isso é equivalente a uma solicitação HTTP, mas ele é executado mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="df560-149">This is comparable to an HTTP request, but it runs faster.</span></span>

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a><span data-ttu-id="df560-150">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="df560-150">Additional resources</span></span>

-   <span data-ttu-id="df560-151">**Steve Smith. Controladores de teste** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="df560-151">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="df560-152">**Steve Smith. Testes de integração** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span><span class="sxs-lookup"><span data-stu-id="df560-152">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span></span>

-   <span data-ttu-id="df560-153">**Teste de unidade no .NET Core usando dotnet teste**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span><span class="sxs-lookup"><span data-stu-id="df560-153">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span></span>

-   <span data-ttu-id="df560-154">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="df560-154">**xUnit.net**.</span></span> <span data-ttu-id="df560-155">Site oficial.</span><span class="sxs-lookup"><span data-stu-id="df560-155">Official site.</span></span>
    [<span data-ttu-id="df560-156">*https://xUnit.GitHub.IO/*</span><span class="sxs-lookup"><span data-stu-id="df560-156">*https://xunit.github.io/*</span></span>](https://xunit.github.io/)

-   <span data-ttu-id="df560-157">**Noções básicas de teste de unidade. ** 
     [ *https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="df560-157">**Unit Test Basics.**
[*https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="df560-158">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="df560-158">**Moq**.</span></span> <span data-ttu-id="df560-159">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="df560-159">GitHub repo.</span></span>
    [<span data-ttu-id="df560-160">*https://GitHub.com/moq/moq*</span><span class="sxs-lookup"><span data-stu-id="df560-160">*https://github.com/moq/moq*</span></span>](https://github.com/moq/moq)

-   <span data-ttu-id="df560-161">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="df560-161">**NUnit**.</span></span> <span data-ttu-id="df560-162">Site oficial.</span><span class="sxs-lookup"><span data-stu-id="df560-162">Official site.</span></span>
    [<span data-ttu-id="df560-163">*https://www.NUnit.org/*</span><span class="sxs-lookup"><span data-stu-id="df560-163">*https://www.nunit.org/*</span></span>](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="df560-164">Testes de implementação de serviços em um aplicativo de contêiner de vários</span><span class="sxs-lookup"><span data-stu-id="df560-164">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="df560-165">Conforme observado anteriormente, quando você testar o contêiner de vários aplicativos, todos os microservices precisa estar executando dentro do cluster de host ou o contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="df560-165">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="df560-166">Testes de serviço de ponta a ponta que incluem várias operações que envolvem várias microservices exigem que você implantar e iniciar o aplicativo inteiro no host do Docker executando docker-compor up (ou um mecanismo comparável se você estiver usando um orchestrator).</span><span class="sxs-lookup"><span data-stu-id="df560-166">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="df560-167">Quando o aplicativo inteiro e todos os seus serviços estiver em execução, você pode executar testes funcionais e integração de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="df560-167">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="df560-168">Existem algumas abordagens que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="df560-168">There are a few approaches you can use.</span></span> <span data-ttu-id="df560-169">No arquivo de docker compose.yml que você usa para implantar o aplicativo (ou aquelas semelhantes, como o docker compose.ci.build.yml), no nível da solução você pode expandir o ponto de entrada para usar [dotnet teste](https://docs.microsoft.com/dotnet/core/tools/dotnet-test).</span><span class="sxs-lookup"><span data-stu-id="df560-169">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](https://docs.microsoft.com/dotnet/core/tools/dotnet-test).</span></span> <span data-ttu-id="df560-170">Você também pode usar outro arquivo de redação que executará os testes na imagem de que destino.</span><span class="sxs-lookup"><span data-stu-id="df560-170">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="df560-171">Usando outro arquivo de redação para testes de integração que inclui seu microservices e bancos de dados em contêineres, você pode garantir que os dados relacionados sempre são redefinidos para seu estado original antes de executar os testes.</span><span class="sxs-lookup"><span data-stu-id="df560-171">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="df560-172">Depois que o aplicativo de redação está em execução, você pode tirar proveito de pontos de interrupção e exceções se você estiver executando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df560-172">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="df560-173">Ou você pode executar os testes de integração automaticamente em seu pipeline de CI no Visual Studio Team Services ou qualquer outro sistema de CI/CD que dá suporte a contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="df560-173">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="df560-174">[Anterior] (assinar-events.md) [Avançar] (... /microservice-DDD-CQRS-Patterns/index.MD)</span><span class="sxs-lookup"><span data-stu-id="df560-174">[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
