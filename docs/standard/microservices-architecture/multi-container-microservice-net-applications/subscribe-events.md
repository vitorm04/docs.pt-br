---
title: Assinando eventos
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Assinando eventos"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: fe17b53a39ff2964cd60183e291e2936d3ba28df
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="subscribing-to-events"></a><span data-ttu-id="1daf2-104">Assinando eventos</span><span class="sxs-lookup"><span data-stu-id="1daf2-104">Subscribing to events</span></span>

<span data-ttu-id="1daf2-105">A primeira etapa para usar o barramento de evento é assinar microservices os eventos que desejam receber.</span><span class="sxs-lookup"><span data-stu-id="1daf2-105">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="1daf2-106">Isso deve ser feito em microservices o receptor.</span><span class="sxs-lookup"><span data-stu-id="1daf2-106">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="1daf2-107">O código simple a seguir mostra o que cada destinatário microsserviço precisa implementar ao iniciar o serviço (ou seja, na inicialização de classe) para que ela assina os eventos ele precisa.</span><span class="sxs-lookup"><span data-stu-id="1daf2-107">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the Startup class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="1daf2-108">Por exemplo, o microsserviço basket.api precisa se inscrever em ProductPriceChangedIntegrationEvent mensagens.</span><span class="sxs-lookup"><span data-stu-id="1daf2-108">For instance, the basket.api microservice needs to subscribe to ProductPriceChangedIntegrationEvent messages.</span></span> <span data-ttu-id="1daf2-109">Isso torna o microsserviço reconhece as alterações para o preço do produto e permite que ele avisar o usuário sobre a alteração se o produto está em sua cesta do usuário.</span><span class="sxs-lookup"><span data-stu-id="1daf2-109">This makes the microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();
eventBus.Subscribe<ProductPriceChangedIntegrationEvent>(
    ProductPriceChangedIntegrationEventHandler);
