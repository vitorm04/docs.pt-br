---
title: Assinando eventos
description: Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Entenda os detalhes de publicação e assinatura de eventos de integração.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: d32c643e553dfe3ce52e3e2ce8aaf1ea3a296de6
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297290"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="dd273-103">Assinando eventos</span><span class="sxs-lookup"><span data-stu-id="dd273-103">Subscribing to events</span></span>

<span data-ttu-id="dd273-104">A primeira etapa para usar o barramento de eventos é fazer com que os microsserviços assinem os eventos que eles desejam receber.</span><span class="sxs-lookup"><span data-stu-id="dd273-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="dd273-105">Isso deve ser feito nos microsserviços destinatários.</span><span class="sxs-lookup"><span data-stu-id="dd273-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="dd273-106">O código simples a seguir mostra o que cada destinatário de microsserviço precisa implementar ao iniciar o serviço (ou seja, a classe `Startup`) para assinar os eventos que precisa.</span><span class="sxs-lookup"><span data-stu-id="dd273-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="dd273-107">Nesse caso, o microsserviço `basket.api` precisa assinar as mensagens `ProductPriceChangedIntegrationEvent` e `OrderStartedIntegrationEvent`.</span><span class="sxs-lookup"><span data-stu-id="dd273-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span> 

<span data-ttu-id="dd273-108">Por exemplo, ao assinar o evento `ProductPriceChangedIntegrationEvent`, o microsserviço carrinho de compras tomará ciência de qualquer mudança no preço do produto e será capaz de avisar o usuário a respeito da alteração, caso o produto esteja em seu carrinho de compras.</span><span class="sxs-lookup"><span data-stu-id="dd273-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="dd273-109">Depois que esse código for executado, o microsserviço assinante escutará por meio de canais RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="dd273-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="dd273-110">Quando qualquer mensagem do tipo ProductPriceChangedIntegrationEvent chegar, o código invocará o manipulador de eventos, que será passado a ele e processará o evento.</span><span class="sxs-lookup"><span data-stu-id="dd273-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="dd273-111">Publicando eventos por meio do barramento de eventos</span><span class="sxs-lookup"><span data-stu-id="dd273-111">Publishing events through the event bus</span></span>

<span data-ttu-id="dd273-112">Por fim, o remetente da mensagem (microsserviço de origem) publica os eventos de integração com um código semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dd273-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="dd273-113">(Esse é um exemplo simplificado, que não leva a atomicidade em consideração). Você poderia implementar um código semelhante sempre que um evento tivesse que ser propagado por vários microsserviços, geralmente logo após a confirmação dos dados ou das transações do microsserviço de origem.</span><span class="sxs-lookup"><span data-stu-id="dd273-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="dd273-114">Primeiro, o objeto de implementação do barramento de eventos (baseado no RabbitMQ ou em um barramento de serviço) seria injetado no construtor do controlador, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="dd273-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

<span data-ttu-id="dd273-115">Em seguida, você o usaria nos métodos do controlador, como no método UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="dd273-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("items")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

<span data-ttu-id="dd273-116">Nesse caso, como o microsserviço de origem é um microsserviço CRUD simples, o código é colocado diretamente em um controlador de API Web.</span><span class="sxs-lookup"><span data-stu-id="dd273-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> 
 
