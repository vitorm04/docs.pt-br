---
title: Implementando o padrão de Disjuntor
description: Arquitetura de Microsserviços do .NET para aplicativos .NET em contêineres | Implementando o padrão de Disjuntor
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.openlocfilehash: 2c89992c4c60ca7f1085050e6fed4922ecd4d8cc
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106117"
---
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="d5458-103">Implementando o padrão de Disjuntor</span><span class="sxs-lookup"><span data-stu-id="d5458-103">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="d5458-104">Conforme observado anteriormente, você deve tratar falhas que podem consumir uma quantidade variável de tempo de recuperação, como pode acontecer quando você tenta se conectar a um serviço ou um recurso remoto.</span><span class="sxs-lookup"><span data-stu-id="d5458-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="d5458-105">Lidar com esse tipo de falha pode melhorar a estabilidade e a resiliência de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d5458-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="d5458-106">Em um ambiente distribuído, chamadas para serviços e recursos remotos poderão falhar devido a falhas transitórias, como conexões lentas de rede e tempos limites ou se os recursos estiverem lentos ou temporariamente não disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d5458-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="d5458-107">Essas falhas geralmente são corrigidas automaticamente após um curto período, e um aplicativo em nuvem robusto deve estar preparado para lidar com elas usando uma estratégia como o padrão de Novas Tentativas.</span><span class="sxs-lookup"><span data-stu-id="d5458-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="d5458-108">No entanto, também pode haver situações em que as falhas são devido a eventos inesperados que podem levar muito mais tempo para serem corrigidos.</span><span class="sxs-lookup"><span data-stu-id="d5458-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="d5458-109">Essas falhas podem variar em termos de gravidade de uma perda parcial de conectividade até a falha completa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="d5458-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="d5458-110">Nessas situações, pode não ter sentido um aplicativo repetir continuamente uma operação que é improvável que seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d5458-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="d5458-111">Em vez disso, o aplicativo deve ser codificado para aceitar que a operação falhou e lidar com falhas adequadamente.</span><span class="sxs-lookup"><span data-stu-id="d5458-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="d5458-112">O padrão de Disjuntor tem uma finalidade diferente que o padrão de Novas Tentativas.</span><span class="sxs-lookup"><span data-stu-id="d5458-112">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="d5458-113">O padrão de Novas Tentativas permite que um aplicativo repita uma operação na expectativa de que a ela acabará sendo bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d5458-113">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="d5458-114">O padrão de Disjuntor impede que um aplicativo execute uma operação que é provavelmente falhará.</span><span class="sxs-lookup"><span data-stu-id="d5458-114">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="d5458-115">Um aplicativo pode combinar esses dois padrões usando o padrão de Novas Tentativas para invocar uma operação por meio de um disjuntor.</span><span class="sxs-lookup"><span data-stu-id="d5458-115">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="d5458-116">No entanto, a lógica de novas tentativas deve ser sensível a qualquer exceção retornada pelo disjuntor e deve abandonar tentativas de repetição se o disjuntor indica que uma falha não é transitória.</span><span class="sxs-lookup"><span data-stu-id="d5458-116">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="d5458-117">Implementar um padrão de Disjuntor com Polly</span><span class="sxs-lookup"><span data-stu-id="d5458-117">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="d5458-118">Como durante a implementação de novas tentativas, a abordagem recomendada para disjuntores é aproveitar as comprovadas bibliotecas .NET, como Polly.</span><span class="sxs-lookup"><span data-stu-id="d5458-118">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="d5458-119">O aplicativo eShopOnContainers usa a política de Disjuntor do Polly durante a implementação de novas tentativas HTTP.</span><span class="sxs-lookup"><span data-stu-id="d5458-119">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="d5458-120">Na verdade, o aplicativo se aplica a ambas as políticas para a classe de utilitários ResilientHttpClient.</span><span class="sxs-lookup"><span data-stu-id="d5458-120">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="d5458-121">Sempre que você usar um objeto do tipo ResilientHttpClient para solicitações HTTP (da eShopOnContainers), estará aplicando essas duas políticas, mas poderá adicionar mais políticas também.</span><span class="sxs-lookup"><span data-stu-id="d5458-121">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="d5458-122">Aqui, a única adição ao código usado para novas tentativas de chamada HTTP é o código em que você adiciona a política de Disjuntor à lista de políticas a usar, conforme mostrado no final do código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5458-122">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
            // number of retries
            6,
            // exponential backofff
            retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
            // on retry
            (exception, timeSpan, retryCount, context) =>
            {
                var msg = $"Retry {retryCount} implemented with Polly RetryPolicy " +
                    $"of {context.PolicyKey} " +
                    $"at {context.ExecutionKey}, " +
                    $"due to: {exception}.";
                _logger.LogWarning(msg);
                _logger.LogDebug(msg);
            }),
            Policy.Handle<HttpRequestException>()
                .CircuitBreakerAsync(
                    // number of exceptions before breaking circuit
                    5,
                    // time circuit opened before retry
                    TimeSpan.FromMinutes(1),
                    (exception, duration) =>
                    {
                        // on circuit opened
                        _logger.LogTrace("Circuit breaker opened");
                    },
                    () =>
                    {
                        // on circuit closed
                        _logger.LogTrace("Circuit breaker reset");
                    })
    };
}
```

<span data-ttu-id="d5458-123">O código adiciona uma política ao wrapper HTTP.</span><span class="sxs-lookup"><span data-stu-id="d5458-123">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="d5458-124">Essa política define um disjuntor que se abre quando o código detecta o número especificado de exceções consecutivas (exceções em sequência), conforme passado no parâmetro exceptionsAllowedBeforeBreaking (cinco, neste caso).</span><span class="sxs-lookup"><span data-stu-id="d5458-124">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="d5458-125">Quando o circuito está aberto, as solicitações HTTP não funcionam, mas uma exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="d5458-125">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="d5458-126">Disjuntores também deverão ser usados para redirecionar solicitações para uma infraestrutura de fallback se puder ter problemas em um recurso específico implantado em um ambiente diferente do aplicativo cliente ou do serviço que está executando a chamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="d5458-126">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="d5458-127">Dessa forma, se houver uma interrupção no datacenter que afete apenas os microsserviços de back-end, mas não os aplicativos cliente, os aplicativos cliente poderão redirecionar para os serviços de fallback.</span><span class="sxs-lookup"><span data-stu-id="d5458-127">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="d5458-128">O Polly está planejando uma nova política para automatizar esse cenário de [política de failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy).</span><span class="sxs-lookup"><span data-stu-id="d5458-128">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="d5458-129">Obviamente, todos esses recursos são para casos em que você está gerenciando o failover de dentro do código .NET, em vez de deixar que o Azure o gerencie automaticamente para você, com transparência de local.</span><span class="sxs-lookup"><span data-stu-id="d5458-129">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="d5458-130">Usando a classe de utilitário ResilientHttpClient de eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="d5458-130">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="d5458-131">Você pode usar a classe de utilitário ResilientHttpClient de modo semelhante a como usa a classe .NET HttpClient.</span><span class="sxs-lookup"><span data-stu-id="d5458-131">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="d5458-132">No exemplo a seguir do aplicativo Web do MVC eShopOnContainers (a classe de agente OrderingService usada por OrderController), o objeto ResilientHttpClient é injetado pelo parâmetro httpClient do construtor.</span><span class="sxs-lookup"><span data-stu-id="d5458-132">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="d5458-133">Então o objeto é usado para executar solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="d5458-133">Then the object is used to perform HTTP requests.</span></span>

```csharp
public class OrderingService : IOrderingService
{
    private IHttpClient _apiClient;
    private readonly string _remoteServiceBaseUrl;
    private readonly IOptionsSnapshot<AppSettings> _settings;
    private readonly IHttpContextAccessor _httpContextAccesor;

