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
# <a name="implementing-the-circuit-breaker-pattern"></a>Implementando o padrão de Disjuntor

Conforme observado anteriormente, você deve tratar falhas que podem consumir uma quantidade variável de tempo de recuperação, como pode acontecer quando você tentar se conectar a um serviço remoto ou um recurso. Esse tipo de falha de tratamento pode melhorar a estabilidade e a resiliência de um aplicativo.

Em um ambiente distribuído, chamadas para serviços e recursos remotos pode falhar devido a falhas transitórias, como conexões lentas de rede e o tempo limite, ou se os recursos estão sendo lenta ou estão temporariamente indisponíveis. Essas falhas geralmente corrigidos automaticamente após um curto período de tempo e um aplicativo em nuvem robusto deve estar preparado para lidar com eles por meio de uma estratégia de como o padrão de repetição.

No entanto, também pode haver situações em que as falhas são devido a eventos inesperados que podem levar muito mais tempo para corrigir. Essas falhas podem variar de severidade de uma perda parcial de conectividade para a falha completa de um serviço. Nessas situações, pode ser sem sentido para um aplicativo tentará continuamente uma operação que é improvável que seja bem-sucedida. Em vez disso, o aplicativo deve ser codificado para aceitar a operação falhou e lidar com falhas adequadamente.

O padrão de disjuntor tem uma finalidade diferente que o padrão de repetição. O padrão de repetição permite que um aplicativo repetir uma operação na expectativa de que a operação eventualmente será bem-sucedida. O padrão de disjuntor impede que um aplicativo executando uma operação que é provavelmente falharão. Um aplicativo pode combinar esses dois padrões usando o padrão de repetição para invocar uma operação por meio de um disjuntor. No entanto, a lógica de repetição deve ser sensível a qualquer exceção retornadas pelo Disjuntor, e ele deve abandonar tentativas de repetição se o disjuntor indica que uma falha não é transitória.

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>Implementar um padrão de disjuntor com Polly

Como durante a implementação de novas tentativas, a abordagem recomendada para disjuntores é tirar proveito das comprovada bibliotecas .NET como Polly.

O aplicativo de eShopOnContainers usa a política de disjuntor Polly durante a implementação de novas tentativas HTTP. Na verdade, o aplicativo se aplica a ambas as políticas para a classe de utilitário ResilientHttpClient. Sempre que você usar um objeto do tipo ResilientHttpClient solicitações HTTP (da eShopOnContainers), você aplicará os dois essas políticas, mas você pode adicionar políticas adicionais, muito.

A adição somente para o código usado para novas tentativas de chamada HTTP é o código em que a política de disjuntor é adicionar à lista de políticas para usar, conforme mostrado no final do código a seguir:

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

O código adiciona uma política para o wrapper HTTP. Se a diretiva define um disjuntor é aberta quando o código detecta o número especificado de exceções consecutivos (exceções em uma linha), como passado no parâmetro exceptionsAllowedBeforeBreaking (5 neste caso). Quando o circuito está aberto, solicitações HTTP não funcionam, mas uma exceção é gerada.

Disjuntores também deve ser usados para redirecionar solicitações para uma infraestrutura de fallback se você pode ter problemas em um recurso específico que é implantado em um ambiente diferente do que o aplicativo cliente ou serviço que está executando a chamada HTTP. Dessa forma, se houver uma interrupção no datacenter, que afeta apenas o microservices de back-end, mas não seus aplicativos de cliente, os aplicativos cliente podem redirecionar para os serviços de fallbacks. Polly está planejando uma nova política para automatizar esse procedimento [política de failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) cenário.

Obviamente, todos esses recursos são para casos em que você está gerenciando o failover de dentro do código do .NET, em vez de tê-la gerenciadas automaticamente para você pelo Azure, com transparência de local.

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>Usando a classe de utilitário ResilientHttpClient de eShopOnContainers

Você pode usar a classe de utilitário ResilientHttpClient de forma semelhante de como usar a classe .NET HttpClient. No exemplo a seguir do aplicativo da web do MVC eShopOnContainers (a classe de agente OrderingService usada por OrderController), o objeto ResilientHttpClient é injetado pelo parâmetro httpClient do construtor. Em seguida, o objeto é usado para executar solicitações HTTP.

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

Sempre que o \_apiClient objeto de membro for usado, ele usa internamente a classe de invólucro com Polly policiesؙ — a política de repetição, a política de disjuntor e outra política que talvez você queira aplicar da coleção de políticas Polly.

## <a name="testing-retries-in-eshoponcontainers"></a>Testando as repetições em eShopOnContainers

Sempre que iniciar a solução de eShopOnContainers em um host do Docker, ela precisa iniciar vários contêineres. Alguns dos contêineres são mais lentos para iniciar e inicializar, como o contêiner do SQL Server. Isso é especialmente verdadeiro na primeira vez que você implantar o aplicativo eShopOnContainers no Docker, porque é necessário configurar as imagens e o banco de dados. O fato de que alguns contêineres mais lenta do que outros podem causar o restante dos serviços inicialmente lançar exceções de HTTP, mesmo se você definir dependências entre contêineres em iniciam a compor docker nível, conforme explicado nas seções anteriores. Os docker-compõem as dependências entre os contêineres são apenas no nível do processo. O processo de ponto de entrada do contêiner pode ser iniciado, mas o SQL Server talvez não esteja pronto para consultas. O resultado pode ser uma cascata de erros e o aplicativo pode obter uma exceção ao tentar consumir esse contêiner específico.

