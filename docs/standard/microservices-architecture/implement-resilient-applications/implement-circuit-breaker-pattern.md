---
title: Implementando o padrão de Disjuntor
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementar o padrão de disjuntor como um sistema complementar para repetições de HTTP
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: d5902c5a0744d74ae5086a4df3aee606b24b6030
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875161"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="c6bd2-103">Implementar o padrão de disjuntor</span><span class="sxs-lookup"><span data-stu-id="c6bd2-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="c6bd2-104">Conforme já observado, você deve tratar as falhas que podem gastar uma quantidade variável de tempo para a recuperação, como pode acontecer quando você tenta se conectar a um serviço ou a um recurso remoto.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as it might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="c6bd2-105">Lidar com esse tipo de falha pode melhorar a estabilidade e a resiliência de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="c6bd2-106">Em um ambiente distribuído, chamadas para serviços e recursos remotos poderão falhar devido a falhas transitórias, como conexões lentas de rede e tempos limites ou se os recursos estiverem lentos ou temporariamente não disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="c6bd2-107">Essas falhas geralmente são corrigidas automaticamente após um curto período, e um aplicativo em nuvem robusto deve estar preparado para lidar com elas usando uma estratégia como o “padrão de repetição”.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span> 

<span data-ttu-id="c6bd2-108">No entanto, também pode haver situações em que as falhas são devido a eventos inesperados que podem levar muito mais tempo para serem corrigidos.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="c6bd2-109">Essas falhas podem variar em termos de gravidade de uma perda parcial de conectividade até a falha completa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="c6bd2-110">Nessas situações, pode não ter sentido um aplicativo repetir continuamente uma operação que é improvável que seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> 

<span data-ttu-id="c6bd2-111">Em vez disso, o aplicativo deve ser codificado para aceitar que a operação falhou e lidar com falhas adequadamente.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="c6bd2-112">O mau uso das repetições de HTTP pode resultar na criação de um ataque de [DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack) (negação de serviço) dentro do próprio software.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="c6bd2-113">Quando um microsserviço falha ou apresenta um desempenho lento, vários clientes podem fazer novas tentativas de solicitações com falha repetidamente.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="c6bd2-114">Isso cria um risco perigoso de aumentar exponencialmente o tráfego direcionado ao serviço com falha.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="c6bd2-115">Portanto, é necessário algum tipo de barreira de defesa para que as repetições de solicitação sejam interrompidas quando não vale a pena continuar tentando.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-115">Therefore, you need some kind of defense barrier so the retries stop requests when it is not worth to keep trying.</span></span> <span data-ttu-id="c6bd2-116">Essa barreira de defesa é exatamente o disjuntor.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="c6bd2-117">O padrão de disjuntor tem uma finalidade diferente do "padrão de repetição".</span><span class="sxs-lookup"><span data-stu-id="c6bd2-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="c6bd2-118">O “padrão de repetição” permite que um aplicativo repita uma operação na expectativa de que a ela acabará sendo bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="c6bd2-119">O padrão de Disjuntor impede que um aplicativo execute uma operação que é provavelmente falhará.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-119">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="c6bd2-120">O aplicativo pode combinar esses dois padrões.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-120">An application can combine these two patterns.</span></span> <span data-ttu-id="c6bd2-121">No entanto, a lógica de repetição deve reconhecer qualquer exceção retornada pelo disjuntor e deve abandonar as tentativas de repetição quando o disjuntor indica que uma falha não é transitória.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a><span data-ttu-id="c6bd2-122">Implementar o padrão de disjuntor com HttpClientFactory e Polly</span><span class="sxs-lookup"><span data-stu-id="c6bd2-122">Implement Circuit Breaker pattern with HttpClientFactory and Polly</span></span>

<span data-ttu-id="c6bd2-123">Como durante a implementação de repetições, a abordagem recomendada para disjuntores é aproveitar as comprovadas bibliotecas do .NET, como a Polly e sua integração nativa com o HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with HttpClientFactory.</span></span>

<span data-ttu-id="c6bd2-124">Adicionar uma política de disjuntor no pipeline do middleware de saída do HttpClientFactory é tão simples quanto adicionar uma única parte incremental de código ao que você já tem ao usar HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-124">Adding a circuit breaker policy into your HttpClientFactory outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using HttpClientFactory.</span></span>

<span data-ttu-id="c6bd2-125">Aqui, a única adição ao código usado para repetições de chamada HTTP é o código no qual você adiciona a política de disjuntor à lista de políticas a serem usadas, conforme é mostrado no código incremental a seguir, que faz parte do método ConfigureServices().</span><span class="sxs-lookup"><span data-stu-id="c6bd2-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to 5 minutes
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="c6bd2-126">O método `AddPolicyHandler()` é o que adiciona políticas aos objetos HttpClient que serão usados.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-126">The `AddPolicyHandler()`method is what adds policies to the HttpClient objects you will use.</span></span> <span data-ttu-id="c6bd2-127">Nesse caso, ele está adicionando uma política da Polly para um disjuntor.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-127">In this case, it is adding a Polly’s policy for a circuit breaker.</span></span>