<span data-ttu-id="dd273-117">Em microsserviços mais avançados, como ao usar abordagens de CQRS, ele pode ser implementado na classe `CommandHandler`, dentro do método `Handle()`.</span><span class="sxs-lookup"><span data-stu-id="dd273-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span> 

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="dd273-118">Criando atomicidade e resiliência ao publicar no barramento de eventos</span><span class="sxs-lookup"><span data-stu-id="dd273-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="dd273-119">Ao publicar eventos de integração por meio de um sistema de mensagens distribuído como o barramento de eventos, surge o problema da atualização do banco de dados original e da publicação de um evento de forma atômica (ou seja, ambas as operações são concluídas ou nenhuma delas).</span><span class="sxs-lookup"><span data-stu-id="dd273-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="dd273-120">Por exemplo, no exemplo simplificado mostrado anteriormente, o código confirma os dados no banco de dados quando o preço do produto é alterado e, em seguida, publica uma mensagem ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="dd273-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="dd273-121">Inicialmente, pode parecer essencial que essas duas operações sejam executada atomicamente.</span><span class="sxs-lookup"><span data-stu-id="dd273-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="dd273-122">No entanto, se você estivesse usando uma transação distribuída que envolvesse o banco de dados e o agente de mensagens, assim como faria em sistemas mais antigos, como o [MSMQ (Enfileiramento de Mensagens da Microsoft)](https://msdn.microsoft.com/library/ms711472\(v=vs.85\).aspx), isso não seria recomendado pelos motivos descritos pelo [Teorema CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="dd273-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472\(v=vs.85\).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="dd273-123">Basicamente, você usa microsserviços para criar sistemas escalonáveis e altamente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="dd273-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="dd273-124">Simplificando um pouco, o teorema CAP enuncia que não é possível criar um banco de dados (ou um microsserviço proprietário desse modelo) que seja continuamente disponível, altamente consistente *e* tolerante a qualquer partição.</span><span class="sxs-lookup"><span data-stu-id="dd273-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="dd273-125">Você deve escolher duas dessas três propriedades.</span><span class="sxs-lookup"><span data-stu-id="dd273-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="dd273-126">Em arquiteturas baseadas em microsserviços, você deve escolher a disponibilidade e a tolerância e deve tirar a ênfase da coerência forte.</span><span class="sxs-lookup"><span data-stu-id="dd273-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="dd273-127">Portanto, na maioria dos aplicativos modernos baseados em microsserviços, geralmente não é interessante usar transações distribuídas no sistema de mensagens, como ao implementar [transações distribuídas](https://msdn.microsoft.com/library/ms681205\(v=vs.85\).aspx) com base no DTC (Coordenador de Transações Distribuídas) do Windows com o [MSMQ](https://msdn.microsoft.com/library/ms711472\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="dd273-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms681205\(v=vs.85\).aspx) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472\(v=vs.85\).aspx).</span></span>

<span data-ttu-id="dd273-128">Vamos voltar para o problema inicial e o respectivo exemplo.</span><span class="sxs-lookup"><span data-stu-id="dd273-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="dd273-129">Se o serviço falhar após a atualização do banco de dados (nesse caso, logo após a linha de código com \_context.SaveChangesAsync()), mas antes que o evento de integração seja publicado, todo o sistema poderá se tornar inconsistente.</span><span class="sxs-lookup"><span data-stu-id="dd273-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="dd273-130">Isso pode ser crítico, dependendo da operação de negócios específica com a qual você está lidando.</span><span class="sxs-lookup"><span data-stu-id="dd273-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="dd273-131">Como mencionado anteriormente na seção de arquitetura, você pode ter várias abordagens para lidar com esse problema:</span><span class="sxs-lookup"><span data-stu-id="dd273-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="dd273-132">Usando o padrão [Event Sourcing](https://msdn.microsoft.com/library/dn589792.aspx) completo.</span><span class="sxs-lookup"><span data-stu-id="dd273-132">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="dd273-133">Usando [mineração do log de transações](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="dd273-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="dd273-134">Usando o [padrão Outbox](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="dd273-134">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="dd273-135">Essa é uma tabela transacional para armazenar os eventos de integração (estendendo a transação local).</span><span class="sxs-lookup"><span data-stu-id="dd273-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="dd273-136">Neste cenário, o uso do padrão ES (Event Sourcing) completo é uma das melhores abordagens, se não for *a* melhor.</span><span class="sxs-lookup"><span data-stu-id="dd273-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="dd273-137">No entanto, em muitos cenários de aplicativo, pode ser impossível implementar um sistema completo de ES.</span><span class="sxs-lookup"><span data-stu-id="dd273-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="dd273-138">O ES significa o armazenamento somente dos eventos de domínio em seu banco de dados transacional, em vez de armazenar dados do estado atual.</span><span class="sxs-lookup"><span data-stu-id="dd273-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="dd273-139">Armazenar apenas os eventos de domínio pode ter grandes benefícios, como ter o histórico do sistema disponível e poder determinar o estado do sistema em qualquer momento no passado.</span><span class="sxs-lookup"><span data-stu-id="dd273-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="dd273-140">No entanto, implementar um sistema de ES completo exige que você refaça a arquitetura da maior parte do seu sistema e também pode apresentar muitas outras complexidades e requisitos.</span><span class="sxs-lookup"><span data-stu-id="dd273-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="dd273-141">Por exemplo, vai ser interessante usar um banco de dados criado especificamente para fornecimento de eventos, como o [Event Store](https://eventstore.org/), ou um banco de dados orientado a documentos, como Azure Cosmos DB, MongoDB, Cassandra, CouchDB ou RavenDB.</span><span class="sxs-lookup"><span data-stu-id="dd273-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="dd273-142">O ES é uma ótima abordagem para esse problema, mas não é a solução mais fácil, a menos que você já esteja familiarizado com fornecimento de eventos.</span><span class="sxs-lookup"><span data-stu-id="dd273-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="dd273-143">A opção de usar a mineração do log de transações pode, inicialmente, parecer muito transparente.</span><span class="sxs-lookup"><span data-stu-id="dd273-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="dd273-144">No entanto, para usar essa abordagem, o microsserviço deverá ser acoplado ao seu log de transações do RDBMS, como o log de transações do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dd273-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="dd273-145">Isso provavelmente não é interessante.</span><span class="sxs-lookup"><span data-stu-id="dd273-145">This is probably not desirable.</span></span> <span data-ttu-id="dd273-146">Outra desvantagem é que as atualizações de baixo nível registradas no log de transações podem não estar no mesmo nível que seus eventos de integração de alto nível.</span><span class="sxs-lookup"><span data-stu-id="dd273-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="dd273-147">Nesse caso, o processo de engenharia reversa dessas operações do log de transações poderá ser difícil.</span><span class="sxs-lookup"><span data-stu-id="dd273-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="dd273-148">Uma abordagem equilibrada é uma combinação de uma tabela de banco de dados transacional e um padrão de ES simplificado.</span><span class="sxs-lookup"><span data-stu-id="dd273-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="dd273-149">Você pode usar um estado, como "pronto para publicar o evento," que você define no evento original ao confirmá-lo para a tabela de eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="dd273-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="dd273-150">Em seguida, você tenta publicar o evento no barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="dd273-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="dd273-151">Se a ação publicar evento for bem sucedida, você iniciará outra transação no serviço de origem e mudará o estado de "pronto para publicar o evento" para "evento já publicado".</span><span class="sxs-lookup"><span data-stu-id="dd273-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="dd273-152">Se a ação publicar evento falhar no barramento de eventos, os dados ainda não estarão inconsistentes no microsserviço origem – ainda estarão marcados como "pronto para publicar o evento" e, em relação ao restante dos serviços, eles estarão eventualmente consistentes.</span><span class="sxs-lookup"><span data-stu-id="dd273-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="dd273-153">Você sempre fazer com que trabalhos em segundo plano verifiquem o estado das transações ou dos eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="dd273-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="dd273-154">Se o trabalho encontrar um evento no estado "pronto para publicar o evento", ele poderá tentar publicá-lo novamente no barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="dd273-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="dd273-155">Observe que, com essa abordagem, você estará persistindo apenas os eventos de integração de cada microsserviço de origem e somente os eventos que você deseja comunicar para outros microsserviços ou sistemas externos.</span><span class="sxs-lookup"><span data-stu-id="dd273-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="dd273-156">Por outro lado, em um sistema completo de ES, você também armazena todos os eventos de domínio.</span><span class="sxs-lookup"><span data-stu-id="dd273-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="dd273-157">Portanto, essa abordagem equilibrada é um sistema de ES simplificado.</span><span class="sxs-lookup"><span data-stu-id="dd273-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="dd273-158">Você precisa de uma lista de eventos de integração com os respectivos estados atuais ("pronto para publicar" versus "publicado").</span><span class="sxs-lookup"><span data-stu-id="dd273-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="dd273-159">Mas você só precisa implementar esses estados para os eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="dd273-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="dd273-160">E, nessa abordagem, não é necessário armazenar todos os dados de domínio como eventos no banco de dados transacional, como você faria em um sistema completo de ES.</span><span class="sxs-lookup"><span data-stu-id="dd273-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="dd273-161">Se já está usando um banco de dados relacional, você pode usar uma tabela transacional para armazenar eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="dd273-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="dd273-162">Para obter a atomicidade em seu aplicativo, você usa um processo de duas etapas com base nas transações locais.</span><span class="sxs-lookup"><span data-stu-id="dd273-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="dd273-163">Basicamente, você tem uma tabela IntegrationEvent no mesmo banco de dados em que estão as entidades de domínio.</span><span class="sxs-lookup"><span data-stu-id="dd273-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="dd273-164">Essa tabela funciona como um seguro para a obtenção de atomicidade, para que você inclua eventos de integração persistidos nas mesmas transações que estão confirmando seus dados de domínio.</span><span class="sxs-lookup"><span data-stu-id="dd273-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="dd273-165">Passo a passo, o processo é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dd273-165">Step by step, the process goes like this:</span></span>

1.  <span data-ttu-id="dd273-166">O aplicativo inicia uma transação de banco de dados local.</span><span class="sxs-lookup"><span data-stu-id="dd273-166">The application begins a local database transaction.</span></span>

2.  <span data-ttu-id="dd273-167">Em seguida, ele atualiza o estado das suas entidades de domínio e insere um evento na tabela de eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="dd273-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3.  <span data-ttu-id="dd273-168">Por fim, ele confirma a transação, de modo que você obtenha a atomicidade desejada e</span><span class="sxs-lookup"><span data-stu-id="dd273-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4.  <span data-ttu-id="dd273-169">Você publica o evento de alguma forma (a seguir).</span><span class="sxs-lookup"><span data-stu-id="dd273-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="dd273-170">Ao implementar as etapas de publicação dos eventos, você tem estas opções:</span><span class="sxs-lookup"><span data-stu-id="dd273-170">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="dd273-171">Publicar o evento de integração logo após a confirmação da transação e usar outra transação local para marcar os eventos na tabela como sendo publicados.</span><span class="sxs-lookup"><span data-stu-id="dd273-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="dd273-172">Em seguida, usar a tabela apenas como um artefato para controlar os eventos de integração, em caso de problemas com os microsserviços remotos, e executar ações compensatórias com base nos eventos de integração armazenados.</span><span class="sxs-lookup"><span data-stu-id="dd273-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="dd273-173">Usar a tabela como um tipo de fila.</span><span class="sxs-lookup"><span data-stu-id="dd273-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="dd273-174">Um thread ou processo do aplicativo separado consulta a tabela de eventos de integração, publica os eventos no barramento de eventos e, em seguida, usa uma transação local para marcar os eventos como publicados.</span><span class="sxs-lookup"><span data-stu-id="dd273-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="dd273-175">A Figura 6-22 mostra a arquitetura da primeira dessas abordagens.</span><span class="sxs-lookup"><span data-stu-id="dd273-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Uma abordagem para lidar com a atomicidade ao publicar eventos: usar uma transação para confirmar o evento em uma tabela de log de eventos e, em seguida, outra transação para publicá-lo (usado em eShopOnContainers)](./media/image23.png)

<span data-ttu-id="dd273-177">**Figura 6-22**.</span><span class="sxs-lookup"><span data-stu-id="dd273-177">**Figure 6-22**.</span></span> <span data-ttu-id="dd273-178">Atomicidade ao publicar eventos no barramento de eventos</span><span class="sxs-lookup"><span data-stu-id="dd273-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="dd273-179">A abordagem ilustrada na Figura 6-22 não tem um microsserviço de trabalho adicional, que é responsável por verificar e confirmar o êxito dos eventos de integração publicados.</span><span class="sxs-lookup"><span data-stu-id="dd273-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="dd273-180">Em caso de falha, esse microsserviço de trabalho verificador adicional pode ler os eventos na tabela e publicá-los novamente, ou seja, repetir a etapa 2.</span><span class="sxs-lookup"><span data-stu-id="dd273-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="dd273-181">Em relação à segunda abordagem: você usa a tabela EventLog como uma fila e sempre usa um microsserviço de trabalho para publicar as mensagens.</span><span class="sxs-lookup"><span data-stu-id="dd273-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="dd273-182">Nesse caso, o processo é como o mostrado na Figura 6-23.</span><span class="sxs-lookup"><span data-stu-id="dd273-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="dd273-183">Ela mostra um microsserviço adicional, e a tabela é a única fonte durante a publicação de eventos.</span><span class="sxs-lookup"><span data-stu-id="dd273-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Outra abordagem para lidar com a atomicidade: fazer a publicação em uma tabela de log de eventos e, em seguida, usar outro microsserviço (um trabalho em segundo plano) para publicar o evento.](./media/image24.png)

