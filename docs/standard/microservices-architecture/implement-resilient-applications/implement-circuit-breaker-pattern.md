---
title: Implementando o padrão de Disjuntor
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementar o padrão de disjuntor como um sistema complementar para repetições de HTTP
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 8cd3564e5240ec5a8783edb336957549be27ea6a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274551"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="5925f-103">Implementar o padrão de disjuntor</span><span class="sxs-lookup"><span data-stu-id="5925f-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="5925f-104">Conforme observado anteriormente, você deve tratar falhas que podem consumir uma quantidade variável de tempo de recuperação, como pode acontecer quando você tenta se conectar a um serviço ou um recurso remoto.</span><span class="sxs-lookup"><span data-stu-id="5925f-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="5925f-105">Lidar com esse tipo de falha pode melhorar a estabilidade e a resiliência de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5925f-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="5925f-106">Em um ambiente distribuído, chamadas para serviços e recursos remotos poderão falhar devido a falhas transitórias, como conexões lentas de rede e tempos limites ou se os recursos estiverem lentos ou temporariamente não disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5925f-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="5925f-107">Essas falhas geralmente são corrigidas automaticamente após um curto período, e um aplicativo em nuvem robusto deve estar preparado para lidar com elas usando uma estratégia como o “padrão de repetição”.</span><span class="sxs-lookup"><span data-stu-id="5925f-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span> 

<span data-ttu-id="5925f-108">No entanto, também pode haver situações em que as falhas são devido a eventos inesperados que podem levar muito mais tempo para serem corrigidos.</span><span class="sxs-lookup"><span data-stu-id="5925f-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="5925f-109">Essas falhas podem variar em termos de gravidade de uma perda parcial de conectividade até a falha completa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="5925f-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="5925f-110">Nessas situações, pode não ter sentido um aplicativo repetir continuamente uma operação que é improvável que seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5925f-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> 

<span data-ttu-id="5925f-111">Em vez disso, o aplicativo deve ser codificado para aceitar que a operação falhou e lidar com falhas adequadamente.</span><span class="sxs-lookup"><span data-stu-id="5925f-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="5925f-112">O mau uso das repetições de HTTP pode resultar na criação de um ataque de [DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack) (negação de serviço) dentro do próprio software.</span><span class="sxs-lookup"><span data-stu-id="5925f-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="5925f-113">Quando um microsserviço falha ou apresenta um desempenho lento, vários clientes podem fazer novas tentativas de solicitações com falha repetidamente.</span><span class="sxs-lookup"><span data-stu-id="5925f-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="5925f-114">Isso cria um risco perigoso de aumentar exponencialmente o tráfego direcionado ao serviço com falha.</span><span class="sxs-lookup"><span data-stu-id="5925f-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="5925f-115">Portanto, é necessário algum tipo de barreira de defesa para que as solicitações excessivas sejam interrompidas quando não valer a pena continuar tentando.</span><span class="sxs-lookup"><span data-stu-id="5925f-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it is not worth keeping trying.</span></span> <span data-ttu-id="5925f-116">Essa barreira de defesa é exatamente o disjuntor.</span><span class="sxs-lookup"><span data-stu-id="5925f-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="5925f-117">O padrão de disjuntor tem uma finalidade diferente do "padrão de repetição".</span><span class="sxs-lookup"><span data-stu-id="5925f-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="5925f-118">O “padrão de repetição” permite que um aplicativo repita uma operação na expectativa de que a ela acabará sendo bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5925f-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="5925f-119">O padrão de Disjuntor impede que um aplicativo execute uma operação que é provavelmente falhará.</span><span class="sxs-lookup"><span data-stu-id="5925f-119">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="5925f-120">O aplicativo pode combinar esses dois padrões.</span><span class="sxs-lookup"><span data-stu-id="5925f-120">An application can combine these two patterns.</span></span> <span data-ttu-id="5925f-121">No entanto, a lógica de repetição deve reconhecer qualquer exceção retornada pelo disjuntor e deve abandonar as tentativas de repetição quando o disjuntor indica que uma falha não é transitória.</span><span class="sxs-lookup"><span data-stu-id="5925f-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a><span data-ttu-id="5925f-122">Implementar o padrão de disjuntor com HttpClientFactory e Polly</span><span class="sxs-lookup"><span data-stu-id="5925f-122">Implement Circuit Breaker pattern with HttpClientFactory and Polly</span></span>

