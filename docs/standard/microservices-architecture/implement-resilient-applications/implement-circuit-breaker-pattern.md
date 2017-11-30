---
title: "Implementando o padrão de Disjuntor"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementando o padrão de Disjuntor"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2a629e25a7565aaba156f68cf06d9a24b6c2b8b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="10ac4-104">Implementando o padrão de Disjuntor</span><span class="sxs-lookup"><span data-stu-id="10ac4-104">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="10ac4-105">Conforme observado anteriormente, você deve tratar falhas que podem consumir uma quantidade variável de tempo de recuperação, como pode acontecer quando você tentar se conectar a um serviço remoto ou um recurso.</span><span class="sxs-lookup"><span data-stu-id="10ac4-105">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="10ac4-106">Esse tipo de falha de tratamento pode melhorar a estabilidade e a resiliência de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10ac4-106">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="10ac4-107">Em um ambiente distribuído, chamadas para serviços e recursos remotos pode falhar devido a falhas transitórias, como conexões lentas de rede e o tempo limite, ou se os recursos estão sendo lenta ou estão temporariamente indisponíveis.</span><span class="sxs-lookup"><span data-stu-id="10ac4-107">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="10ac4-108">Essas falhas geralmente corrigidos automaticamente após um curto período de tempo e um aplicativo em nuvem robusto deve estar preparado para lidar com eles por meio de uma estratégia de como o padrão de repetição.</span><span class="sxs-lookup"><span data-stu-id="10ac4-108">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="10ac4-109">No entanto, também pode haver situações em que as falhas são devido a eventos inesperados que podem levar muito mais tempo para corrigir.</span><span class="sxs-lookup"><span data-stu-id="10ac4-109">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="10ac4-110">Essas falhas podem variar de severidade de uma perda parcial de conectividade para a falha completa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="10ac4-110">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="10ac4-111">Nessas situações, pode ser sem sentido para um aplicativo tentará continuamente uma operação que é improvável que seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="10ac4-111">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="10ac4-112">Em vez disso, o aplicativo deve ser codificado para aceitar a operação falhou e lidar com falhas adequadamente.</span><span class="sxs-lookup"><span data-stu-id="10ac4-112">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="10ac4-113">O padrão de disjuntor tem uma finalidade diferente que o padrão de repetição.</span><span class="sxs-lookup"><span data-stu-id="10ac4-113">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="10ac4-114">O padrão de repetição permite que um aplicativo repetir uma operação na expectativa de que a operação eventualmente será bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="10ac4-114">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="10ac4-115">O padrão de disjuntor impede que um aplicativo executando uma operação que é provavelmente falharão.</span><span class="sxs-lookup"><span data-stu-id="10ac4-115">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="10ac4-116">Um aplicativo pode combinar esses dois padrões usando o padrão de repetição para invocar uma operação por meio de um disjuntor.</span><span class="sxs-lookup"><span data-stu-id="10ac4-116">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="10ac4-117">No entanto, a lógica de repetição deve ser sensível a qualquer exceção retornadas pelo Disjuntor, e ele deve abandonar tentativas de repetição se o disjuntor indica que uma falha não é transitória.</span><span class="sxs-lookup"><span data-stu-id="10ac4-117">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="10ac4-118">Implementar um padrão de disjuntor com Polly</span><span class="sxs-lookup"><span data-stu-id="10ac4-118">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="10ac4-119">Como durante a implementação de novas tentativas, a abordagem recomendada para disjuntores é tirar proveito das comprovada bibliotecas .NET como Polly.</span><span class="sxs-lookup"><span data-stu-id="10ac4-119">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="10ac4-120">O aplicativo de eShopOnContainers usa a política de disjuntor Polly durante a implementação de novas tentativas HTTP.</span><span class="sxs-lookup"><span data-stu-id="10ac4-120">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="10ac4-121">Na verdade, o aplicativo se aplica a ambas as políticas para a classe de utilitário ResilientHttpClient.</span><span class="sxs-lookup"><span data-stu-id="10ac4-121">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="10ac4-122">Sempre que você usar um objeto do tipo ResilientHttpClient solicitações HTTP (da eShopOnContainers), você aplicará os dois essas políticas, mas você pode adicionar políticas adicionais, muito.</span><span class="sxs-lookup"><span data-stu-id="10ac4-122">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="10ac4-123">A adição somente para o código usado para novas tentativas de chamada HTTP é o código em que a política de disjuntor é adicionar à lista de políticas para usar, conforme mostrado no final do código a seguir:</span><span class="sxs-lookup"><span data-stu-id="10ac4-123">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

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