<span data-ttu-id="c6bd2-128">Para obter uma abordagem mais modular, a política de disjuntor é definida em um método separado chamado GetCircuitBreakerPolicy(), como o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-128">In order to have a more modular approach, the Circuit Breaker Policy is defined in a separate method named GetCircuitBreakerPolicy(), as the following code.</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="c6bd2-129">No exemplo de código acima, a política de disjuntor é configurada para interromper ou abrir o circuito quando ocorrerem cinco exceções ao repetir as solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five exceptions when retrying the Http requests.</span></span> <span data-ttu-id="c6bd2-130">Assim, 30 segundos será a duração da interrupção.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-130">Then, 30 seconds will be the duration or the break.</span></span>

<span data-ttu-id="c6bd2-131">Os disjuntores também devem ser usados para redirecionar solicitações a uma infraestrutura de fallback quando há problemas em um recurso específico implantado em um ambiente diferente do aplicativo ou do serviço cliente que está executando a chamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-131">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="c6bd2-132">Dessa forma, se houver uma interrupção no datacenter que afete apenas os microsserviços de back-end, mas não os aplicativos cliente, os aplicativos cliente poderão redirecionar para os serviços de fallback.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-132">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="c6bd2-133">O Polly está planejando uma nova política para automatizar esse cenário de [política de failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy).</span><span class="sxs-lookup"><span data-stu-id="c6bd2-133">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span> 

<span data-ttu-id="c6bd2-134">Todos esses recursos são para casos em que você está gerenciando o failover de dentro do código do .NET, em vez de deixar que o Azure o gerencie automaticamente com transparência de local.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-134">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span> 

<span data-ttu-id="c6bd2-135">De uma perspectiva de uso, ao usar o HttpClient, não é necessário adicionar nada de novo, porque o código é o mesmo que ao usar o HttpClient com o HttpClientFactory, conforme é mostrado nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-135">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using HttpClient with HttpClientFactory, as shown in previous sections.</span></span> 

## <a name="testing-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="c6bd2-136">Testando repetições de HTTP e disjuntores no eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c6bd2-136">Testing Http retries and circuit breakers in eShopOnContainers</span></span>


<span data-ttu-id="c6bd2-137">Sempre que você inicia a solução eShopOnContainers em um host do Docker, ela precisa iniciar vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-137">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="c6bd2-138">Alguns dos contêineres são mais lentos em iniciar e inicializar, como o contêiner do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-138">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="c6bd2-139">Isso é especialmente verdadeiro na primeira vez que você implanta o aplicativo eShopOnContainers no Docker, porque é necessário configurar as imagens e o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-139">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="c6bd2-140">O fato de que alguns contêineres iniciam mais lentamente do que outros pode fazer o restante dos serviços lançarem exceções HTTP, mesmo que você defina dependências entre contêineres no nível do Docker Compose, como explicado nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-140">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="c6bd2-141">Essas dependências do Docker Compose entre os contêineres são apenas no nível do processo.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-141">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="c6bd2-142">O processo de ponto de entrada do contêiner pode ser iniciado, mas o SQL Server talvez não esteja pronto para consultas.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-142">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="c6bd2-143">O resultado pode ser uma cascata de erros e o aplicativo pode obter uma exceção ao tentar consumir aquele contêiner específico.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-143">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span> 

<span data-ttu-id="c6bd2-144">Você também pode ver esse tipo de erro na inicialização quando o aplicativo está sendo implantado para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-144">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="c6bd2-145">Nesse caso, os orquestradores poderão estar movendo contêineres de um nó ou VM para outro (ou seja, começando novas instâncias) ao equilibrar o número de contêineres entre nós do cluster.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-145">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="c6bd2-146">A maneira como 'eShopOnContainers' resolve esses problemas ao iniciar todos os contêineres é usando o padrão de repetições ilustrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-146">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span> 

### <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="c6bd2-147">Testando o disjuntor em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c6bd2-147">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="c6bd2-148">Há algumas maneiras de interromper/abrir o circuito e testá-lo com o eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-148">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="c6bd2-149">Uma opção é reduzir o número permitido de novas tentativas a 1 na política de disjuntor e reimplantar toda a solução no Docker.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-149">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="c6bd2-150">Com uma única nova tentativa, há uma boa chance de que uma solicitação HTTP falhe durante a implantação, o disjuntor se abra e você receba um erro.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-150">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="c6bd2-151">Outra opção é usar o middleware personalizado implementado no microsserviço Cesta.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-151">Another option is to use custom middleware that is implemented in the Basket microservice.</span></span> <span data-ttu-id="c6bd2-152">Quando esse middleware é habilitado, ele captura todas as solicitações HTTP e retorna o código de status 500.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-152">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="c6bd2-153">Você pode habilitar o middleware fazendo uma solicitação GET para o URI de falha, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6bd2-153">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`