<span data-ttu-id="5925f-123">Como durante a implementação de repetições, a abordagem recomendada para disjuntores é aproveitar as comprovadas bibliotecas do .NET, como a Polly e sua integração nativa com o HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="5925f-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with HttpClientFactory.</span></span>

<span data-ttu-id="5925f-124">Adicionar uma política de disjuntor no pipeline do middleware de saída do HttpClientFactory é tão simples quanto adicionar uma única parte incremental de código ao que você já tem ao usar HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="5925f-124">Adding a circuit breaker policy into your HttpClientFactory outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using HttpClientFactory.</span></span>

<span data-ttu-id="5925f-125">Aqui, a única adição ao código usado para repetições de chamada HTTP é o código no qual você adiciona a política de disjuntor à lista de políticas a serem usadas, conforme é mostrado no código incremental a seguir, que faz parte do método ConfigureServices().</span><span class="sxs-lookup"><span data-stu-id="5925f-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to 5 minutes
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="5925f-126">O método `AddPolicyHandler()` é o que adiciona políticas aos objetos HttpClient que serão usados.</span><span class="sxs-lookup"><span data-stu-id="5925f-126">The `AddPolicyHandler()`method is what adds policies to the HttpClient objects you will use.</span></span> <span data-ttu-id="5925f-127">Nesse caso, ele está adicionando uma política da Polly para um disjuntor.</span><span class="sxs-lookup"><span data-stu-id="5925f-127">In this case, it is adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="5925f-128">Para obter uma abordagem mais modular, a política de disjuntor é definida em um método separado chamado GetCircuitBreakerPolicy(), como o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5925f-128">In order to have a more modular approach, the Circuit Breaker Policy is defined in a separate method named GetCircuitBreakerPolicy(), as the following code.</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="5925f-129">No exemplo de código acima, a política de disjuntor é configurada para interromper ou abrir o circuito quando ocorrerem cinco falhas consecutivas ao repetir as solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="5925f-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="5925f-130">Quando isso acontece, o circuito será interrompido por 30 segundos: nesse período, chamadas falharão imediatamente pelo disjuntor em vez de serem colocadas.</span><span class="sxs-lookup"><span data-stu-id="5925f-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="5925f-131">A política automaticamente interpreta [exceções relevantes e códigos de status HTTP](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) como falhas.</span><span class="sxs-lookup"><span data-stu-id="5925f-131">The policy automatically interprets [relevant exceptions and HTTP status codes](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="5925f-132">Os disjuntores também devem ser usados para redirecionar solicitações a uma infraestrutura de fallback quando há problemas em um recurso específico implantado em um ambiente diferente do aplicativo ou do serviço cliente que está executando a chamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="5925f-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="5925f-133">Dessa forma, se houver uma interrupção no datacenter que afete apenas os microsserviços de back-end, mas não os aplicativos cliente, os aplicativos cliente poderão redirecionar para os serviços de fallback.</span><span class="sxs-lookup"><span data-stu-id="5925f-133">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="5925f-134">O Polly está planejando uma nova política para automatizar esse cenário de [política de failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy).</span><span class="sxs-lookup"><span data-stu-id="5925f-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span> 

<span data-ttu-id="5925f-135">Todos esses recursos são para casos em que você está gerenciando o failover de dentro do código do .NET, em vez de deixar que o Azure o gerencie automaticamente com transparência de local.</span><span class="sxs-lookup"><span data-stu-id="5925f-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span> 

<span data-ttu-id="5925f-136">De uma perspectiva de uso, ao usar o HttpClient, não é necessário adicionar nada de novo, porque o código é o mesmo que ao usar o HttpClient com o HttpClientFactory, conforme é mostrado nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="5925f-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using HttpClient with HttpClientFactory, as shown in previous sections.</span></span> 