```

<span data-ttu-id="1daf2-110">Depois que esse código é executado, o assinante microsserviço estará escutando por meio de canais de RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="1daf2-110">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="1daf2-111">Quando qualquer mensagem do tipo ProductPriceChangedIntegrationEvent chega, o código invoca o manipulador de eventos que é passado a ele e processa o evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-111">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="1daf2-112">Publicar eventos por meio do barramento de evento</span><span class="sxs-lookup"><span data-stu-id="1daf2-112">Publishing events through the event bus</span></span>

<span data-ttu-id="1daf2-113">Por fim, o remetente da mensagem (origem microsserviço) publica os eventos de integração com o código semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1daf2-113">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="1daf2-114">(Isso é um exemplo simplificado que não precise de atomicidade em conta). Você poderia implementar um código semelhante sempre que um evento deve ser propagado por vários microservices, geralmente logo após a confirmação de dados ou transações de microsserviço a origem.</span><span class="sxs-lookup"><span data-stu-id="1daf2-114">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="1daf2-115">Primeiro, o objeto de implementação de barramento de evento (com base em RabbitMQ ou em um barramento de serviço) seria injetado no construtor do controlador, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="1daf2-115">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="1daf2-116">Em seguida, você usá-lo de métodos do controlador, como no método UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="1daf2-116">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("update")]
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

<span data-ttu-id="1daf2-117">Nesse caso, como o microsserviço de origem é um microsserviço CRUD simple, que o código é colocado à direita em um controlador Web API.</span><span class="sxs-lookup"><span data-stu-id="1daf2-117">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> <span data-ttu-id="1daf2-118">No microservices mais avançadas, ele pode ser implementado na classe CommandHandler, à direita depois que os dados originais são confirmados.</span><span class="sxs-lookup"><span data-stu-id="1daf2-118">In more advanced microservices, it could be implemented in the CommandHandler class, right after the original data is committed.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="1daf2-119">Criando a atomicidade e a resiliência durante a publicação para o barramento de evento</span><span class="sxs-lookup"><span data-stu-id="1daf2-119">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="1daf2-120">Quando você publica os eventos de integração por meio de um sistema de mensagens distribuídas sistema como o barramento de evento, você tem o problema de forma atômica atualizando o banco de dados original e publicação de um evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-120">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event.</span></span> <span data-ttu-id="1daf2-121">Por exemplo, no exemplo simplificado mostrado anteriormente, o código confirma dados o banco de dados quando o preço do produto é alterado e, em seguida, publica uma mensagem ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="1daf2-121">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="1daf2-122">Inicialmente, ele pode ser essencial que essas duas operações ser executada atomicamente.</span><span class="sxs-lookup"><span data-stu-id="1daf2-122">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="1daf2-123">No entanto, se você estiver usando uma transação distribuída que envolvem o banco de dados e a mensagem do agente, como faria em sistemas mais antigos como [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), isso não é recomendado pelos motivos descritos pela [Teorema de CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="1daf2-123">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="1daf2-124">Basicamente, você deve usar microservices para criar sistemas escalonáveis e altamente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1daf2-124">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="1daf2-125">Simplificando um pouco, o Teorema de CAP diz que você não pode criar um banco de dados (ou um microsserviço que possui seu modelo) que é continuamente disponíveis, altamente consistente, *e* tolerante a falhas para qualquer partição.</span><span class="sxs-lookup"><span data-stu-id="1daf2-125">Simplifying somewhat, the CAP theorem says that you cannot build a database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="1daf2-126">Você deve escolher dois desses três propriedades.</span><span class="sxs-lookup"><span data-stu-id="1daf2-126">You must choose two of these three properties.</span></span>

<span data-ttu-id="1daf2-127">Em arquiteturas de microservices, você deve escolher a disponibilidade e a tolerância e você deve remover consistência forte.</span><span class="sxs-lookup"><span data-stu-id="1daf2-127">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="1daf2-128">Portanto, na maioria dos aplicativos baseados em microsserviço, geralmente não desejar usar transações distribuídas no sistema de mensagens, como faz quando você implementa [transações distribuídas](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) com base em que a transação distribuída do Windows DTC (coordenador) com [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="1daf2-128">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="1daf2-129">Vamos voltar para o problema inicial e o seu exemplo.</span><span class="sxs-lookup"><span data-stu-id="1daf2-129">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="1daf2-130">Se o serviço falhar após a atualização do banco de dados (nesse caso, logo após a linha de código com \_contexto. SaveChangesAsync()), mas antes do evento de integração é publicado, todo o sistema pode se tornar inconsistente.</span><span class="sxs-lookup"><span data-stu-id="1daf2-130">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="1daf2-131">Isso pode ser crítico, dependendo da operação de negócios específicas que você está lidando com negócios.</span><span class="sxs-lookup"><span data-stu-id="1daf2-131">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="1daf2-132">Como mencionado anteriormente na seção de arquitetura, você pode ter várias abordagens para lidar com esse problema:</span><span class="sxs-lookup"><span data-stu-id="1daf2-132">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="1daf2-133">Usando o completo [padrão de evento de fornecimento](https://msdn.microsoft.com/en-us/library/dn589792.aspx).</span><span class="sxs-lookup"><span data-stu-id="1daf2-133">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/en-us/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="1daf2-134">Usando [mineração do log de transações](http://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="1daf2-134">Using [transaction log mining](http://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="1daf2-135">Usando o [da caixa de saída padrão](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="1daf2-135">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="1daf2-136">Essa é uma tabela transacional para armazenar os eventos de integração (estendendo a transação local).</span><span class="sxs-lookup"><span data-stu-id="1daf2-136">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="1daf2-137">Para este cenário, usando o padrão de evento Sourcing (ES) completo é um dos melhores abordagens, se não *o* melhor.</span><span class="sxs-lookup"><span data-stu-id="1daf2-137">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="1daf2-138">No entanto, em muitos cenários de aplicativo, você pode não ser capaz de implementar um sistema completo de ES.</span><span class="sxs-lookup"><span data-stu-id="1daf2-138">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="1daf2-139">ES significa armazenar apenas os eventos de domínio em seu banco de dados transacional, em vez de armazenar dados de estado atual.</span><span class="sxs-lookup"><span data-stu-id="1daf2-139">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="1daf2-140">Armazenar apenas os eventos de domínio pode ter grandes benefícios, como tendo o histórico do sistema disponível e ser capaz de determinar o estado do sistema em qualquer momento no passado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-140">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="1daf2-141">No entanto, implementar um sistema completo de ES exige que você Refaça a maior parte do seu sistema de arquitetura e apresenta muitas outras complexidades e os requisitos.</span><span class="sxs-lookup"><span data-stu-id="1daf2-141">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="1daf2-142">Por exemplo, convém usar um banco de dados feito especificamente para fornecimento de evento, como [repositório de eventos](https://geteventstore.com/), ou um banco de dados orientado por documentos, como o banco de dados do Azure Cosmos, MongoDB, Cassandra, CouchDB ou RavenDB.</span><span class="sxs-lookup"><span data-stu-id="1daf2-142">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://geteventstore.com/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="1daf2-143">ES é uma abordagem ótima para esse problema, mas não a solução mais fácil, a menos que você já estiver familiarizado com o fornecimento do evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-143">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="1daf2-144">A opção de usar o log de transações de mineração inicialmente parece muito transparente.</span><span class="sxs-lookup"><span data-stu-id="1daf2-144">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="1daf2-145">No entanto, para usar essa abordagem, o microsserviço deve ser associada ao seu log de transações do RDBMS, como o log de transações do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1daf2-145">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="1daf2-146">Isso provavelmente não é desejável.</span><span class="sxs-lookup"><span data-stu-id="1daf2-146">This is probably not desirable.</span></span> <span data-ttu-id="1daf2-147">Outra desvantagem é que as atualizações de baixo nível registradas no log de transações podem não estar no mesmo nível como seus eventos de integração de alto nível.</span><span class="sxs-lookup"><span data-stu-id="1daf2-147">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="1daf2-148">Nesse caso, o processo de engenharia reversa essas operações de log de transações podem ser difícil.</span><span class="sxs-lookup"><span data-stu-id="1daf2-148">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="1daf2-149">Uma abordagem equilibrada é uma combinação de uma tabela de banco de dados transacional e um padrão de ES simplificado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-149">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="1daf2-150">Você pode usar um estado, como "pronto para publicar o evento," que você definir no evento original quando confirmá-la para a tabela de eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="1daf2-150">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="1daf2-151">Em seguida, tentar publicar o evento para o barramento de evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-151">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="1daf2-152">Se a ação de evento de publicação tiver êxito, iniciar outra transação no serviço de origem e mover o estado de "pronto para publicar o evento" para "evento" já foi publicado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-152">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="1daf2-153">Se a ação de evento de publicação no evento de barramento falhar, os dados ainda não será inconsistentes dentro de microsserviço origem — ainda está marcado como "pronto para publicar o evento" e, em relação ao restante dos serviços, eventualmente será consistente.</span><span class="sxs-lookup"><span data-stu-id="1daf2-153">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="1daf2-154">Você sempre pode ter trabalhos em segundo plano verificar o estado das transações ou eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="1daf2-154">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="1daf2-155">Se o trabalho de encontrar um evento no estado "pronto publicar o evento", pode tentar publicar novamente o evento para o barramento de evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-155">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="1daf2-156">Observe que, com essa abordagem, você é persistentes apenas os eventos de integração para cada microsserviço de origem e somente os eventos que você deseja se comunicar com outros microservices ou sistemas externos.</span><span class="sxs-lookup"><span data-stu-id="1daf2-156">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="1daf2-157">Em contraste, em um sistema completo de ES, armazenar todos os eventos de domínio.</span><span class="sxs-lookup"><span data-stu-id="1daf2-157">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="1daf2-158">Portanto, essa abordagem equilibrada é um sistema de ES simplificado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-158">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="1daf2-159">Você precisa de uma lista de eventos de integração com seu estado atual ("pronto para publicar" versus "publicado").</span><span class="sxs-lookup"><span data-stu-id="1daf2-159">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="1daf2-160">Mas você só precisa implementar esses estados para os eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="1daf2-160">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="1daf2-161">E nessa abordagem, você não precisa armazenar todos os seus dados de domínio como eventos no banco de dados transacional, como você faria em um sistema completo de ES.</span><span class="sxs-lookup"><span data-stu-id="1daf2-161">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="1daf2-162">Se você já estiver usando um banco de dados relacional, você pode usar uma tabela transacional para armazenar eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="1daf2-162">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="1daf2-163">Para obter a atomicidade em seu aplicativo, você deve usar um processo de duas etapas com base em transações locais.</span><span class="sxs-lookup"><span data-stu-id="1daf2-163">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="1daf2-164">Basicamente, você tem uma tabela de IntegrationEvent no mesmo banco de dados em que as entidades de domínio.</span><span class="sxs-lookup"><span data-stu-id="1daf2-164">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="1daf2-165">Essa tabela funciona como um seguro para a obtenção de atomicidade para que você incluir persistentes eventos de integração para as mesmas transações que estejam sendo confirmadas seus dados de domínio.</span><span class="sxs-lookup"><span data-stu-id="1daf2-165">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="1daf2-166">Passo a passo, o processo é a seguinte: o aplicativo começa uma transação de banco de dados local.</span><span class="sxs-lookup"><span data-stu-id="1daf2-166">Step by step, the process goes like this: the application begins a local database transaction.</span></span> <span data-ttu-id="1daf2-167">Em seguida, ele atualizará o estado de suas entidades de domínio e insere um evento na tabela de eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="1daf2-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span> <span data-ttu-id="1daf2-168">Finalmente, ele confirma a transação.</span><span class="sxs-lookup"><span data-stu-id="1daf2-168">Finally, it commits the transaction.</span></span> <span data-ttu-id="1daf2-169">Você obtém a atomicidade desejada.</span><span class="sxs-lookup"><span data-stu-id="1daf2-169">You get the desired atomicity.</span></span>

<span data-ttu-id="1daf2-170">Ao implementar as etapas de publicação de eventos, você tem estas opções:</span><span class="sxs-lookup"><span data-stu-id="1daf2-170">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="1daf2-171">Publicar o evento de integração logo após a confirmação da transação e usar outra transação local para marcar os eventos na tabela que está sendo publicado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="1daf2-172">Em seguida, use a tabela como um artefato para controlar os eventos de integração em caso de problemas de microservices remoto e executar ações compensatórios com base em eventos de integração armazenado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="1daf2-173">Use a tabela como um tipo de fila.</span><span class="sxs-lookup"><span data-stu-id="1daf2-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="1daf2-174">Um thread de aplicativo separado ou o processo de consulta a tabela de eventos de integração, publica os eventos do barramento de evento e, em seguida, usa uma transação local para marcar os eventos como publicado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="1daf2-175">Figura 8-22 mostra a arquitetura para a primeira dessas abordagens.</span><span class="sxs-lookup"><span data-stu-id="1daf2-175">Figure 8-22 shows the architecture for the first of these approaches.</span></span>

![](./media/image23.png)

<span data-ttu-id="1daf2-176">**Figura 8-22**.</span><span class="sxs-lookup"><span data-stu-id="1daf2-176">**Figure 8-22**.</span></span> <span data-ttu-id="1daf2-177">Atomicidade ao publicar eventos do barramento de evento</span><span class="sxs-lookup"><span data-stu-id="1daf2-177">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="1daf2-178">A abordagem ilustrada na Figura 8-22 está faltando um microsserviço adicionais do trabalhador que é responsável por verificar e confirmar o êxito dos eventos de integração publicado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-178">The approach illustrated in Figure 8-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="1daf2-179">Em caso de falha, que microsserviço de trabalho adicionais verificador pode ler os eventos da tabela e publicá-los novamente.</span><span class="sxs-lookup"><span data-stu-id="1daf2-179">In case of failure, that additional checker worker microservice can read events from the table and republish them.</span></span>

<span data-ttu-id="1daf2-180">Sobre a segunda abordagem: use a tabela de log de eventos como uma fila e sempre usar um microsserviço de trabalho para publicar as mensagens.</span><span class="sxs-lookup"><span data-stu-id="1daf2-180">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="1daf2-181">Nesse caso, o processo de como é mostrado na Figura 8-23.</span><span class="sxs-lookup"><span data-stu-id="1daf2-181">In that case, the process is like that shown in Figure 8-23.</span></span> <span data-ttu-id="1daf2-182">Isso mostra um microsserviço adicional, e a tabela é a única fonte ao publicar eventos.</span><span class="sxs-lookup"><span data-stu-id="1daf2-182">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![](./media/image24.png)

<span data-ttu-id="1daf2-183">**Figura 8-23**.</span><span class="sxs-lookup"><span data-stu-id="1daf2-183">**Figure 8-23**.</span></span> <span data-ttu-id="1daf2-184">Atomicidade ao publicar eventos do barramento de evento com um microsserviço de trabalho</span><span class="sxs-lookup"><span data-stu-id="1daf2-184">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="1daf2-185">Para simplificar, o exemplo de eShopOnContainers usa a primeira abordagem (sem nenhum processos adicionais ou verificador microservices) e o barramento de evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-185">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="1daf2-186">No entanto, o eShopOnContainers não trata todos os casos de falha possíveis.</span><span class="sxs-lookup"><span data-stu-id="1daf2-186">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="1daf2-187">Em um aplicativo real, implantado na nuvem, você deve adotar o fato de que problemas surgirão eventualmente, e você deve implementar que verifique e reenviar lógica.</span><span class="sxs-lookup"><span data-stu-id="1daf2-187">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="1daf2-188">Usando a tabela como uma fila pode ser mais eficiente do que a primeira abordagem, se você tiver essa tabela como uma única fonte de eventos ao publicá-los por meio do barramento de evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-188">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="1daf2-189">Implementando a atomicidade ao publicar eventos de integração por meio do barramento de evento</span><span class="sxs-lookup"><span data-stu-id="1daf2-189">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="1daf2-190">O código a seguir mostra como você pode criar uma única transação que envolve vários objetos DbContext — um contexto relacionados aos dados originais que está sendo atualizados e o contexto de segundo relacionada à tabela IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="1daf2-190">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="1daf2-191">Observe que a transação no código de exemplo a seguir não será resiliente se conexões ao banco de dados tem qualquer problema ao tempo quando o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-191">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="1daf2-192">Isso pode ocorrer em sistemas baseados em nuvem como o Azure SQL DB, que pode mover bancos de dados entre servidores.</span><span class="sxs-lookup"><span data-stu-id="1daf2-192">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="1daf2-193">Para implementar transações resilientes em vários contextos, consulte o [Implementando conexões Entity Framework Core SQL](#implementing_resilient_EFCore_SQL_conns) seção posteriormente neste guia.</span><span class="sxs-lookup"><span data-stu-id="1daf2-193">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](#implementing_resilient_EFCore_SQL_conns) section later in this guide.</span></span>

<span data-ttu-id="1daf2-194">Para maior clareza, o exemplo a seguir mostra todo o processo em um único segmento de código.</span><span class="sxs-lookup"><span data-stu-id="1daf2-194">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="1daf2-195">No entanto, a implementação de eShopOnContainers, na verdade, é Refatorada e dividir essa lógica em várias classes, sendo mais fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="1daf2-195">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult>
    UpdateProduct([FromBody]CatalogItem productToUpdate)
{
    var catalogItem = await _catalogContext.CatalogItems
        .SingleOrDefaultAsync(i => i.Id == productToUpdate.Id);

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

   // Publish to event bus only if product price changed

   if (raiseProductPriceChangedEvent)
   {
       _eventBus.Publish(priceChangedEvent);
       integrationEventLogService.MarkEventAsPublishedAsync(
           priceChangedEvent);
   }

   return Ok();
}
```