<span data-ttu-id="10ac4-124">O código adiciona uma política para o wrapper HTTP.</span><span class="sxs-lookup"><span data-stu-id="10ac4-124">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="10ac4-125">Se a diretiva define um disjuntor é aberta quando o código detecta o número especificado de exceções consecutivos (exceções em uma linha), como passado no parâmetro exceptionsAllowedBeforeBreaking (5 neste caso).</span><span class="sxs-lookup"><span data-stu-id="10ac4-125">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="10ac4-126">Quando o circuito está aberto, solicitações HTTP não funcionam, mas uma exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="10ac4-126">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="10ac4-127">Disjuntores também deve ser usados para redirecionar solicitações para uma infraestrutura de fallback se você pode ter problemas em um recurso específico que é implantado em um ambiente diferente do que o aplicativo cliente ou serviço que está executando a chamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="10ac4-127">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="10ac4-128">Dessa forma, se houver uma interrupção no datacenter, que afeta apenas o microservices de back-end, mas não seus aplicativos de cliente, os aplicativos cliente podem redirecionar para os serviços de fallbacks.</span><span class="sxs-lookup"><span data-stu-id="10ac4-128">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="10ac4-129">Polly está planejando uma nova política para automatizar esse procedimento [política de failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) cenário.</span><span class="sxs-lookup"><span data-stu-id="10ac4-129">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="10ac4-130">Obviamente, todos esses recursos são para casos em que você está gerenciando o failover de dentro do código do .NET, em vez de tê-la gerenciadas automaticamente para você pelo Azure, com transparência de local.</span><span class="sxs-lookup"><span data-stu-id="10ac4-130">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="10ac4-131">Usando a classe de utilitário ResilientHttpClient de eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="10ac4-131">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="10ac4-132">Você pode usar a classe de utilitário ResilientHttpClient de forma semelhante de como usar a classe .NET HttpClient.</span><span class="sxs-lookup"><span data-stu-id="10ac4-132">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="10ac4-133">No exemplo a seguir do aplicativo da web do MVC eShopOnContainers (a classe de agente OrderingService usada por OrderController), o objeto ResilientHttpClient é injetado pelo parâmetro httpClient do construtor.</span><span class="sxs-lookup"><span data-stu-id="10ac4-133">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="10ac4-134">Em seguida, o objeto é usado para executar solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="10ac4-134">Then the object is used to perform HTTP requests.</span></span>

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