## <a name="testing-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="5925f-137">Testando repetições de HTTP e disjuntores no eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="5925f-137">Testing Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="5925f-138">Sempre que você inicia a solução eShopOnContainers em um host do Docker, ela precisa iniciar vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="5925f-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="5925f-139">Alguns dos contêineres são mais lentos em iniciar e inicializar, como o contêiner do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5925f-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="5925f-140">Isso é especialmente verdadeiro na primeira vez que você implanta o aplicativo eShopOnContainers no Docker, porque é necessário configurar as imagens e o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5925f-140">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="5925f-141">O fato de que alguns contêineres iniciam mais lentamente do que outros pode fazer o restante dos serviços lançarem exceções HTTP, mesmo que você defina dependências entre contêineres no nível do Docker Compose, como explicado nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="5925f-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="5925f-142">Essas dependências do Docker Compose entre os contêineres são apenas no nível do processo.</span><span class="sxs-lookup"><span data-stu-id="5925f-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="5925f-143">O processo de ponto de entrada do contêiner pode ser iniciado, mas o SQL Server talvez não esteja pronto para consultas.</span><span class="sxs-lookup"><span data-stu-id="5925f-143">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="5925f-144">O resultado pode ser uma cascata de erros e o aplicativo pode obter uma exceção ao tentar consumir aquele contêiner específico.</span><span class="sxs-lookup"><span data-stu-id="5925f-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span> 

<span data-ttu-id="5925f-145">Você também pode ver esse tipo de erro na inicialização quando o aplicativo está sendo implantado para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="5925f-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="5925f-146">Nesse caso, os orquestradores poderão estar movendo contêineres de um nó ou VM para outro (ou seja, começando novas instâncias) ao equilibrar o número de contêineres entre nós do cluster.</span><span class="sxs-lookup"><span data-stu-id="5925f-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="5925f-147">A maneira como 'eShopOnContainers' resolve esses problemas ao iniciar todos os contêineres é usando o padrão de repetições ilustrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5925f-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span> 

### <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="5925f-148">Testando o disjuntor em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="5925f-148">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="5925f-149">Há algumas maneiras de interromper/abrir o circuito e testá-lo com o eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="5925f-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="5925f-150">Uma opção é reduzir o número permitido de novas tentativas a 1 na política de disjuntor e reimplantar toda a solução no Docker.</span><span class="sxs-lookup"><span data-stu-id="5925f-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="5925f-151">Com uma única nova tentativa, há uma boa chance de que uma solicitação HTTP falhe durante a implantação, o disjuntor se abra e você receba um erro.</span><span class="sxs-lookup"><span data-stu-id="5925f-151">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="5925f-152">Outra opção é usar o middleware personalizado implementado no microsserviço Cesta.</span><span class="sxs-lookup"><span data-stu-id="5925f-152">Another option is to use custom middleware that is implemented in the Basket microservice.</span></span> <span data-ttu-id="5925f-153">Quando esse middleware é habilitado, ele captura todas as solicitações HTTP e retorna o código de status 500.</span><span class="sxs-lookup"><span data-stu-id="5925f-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="5925f-154">Você pode habilitar o middleware fazendo uma solicitação GET para o URI de falha, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5925f-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`

<span data-ttu-id="5925f-155">Essa solicitação retorna o estado atual do middleware.</span><span class="sxs-lookup"><span data-stu-id="5925f-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="5925f-156">Se o middleware estiver habilitado, a solicitação retornará o código de status 500.</span><span class="sxs-lookup"><span data-stu-id="5925f-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="5925f-157">Se o middleware estiver desabilitado, não haverá nenhuma resposta.</span><span class="sxs-lookup"><span data-stu-id="5925f-157">If the middleware is disabled, there is no response.</span></span> 

- `GET http://localhost:5103/failing?enable`

<span data-ttu-id="5925f-158">Essa solicitação habilita o middleware.</span><span class="sxs-lookup"><span data-stu-id="5925f-158">This request enables the middleware.</span></span> 

- `GET http://localhost:5103/failing?disable`

<span data-ttu-id="5925f-159">Essa solicitação desabilita o middleware.</span><span class="sxs-lookup"><span data-stu-id="5925f-159">This request disables the middleware.</span></span> 