<span data-ttu-id="c6bd2-154">Essa solicitação retorna o estado atual do middleware.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-154">This request returns the current state of the middleware.</span></span> <span data-ttu-id="c6bd2-155">Se o middleware estiver habilitado, a solicitação retornará o código de status 500.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-155">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="c6bd2-156">Se o middleware estiver desabilitado, não haverá nenhuma resposta.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-156">If the middleware is disabled, there is no response.</span></span> 

- `GET http://localhost:5103/failing?enable`

<span data-ttu-id="c6bd2-157">Essa solicitação habilita o middleware.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-157">This request enables the middleware.</span></span> 

- `GET http://localhost:5103/failing?disable`

<span data-ttu-id="c6bd2-158">Essa solicitação desabilita o middleware.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-158">This request disables the middleware.</span></span> 

<span data-ttu-id="c6bd2-159">Por exemplo, quando o aplicativo estiver em execução, você poderá habilitar o middleware fazendo uma solicitação usando o seguinte URI em qualquer navegador.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-159">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="c6bd2-160">Observe que o microsserviço de ordenação usa a porta 5103.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-160">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable` 

<span data-ttu-id="c6bd2-161">Em seguida, você pode verificar o status usando o URI http://localhost:5103/failing, conforme é mostrado na Figura 10-4.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-161">You can then check the status using the URI http://localhost:5103/failing, as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="c6bd2-162">**Figura 10-4**.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-162">**Figure 10-4**.</span></span> <span data-ttu-id="c6bd2-163">Verificando o estado do middleware ASP.NET com "Falha" – neste caso, desabilitado.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-163">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="c6bd2-164">Neste ponto, o de microsserviço Cesta responde com o código de status 500 sempre que você o chama ou invoca.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-164">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="c6bd2-165">Depois que o middleware estiver em execução, você poderá tentar fazer um pedido do aplicativo Web MVC.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-165">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="c6bd2-166">Como as solicitações falham, o circuito é aberto.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-166">Because the requests fail, the circuit will open.</span></span> 

<span data-ttu-id="c6bd2-167">No exemplo a seguir, você pode ver que o aplicativo Web MVC tem um bloco catch na lógica para fazer um pedido.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-167">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="c6bd2-168">Se o código capturar uma exceção de circuito aberto, ele mostrará ao usuário uma mensagem amigável informando-o para esperar.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-168">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="c6bd2-169">Segue um resumo.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-169">Here’s a summary.</span></span> <span data-ttu-id="c6bd2-170">A política de repetição tenta várias vezes fazer a solicitação HTTP e obtém os erros HTTP.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-170">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="c6bd2-171">Quando o número de repetições atinge o número máximo definido para a política de Disjuntor (nesse caso, 5), o aplicativo gera uma BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-171">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="c6bd2-172">O resultado é uma mensagem amigável, como mostra a Figura 10-5.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-172">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="c6bd2-173">**Figura 10-5**.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-173">**Figure 10-5**.</span></span> <span data-ttu-id="c6bd2-174">Disjuntor retornando um erro na interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c6bd2-174">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="c6bd2-175">Você pode implementar uma lógica diferente para quando abrir/interromper o circuito.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-175">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="c6bd2-176">Ou você poderá tentar uma solicitação HTTP para um microsserviço de back-end diferente se houver um datacenter de fallback ou um sistema redundante de back-end.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-176">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span> 

<span data-ttu-id="c6bd2-177">Por fim, outra possibilidade do `CircuitBreakerPolicy` é usar `Isolate` (que força o circuito a abrir e a continuar aberto) e `Reset` (que o fecha novamente).</span><span class="sxs-lookup"><span data-stu-id="c6bd2-177">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="c6bd2-178">Isso pode ser usado para criar um ponto de extremidade HTTP de utilitário que invoque Isolar e Reiniciar diretamente na política.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-178">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="c6bd2-179">Esse ponto de extremidade HTTP também pode ser usado, adequadamente protegido, em produção para isolar temporariamente um sistema downstream, como quando você deseja atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-179">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="c6bd2-180">Ou poderia desarmar o circuito manualmente para proteger o sistema a downstream que você suspeita ter falha.</span><span class="sxs-lookup"><span data-stu-id="c6bd2-180">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>


## <a name="additional-resources"></a><span data-ttu-id="c6bd2-181">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c6bd2-181">Additional resources</span></span>


-   <span data-ttu-id="c6bd2-182">**Padrão de disjuntor**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="c6bd2-182">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c6bd2-183">[Anterior](implement-http-call-retries-exponential-backoff-polly.md)
[Próximo](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="c6bd2-183">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
