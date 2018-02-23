---
title: "Implementando o padrão de Disjuntor"
description: "Arquitetura de Microsserviços do .NET para aplicativos .NET em contêineres | Implementando o padrão de Disjuntor"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d7db6899068f84f9165022cfbf17767a75e7db9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a>Implementando o padrão de Disjuntor

Conforme observado anteriormente, você deve tratar falhas que podem consumir uma quantidade variável de tempo de recuperação, como pode acontecer quando você tenta se conectar a um serviço ou um recurso remoto. Lidar com esse tipo de falha pode melhorar a estabilidade e a resiliência de um aplicativo.

Em um ambiente distribuído, chamadas para serviços e recursos remotos poderão falhar devido a falhas transitórias, como conexões lentas de rede e tempos limites ou se os recursos estiverem lentos ou temporariamente não disponíveis. Essas falhas geralmente são corrigidas automaticamente após um curto período, e um aplicativo em nuvem robusto deve estar preparado para lidar com elas usando uma estratégia como o padrão de Novas Tentativas.

No entanto, também pode haver situações em que as falhas são devido a eventos inesperados que podem levar muito mais tempo para serem corrigidos. Essas falhas podem variar em termos de gravidade de uma perda parcial de conectividade até a falha completa de um serviço. Nessas situações, pode não ter sentido um aplicativo repetir continuamente uma operação que é improvável que seja bem-sucedida. Em vez disso, o aplicativo deve ser codificado para aceitar que a operação falhou e lidar com falhas adequadamente.

O padrão de Disjuntor tem uma finalidade diferente que o padrão de Novas Tentativas. O padrão de Novas Tentativas permite que um aplicativo repita uma operação na expectativa de que a ela acabará sendo bem-sucedida. O padrão de Disjuntor impede que um aplicativo execute uma operação que é provavelmente falhará. Um aplicativo pode combinar esses dois padrões usando o padrão de Novas Tentativas para invocar uma operação por meio de um disjuntor. No entanto, a lógica de novas tentativas deve ser sensível a qualquer exceção retornada pelo disjuntor e deve abandonar tentativas de repetição se o disjuntor indica que uma falha não é transitória.

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>Implementar um padrão de Disjuntor com Polly

Como durante a implementação de novas tentativas, a abordagem recomendada para disjuntores é aproveitar as comprovadas bibliotecas .NET, como Polly.

O aplicativo eShopOnContainers usa a política de Disjuntor do Polly durante a implementação de novas tentativas HTTP. Na verdade, o aplicativo se aplica a ambas as políticas para a classe de utilitários ResilientHttpClient. Sempre que você usar um objeto do tipo ResilientHttpClient para solicitações HTTP (da eShopOnContainers), estará aplicando essas duas políticas, mas poderá adicionar mais políticas também.

Aqui, a única adição ao código usado para novas tentativas de chamada HTTP é o código em que você adiciona a política de Disjuntor à lista de políticas a usar, conforme mostrado no final do código a seguir:

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

O código adiciona uma política ao wrapper HTTP. Essa política define um disjuntor que se abre quando o código detecta o número especificado de exceções consecutivas (exceções em sequência), conforme passado no parâmetro exceptionsAllowedBeforeBreaking (cinco, neste caso). Quando o circuito está aberto, as solicitações HTTP não funcionam, mas uma exceção é gerada.

Disjuntores também deverão ser usados para redirecionar solicitações para uma infraestrutura de fallback se puder ter problemas em um recurso específico implantado em um ambiente diferente do aplicativo cliente ou do serviço que está executando a chamada HTTP. Dessa forma, se houver uma interrupção no datacenter que afete apenas os microsserviços de back-end, mas não os aplicativos cliente, os aplicativos cliente poderão redirecionar para os serviços de fallback. O Polly está planejando uma nova política para automatizar esse cenário de [política de failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy).

Obviamente, todos esses recursos são para casos em que você está gerenciando o failover de dentro do código .NET, em vez de deixar que o Azure o gerencie automaticamente para você, com transparência de local.

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>Usando a classe de utilitário ResilientHttpClient de eShopOnContainers

Você pode usar a classe de utilitário ResilientHttpClient de modo semelhante a como usa a classe .NET HttpClient. No exemplo a seguir do aplicativo Web do MVC eShopOnContainers (a classe de agente OrderingService usada por OrderController), o objeto ResilientHttpClient é injetado pelo parâmetro httpClient do construtor. Então o objeto é usado para executar solicitações HTTP.

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

Sempre que o membro do objeto \_apiClient é usado, ele usa internamente a classe wrapper com políticas do Polly: a política de repetição, a política de Disjuntor e outra política que talvez você queira aplicar da coleção de políticas do Polly.

## <a name="testing-retries-in-eshoponcontainers"></a>Testando repetições em eShopOnContainers

Sempre que você inicia a solução eShopOnContainers em um host do Docker, ela precisa iniciar vários contêineres. Alguns dos contêineres são mais lentos em iniciar e inicializar, como o contêiner do SQL Server. Isso é especialmente verdadeiro na primeira vez que você implanta o aplicativo eShopOnContainers no Docker, porque é necessário configurar as imagens e o banco de dados. O fato de que alguns contêineres iniciam mais lentamente do que outros pode fazer o restante dos serviços lançarem exceções HTTP, mesmo que você defina dependências entre contêineres no nível do Docker Compose, como explicado nas seções anteriores. Essas dependências do Docker Compose entre os contêineres são apenas no nível do processo. O processo de ponto de entrada do contêiner pode ser iniciado, mas o SQL Server talvez não esteja pronto para consultas. O resultado pode ser uma cascata de erros e o aplicativo pode obter uma exceção ao tentar consumir aquele contêiner específico.