<span data-ttu-id="dd273-185">**Figura 6-23**.</span><span class="sxs-lookup"><span data-stu-id="dd273-185">**Figure 6-23**.</span></span> <span data-ttu-id="dd273-186">Atomicidade ao publicar eventos no barramento de eventos com um microsserviço de trabalho</span><span class="sxs-lookup"><span data-stu-id="dd273-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="dd273-187">Para simplificar, o exemplo eShopOnContainers usa a primeira abordagem (sem processos adicionais nem microsserviços verificadores) e o barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="dd273-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="dd273-188">No entanto, o eShopOnContainers não trata todos os casos de falha possíveis.</span><span class="sxs-lookup"><span data-stu-id="dd273-188">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="dd273-189">Em um aplicativo real implantado na nuvem, você deve aceitar o fato de que os problemas surgirão eventualmente, e você deverá implementar essa lógica de verificação e reenvio.</span><span class="sxs-lookup"><span data-stu-id="dd273-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="dd273-190">O uso da tabela como uma fila pode ser mais eficiente do que a primeira abordagem se você tem essa tabela como uma única fonte de eventos ao publicá-los (com o trabalho) por meio do barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="dd273-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="dd273-191">Implementando atomicidade ao publicar eventos de integração por meio do barramento de eventos</span><span class="sxs-lookup"><span data-stu-id="dd273-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="dd273-192">O código a seguir mostra como criar uma única transação que envolva vários objetos DbContext: um contexto relacionados aos dados originais que estão sendo atualizados e o segundo contexto relacionado à tabela IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="dd273-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="dd273-193">Observe que a transação, no código de exemplo abaixo, não será resiliente se as conexões com o banco de dados enfrentarem qualquer problema no momento em que o código estiver sendo executado.</span><span class="sxs-lookup"><span data-stu-id="dd273-193">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="dd273-194">Isso pode ocorrer em sistemas baseados em nuvem, como o BD SQL do Azure, que pode mover bancos de dados entre servidores.</span><span class="sxs-lookup"><span data-stu-id="dd273-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="dd273-195">Para implementar transações resilientes em vários contextos, consulte a seção [Implementando conexões de SQL do Entity Framework Core resilientes](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) mais adiante, neste guia.</span><span class="sxs-lookup"><span data-stu-id="dd273-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="dd273-196">Para maior clareza, o exemplo a seguir mostra todo o processo em um único segmento de código.</span><span class="sxs-lookup"><span data-stu-id="dd273-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="dd273-197">No entanto, a implementação do eShopOnContainers refatorou e dividiu essa lógica em várias classes, sendo mais fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="dd273-197">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate) 
{
  var catalogItem = 
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id == 
                                                               productToUpdate.Id); 
  if (catalogItem == null) return NotFound();

  bool raiseProductPriceChangedEvent = false; 
  IntegrationEvent priceChangedEvent = null; 

  if (catalogItem.Price != productToUpdate.Price) 
          raiseProductPriceChangedEvent = true; 

  if (raiseProductPriceChangedEvent) // Create event if price has changed
  {
      var oldPrice = catalogItem.Price; 
      priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
                                                                  productToUpdate.Price, 
                                                                  oldPrice); 
  }
  // Update current product
  catalogItem = productToUpdate; 

  // Just save the updated product if the Product's Price hasn't changed.
  if (!raiseProductPriceChangedEvent) 
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
        // Achieving atomicity between original DB and the IntegrationEventLog 
        // with a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
           _catalogContext.CatalogItems.Update(catalogItem); 
           await _catalogContext.SaveChangesAsync();

           // Save to EventLog only if product price changed
           if(raiseProductPriceChangedEvent) 
               await _integrationEventLogService.SaveEventAsync(priceChangedEvent); 

           transaction.Commit();
        }   

      // Publish the intergation event through the event bus
      _eventBus.Publish(priceChangedEvent); 

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent); 
  }

  return Ok();
}