<span data-ttu-id="1daf2-196">Depois que o evento de integração ProductPriceChangedIntegrationEvent é criado, a transação que armazena a operação de domínio original (atualizar o item de catálogo) também inclui a persistência do evento na tabela de log de eventos.</span><span class="sxs-lookup"><span data-stu-id="1daf2-196">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="1daf2-197">Isso faz com que uma única transação, e sempre será capaz de verificar se as mensagens de evento são enviadas.</span><span class="sxs-lookup"><span data-stu-id="1daf2-197">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="1daf2-198">A tabela de log de eventos é atualizada atomicamente com a operação de banco de dados original, usando uma transação local no mesmo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1daf2-198">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="1daf2-199">Se qualquer uma das operações falhar, uma exceção será lançada e a transação reverte qualquer operação concluída, assim, manter a consistência entre as operações de domínio e as mensagens de eventos enviadas.</span><span class="sxs-lookup"><span data-stu-id="1daf2-199">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages sent.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="1daf2-200">Receber mensagens de assinaturas: manipuladores de eventos no destinatário microservices</span><span class="sxs-lookup"><span data-stu-id="1daf2-200">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="1daf2-201">Além da lógica de assinatura de evento, você precisa implementar o código interno para os manipuladores de eventos de integração (como um método de retorno de chamada).</span><span class="sxs-lookup"><span data-stu-id="1daf2-201">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="1daf2-202">O manipulador de eventos é onde você especifica onde as mensagens de eventos de um determinado tipo serão recebidas e processadas.</span><span class="sxs-lookup"><span data-stu-id="1daf2-202">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="1daf2-203">Primeiro, um manipulador de eventos recebe uma instância de eventos do barramento de evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-203">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="1daf2-204">Em seguida, ele localiza o componente a ser processado relacionados a esse evento de integração, propagando e a manter o evento como uma alteração no estado em que o destinatário microsserviço.</span><span class="sxs-lookup"><span data-stu-id="1daf2-204">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="1daf2-205">Por exemplo, se um evento ProductPriceChanged se origina no microsserviço catálogo, ele é tratado no microsserviço carrinho e altera o estado de microsserviço de carrinho esse destinatário bem, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1daf2-205">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="1daf2-206">O manipulador de eventos deve verificar se o produto existe em qualquer uma das instâncias do carrinho.</span><span class="sxs-lookup"><span data-stu-id="1daf2-206">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="1daf2-207">Ele também atualiza o preço de item para cada item de linha do carrinho relacionados.</span><span class="sxs-lookup"><span data-stu-id="1daf2-207">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="1daf2-208">Por fim, ele cria um alerta a ser exibido para o usuário sobre a alteração de preço, conforme mostrado na Figura 8-24.</span><span class="sxs-lookup"><span data-stu-id="1daf2-208">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 8-24.</span></span>