<span data-ttu-id="10ac4-135">Sempre que o \_apiClient objeto de membro for usado, ele usa internamente a classe de invólucro com Polly policiesؙ — a política de repetição, a política de disjuntor e outra política que talvez você queira aplicar da coleção de políticas Polly.</span><span class="sxs-lookup"><span data-stu-id="10ac4-135">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="10ac4-136">Testando as repetições em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="10ac4-136">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="10ac4-137">Sempre que iniciar a solução de eShopOnContainers em um host do Docker, ela precisa iniciar vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="10ac4-137">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="10ac4-138">Alguns dos contêineres são mais lentos para iniciar e inicializar, como o contêiner do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="10ac4-138">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="10ac4-139">Isso é especialmente verdadeiro na primeira vez que você implantar o aplicativo eShopOnContainers no Docker, porque é necessário configurar as imagens e o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="10ac4-139">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="10ac4-140">O fato de que alguns contêineres mais lenta do que outros podem causar o restante dos serviços inicialmente lançar exceções de HTTP, mesmo se você definir dependências entre contêineres em iniciam a compor docker nível, conforme explicado nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="10ac4-140">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="10ac4-141">Os docker-compõem as dependências entre os contêineres são apenas no nível do processo.</span><span class="sxs-lookup"><span data-stu-id="10ac4-141">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="10ac4-142">O processo de ponto de entrada do contêiner pode ser iniciado, mas o SQL Server talvez não esteja pronto para consultas.</span><span class="sxs-lookup"><span data-stu-id="10ac4-142">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="10ac4-143">O resultado pode ser uma cascata de erros e o aplicativo pode obter uma exceção ao tentar consumir esse contêiner específico.</span><span class="sxs-lookup"><span data-stu-id="10ac4-143">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="10ac4-144">Você também poderá ver esse tipo de erro na inicialização, quando o aplicativo é implantado para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="10ac4-144">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="10ac4-145">Nesse caso, orchestrators pode ser mover contêineres de um nó ou máquina virtual para outro (isto é, começando a novas instâncias) quando o número de contêineres de balanceamento entre nós do cluster.</span><span class="sxs-lookup"><span data-stu-id="10ac4-145">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="10ac4-146">É a maneira eShopOnContainers resolve esse problema usando o padrão de repetição que são ilustrados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="10ac4-146">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="10ac4-147">Também é por que, ao iniciar a solução, você poderá obter rastreamentos de log ou avisos semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="10ac4-147">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="10ac4-148">"**Repetição 1 implementado com RetryPolicy de Polly**, devido à: System.Net.Http.HttpRequestException: Ocorreu um erro ao enviar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="10ac4-148">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="10ac4-149"> ---&gt;System.Net.Http.CurlException: Não foi possível conectar ao servidor\\n em System.Net.Http.CurlHandler.ThrowIfCURLEError (erro CURLcode)\\n em \[... \].</span><span class="sxs-lookup"><span data-stu-id="10ac4-149"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="10ac4-150">Testando o disjuntor em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="10ac4-150">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="10ac4-151">Há algumas maneiras de abrir o circuito e testá-lo com eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="10ac4-151">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="10ac4-152">Uma opção é reduzir o número permitido de tentativas de 1 na política de disjuntor e reimplantar a solução completa para o Docker.</span><span class="sxs-lookup"><span data-stu-id="10ac4-152">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="10ac4-153">Com uma repetição de único, há uma boa chance de que uma solicitação HTTP falhará durante a implantação, o disjuntor será aberto e você obterá um erro.</span><span class="sxs-lookup"><span data-stu-id="10ac4-153">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="10ac4-154">Outra opção é usar o middleware personalizado que é implementado no microsserviço a ordenação.</span><span class="sxs-lookup"><span data-stu-id="10ac4-154">Another option is to use custom middleware that is implemented in the ordering microservice.</span></span> <span data-ttu-id="10ac4-155">Quando este middleware estiver habilitado, ele captura todas as solicitações HTTP e retorna o código de status 500.</span><span class="sxs-lookup"><span data-stu-id="10ac4-155">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="10ac4-156">Você pode habilitar o middleware fazendo uma solicitação GET para a falha do URI, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="10ac4-156">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="10ac4-157">OBTER/falha</span><span class="sxs-lookup"><span data-stu-id="10ac4-157">GET /failing</span></span>

<span data-ttu-id="10ac4-158">Essa solicitação retorna o estado atual do middleware.</span><span class="sxs-lookup"><span data-stu-id="10ac4-158">This request returns the current state of the middleware.</span></span> <span data-ttu-id="10ac4-159">Se o middleware estiver habilitado, a solicitação retorna o código de status 500.</span><span class="sxs-lookup"><span data-stu-id="10ac4-159">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="10ac4-160">Se o middleware está desativado, não há nenhuma resposta.</span><span class="sxs-lookup"><span data-stu-id="10ac4-160">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="10ac4-161">OBTER/falhando? habilitar</span><span class="sxs-lookup"><span data-stu-id="10ac4-161">GET /failing?enable</span></span>

