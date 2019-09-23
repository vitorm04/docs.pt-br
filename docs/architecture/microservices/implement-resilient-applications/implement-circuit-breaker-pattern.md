---
title: Implementando o padrão de Disjuntor
description: Saiba como implementar o padrão de disjuntor como um sistema complementar para repetições de HTTP.
ms.date: 10/16/2018
ms.openlocfilehash: eec14273cb9480df51d6e5865106ccfc045845c4
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181932"
---
# <a name="implement-the-circuit-breaker-pattern"></a>Implementar o padrão de disjuntor

Conforme observado anteriormente, você deve tratar falhas que podem consumir uma quantidade variável de tempo de recuperação, como pode acontecer quando você tenta se conectar a um serviço ou um recurso remoto. Lidar com esse tipo de falha pode melhorar a estabilidade e a resiliência de um aplicativo.

Em um ambiente distribuído, chamadas para serviços e recursos remotos poderão falhar devido a falhas transitórias, como conexões lentas de rede e tempos limites ou se os recursos estiverem lentos ou temporariamente não disponíveis. Essas falhas geralmente são corrigidas automaticamente após um curto período, e um aplicativo em nuvem robusto deve estar preparado para lidar com elas usando uma estratégia como o “padrão de repetição”. 

No entanto, também pode haver situações em que as falhas são devido a eventos inesperados que podem levar muito mais tempo para serem corrigidos. Essas falhas podem variar em termos de gravidade de uma perda parcial de conectividade até a falha completa de um serviço. Nessas situações, talvez não tenha sentido um aplicativo repetir continuamente uma operação que provavelmente não será bem-sucedida. 

Em vez disso, o aplicativo deve ser codificado para aceitar que a operação falhou e lidar com falhas adequadamente.

O mau uso das repetições de HTTP pode resultar na criação de um ataque de [DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack) (negação de serviço) dentro do próprio software. Quando um microsserviço falha ou apresenta um desempenho lento, vários clientes podem fazer novas tentativas de solicitações com falha repetidamente. Isso cria um risco perigoso de aumentar exponencialmente o tráfego direcionado ao serviço com falha.

Portanto, você precisa de algum tipo de barreira de defesa para as que solicitações excessivas sejam interrompidas quando não valer a pena continuar tentando. Essa barreira de defesa é exatamente o disjuntor.

O padrão de disjuntor tem uma finalidade diferente do "padrão de repetição". O “padrão de repetição” permite que um aplicativo repita uma operação na expectativa de que a ela acabará sendo bem-sucedida. O padrão de disjuntor impede que um aplicativo execute uma operação que provavelmente falhará. O aplicativo pode combinar esses dois padrões. No entanto, a lógica de repetição deve reconhecer qualquer exceção retornada pelo disjuntor e deve abandonar as tentativas de repetição quando o disjuntor indica que uma falha não é transitória.

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a>Implementar o padrão de disjuntor com HttpClientFactory e Polly

Como durante a implementação de repetições, a abordagem recomendada para disjuntores é aproveitar as comprovadas bibliotecas do .NET, como a Polly e sua integração nativa com o HttpClientFactory.

Adicionar uma política de disjuntor no pipeline do middleware de saída do HttpClientFactory é tão simples quanto adicionar uma única parte incremental de código ao que você já tem ao usar HttpClientFactory.

Aqui, a única adição ao código usado para repetições de chamada HTTP é o código no qual você adiciona a política de disjuntor à lista de políticas a serem usadas, conforme é mostrado no código incremental a seguir, que faz parte do método ConfigureServices().

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

O método `AddPolicyHandler()` é aquele que adiciona políticas aos objetos `HttpClient` que você usará. Nesse caso, ele está adicionando uma política da Polly a um disjuntor.

Para obter uma abordagem mais modular, a política de disjuntor é definida em um método separado chamado `GetCircuitBreakerPolicy()`, mostrado no código a seguir:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