```

<span data-ttu-id="dd273-198">Depois que o evento de integração ProductPriceChangedIntegrationEvent é criado, a transação que armazena a operação de domínio original (atualizar o item de catálogo) também inclui a persistência do evento na tabela EventLog.</span><span class="sxs-lookup"><span data-stu-id="dd273-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="dd273-199">Isso faz com que ele se torne uma única transação, e sempre será possível verificar se as mensagens de evento foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="dd273-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="dd273-200">A tabela do log de eventos é atualizada atomicamente com a operação do banco de dados original, usando uma transação local no mesmo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="dd273-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="dd273-201">Se uma das operações falha, uma exceção é gerada e a transação reverte qualquer operação concluída, mantendo a consistência entre as operações de domínio e as mensagens de evento salvas na tabela.</span><span class="sxs-lookup"><span data-stu-id="dd273-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="dd273-202">Recebendo mensagens de assinaturas: manipuladores de eventos em microsserviços destinatários</span><span class="sxs-lookup"><span data-stu-id="dd273-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="dd273-203">Além da lógica de assinatura de evento, você precisa implementar o código interno para os manipuladores de eventos de integração (como um método de retorno de chamada).</span><span class="sxs-lookup"><span data-stu-id="dd273-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="dd273-204">O manipulador de eventos é o local em que você especifica o local em que as mensagens de eventos de um determinado tipo serão recebidas e processadas.</span><span class="sxs-lookup"><span data-stu-id="dd273-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="dd273-205">Primeiro, um manipulador de eventos recebe uma instância de evento do barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="dd273-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="dd273-206">Em seguida, ele localiza o componente a ser processado, relacionado a esse evento de integração, propagando e persistindo o evento como uma alteração no estado no microsserviço destinatário.</span><span class="sxs-lookup"><span data-stu-id="dd273-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="dd273-207">Por exemplo, se um evento ProductPriceChanged se origina no microsserviço catálogo, ele é tratado no microsserviço carrinho de compras e também altera o estado nesse microsserviço destinatário de carrinho de compras, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="dd273-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

<span data-ttu-id="dd273-208">O manipulador de eventos deve verificar se o produto existe em qualquer uma das instâncias do carrinho de compras.</span><span class="sxs-lookup"><span data-stu-id="dd273-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="dd273-209">Ele também atualiza o preço do item para cada item de linha relacionado ao carrinho.</span><span class="sxs-lookup"><span data-stu-id="dd273-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="dd273-210">Por fim, ele cria um alerta sobre a alteração de preço, que será exibido para o usuário, conforme mostrado na Figura 6-24.</span><span class="sxs-lookup"><span data-stu-id="dd273-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Exibição do navegador da notificação de alteração de preço no carrinho do usuário.](./media/image25.png)

<span data-ttu-id="dd273-212">**Figura 6-24**.</span><span class="sxs-lookup"><span data-stu-id="dd273-212">**Figure 6-24**.</span></span> <span data-ttu-id="dd273-213">Exibindo uma alteração de preço de item em um carrinho de compras, conforme comunicado pelos eventos de integração</span><span class="sxs-lookup"><span data-stu-id="dd273-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="dd273-214">Idempotência em eventos de mensagem de atualização</span><span class="sxs-lookup"><span data-stu-id="dd273-214">Idempotency in update message events</span></span>

<span data-ttu-id="dd273-215">Um aspecto importante dos eventos de mensagem de atualização é que uma falha em qualquer ponto da comunicação deverá fazer com que a mensagem seja repetida.</span><span class="sxs-lookup"><span data-stu-id="dd273-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="dd273-216">Caso contrário, uma tarefa em segundo plano poderá tentar publicar um evento que já tenha sido publicado, criando uma condição de corrida.</span><span class="sxs-lookup"><span data-stu-id="dd273-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="dd273-217">Você precisa se certificar de que as atualizações sejam idempotentes ou que elas forneçam informações suficientes para garantir que você possa detectar uma duplicata, descartá-la e enviar apenas uma resposta de volta.</span><span class="sxs-lookup"><span data-stu-id="dd273-217">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="dd273-218">Conforme observado anteriormente, a idempotência significa que uma operação poderá ser executada várias vezes sem alterar o resultado.</span><span class="sxs-lookup"><span data-stu-id="dd273-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="dd273-219">Em um ambiente de sistema de mensagens, como ao comunicar eventos, um evento será idempotente se ele puder ser entregue várias vezes sem alterar o resultado para o microsserviço destinatário.</span><span class="sxs-lookup"><span data-stu-id="dd273-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="dd273-220">Isso pode ser necessário devido à natureza do evento em si ou devido à maneira como o sistema manipula o evento.</span><span class="sxs-lookup"><span data-stu-id="dd273-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="dd273-221">A idempotência de mensagem é importante em qualquer aplicativo que use o sistema de mensagens, e não apenas em aplicativos que implementam o padrão do barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="dd273-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="dd273-222">Um exemplo de uma operação idempotente é uma instrução SQL que insere dados em uma tabela somente se os dados ainda não estiverem na tabela.</span><span class="sxs-lookup"><span data-stu-id="dd273-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="dd273-223">Não importa quantas vezes você executa essa instrução insert do SQL; o resultado será o mesmo: a tabela conterá esses dados.</span><span class="sxs-lookup"><span data-stu-id="dd273-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="dd273-224">Essa idempotência também poderá ser necessária ao lidar com mensagens se houver chances de que elas sejam enviadas e processadas mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="dd273-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="dd273-225">Por exemplo, se a lógica de repetição fizer com que um remetente envie exatamente a mesma mensagem mais de uma vez, você precisará verificar se ela é idempotente.</span><span class="sxs-lookup"><span data-stu-id="dd273-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="dd273-226">É possível projetar mensagens idempotentes.</span><span class="sxs-lookup"><span data-stu-id="dd273-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="dd273-227">Por exemplo, crie um evento que indica "definir o preço do produto como US$ 25" em vez de "adicionar US$ 5 ao preço do produto".</span><span class="sxs-lookup"><span data-stu-id="dd273-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="dd273-228">A primeira mensagem pode ser processada com segurança qualquer número de vezes e o resultado será o mesmo.</span><span class="sxs-lookup"><span data-stu-id="dd273-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="dd273-229">Isso não é válido para a segunda mensagem.</span><span class="sxs-lookup"><span data-stu-id="dd273-229">That is not true for the second message.</span></span> <span data-ttu-id="dd273-230">Mas, mesmo no primeiro caso, talvez não seja interessante processar o primeiro evento, porque o sistema também pode ter enviado um evento de alteração de preço mais recente, e o novo preço seria substituído.</span><span class="sxs-lookup"><span data-stu-id="dd273-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="dd273-231">Outro exemplo poderia ser o de um evento de pedido concluído propagado para vários assinantes.</span><span class="sxs-lookup"><span data-stu-id="dd273-231">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="dd273-232">É importante que as informações de pedidos sejam atualizadas em outros sistemas apenas uma vez, mesmo que haja eventos de mensagem duplicada para o mesmo evento pedido concluído.</span><span class="sxs-lookup"><span data-stu-id="dd273-232">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="dd273-233">É conveniente ter algum tipo de identidade por evento, para que você possa criar uma lógica que imponha que cada evento seja processado apenas uma vez em cada destinatário.</span><span class="sxs-lookup"><span data-stu-id="dd273-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="dd273-234">Alguns processamentos de mensagens são inerentemente idempotentes.</span><span class="sxs-lookup"><span data-stu-id="dd273-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="dd273-235">Por exemplo, se um sistema gerar miniaturas de imagem, não importará quantas vezes a mensagem sobre a miniatura gerada vai ser processada; o resultado será que as miniaturas foram geradas e elas serão sempre as mesmas.</span><span class="sxs-lookup"><span data-stu-id="dd273-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="dd273-236">Por outro lado, operações como chamar um gateway de pagamento para cobrar um cartão de crédito jamais poderão ser idempotentes.</span><span class="sxs-lookup"><span data-stu-id="dd273-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="dd273-237">Nesses casos, você precisa garantir que o processamento de uma mensagem várias vezes tenha o efeito que você espera.</span><span class="sxs-lookup"><span data-stu-id="dd273-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dd273-238">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="dd273-238">Additional resources</span></span>

-   <span data-ttu-id="dd273-239">**Respeitando a idempotência da mensagem**</span><span class="sxs-lookup"><span data-stu-id="dd273-239">**Honoring message idempotency**</span></span> <br/>
    [*https://msdn.microsoft.com/library/jj591565.aspx#honoring_message_idempotency*](https://msdn.microsoft.com/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="dd273-240">Eliminando a duplicação de mensagens de eventos de integração</span><span class="sxs-lookup"><span data-stu-id="dd273-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="dd273-241">Você pode se certificar de que os eventos de mensagem sejam enviados e processados apenas uma vez por assinante em diferentes níveis.</span><span class="sxs-lookup"><span data-stu-id="dd273-241">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="dd273-242">Uma maneira é usar um recurso de eliminação de duplicação oferecido pela infraestrutura do sistema de mensagens que você está usando.</span><span class="sxs-lookup"><span data-stu-id="dd273-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="dd273-243">Outra é implementar uma lógica personalizada no microsserviço de destino.</span><span class="sxs-lookup"><span data-stu-id="dd273-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="dd273-244">A melhor opção é ter validações no nível de transporte e no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd273-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="dd273-245">Eliminando a duplicação de eventos de mensagem no nível do EventHandler</span><span class="sxs-lookup"><span data-stu-id="dd273-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="dd273-246">Uma maneira de se certificar que um evento será processado apenas uma vez por qualquer destinatário é implementar alguma lógica durante o processamento de eventos de mensagem em manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="dd273-246">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="dd273-247">Por exemplo, essa é a abordagem usada no aplicativo eShopOnContainers, como você pode ver no [código-fonte da classe UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) quando ele recebe um evento de integração UserCheckoutAcceptedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="dd273-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives an UserCheckoutAcceptedIntegrationEvent integration event.</span></span> <span data-ttu-id="dd273-248">(Nesse caso, encapsulamos o CreateOrderCommand com um IdentifiedCommand, usando o eventMsg.RequestId como um identificador, antes de enviá-lo para o manipulador de comando).</span><span class="sxs-lookup"><span data-stu-id="dd273-248">(In this case we wrap the CreateOrderCommand with an IdentifiedCommand, using the eventMsg.RequestId as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="dd273-249">Eliminando a duplicação de mensagens ao usar RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="dd273-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="dd273-250">Quando ocorrem falhas intermitentes na rede, as mensagens podem ser duplicadas e o destinatário da mensagem deve estar preparado para lidar com essas mensagens duplicadas.</span><span class="sxs-lookup"><span data-stu-id="dd273-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="dd273-251">Sempre que possível, os destinatários devem lidar com as mensagens de maneira idempotente, pois isso é melhor que tratá-las explicitamente com a eliminação de duplicação.</span><span class="sxs-lookup"><span data-stu-id="dd273-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="dd273-252">De acordo com a [documentação do RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Se uma mensagem for entregue a um consumidor e, em seguida, recolocada na fila (porque ela não foi reconhecida antes que a conexão do consumidor caísse, por exemplo), o RabbitMQ definirá o sinalizador redelivered na mensagem quando ela for entregue novamente (tanto para o mesmo consumidor quanto para um consumidor diferente).</span><span class="sxs-lookup"><span data-stu-id="dd273-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="dd273-253">Se o sinalizador "redelivered" for definido, o destinatário deverá considerar que a mensagem poderá já ter sido processada.</span><span class="sxs-lookup"><span data-stu-id="dd273-253">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="dd273-254">Mas isso não é garantido; a mensagem pode nunca ter alcançado o destinatário depois de deixar o agente de mensagens, talvez por causa de problemas de rede.</span><span class="sxs-lookup"><span data-stu-id="dd273-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="dd273-255">Por outro lado, se o sinalizador "redelivered" não estiver definido, será uma certeza de que a mensagem não foi enviada mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="dd273-255">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="dd273-256">Portanto, o destinatário deverá eliminar a duplicação de mensagens ou processar mensagens de maneira idempotente somente se o sinalizador "redelivered" estiver definido na mensagem.</span><span class="sxs-lookup"><span data-stu-id="dd273-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dd273-257">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="dd273-257">Additional resources</span></span>

-   <span data-ttu-id="dd273-258">**eShopOnContainers bifurcado usando NServiceBus (software específico)**</span><span class="sxs-lookup"><span data-stu-id="dd273-258">**Forked eShopOnContainers using NServiceBus (Particular Software)**</span></span> <br/>
    [*https://go.particular.net/eShopOnContainers*](https://go.particular.net/eShopOnContainers)

-   <span data-ttu-id="dd273-259">**Mensagens controladas por evento**</span><span class="sxs-lookup"><span data-stu-id="dd273-259">**Event Driven Messaging**</span></span> <br/>
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   <span data-ttu-id="dd273-260">**Jimmy Bogard. Refatoração para resiliência: avaliação do acoplamento**</span><span class="sxs-lookup"><span data-stu-id="dd273-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**</span></span> <br/>
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   <span data-ttu-id="dd273-261">**Canal de publicação/assinatura**</span><span class="sxs-lookup"><span data-stu-id="dd273-261">**Publish-Subscribe channel**</span></span> <br/>
    [*https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   <span data-ttu-id="dd273-262">**Comunicação entre contextos limitados**</span><span class="sxs-lookup"><span data-stu-id="dd273-262">**Communicating Between Bounded Contexts**</span></span> <br/>
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   <span data-ttu-id="dd273-263">**Consistência eventual**</span><span class="sxs-lookup"><span data-stu-id="dd273-263">**Eventual Consistency**</span></span> <br/>
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   <span data-ttu-id="dd273-264">**Philip Brown. Estratégias para integrar contextos limitados**</span><span class="sxs-lookup"><span data-stu-id="dd273-264">**Philip Brown. Strategies for Integrating Bounded Contexts**</span></span> <br/>
    [*https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   <span data-ttu-id="dd273-265">**Chris Richardson. Desenvolvendo microsserviços transacionais usando agregações, origem de eventos e CQRS – parte 2**</span><span class="sxs-lookup"><span data-stu-id="dd273-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**</span></span> <br/>
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   <span data-ttu-id="dd273-266">**Chris Richardson. Padrão de origem de eventos**</span><span class="sxs-lookup"><span data-stu-id="dd273-266">**Chris Richardson. Event Sourcing pattern**</span></span> <br/>
    [*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)

-   <span data-ttu-id="dd273-267">**Introdução à origem de eventos**</span><span class="sxs-lookup"><span data-stu-id="dd273-267">**Introducing Event Sourcing**</span></span> <br/>
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)

-   <span data-ttu-id="dd273-268">**Banco de dados Event Store**.</span><span class="sxs-lookup"><span data-stu-id="dd273-268">**Event Store database**.</span></span> <span data-ttu-id="dd273-269">Site oficial.</span><span class="sxs-lookup"><span data-stu-id="dd273-269">Official site.</span></span> <br/>
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   <span data-ttu-id="dd273-270">**Patrick Nommensen. Gerenciamento de dados controlado por evento para microsserviços**</span><span class="sxs-lookup"><span data-stu-id="dd273-270">**Patrick Nommensen. Event-Driven Data Management for Microservices**</span></span> <br/>
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *

-   <span data-ttu-id="dd273-271">**O Teorema de CAP**</span><span class="sxs-lookup"><span data-stu-id="dd273-271">**The CAP Theorem**</span></span> <br/>
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)

-   <span data-ttu-id="dd273-272">**O que é o Teorema de CAP?**</span><span class="sxs-lookup"><span data-stu-id="dd273-272">**What is CAP Theorem?**</span></span> <br/>
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   <span data-ttu-id="dd273-273">**Guia de Consistência de Dados**</span><span class="sxs-lookup"><span data-stu-id="dd273-273">**Data Consistency Primer**</span></span> <br/>
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   <span data-ttu-id="dd273-274">**Rick Saling. O Teorema de CAP: por que “tudo está diferente” na nuvem e na Internet**</span><span class="sxs-lookup"><span data-stu-id="dd273-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**</span></span> <br/>
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   <span data-ttu-id="dd273-275">**Eric Brewer. CAP doze anos depois: como as "regras" mudaram**</span><span class="sxs-lookup"><span data-stu-id="dd273-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**</span></span> <br/>
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   <span data-ttu-id="dd273-276">**Barramento de Serviço do Azure. Sistema de mensagens agenciado: detecção de duplicidades**</span><span class="sxs-lookup"><span data-stu-id="dd273-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**</span></span>  <br/>
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   <span data-ttu-id="dd273-277">**Guia de Confiabilidade** (documentação do RabbitMQ)\*</span><span class="sxs-lookup"><span data-stu-id="dd273-277">**Reliability Guide** (RabbitMQ documentation)\*</span></span> <br/>
    [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html#consumer)

-   <span data-ttu-id="dd273-278">**Participando de transações externas (DTC)** (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="dd273-278">**Participating in External (DTC) Transactions** (MSMQ)</span></span> <br/>
    [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   <span data-ttu-id="dd273-279">**Barramento de Serviço do Azure. Sistema de mensagens agenciado: detecção de duplicidades**</span><span class="sxs-lookup"><span data-stu-id="dd273-279">**Azure Service Bus. Brokered Messaging: Duplicate Detection**</span></span> <br/>
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   <span data-ttu-id="dd273-280">**Guia de Confiabilidade** (documentação do RabbitMQ)</span><span class="sxs-lookup"><span data-stu-id="dd273-280">**Reliability Guide** (RabbitMQ documentation)</span></span> <br/>
    [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
<span data-ttu-id="dd273-281">[Anterior](rabbitmq-event-bus-development-test-environment.md)
[Próximo](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="dd273-281">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