<span data-ttu-id="10ac4-162">Essa solicitação permite que o middleware.</span><span class="sxs-lookup"><span data-stu-id="10ac4-162">This request enables the middleware.</span></span>

-   <span data-ttu-id="10ac4-163">OBTER/falhando? desabilitar</span><span class="sxs-lookup"><span data-stu-id="10ac4-163">GET /failing?disable</span></span>

<span data-ttu-id="10ac4-164">Essa solicitação desabilita o middleware.</span><span class="sxs-lookup"><span data-stu-id="10ac4-164">This request disables the middleware.</span></span>

<span data-ttu-id="10ac4-165">Por exemplo, quando o aplicativo estiver em execução, você pode habilitar o middleware fazendo uma solicitação usando o seguinte URI em qualquer navegador.</span><span class="sxs-lookup"><span data-stu-id="10ac4-165">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="10ac4-166">Observe que a ordenação microsserviço usa a porta 5102.</span><span class="sxs-lookup"><span data-stu-id="10ac4-166">Note that the ordering microservice uses port 5102.</span></span>

<span data-ttu-id="10ac4-167">http://localhost:5102 / falhando? habilitar</span><span class="sxs-lookup"><span data-stu-id="10ac4-167">http://localhost:5102/failing?enable</span></span>

<span data-ttu-id="10ac4-168">Em seguida, você pode verificar o status usando o URI de [http://localhost:5102 / falha](http://localhost:5100/failing), conforme mostrado na Figura 10-4.</span><span class="sxs-lookup"><span data-stu-id="10ac4-168">You can then check the status using the URI [http://localhost:5102/failing](http://localhost:5100/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="10ac4-169">**Figura 10-4**.</span><span class="sxs-lookup"><span data-stu-id="10ac4-169">**Figure 10-4**.</span></span> <span data-ttu-id="10ac4-170">Simulando uma falha com o ASP.NET middleware</span><span class="sxs-lookup"><span data-stu-id="10ac4-170">Simulating a failure with ASP.NET middleware</span></span>

<span data-ttu-id="10ac4-171">Neste ponto, o ordenação responde de microsserviço com código de status 500 sempre que você chamar invocá-lo.</span><span class="sxs-lookup"><span data-stu-id="10ac4-171">At this point, the ordering microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="10ac4-172">Depois que o middleware está em execução, você pode tentar fazer um pedido do aplicativo da web MVC.</span><span class="sxs-lookup"><span data-stu-id="10ac4-172">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="10ac4-173">Como as solicitações falhar, o circuito será aberto.</span><span class="sxs-lookup"><span data-stu-id="10ac4-173">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="10ac4-174">No exemplo a seguir, você pode ver que o aplicativo da web MVC tem um catch bloquear na lógica para fazer um pedido.</span><span class="sxs-lookup"><span data-stu-id="10ac4-174">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="10ac4-175">Se o código de captura uma exceção de circuito aberto, ele mostra o usuário uma mensagem amigável informando de espera.</span><span class="sxs-lookup"><span data-stu-id="10ac4-175">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
[HttpPost]
public async Task<IActionResult> Create(Order model, string action)
{
    try
    {
        if (ModelState.IsValid)
        {
            var user = _appUserParser.Parse(HttpContext.User);
            await _orderSvc.CreateOrder(model);
            //Redirect to historic list.
            return RedirectToAction("Index");
        }
    }
    catch(BrokenCircuitException ex)
    {
        ModelState.AddModelError("Error",
            "It was not possible to create a new order, please try later on");
    }
    return View(model);
}
```

<span data-ttu-id="10ac4-176">Aqui está um resumo.</span><span class="sxs-lookup"><span data-stu-id="10ac4-176">Here’s a summary.</span></span> <span data-ttu-id="10ac4-177">A política de repetição tenta várias vezes para fazer a solicitação HTTP e obtém os erros HTTP.</span><span class="sxs-lookup"><span data-stu-id="10ac4-177">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="10ac4-178">Quando o número de tentativas atinge o número máximo definido para a política de Disjuntor (nesse caso, 5), o aplicativo gera um BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="10ac4-178">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="10ac4-179">O resultado é uma mensagem amigável, como mostrado na Figura 10-5.</span><span class="sxs-lookup"><span data-stu-id="10ac4-179">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="10ac4-180">**Figura 10-5**.</span><span class="sxs-lookup"><span data-stu-id="10ac4-180">**Figure 10-5**.</span></span> <span data-ttu-id="10ac4-181">Disjuntor retornando um erro na interface do usuário</span><span class="sxs-lookup"><span data-stu-id="10ac4-181">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="10ac4-182">Você pode implementar uma lógica diferente de quando o circuito aberto.</span><span class="sxs-lookup"><span data-stu-id="10ac4-182">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="10ac4-183">Ou você pode tentar uma solicitação HTTP em um microsserviço de back-end diferente, se houver um fallback datacenter ou um sistema redundante de back-end.</span><span class="sxs-lookup"><span data-stu-id="10ac4-183">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="10ac4-184">Por fim, outra possibilidade do CircuitBreakerPolicy é usar isolam (que força aberto e mantém aberta do circuito) e redefinição (que fecha novamente).</span><span class="sxs-lookup"><span data-stu-id="10ac4-184">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="10ac4-185">Essas páginas podem ser usadas para criar um ponto de extremidade HTTP de utilitário que invoca a isolar e redefina diretamente na política.</span><span class="sxs-lookup"><span data-stu-id="10ac4-185">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="10ac4-186">Tal um ponto de extremidade HTTP também pode ser usado, adequadamente protegidos em produção para isolar temporariamente um sistema downstream, como quando você deseja atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="10ac4-186">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="10ac4-187">Ou, ele poderia trip circuito manualmente para proteger o sistema downstream que suspeito ser com falha.</span><span class="sxs-lookup"><span data-stu-id="10ac4-187">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="10ac4-188">Adicionando uma estratégia de variação para a política de repetição</span><span class="sxs-lookup"><span data-stu-id="10ac4-188">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="10ac4-189">Uma política de repetição regular pode afetar o sistema em casos de escalabilidade e alta simultaneidade e em alto de contenção.</span><span class="sxs-lookup"><span data-stu-id="10ac4-189">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="10ac4-190">Para superar os picos de repetições semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação para a algoritmo/política de repetição.</span><span class="sxs-lookup"><span data-stu-id="10ac4-190">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="10ac4-191">Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade para a retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="10ac4-191">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="10ac4-192">Isso se espalha os picos quando surgem problemas.</span><span class="sxs-lookup"><span data-stu-id="10ac4-192">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="10ac4-193">Quando você usa Polly, código para implementar a tremulação pode parecer com o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="10ac4-193">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="10ac4-194">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="10ac4-194">Additional resources</span></span>

-   <span data-ttu-id="10ac4-195">**Repita padrão**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="10ac4-195">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="10ac4-196">**Resiliência de Conexão** (Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="10ac4-196">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="10ac4-197">**Polly** (biblioteca de tratamento de falhas transitórias e resiliência do .NET) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="10ac4-197">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="10ac4-198">**Padrão de disjuntor**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="10ac4-198">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="10ac4-199">**Marc Esteves. Variação: Tornar as coisas melhor com aleatoriedade** https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="10ac4-199">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="10ac4-200">[Anterior] (implement-http-call-retries-exponential-backoff-polly.md) [Avançar] (monitor-aplicativo-health.md)</span><span class="sxs-lookup"><span data-stu-id="10ac4-200">[Previous] (implement-http-call-retries-exponential-backoff-polly.md) [Next] (monitor-app-health.md)</span></span>