Você também pode ver esse tipo de erro na inicialização quando o aplicativo está sendo implantado para a nuvem. Nesse caso, os orquestradores poderão estar movendo contêineres de um nó ou VM para outro (ou seja, começando novas instâncias) ao equilibrar o número de contêineres entre nós do cluster.

A maneira como o eShopOnContainers resolve esse problema é usando o padrão de Novas Tentativas ilustrado anteriormente. Também é por isso que, ao iniciar a solução, você poderá obter rastreamentos de log ou avisos semelhante ao seguinte:

> "**Nova Tentativa 1 implementada com RetryPolicy do Polly** devido a: System.Net.Http.HttpRequestException: ocorreu um erro ao enviar a solicitação. ---&gt; System.Net.Http.CurlException: não foi possível conectar-se ao servidor\\n em System.Net.Http.CurlHandler.ThrowIfCURLEError (erro CURLcode)\\n em \[…\].

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>Testando o disjuntor em eShopOnContainers

Existem algumas maneiras de abrir o circuito e testá-lo com eShopOnContainers.

Uma opção é reduzir o número permitido de novas tentativas a 1 na política de disjuntor e reimplantar toda a solução no Docker. Com uma única nova tentativa, há uma boa chance de que uma solicitação HTTP falhe durante a implantação, o disjuntor se abra e você receba um erro.

Outra opção é usar o middleware personalizado implementado no microsserviço `Basket`. Quando esse middleware é habilitado, ele captura todas as solicitações HTTP e retorna o código de status 500. Você pode habilitar o middleware fazendo uma solicitação GET para o URI de falha, como o seguinte:

-   GET /failing

Essa solicitação retorna o estado atual do middleware. Se o middleware estiver habilitado, a solicitação retornará o código de status 500. Se o middleware estiver desabilitado, não haverá nenhuma resposta.

-   GET /failing?enable

Essa solicitação habilita o middleware.

-   GET /failing?disable

Essa solicitação desabilita o middleware.

Por exemplo, quando o aplicativo estiver em execução, você poderá habilitar o middleware fazendo uma solicitação usando o seguinte URI em qualquer navegador. Observe que o microsserviço de ordenação usa a porta 5103.

http://localhost:5103/failing?enable

Em seguida, você pode verificar o status usando o URI [http://localhost:5103/failing](http://localhost:5103/failing), conforme mostra a Figura 10-4.

![](./media/image4.png)

**Figura 10-4**. Verificando o estado do middleware ASP.NET com "Falha" – neste caso, desabilitado. 

Neste ponto, o de microsserviço Cesta responde com o código de status 500 sempre que você o chama ou invoca.

Depois que o middleware estiver em execução, você poderá tentar fazer um pedido do aplicativo Web MVC. Como as solicitações falham, o circuito é aberto.

No exemplo a seguir, você pode ver que o aplicativo Web MVC tem um bloco catch na lógica para fazer um pedido. Se o código capturar uma exceção de circuito aberto, ele mostrará ao usuário uma mensagem amigável informando-o para esperar.

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

Segue um resumo. A política de repetição tenta várias vezes fazer a solicitação HTTP e obtém os erros HTTP. Quando o número de novas tentativas atinge o número máximo definido para a política de Disjuntor (neste caso, 5), o aplicativo gera uma BrokenCircuitException. O resultado é uma mensagem amigável, como mostra a Figura 10-5.

![](./media/image5.png)

**Figura 10-5**. Disjuntor retornando um erro na interface do usuário

Você pode implementar uma lógica diferente de quando abrir o circuito. Ou você poderá tentar uma solicitação HTTP para um microsserviço de back-end diferente se houver um datacenter de fallback ou um sistema redundante de back-end.

Por fim, outra possibilidade do CircuitBreakerPolicy é usar Isolar (que força a abertura e mantém o circuito aberto) e Reiniciar (que o fecha novamente). Isso pode ser usado para criar um ponto de extremidade HTTP de utilitário que invoque Isolar e Reiniciar diretamente na política. Esse ponto de extremidade HTTP também pode ser usado, adequadamente protegido, em produção para isolar temporariamente um sistema downstream, como quando você deseja atualizá-lo. Ou poderia desarmar o circuito manualmente para proteger o sistema a downstream que você suspeita ter falha.

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>Adicionando uma estratégia de tremulação à política de repetição

Uma política de Repetição regular pode afetar o sistema em casos de alta simultaneidade e escalabilidade e sob alta contenção. Para superar os picos de novas tentativas semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação à política/ao algoritmo de novas tentativas. Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade à retirada exponencial. Isso espalha os picos quando surgem problemas. Quando você usa o Polly, o código para implementar a variação pode se parecer com o exemplo a seguir:

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a>Recursos adicionais

-   **Padrão de repetição**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **Resiliência de Conexão** (Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Polly** (biblioteca de tratamento de falhas transitórias e resiliência do .NET) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **Padrão de Disjuntor**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Marc Brooker. Variação: melhorando as coisas com aleatoriedade** https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[Anterior] (implement-http-call-retries-exponential-backoff-polly.md) [Próximo] (monitor-app-health.md)