No exemplo de código acima, a política de disjuntor é configurada para interromper ou abrir o circuito quando ocorrerem cinco falhas consecutivas ao repetir as solicitações HTTP. Quando isso acontece, o circuito será interrompido por 30 segundos: nesse período, chamadas falharão imediatamente pelo disjuntor em vez de serem colocadas.  A política automaticamente interpreta [exceções relevantes e códigos de status HTTP](/aspnet/core/fundamentals/http-requests#handle-transient-faults) como falhas.  

Os disjuntores também devem ser usados para redirecionar solicitações a uma infraestrutura de fallback quando há problemas em um recurso específico implantado em um ambiente diferente do aplicativo ou do serviço cliente que está executando a chamada HTTP. Dessa forma, se houver uma interrupção no datacenter que afete apenas os microsserviços de back-end, mas não os aplicativos cliente, os aplicativos cliente poderão redirecionar para os serviços de fallback. O Polly está planejando uma nova política para automatizar esse cenário de [política de failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy). 

Todos esses recursos são para casos em que você está gerenciando o failover de dentro do código do .NET, em vez de deixar que o Azure o gerencie automaticamente com transparência de local. 

De uma perspectiva de uso, ao usar o HttpClient, não é necessário adicionar nada de novo, porque o código é o mesmo que ao usar o HttpClient com o HttpClientFactory, conforme é mostrado nas seções anteriores. 

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Testar repetições de HTTP e disjuntores no eShopOnContainers

Sempre que você inicia a solução eShopOnContainers em um host do Docker, ela precisa iniciar vários contêineres. Alguns dos contêineres são mais lentos em iniciar e inicializar, como o contêiner do SQL Server. Isso é verdadeiro principalmente na primeira vez que você implanta o aplicativo eShopOnContainers no Docker, porque é necessário configurar as imagens e o banco de dados. O fato de que alguns contêineres iniciam mais lentamente do que outros pode fazer o restante dos serviços lançarem exceções HTTP, mesmo que você defina dependências entre contêineres no nível do Docker Compose, como explicado nas seções anteriores. Essas dependências do Docker Compose entre os contêineres são apenas no nível do processo. O processo de ponto de entrada do contêiner pode ser iniciado, mas o SQL Server talvez não esteja pronto para consultas. O resultado pode ser uma cascata de erros e o aplicativo pode obter uma exceção ao tentar consumir aquele contêiner específico.

Você também pode ver esse tipo de erro na inicialização quando o aplicativo está sendo implantado para a nuvem. Nesse caso, os orquestradores poderão estar movendo contêineres de um nó ou VM para outro (ou seja, começando novas instâncias) ao equilibrar o número de contêineres entre nós do cluster.

A maneira como 'eShopOnContainers' resolve esses problemas ao iniciar todos os contêineres é usando o padrão de repetições ilustrado anteriormente. 

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>Testar o disjuntor no eShopOnContainers

Há algumas maneiras de interromper/abrir o circuito e testá-lo com o eShopOnContainers.

Uma opção é reduzir o número permitido de novas tentativas a 1 na política de disjuntor e reimplantar toda a solução no Docker. Com uma única nova tentativa, há uma boa chance de que uma solicitação HTTP falhe durante a implantação, o disjuntor seja aberto e você receba um erro.

Outra opção é usar o middleware personalizado implementado no microsserviço **Cesta**. Quando esse middleware é habilitado, ele captura todas as solicitações HTTP e retorna o código de status 500. Você pode habilitar o middleware fazendo uma solicitação GET para o URI de falha, como o seguinte:

- `GET http://localhost:5103/failing`\
  Essa solicitação retorna o estado atual do middleware. Se o middleware estiver habilitado, a solicitação retornará o código de status 500. Se o middleware estiver desabilitado, não haverá nenhuma resposta.

- `GET http://localhost:5103/failing?enable`\
  Essa solicitação habilita o middleware.

- `GET http://localhost:5103/failing?disable`\
  Essa solicitação desabilita o middleware.

Por exemplo, quando o aplicativo estiver em execução, você poderá habilitar o middleware fazendo uma solicitação usando o seguinte URI em qualquer navegador. Observe que o microsserviço de ordenação usa a porta 5103.

`http://localhost:5103/failing?enable` 

Em seguida, você pode verificar o status usando o URI `http://localhost:5103/failing`, como mostra a Figura 8-5.

![Exibição no navegador do resultado da verificação do status da simulação de middleware com falha](./media/image4.png)

**Figura 8-5**. Verificando o estado do middleware ASP.NET com "Falha" – neste caso, desabilitado.

Neste ponto, o de microsserviço Cesta responde com o código de status 500 sempre que você o chama ou invoca.

Depois que o middleware estiver em execução, você poderá tentar fazer um pedido do aplicativo Web MVC. Como as solicitações falham, o circuito é aberto. 

No exemplo a seguir, você pode ver que o aplicativo Web MVC tem um bloco catch na lógica para fazer um pedido.  Se o código capturar uma exceção de circuito aberto, ele mostrará ao usuário uma mensagem amigável informando-o para esperar.

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

Segue um resumo. A política de repetição tenta várias vezes fazer a solicitação HTTP e obtém os erros HTTP. Quando o número de repetições atinge o número máximo definido para a política de Disjuntor (nesse caso, 5), o aplicativo gera uma BrokenCircuitException. O resultado é uma mensagem amigável, como mostra a Figura 8-6.

![Exibição no navegador do aplicativo Web MVC mostrando uma mensagem de "serviço de cesta inoperante" disparada pela política do disjuntor](./media/image5.png)

**Figura 8-6**. Disjuntor retornando um erro na interface do usuário

Você pode implementar uma lógica diferente para quando abrir/interromper o circuito. Ou você poderá tentar uma solicitação HTTP para um microsserviço de back-end diferente se houver um datacenter de fallback ou um sistema de back-end redundante. 

Por fim, outra possibilidade do `CircuitBreakerPolicy` é usar `Isolate` (que força o circuito a abrir e a continuar aberto) e `Reset` (que o fecha novamente). Isso pode ser usado para criar um ponto de extremidade HTTP de utilitário que invoque Isolar e Reiniciar diretamente na política.  Esse ponto de extremidade HTTP também pode ser usado, adequadamente protegido, em produção para isolar temporariamente um sistema downstream, como quando você deseja atualizá-lo. Ou poderia desarmar o circuito manualmente para proteger o sistema a downstream que você suspeita ter falha.

## <a name="additional-resources"></a>Recursos adicionais

- **Padrão de disjuntor**\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Anterior](implement-http-call-retries-exponential-backoff-polly.md)
>[Próximo](monitor-app-health.md)