    public OrderingService(IOptionsSnapshot<AppSettings> settings,
        IHttpContextAccessor httpContextAccesor,
        IHttpClient httpClient)
    {
        _remoteServiceBaseUrl = $"{settings.Value.OrderingUrl}/api/v1/orders";
        _settings = settings;
        _httpContextAccesor = httpContextAccesor;
        _apiClient = httpClient;
    }

    async public Task<List<Order>> GetMyOrders(ApplicationUser user)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        var ordersUrl = _remoteServiceBaseUrl;
        var dataString = await _apiClient.GetStringAsync(ordersUrl);
        var response = JsonConvert.DeserializeObject<List<Order>>(dataString);
        return response;
    }

    // Other methods ...
    async public Task CreateOrder(Order order)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        _apiClient.Inst.DefaultRequestHeaders.Add("x-requestid",
            order.RequestId.ToString());
        var ordersUrl = $"{_remoteServiceBaseUrl}/new";
        order.CardTypeId = 1;
        order.CardExpirationApiFormat();
        SetFakeIdToProducts(order);
        var response = await _apiClient.PostAsync(ordersUrl, order);
        response.EnsureSuccessStatusCode();
    }
}
```

<span data-ttu-id="d5458-134">Sempre que o membro do objeto \_apiClient é usado, ele usa internamente a classe wrapper com políticas do Polly: a política de repetição, a política de Disjuntor e outra política que talvez você queira aplicar da coleção de políticas do Polly.</span><span class="sxs-lookup"><span data-stu-id="d5458-134">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="d5458-135">Testando repetições em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="d5458-135">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="d5458-136">Sempre que você inicia a solução eShopOnContainers em um host do Docker, ela precisa iniciar vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="d5458-136">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="d5458-137">Alguns dos contêineres são mais lentos em iniciar e inicializar, como o contêiner do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d5458-137">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="d5458-138">Isso é especialmente verdadeiro na primeira vez que você implanta o aplicativo eShopOnContainers no Docker, porque é necessário configurar as imagens e o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d5458-138">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="d5458-139">O fato de que alguns contêineres iniciam mais lentamente do que outros pode fazer o restante dos serviços lançarem exceções HTTP, mesmo que você defina dependências entre contêineres no nível do Docker Compose, como explicado nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="d5458-139">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="d5458-140">Essas dependências do Docker Compose entre os contêineres são apenas no nível do processo.</span><span class="sxs-lookup"><span data-stu-id="d5458-140">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="d5458-141">O processo de ponto de entrada do contêiner pode ser iniciado, mas o SQL Server talvez não esteja pronto para consultas.</span><span class="sxs-lookup"><span data-stu-id="d5458-141">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="d5458-142">O resultado pode ser uma cascata de erros e o aplicativo pode obter uma exceção ao tentar consumir aquele contêiner específico.</span><span class="sxs-lookup"><span data-stu-id="d5458-142">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="d5458-143">Você também pode ver esse tipo de erro na inicialização quando o aplicativo está sendo implantado para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="d5458-143">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="d5458-144">Nesse caso, os orquestradores poderão estar movendo contêineres de um nó ou VM para outro (ou seja, começando novas instâncias) ao equilibrar o número de contêineres entre nós do cluster.</span><span class="sxs-lookup"><span data-stu-id="d5458-144">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="d5458-145">A maneira como o eShopOnContainers resolve esse problema é usando o padrão de Novas Tentativas ilustrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d5458-145">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="d5458-146">Também é por isso que, ao iniciar a solução, você poderá obter rastreamentos de log ou avisos semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5458-146">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="d5458-147">"**Nova Tentativa 1 implementada com RetryPolicy do Polly** devido a: System.Net.Http.HttpRequestException: ocorreu um erro ao enviar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="d5458-147">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="d5458-148"> ---&gt; System.Net.Http.CurlException: não foi possível conectar-se ao servidor\\n em System.Net.Http.CurlHandler.ThrowIfCURLEError (erro CURLcode)\\n em \[…\].</span><span class="sxs-lookup"><span data-stu-id="d5458-148"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="d5458-149">Testando o disjuntor em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="d5458-149">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="d5458-150">Existem algumas maneiras de abrir o circuito e testá-lo com eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="d5458-150">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="d5458-151">Uma opção é reduzir o número permitido de novas tentativas a 1 na política de disjuntor e reimplantar toda a solução no Docker.</span><span class="sxs-lookup"><span data-stu-id="d5458-151">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="d5458-152">Com uma única nova tentativa, há uma boa chance de que uma solicitação HTTP falhe durante a implantação, o disjuntor se abra e você receba um erro.</span><span class="sxs-lookup"><span data-stu-id="d5458-152">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="d5458-153">Outra opção é usar o middleware personalizado implementado no microsserviço `Basket`.</span><span class="sxs-lookup"><span data-stu-id="d5458-153">Another option is to use custom middleware that is implemented in the `Basket` microservice.</span></span> <span data-ttu-id="d5458-154">Quando esse middleware é habilitado, ele captura todas as solicitações HTTP e retorna o código de status 500.</span><span class="sxs-lookup"><span data-stu-id="d5458-154">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="d5458-155">Você pode habilitar o middleware fazendo uma solicitação GET para o URI de falha, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5458-155">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="d5458-156">GET /failing</span><span class="sxs-lookup"><span data-stu-id="d5458-156">GET /failing</span></span>

<span data-ttu-id="d5458-157">Essa solicitação retorna o estado atual do middleware.</span><span class="sxs-lookup"><span data-stu-id="d5458-157">This request returns the current state of the middleware.</span></span> <span data-ttu-id="d5458-158">Se o middleware estiver habilitado, a solicitação retornará o código de status 500.</span><span class="sxs-lookup"><span data-stu-id="d5458-158">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="d5458-159">Se o middleware estiver desabilitado, não haverá nenhuma resposta.</span><span class="sxs-lookup"><span data-stu-id="d5458-159">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="d5458-160">GET /failing?enable</span><span class="sxs-lookup"><span data-stu-id="d5458-160">GET /failing?enable</span></span>

<span data-ttu-id="d5458-161">Essa solicitação habilita o middleware.</span><span class="sxs-lookup"><span data-stu-id="d5458-161">This request enables the middleware.</span></span>

-   <span data-ttu-id="d5458-162">GET /failing?disable</span><span class="sxs-lookup"><span data-stu-id="d5458-162">GET /failing?disable</span></span>

<span data-ttu-id="d5458-163">Essa solicitação desabilita o middleware.</span><span class="sxs-lookup"><span data-stu-id="d5458-163">This request disables the middleware.</span></span>

<span data-ttu-id="d5458-164">Por exemplo, quando o aplicativo estiver em execução, você poderá habilitar o middleware fazendo uma solicitação usando o seguinte URI em qualquer navegador.</span><span class="sxs-lookup"><span data-stu-id="d5458-164">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="d5458-165">Observe que o microsserviço de ordenação usa a porta 5103.</span><span class="sxs-lookup"><span data-stu-id="d5458-165">Note that the ordering microservice uses port 5103.</span></span>

http://localhost:5103/failing?enable

<span data-ttu-id="d5458-166">Em seguida, verifique o status usando o URI [http://localhost:5103/failing](http://localhost:5103/failing), conforme mostrado na Figura 10-4.</span><span class="sxs-lookup"><span data-stu-id="d5458-166">You can then check the status using the URI [http://localhost:5103/failing](http://localhost:5103/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="d5458-167">**Figura 10-4**.</span><span class="sxs-lookup"><span data-stu-id="d5458-167">**Figure 10-4**.</span></span> <span data-ttu-id="d5458-168">Verificando o estado do middleware ASP.NET com "Falha" – neste caso, desabilitado.</span><span class="sxs-lookup"><span data-stu-id="d5458-168">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="d5458-169">Neste ponto, o de microsserviço Cesta responde com o código de status 500 sempre que você o chama ou invoca.</span><span class="sxs-lookup"><span data-stu-id="d5458-169">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="d5458-170">Depois que o middleware estiver em execução, você poderá tentar fazer um pedido do aplicativo Web MVC.</span><span class="sxs-lookup"><span data-stu-id="d5458-170">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="d5458-171">Como as solicitações falham, o circuito é aberto.</span><span class="sxs-lookup"><span data-stu-id="d5458-171">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="d5458-172">No exemplo a seguir, você pode ver que o aplicativo Web MVC tem um bloco catch na lógica para fazer um pedido.</span><span class="sxs-lookup"><span data-stu-id="d5458-172">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="d5458-173">Se o código capturar uma exceção de circuito aberto, ele mostrará ao usuário uma mensagem amigável informando-o para esperar.</span><span class="sxs-lookup"><span data-stu-id="d5458-173">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            //… Other code
        }
        catch (BrokenCircuitException)
        {
            // Catches error when Basket.api is in circuit-opened mode                 
            HandleBrokenCircuitException();
        }
        return View();
    }       

    private void HandleBrokenCircuitException()
    {
        TempData["BasketInoperativeMsg"] = "Basket Service is inoperative, please try later on. (Business message due to Circuit-Breaker)";
    }
}
```