![](./media/image25.png)

<span data-ttu-id="1daf2-209">**Figura 8-24**.</span><span class="sxs-lookup"><span data-stu-id="1daf2-209">**Figure 8-24**.</span></span> <span data-ttu-id="1daf2-210">Exibindo uma alteração de preço de item em um carrinho, como comunicação por eventos de integração</span><span class="sxs-lookup"><span data-stu-id="1daf2-210">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="1daf2-211">Idempotência em eventos de mensagem de atualização</span><span class="sxs-lookup"><span data-stu-id="1daf2-211">Idempotency in update message events</span></span>

<span data-ttu-id="1daf2-212">Um aspecto importante de eventos de mensagem de atualização é uma falha em qualquer ponto de comunicação deve fazer com que a mensagem a ser repetida.</span><span class="sxs-lookup"><span data-stu-id="1daf2-212">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="1daf2-213">Caso contrário, uma tarefa em segundo plano pode tentar publicar um evento que já tenha sido publicado, criando uma condição de corrida.</span><span class="sxs-lookup"><span data-stu-id="1daf2-213">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="1daf2-214">Você precisa para certificar-se de que as atualizações são idempotentes ou que eles fornecem informações suficientes para garantir que você pode detectar uma duplicata, descartá-lo e enviar a resposta de volta apenas um.</span><span class="sxs-lookup"><span data-stu-id="1daf2-214">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="1daf2-215">Conforme observado anteriormente, idempotência significa que uma operação pode ser executada várias vezes sem alterar o resultado.</span><span class="sxs-lookup"><span data-stu-id="1daf2-215">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="1daf2-216">Em um ambiente de mensagens, como ao se comunicar eventos, um evento é idempotente, se ele pode ser fornecido várias vezes sem alterar o resultado para o receptor microsserviço.</span><span class="sxs-lookup"><span data-stu-id="1daf2-216">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="1daf2-217">Isso pode ser necessário devido à natureza do evento em si, ou devido a maneira como o sistema manipula o evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-217">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="1daf2-218">Mensagem idempotência é importante em qualquer aplicativo que usa a mensagem, não apenas em aplicativos que implementam o padrão de barramento de evento.</span><span class="sxs-lookup"><span data-stu-id="1daf2-218">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="1daf2-219">Um exemplo de uma operação idempotente é uma instrução SQL que insere dados em uma tabela somente se os dados não ainda estiver na tabela.</span><span class="sxs-lookup"><span data-stu-id="1daf2-219">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="1daf2-220">Não importa quantas vezes você executar que inserir instrução SQL; o resultado será o mesmo — a tabela conterá esses dados.</span><span class="sxs-lookup"><span data-stu-id="1daf2-220">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="1daf2-221">Idempotência como isso também pode ser necessário ao lidar com mensagens se as mensagens potencialmente enviadas e processados, portanto, mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="1daf2-221">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="1daf2-222">Por exemplo, se a lógica de repetição faz com que um remetente envie exatamente a mesma mensagem mais de uma vez, você precisa certificar-se de que ele é idempotente.</span><span class="sxs-lookup"><span data-stu-id="1daf2-222">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="1daf2-223">É possível design idempotente mensagens.</span><span class="sxs-lookup"><span data-stu-id="1daf2-223">It is possible to design idempotent messages.</span></span> <span data-ttu-id="1daf2-224">Por exemplo, você pode criar um evento que diz "definir o preço do produto \$25" em vez de "adicionar \$5 para o preço do produto."</span><span class="sxs-lookup"><span data-stu-id="1daf2-224">For example, you can create an event that says "set the product price to \$25" instead of "add \$5 to the product price."</span></span> <span data-ttu-id="1daf2-225">Foi possível processar a primeira mensagem com segurança qualquer número de vezes e o resultado será o mesmo.</span><span class="sxs-lookup"><span data-stu-id="1daf2-225">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="1daf2-226">Não é válido para a segunda mensagem.</span><span class="sxs-lookup"><span data-stu-id="1daf2-226">That is not true for the second message.</span></span> <span data-ttu-id="1daf2-227">Mas mesmo no primeiro caso, você pode não processar o primeiro evento, porque o sistema também pode ter enviado um evento de alteração de preço mais recente e você deve substituir o novo preço.</span><span class="sxs-lookup"><span data-stu-id="1daf2-227">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="1daf2-228">Outro exemplo pode ser um evento de pedido concluído foi propagado por vários assinantes.</span><span class="sxs-lookup"><span data-stu-id="1daf2-228">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="1daf2-229">É importante que as informações de ordem sejam atualizados em outros sistemas apenas uma vez, mesmo se houver eventos de mensagem duplicada para o mesmo evento ordem concluída.</span><span class="sxs-lookup"><span data-stu-id="1daf2-229">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="1daf2-230">É conveniente ter algum tipo de identidade por evento para que você possa criar lógica que impõe que cada evento é processado apenas uma vez por destinatário.</span><span class="sxs-lookup"><span data-stu-id="1daf2-230">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="1daf2-231">Algum processamento de mensagem é inerentemente idempotentes.</span><span class="sxs-lookup"><span data-stu-id="1daf2-231">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="1daf2-232">Por exemplo, se um sistema gera miniaturas de imagem, ele não pode importa quantas vezes a mensagem sobre a miniatura gerada é processada; o resultado é que as miniaturas são geradas e elas forem iguais sempre.</span><span class="sxs-lookup"><span data-stu-id="1daf2-232">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="1daf2-233">Por outro lado, as operações como chamar um gateway de pagamento para cobrar o cartão de crédito podem não ser idempotentes em todos os.</span><span class="sxs-lookup"><span data-stu-id="1daf2-233">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="1daf2-234">Nesses casos, você precisa garantir que o processamento de uma mensagem várias vezes tenha o efeito que você espera.</span><span class="sxs-lookup"><span data-stu-id="1daf2-234">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1daf2-235">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1daf2-235">Additional resources</span></span>