Você também poderá ver esse tipo de erro na inicialização, quando o aplicativo é implantado para a nuvem. Nesse caso, orchestrators pode ser mover contêineres de um nó ou máquina virtual para outro (isto é, começando a novas instâncias) quando o número de contêineres de balanceamento entre nós do cluster.

É a maneira eShopOnContainers resolve esse problema usando o padrão de repetição que são ilustrados anteriormente. Também é por que, ao iniciar a solução, você poderá obter rastreamentos de log ou avisos semelhante ao seguinte:

> "**Repetição 1 implementado com RetryPolicy de Polly**, devido à: System.Net.Http.HttpRequestException: Ocorreu um erro ao enviar a solicitação. ---&gt;System.Net.Http.CurlException: Não foi possível conectar ao servidor\\n em System.Net.Http.CurlHandler.ThrowIfCURLEError (erro CURLcode)\\n em \[... \].

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>Testando o disjuntor em eShopOnContainers

Há algumas maneiras de abrir o circuito e testá-lo com eShopOnContainers.

Uma opção é reduzir o número permitido de tentativas de 1 na política de disjuntor e reimplantar a solução completa para o Docker. Com uma repetição de único, há uma boa chance de que uma solicitação HTTP falhará durante a implantação, o disjuntor será aberto e você obterá um erro.

Outra opção é usar o middleware personalizado que é implementado no microsserviço a ordenação. Quando este middleware estiver habilitado, ele captura todas as solicitações HTTP e retorna o código de status 500. Você pode habilitar o middleware fazendo uma solicitação GET para a falha do URI, como o seguinte:

-   OBTER/falha

Essa solicitação retorna o estado atual do middleware. Se o middleware estiver habilitado, a solicitação retorna o código de status 500. Se o middleware está desativado, não há nenhuma resposta.

-   OBTER/falhando? habilitar

Essa solicitação permite que o middleware.

-   OBTER/falhando? desabilitar

Essa solicitação desabilita o middleware.

Por exemplo, quando o aplicativo estiver em execução, você pode habilitar o middleware fazendo uma solicitação usando o seguinte URI em qualquer navegador. Observe que a ordenação microsserviço usa a porta 5102.

http://localhost:5102 / falhando? habilitar

Em seguida, você pode verificar o status usando o URI de [http://localhost:5102 / falha](http://localhost:5100/failing), conforme mostrado na Figura 10-4.

![](./media/image4.png)

**Figura 10-4**. Simulando uma falha com o ASP.NET middleware

Neste ponto, o ordenação responde de microsserviço com código de status 500 sempre que você chamar invocá-lo.

Depois que o middleware está em execução, você pode tentar fazer um pedido do aplicativo da web MVC. Como as solicitações falhar, o circuito será aberto.

No exemplo a seguir, você pode ver que o aplicativo da web MVC tem um catch bloquear na lógica para fazer um pedido. Se o código de captura uma exceção de circuito aberto, ele mostra o usuário uma mensagem amigável informando de espera.

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

Aqui está um resumo. A política de repetição tenta várias vezes para fazer a solicitação HTTP e obtém os erros HTTP. Quando o número de tentativas atinge o número máximo definido para a política de Disjuntor (nesse caso, 5), o aplicativo gera um BrokenCircuitException. O resultado é uma mensagem amigável, como mostrado na Figura 10-5.

![](./media/image5.png)

**Figura 10-5**. Disjuntor retornando um erro na interface do usuário

Você pode implementar uma lógica diferente de quando o circuito aberto. Ou você pode tentar uma solicitação HTTP em um microsserviço de back-end diferente, se houver um fallback datacenter ou um sistema redundante de back-end.

Por fim, outra possibilidade do CircuitBreakerPolicy é usar isolam (que força aberto e mantém aberta do circuito) e redefinição (que fecha novamente). Essas páginas podem ser usadas para criar um ponto de extremidade HTTP de utilitário que invoca a isolar e redefina diretamente na política. Tal um ponto de extremidade HTTP também pode ser usado, adequadamente protegidos em produção para isolar temporariamente um sistema downstream, como quando você deseja atualizá-lo. Ou, ele poderia trip circuito manualmente para proteger o sistema downstream que suspeito ser com falha.

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>Adicionando uma estratégia de variação para a política de repetição

Uma política de repetição regular pode afetar o sistema em casos de escalabilidade e alta simultaneidade e em alto de contenção. Para superar os picos de repetições semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação para a algoritmo/política de repetição. Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade para a retirada exponencial. Isso se espalha os picos quando surgem problemas. Quando você usa Polly, código para implementar a tremulação pode parecer com o exemplo a seguir:

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a>Recursos adicionais

-   **Repita padrão**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **Resiliência de Conexão** (Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Polly** (biblioteca de tratamento de falhas transitórias e resiliência do .NET) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **Padrão de disjuntor**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Marc Esteves. Variação: Tornar as coisas melhor com aleatoriedade** https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[Anterior] (implement-http-call-retries-exponential-backoff-polly.md) [Avançar] (monitor-aplicativo-health.md)