<span data-ttu-id="d5458-174">Segue um resumo.</span><span class="sxs-lookup"><span data-stu-id="d5458-174">Here’s a summary.</span></span> <span data-ttu-id="d5458-175">A política de repetição tenta várias vezes fazer a solicitação HTTP e obtém os erros HTTP.</span><span class="sxs-lookup"><span data-stu-id="d5458-175">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="d5458-176">Quando o número de novas tentativas atinge o número máximo definido para a política de Disjuntor (neste caso, 5), o aplicativo gera uma BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="d5458-176">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="d5458-177">O resultado é uma mensagem amigável, como mostra a Figura 10-5.</span><span class="sxs-lookup"><span data-stu-id="d5458-177">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="d5458-178">**Figura 10-5**.</span><span class="sxs-lookup"><span data-stu-id="d5458-178">**Figure 10-5**.</span></span> <span data-ttu-id="d5458-179">Disjuntor retornando um erro na interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d5458-179">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="d5458-180">Você pode implementar uma lógica diferente de quando abrir o circuito.</span><span class="sxs-lookup"><span data-stu-id="d5458-180">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="d5458-181">Ou você poderá tentar uma solicitação HTTP para um microsserviço de back-end diferente se houver um datacenter de fallback ou um sistema redundante de back-end.</span><span class="sxs-lookup"><span data-stu-id="d5458-181">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="d5458-182">Por fim, outra possibilidade do CircuitBreakerPolicy é usar Isolar (que força a abertura e mantém o circuito aberto) e Reiniciar (que o fecha novamente).</span><span class="sxs-lookup"><span data-stu-id="d5458-182">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="d5458-183">Isso pode ser usado para criar um ponto de extremidade HTTP de utilitário que invoque Isolar e Reiniciar diretamente na política.</span><span class="sxs-lookup"><span data-stu-id="d5458-183">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="d5458-184">Esse ponto de extremidade HTTP também pode ser usado, adequadamente protegido, em produção para isolar temporariamente um sistema downstream, como quando você deseja atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="d5458-184">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="d5458-185">Ou poderia desarmar o circuito manualmente para proteger o sistema a downstream que você suspeita ter falha.</span><span class="sxs-lookup"><span data-stu-id="d5458-185">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="d5458-186">Adicionando uma estratégia de tremulação à política de repetição</span><span class="sxs-lookup"><span data-stu-id="d5458-186">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="d5458-187">Uma política de Repetição regular pode afetar o sistema em casos de alta simultaneidade e escalabilidade e sob alta contenção.</span><span class="sxs-lookup"><span data-stu-id="d5458-187">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="d5458-188">Para superar os picos de novas tentativas semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação à política/ao algoritmo de novas tentativas.</span><span class="sxs-lookup"><span data-stu-id="d5458-188">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="d5458-189">Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade à retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="d5458-189">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="d5458-190">Isso espalha os picos quando surgem problemas.</span><span class="sxs-lookup"><span data-stu-id="d5458-190">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="d5458-191">Quando você usa o Polly, o código para implementar a variação pode se parecer com o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5458-191">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="d5458-192">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d5458-192">Additional resources</span></span>

-   <span data-ttu-id="d5458-193">**Padrão de repetição**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="d5458-193">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="d5458-194">**Resiliência de conexão** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="d5458-194">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="d5458-195">**Polly** (biblioteca de tratamento de falhas transitórias e resiliência do .NET) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="d5458-195">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="d5458-196">**Padrão de disjuntor**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="d5458-196">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="d5458-197">**Marc Brooker. Tremulação: melhorando as coisas com aleatoriedade** https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="d5458-197">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d5458-198">[Anterior](implement-http-call-retries-exponential-backoff-polly.md)
[Próximo](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="d5458-198">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