-   <span data-ttu-id="1daf2-236">**Para respeitar mensagem idempotência** (subtítulo nesta página) [ *https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span><span class="sxs-lookup"><span data-stu-id="1daf2-236">**Honoring message idempotency** (subhead on this page) [*https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span></span>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="1daf2-237">Eliminação da duplicação de mensagens de eventos de integração</span><span class="sxs-lookup"><span data-stu-id="1daf2-237">Deduplicating integration event messages</span></span>

<span data-ttu-id="1daf2-238">Você pode assegurar que os eventos de mensagem são enviados e processados apenas uma vez por assinante em diferentes níveis.</span><span class="sxs-lookup"><span data-stu-id="1daf2-238">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="1daf2-239">Uma maneira é usar um recurso de eliminação de duplicação oferecido pela infraestrutura de mensagens que você está usando.</span><span class="sxs-lookup"><span data-stu-id="1daf2-239">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="1daf2-240">Outra é implementar a lógica personalizada em seu destino microsserviço.</span><span class="sxs-lookup"><span data-stu-id="1daf2-240">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="1daf2-241">A melhor opção é ter validações no nível de transporte e no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1daf2-241">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="1daf2-242">Eventos de eliminação da duplicação de mensagem no nível de EventHandler</span><span class="sxs-lookup"><span data-stu-id="1daf2-242">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="1daf2-243">Uma maneira para certificar-se de que um evento é processado apenas uma vez por qualquer receptor é implementar a lógica de determinadas durante o processamento de eventos de mensagem em manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="1daf2-243">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="1daf2-244">Por exemplo, que é a abordagem usada no aplicativo eShopOnContainers, como você pode ver no [código-fonte](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) da classe OrdersController quando ele recebe um comando CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="1daf2-244">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) of the OrdersController class when it receives a CreateOrderCommand command.</span></span> <span data-ttu-id="1daf2-245">(Nesse caso, usamos um comando de solicitação HTTP, não um mensagem de comando baseado, mas a lógica que você precisa fazer um comando baseado em mensagem idempotente é semelhante).</span><span class="sxs-lookup"><span data-stu-id="1daf2-245">(In this case we use an HTTP request command, not a message-based command, but the logic you need to make a message-based command idempotent is similar.)</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="1daf2-246">Eliminação da duplicação de mensagens ao usar RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="1daf2-246">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="1daf2-247">Quando ocorrem falhas intermitentes de rede, as mensagens podem ser duplicadas e o destinatário da mensagem deve estar pronto para lidar com essas mensagens duplicadas.</span><span class="sxs-lookup"><span data-stu-id="1daf2-247">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="1daf2-248">Se possível, receptores devem lidar com mensagens de forma idempotentes, é melhor que explicitamente tratá-los com eliminação de duplicação.</span><span class="sxs-lookup"><span data-stu-id="1daf2-248">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="1daf2-249">De acordo com o [RabbitMQ documentação](https://www.rabbitmq.com/reliability.html#consumer), "se uma mensagem é entregue a um cliente e, em seguida, retirada da fila (porque ele não foi confirmado antes de descartar a conexão do consumidor, por exemplo), RabbitMQ definirá o sinalizador redelivered em ele quando ele for entregue novamente (para o consumidor mesmo ou um diferente).</span><span class="sxs-lookup"><span data-stu-id="1daf2-249">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="1daf2-250">Se o sinalizador "redelivered" for definido, o receptor deve consideram que, porque a mensagem pode já ter sido processada.</span><span class="sxs-lookup"><span data-stu-id="1daf2-250">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="1daf2-251">Mas que não é garantida; a mensagem pode nunca ter alcançado o destinatário depois que ele foi o agente de mensagens, talvez devido a problemas de rede.</span><span class="sxs-lookup"><span data-stu-id="1daf2-251">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="1daf2-252">Por outro lado, se o sinalizador "redelivered" não está definido, é garantido que a mensagem não foi enviada mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="1daf2-252">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="1daf2-253">Portanto, o receptor deve eliminar a duplicação de mensagens ou processar mensagens de uma maneira idempotente somente se o sinalizador "redelivered" está definido na mensagem.</span><span class="sxs-lookup"><span data-stu-id="1daf2-253">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1daf2-254">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1daf2-254">Additional resources</span></span>

-   <span data-ttu-id="1daf2-255">**Mensagens de eventos controlada por**
    [*http://soapatterns.org/design\_padrões/evento\_controlados por\_de mensagens*](http://soapatterns.org/design_patterns/event_driven_messaging)</span><span class="sxs-lookup"><span data-stu-id="1daf2-255">**Event Driven Messaging**
[*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span></span>

-   <span data-ttu-id="1daf2-256">**Jimmy Bogard. Refatoração em direção a resiliência: Avaliando acoplamento**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span><span class="sxs-lookup"><span data-stu-id="1daf2-256">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**
[*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span></span>

-   <span data-ttu-id="1daf2-257">**Canal de publicação / assinatura**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span><span class="sxs-lookup"><span data-stu-id="1daf2-257">**Publish-Subscribe channel**
[*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span></span>

-   <span data-ttu-id="1daf2-258">**Comunicação entre limitada contextos**
    [*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span><span class="sxs-lookup"><span data-stu-id="1daf2-258">**Communicating Between Bounded Contexts**
[*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span></span>

-   <span data-ttu-id="1daf2-259">**Consistência eventual**
    [*https://en.wikipedia.org/wiki/Eventual\_consistência*](https://en.wikipedia.org/wiki/Eventual_consistency)</span><span class="sxs-lookup"><span data-stu-id="1daf2-259">**Eventual Consistency**
[*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span></span>

-   <span data-ttu-id="1daf2-260">**Philip marrom. Estratégias para a integração limitada contextos**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span><span class="sxs-lookup"><span data-stu-id="1daf2-260">**Philip Brown. Strategies for Integrating Bounded Contexts**
[*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span></span>

-   <span data-ttu-id="1daf2-261">**Carlos Richardson. Desenvolvendo Microservices transacional usando agregações, fornecimento de evento e CQRS - parte 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span><span class="sxs-lookup"><span data-stu-id="1daf2-261">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span></span>

-   <span data-ttu-id="1daf2-262">**Carlos Richardson. Evento originando padrão**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span><span class="sxs-lookup"><span data-stu-id="1daf2-262">**Chris Richardson. Event Sourcing pattern**
[*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span></span>

-   <span data-ttu-id="1daf2-263">**Introdução ao fornecimento de evento**
    [*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span><span class="sxs-lookup"><span data-stu-id="1daf2-263">**Introducing Event Sourcing**
[*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span></span>

-   <span data-ttu-id="1daf2-264">**Banco de dados do repositório de eventos**.</span><span class="sxs-lookup"><span data-stu-id="1daf2-264">**Event Store database**.</span></span> <span data-ttu-id="1daf2-265">Site oficial.</span><span class="sxs-lookup"><span data-stu-id="1daf2-265">Official site.</span></span>
    [<span data-ttu-id="1daf2-266">*https://geteventstore.com/*</span><span class="sxs-lookup"><span data-stu-id="1daf2-266">*https://geteventstore.com/*</span></span>](https://geteventstore.com/)

-   <span data-ttu-id="1daf2-267">**Patrick Nommensen. Gerenciamento de dados para Microservices controlada por evento**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1>*</span><span class="sxs-lookup"><span data-stu-id="1daf2-267">**Patrick Nommensen. Event-Driven Data Management for Microservices**
*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *</span></span>

-   <span data-ttu-id="1daf2-268">**O Teorema de CAP**
    [*https://en.wikipedia.org/wiki/CAP\_Teorema*](https://en.wikipedia.org/wiki/CAP_theorem)</span><span class="sxs-lookup"><span data-stu-id="1daf2-268">**The CAP Theorem**
[*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span></span>

-   <span data-ttu-id="1daf2-269">**O que é o Teorema de Extremidade? ** 
     [ *https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span><span class="sxs-lookup"><span data-stu-id="1daf2-269">**What is CAP Theorem?**
[*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span></span>

-   <span data-ttu-id="1daf2-270">**Primer de consistência de dados**
    [*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span><span class="sxs-lookup"><span data-stu-id="1daf2-270">**Data Consistency Primer**
[*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span></span>

-   <span data-ttu-id="1daf2-271">**Rick Saling. O Teorema de CAP: Por que "Tudo o que é diferente" com a nuvem e a Internet**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span><span class="sxs-lookup"><span data-stu-id="1daf2-271">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**
[*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span></span>

-   <span data-ttu-id="1daf2-272">**Eric Brewer. LIMITE de 12 anos mais tarde: como "Regras" mudaram**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span><span class="sxs-lookup"><span data-stu-id="1daf2-272">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**
[*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span></span>

-   <span data-ttu-id="1daf2-273">**Participar de transações externas (DTC)** (MSMQ) [ *https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span><span class="sxs-lookup"><span data-stu-id="1daf2-273">**Participating in External (DTC) Transactions** (MSMQ) [*https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span></span>

-   <span data-ttu-id="1daf2-274">**Barramento de serviço do Azure. Mensagens orientadas: Detecção de duplicidades**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span><span class="sxs-lookup"><span data-stu-id="1daf2-274">**Azure Service Bus. Brokered Messaging: Duplicate Detection**
[*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span></span>

-   <span data-ttu-id="1daf2-275">**Guia de confiabilidade** (RabbitMQ documentação) [ *https://www.rabbitmq.com/reliability.html\#consumidor*](https://www.rabbitmq.com/reliability.html%23consumer)</span><span class="sxs-lookup"><span data-stu-id="1daf2-275">**Reliability Guide** (RabbitMQ documentation) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="1daf2-276">[Anterior] (rabbitmq-event-bus-development-test-environment.md) [Avançar] (test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="1daf2-276">[Previous] (rabbitmq-event-bus-development-test-environment.md) [Next] (test-aspnet-core-services-web-apps.md)</span></span>