<span data-ttu-id="5925f-160">Por exemplo, quando o aplicativo estiver em execução, você poderá habilitar o middleware fazendo uma solicitação usando o seguinte URI em qualquer navegador.</span><span class="sxs-lookup"><span data-stu-id="5925f-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="5925f-161">Observe que o microsserviço de ordenação usa a porta 5103.</span><span class="sxs-lookup"><span data-stu-id="5925f-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable` 

<span data-ttu-id="5925f-162">Em seguida, você pode verificar o status usando o URI http://localhost:5103/failing, conforme é mostrado na Figura 10-4.</span><span class="sxs-lookup"><span data-stu-id="5925f-162">You can then check the status using the URI http://localhost:5103/failing, as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="5925f-163">**Figura 10-4**.</span><span class="sxs-lookup"><span data-stu-id="5925f-163">**Figure 10-4**.</span></span> <span data-ttu-id="5925f-164">Verificando o estado do middleware ASP.NET com "Falha" – neste caso, desabilitado.</span><span class="sxs-lookup"><span data-stu-id="5925f-164">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="5925f-165">Neste ponto, o de microsserviço Cesta responde com o código de status 500 sempre que você o chama ou invoca.</span><span class="sxs-lookup"><span data-stu-id="5925f-165">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="5925f-166">Depois que o middleware estiver em execução, você poderá tentar fazer um pedido do aplicativo Web MVC.</span><span class="sxs-lookup"><span data-stu-id="5925f-166">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="5925f-167">Como as solicitações falham, o circuito é aberto.</span><span class="sxs-lookup"><span data-stu-id="5925f-167">Because the requests fail, the circuit will open.</span></span> 

<span data-ttu-id="5925f-168">No exemplo a seguir, você pode ver que o aplicativo Web MVC tem um bloco catch na lógica para fazer um pedido.</span><span class="sxs-lookup"><span data-stu-id="5925f-168">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="5925f-169">Se o código capturar uma exceção de circuito aberto, ele mostrará ao usuário uma mensagem amigável informando-o para esperar.</span><span class="sxs-lookup"><span data-stu-id="5925f-169">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {          
            var user = _appUserParser.Parse(HttpContext.User);
            //Http requests using the Typed Client (Service Agent)
            var vm = await _basketSvc.GetBasket(user);
            return View(vm);
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

<span data-ttu-id="5925f-170">Segue um resumo.</span><span class="sxs-lookup"><span data-stu-id="5925f-170">Here’s a summary.</span></span> <span data-ttu-id="5925f-171">A política de repetição tenta várias vezes fazer a solicitação HTTP e obtém os erros HTTP.</span><span class="sxs-lookup"><span data-stu-id="5925f-171">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="5925f-172">Quando o número de repetições atinge o número máximo definido para a política de Disjuntor (nesse caso, 5), o aplicativo gera uma BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="5925f-172">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="5925f-173">O resultado é uma mensagem amigável, como mostra a Figura 10-5.</span><span class="sxs-lookup"><span data-stu-id="5925f-173">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="5925f-174">**Figura 10-5**.</span><span class="sxs-lookup"><span data-stu-id="5925f-174">**Figure 10-5**.</span></span> <span data-ttu-id="5925f-175">Disjuntor retornando um erro na interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5925f-175">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="5925f-176">Você pode implementar uma lógica diferente para quando abrir/interromper o circuito.</span><span class="sxs-lookup"><span data-stu-id="5925f-176">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="5925f-177">Ou você poderá tentar uma solicitação HTTP para um microsserviço de back-end diferente se houver um datacenter de fallback ou um sistema redundante de back-end.</span><span class="sxs-lookup"><span data-stu-id="5925f-177">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span> 

<span data-ttu-id="5925f-178">Por fim, outra possibilidade do `CircuitBreakerPolicy` é usar `Isolate` (que força o circuito a abrir e a continuar aberto) e `Reset` (que o fecha novamente).</span><span class="sxs-lookup"><span data-stu-id="5925f-178">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="5925f-179">Isso pode ser usado para criar um ponto de extremidade HTTP de utilitário que invoque Isolar e Reiniciar diretamente na política.</span><span class="sxs-lookup"><span data-stu-id="5925f-179">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="5925f-180">Esse ponto de extremidade HTTP também pode ser usado, adequadamente protegido, em produção para isolar temporariamente um sistema downstream, como quando você deseja atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="5925f-180">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="5925f-181">Ou poderia desarmar o circuito manualmente para proteger o sistema a downstream que você suspeita ter falha.</span><span class="sxs-lookup"><span data-stu-id="5925f-181">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>


## <a name="additional-resources"></a><span data-ttu-id="5925f-182">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="5925f-182">Additional resources</span></span>


-   <span data-ttu-id="5925f-183">**Padrão de disjuntor**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="5925f-183">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5925f-184">[Anterior](implement-http-call-retries-exponential-backoff-polly.md)
[Próximo](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="5925f-184">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
