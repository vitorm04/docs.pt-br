---
title: Comunicação serviço-serviço
description: Saiba como os microserviços nativos em nuvem back-end se comunicam com outros microsserviços back-end.
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: 926be3c2eb4513c89ebcd1f31dceb7d58639dc6f
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523557"
---
# <a name="service-to-service-communication"></a>Comunicação serviço-serviço

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Saindo do cliente front-end, agora abordamos microserviços back-end se comunicando entre si.

Ao construir um aplicativo nativo da nuvem, você vai querer ser sensível à forma como os serviços back-end se comunicam entre si. Idealmente, quanto menos comunicação entre serviços, melhor. No entanto, a evasão nem sempre é possível, pois os serviços back-end muitas vezes dependem uns dos outros para concluir uma operação.

Existem várias abordagens amplamente aceitas para implementar a comunicação entre serviços. O *tipo de interação de comunicação* muitas vezes determinará a melhor abordagem.

Considere os seguintes tipos de interação:

- *Consulta* – quando um microserviço de chamada requer uma resposta de um chamado microserviço, como: "Ei, me dê as informações do comprador para uma determinada id do cliente".

- *Comando* – quando o microserviço de chamada precisa de outro microserviço para executar uma ação, mas não requer uma resposta, como: "Ei, apenas enviar esta ordem".

- *Evento* – quando um microserviço, chamado de editor, levanta um evento que o estado mudou ou uma ação ocorreu. Outros microsserviços, chamados de assinantes, interessados, podem reagir ao evento adequadamente. O editor e os assinantes não estão cientes um do outro.

Os sistemas de microsserviço normalmente usam uma combinação desses tipos de interação ao executar operações que requerem interação entre serviços. Vamos dar uma olhada de perto em cada um e como você pode implementá-los.

## <a name="queries"></a>Consultas

Muitas vezes, um microserviço pode precisar *consultar* outro, exigindo uma resposta imediata para concluir uma operação. Um microserviço de cesta de compras pode precisar de informações sobre o produto e um preço para adicionar um item à sua cesta. Há uma série de abordagens para implementar operações de consulta.

### <a name="requestresponse-messaging"></a>Solicitação/Mensagens de Resposta

Uma opção para implementar esse cenário é o microserviço back-end chamar para fazer solicitações HTTP diretas para os microsserviços que ele precisa consultar, mostrado na Figura 4-8.

![Comunicação HTTP direta](./media/direct-http-communication.png)

**Figura 4-8**. Comunicação HTTP direta

Embora as chamadas HTTP diretas entre microsserviços sejam relativamente simples de implementar, deve-se tomar cuidado para minimizar essa prática. Para começar, essas chamadas são sempre *síncronas* e bloquearão a operação até que um resultado seja devolvido ou os tempos de solicitação sejam cancelados. O que antes eram serviços independentes e independentes, capazes de evoluir independentemente e implantar com frequência, agora se acoplam um ao outro. À medida que o acoplamento entre microserviços aumenta, seus benefícios arquitetônicos diminuem.

Executar uma solicitação pouco freqüente que faça uma única chamada HTTP direta para outro microserviço pode ser aceitável para alguns sistemas. No entanto, chamadas de alto volume que invocam chamadas HTTP diretas para vários microserviços não são aconselháveis. Eles podem aumentar a latência e impactar negativamente o desempenho, escalabilidade e disponibilidade do seu sistema. Pior ainda, uma longa série de comunicação HTTP direta pode levar a cadeias profundas e complexas de chamadas de microsserviços síncronos, mostradas na Figura 4-9:

![Acorrentando consultas HTTP](./media/chaining-http-queries.png)

**Figura 4-9**. Acorrentando consultas HTTP

Você certamente pode imaginar o risco no design mostrado na imagem anterior. O que \#acontece se o Passo 3 falhar? Ou \#o passo 8 falha? Como você se recupera? E se \#o Passo 6 for lento porque o serviço subjacente está ocupado? Como você continua? Mesmo que tudo funcione corretamente, pense na latência que esta chamada incorreria, que é a soma da latência de cada etapa.

O grande grau de acoplamento na imagem anterior sugere que os serviços não foram modelados de forma ideal. Seria bom para a equipe revisitar seu projeto.

### <a name="materialized-view-pattern"></a>Padrão de Exibição Materializada

Uma opção popular para remover o acoplamento de microsserviços é o [padrão De exibição materializada](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). Com esse padrão, um microserviço armazena sua própria cópia local e desnormalizada de dados que pertencem a outros serviços. Em vez de o microserviço Do Shopping Basket consultando o Catálogo de Produtos e os microsserviços de preços, ele mantém sua própria cópia local desses dados. Este padrão elimina o acoplamento desnecessário e melhora a confiabilidade e o tempo de resposta. Toda a operação é executada dentro de um único processo. Exploramos este padrão e outras preocupações de dados no Capítulo 5.

### <a name="service-aggregator-pattern"></a>Padrão agregador de serviços

Outra opção para eliminar o acoplamento microserviço para microserviço é [um microserviço agregador,](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/)mostrado em roxo na Figura 4-10.

![Serviço agregador](./media/aggregator-service.png)

**Figura 4-10**. Microserviço agregador

O padrão isola uma operação que faz chamadas para vários microserviços back-end, centralizando sua lógica em um microserviço especializado.  O microserviço agregador de checkout roxo na figura anterior orquestra o fluxo de trabalho para a operação checkout. Ele inclui chamadas para vários microserviços back-end em uma ordem seqüenciada. Os dados do fluxo de trabalho são agregados e devolvidos ao chamador. Embora ainda implemente chamadas HTTP diretas, o microserviço agregador reduz as dependências diretas entre microserviços back-end.

### <a name="requestreply-pattern"></a>Padrão de solicitação/resposta

Outra abordagem para desacoplar mensagens HTTP síncronas é um [Padrão de Solicitação-Resposta](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html), que usa comunicação de fila. A comunicação usando uma fila é sempre um canal unidirecional, com um produtor enviando a mensagem e o consumidor recebendo.a. Com esse padrão, tanto uma fila de solicitação quanto uma fila de resposta são implementadas, mostradas na Figura 4-11.

![Padrão de solicitação-resposta](./media/request-reply-pattern.png)

**Figura 4-11**. Padrão de solicitação-resposta

Aqui, o produtor de mensagens cria uma mensagem baseada em consulta que contém um ID de correlação exclusivo e coloca-a em uma fila de solicitação. O serviço de consumo desfaz as mensagens, processa-as e coloca a resposta na fila de resposta com o mesmo ID de correlação. O serviço do produtor desfaz a mensagem, combina com o ID de correlação e continua processando. Nós cobrimos filas em detalhes na próxima seção.

## <a name="commands"></a>Comandos

Outro tipo de interação de comunicação é um *comando.* Um microserviço pode precisar de outro microserviço para realizar uma ação. O microserviço Ordering pode precisar do microserviço Envio para criar um carregamento para um pedido aprovado. Na Figura 4-12, um microserviço, chamado de Produtor, envia uma mensagem para outro microserviço, o Consumidor, ordenando-o a fazer alguma coisa.

![Interação de comando com uma fila](./media/command-interaction-with-queue.png)

**Figura 4-12**. Interação de comando com uma fila

Na maioria das vezes, o produtor não precisa de uma resposta e pode *disparar e esquecer* a mensagem. Se uma resposta for necessária, o Consumidor envia uma mensagem separada de volta ao Produtor em outro canal. Uma mensagem de comando é melhor enviada assíncronamente com uma fila de mensagens. apoiado por um corretor de mensagens leve. No diagrama anterior, observe como uma fila separa e desacopla ambos os serviços.

Uma fila de mensagens é uma construção intermediária através da qual um produtor e consumidor passam uma mensagem. As filas implementam um padrão de mensagens assíncrona e ponto a ponto. O Produtor sabe para onde um comando precisa ser enviado e rotas adequadamente. A fila garante que uma mensagem seja processada exatamente por uma das instâncias de consumo que estão sendo lidos no canal. Nesse cenário, tanto o produtor quanto o serviço ao consumidor podem se dimensionar sem afetar o outro. Além disso, as tecnologias podem ser díspares de cada lado, o que significa que podemos ter um microserviço Java chamando um microserviço [Golang.](https://golang.org)

No capítulo 1, falamos sobre *serviços de apoio.* Os serviços de apoio são recursos auxiliares dos quais dependem os sistemas nativos em nuvem. Filas de mensagens são serviços de backup. A nuvem do Azure suporta dois tipos de filas de mensagens que seus sistemas nativos na nuvem podem consumir para implementar mensagens de comando: filas de armazenamento azure e filas de ônibus de serviço do Azure.

### <a name="azure-storage-queues"></a>Filas de Armazenamento do Azure

As filas de armazenamento do Azure oferecem uma infra-estrutura de fila simples que é rápida, acessível e apoiada por contas de armazenamento do Azure.

[As filas de armazenamento do Azure](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction) possuem um mecanismo de fila baseado em REST com mensagens confiáveis e persistentes. Eles fornecem um conjunto mínimo de recursos, mas são baratos e armazenam milhões de mensagens. Sua capacidade varia até 500 TB. Uma única mensagem pode ter até 64 KB de tamanho.

Você pode acessar mensagens de qualquer lugar do mundo através de chamadas autenticadas usando HTTP ou HTTPS. As filas de armazenamento podem ser dimensionadas para um grande número de clientes simultâneos para lidar com picos de tráfego.

Dito isto, há limitações com o serviço:

- A ordem da mensagem não é garantida.

- Uma mensagem só pode persistir por sete dias antes de ser removida automaticamente.

- O suporte para gerenciamento de estado, detecção de duplicatas ou transações não está disponível.

A figura 4-13 mostra a hierarquia de uma fila de armazenamento do Azure.

![Hierarquia da fila de armazenamento](./media/storage-queue-hierarchy.png)

**Figura 4-13**. Hierarquia da fila de armazenamento

Na figura anterior, observe como as filas de armazenamento armazenam suas mensagens na conta de armazenamento do Azure subjacente.

Para desenvolvedores, a Microsoft fornece várias bibliotecas do lado do cliente e do servidor para processamento de fila de armazenamento. A maioria das principais plataformas são suportadas, incluindo .NET, Java, JavaScript, Ruby, Python e Go. Os desenvolvedores nunca devem se comunicar diretamente com essas bibliotecas. Isso acoplará firmemente seu código de microserviço ao serviço Azure Storage Queue. É uma prática melhor para isolar os detalhes de implementação da API. Introduzir uma camada de intermediação, ou API intermediária, que expõe operações genéricas e encapsula a biblioteca de concreto. Este acoplamento solto permite que você troque um serviço de fila por outro sem ter que fazer alterações no código de serviço principal da linha.

As filas de armazenamento do Azure são uma opção econômica para implementar mensagens de comando em seus aplicativos nativos da nuvem. Especialmente quando um tamanho de fila excederá 80 GB, ou um simples conjunto de recursos é aceitável. Você só paga pelo armazenamento das mensagens; não há taxas fixas por hora.

### <a name="azure-service-bus-queues"></a>Filas do Barramento de Serviço do Azure

Para obter requisitos mais complexos de mensagens, considere as filas do Ônibus de Serviço Do Azure.

Sentado em cima de uma infra-estrutura de mensagens robusta, [o Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) suporta um modelo de *mensagens intermediado.* As mensagens são armazenadas de forma confiável em um corretor (a fila) até serem recebidas pelo consumidor. A fila garante a entrega de mensagens FIFO (First-In/First-Out, respeitando a ordem em que as mensagens foram adicionadas à fila.

O tamanho de uma mensagem pode ser muito maior, até 256 KB. As mensagens são persistidas na fila por um período ilimitado de tempo. Service Bus suporta não apenas chamadas baseadas em HTTP, mas também fornece suporte total para o [protocolo AMPQ](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview). O AMPQ é um padrão aberto entre os fornecedores que suporta um protocolo binário e graus mais altos de confiabilidade.

Service Bus fornece um rico conjunto de recursos, incluindo [suporte a transações](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) e um [recurso de detecção duplicada](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection). A fila garante "no máximo uma vez a entrega" por mensagem. Ele descarta automaticamente uma mensagem que já foi enviada. Se um produtor estiver em dúvida, ele pode reenviar a mesma mensagem, e a Service Bus garante que apenas uma cópia será processada. A detecção duplicada libera você de ter que construir encanamentos adicionais de infra-estrutura.

Mais dois recursos corporativos são particionamento e sessões. Uma fila convencional de Service Bus é tratada por um único corretor de mensagens e armazenada em uma única loja de mensagens. Mas, [o Particionamento de Ônibus de Serviço](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) espalha a fila em vários corretores de mensagens e lojas de mensagens. O throughput geral não é mais limitado pelo desempenho de um único corretor de mensagens ou loja de mensagens. Uma paralisação temporária de uma loja de mensagens não torna indisponível uma fila particionada.

[As sessões de ônibus](https://codingcanvas.com/azure-service-bus-sessions/) de serviço fornecem uma maneira de enviar mensagens relacionadas ao grupo. Imagine um cenário de fluxo de trabalho onde as mensagens devem ser processadas em conjunto e a operação concluída no final. Para aproveitar, as sessões devem ser explicitamente habilitadas para a fila e cada mensagem relacionada deve conter o mesmo ID da sessão.

No entanto, existem algumas ressalvas importantes: o tamanho das filas de ônibus de serviço é limitado a 80 GB, que é muito menor do que o que está disponível nas filas das lojas. Além disso, as filas de Ônibus de Serviço incorrem em um custo base e carga por operação.

A Figura 4-14 descreve a arquitetura de alto nível de uma fila de Ônibus de Serviço.

![Fila do Barramento de Serviço](./media/service-bus-queue.png)

**Figura 4-14**. Fila do Barramento de Serviço

Na figura anterior, observe a relação ponto a ponto. Duas instâncias do mesmo provedor estão enfileirando mensagens em uma única fila de Ônibus de Serviço. Cada mensagem é consumida por apenas uma das três instâncias de consumo à direita. Em seguida, discutimos como implementar mensagens onde diferentes consumidores podem estar interessados na mesma mensagem.

## <a name="events"></a>Eventos

A fila de mensagens é uma maneira eficaz de implementar a comunicação onde um produtor pode enviar uma mensagem a um consumidor de forma assíncrona. No entanto, o que acontece quando *muitos consumidores diferentes* estão interessados na mesma mensagem? Uma fila de mensagens dedicada para cada consumidor não seria bem dimensionada e se tornaria difícil de gerenciar.

Para abordar esse cenário, passamos para o terceiro tipo de interação de mensagem, o *evento.* Um microserviço anuncia que uma ação ocorreu. Outros microsserviços, se interessados, reagem à ação, ou evento.

O evento é um processo de duas etapas. Para uma determinada alteração de estado, um microserviço publica um evento para um corretor de mensagens, disponibilizando-o para qualquer outro microserviço interessado. O microserviço interessado é notificado assinando o evento no corretor de mensagens. Você usa o padrão [Publicar/Assinar](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) para implementar a [comunicação baseada em eventos](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications).

A Figura 4-15 mostra uma cesta de compras de microserviço publicando um evento com outros dois microsserviços assinando-o.

![Mensagens orientadas a eventos](./media/event-driven-messaging.png)

**Figura 4-15**. Mensagens orientadas a eventos

Observe o componente *de barramento* de eventos que fica no meio do canal de comunicação. É uma classe personalizada que encapsula o corretor de mensagens e a desvincula do aplicativo subjacente. Os microserviços de encomenda e inventário operam o evento de forma independente, sem conhecimento uns dos outros, nem o microserviço da cesta de compras. Quando o evento registrado é publicado no ônibus do evento, eles agem sobre ele.

Com o eventing, passamos da tecnologia de fila para *tópicos.* Um [tópico](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) é semelhante a uma fila, mas suporta um padrão de mensagens de um a muitos. Um microserviço publica uma mensagem. Vários microserviços subscritos podem optar por receber e agir sobre essa mensagem. A Figura 4-16 mostra uma arquitetura de tópicos.

![Arquitetura de tópicos](./media/topic-architecture.png)

**Figura 4-16**. Arquitetura de tópicos

Na figura anterior, os editores enviam mensagens para o tema. No final, os assinantes recebem mensagens de assinaturas. No meio, o tópico encaminha mensagens para assinaturas com base em um conjunto de *regras,* mostradas em caixas azuis escuras. As regras agem como um filtro que encaminha mensagens específicas para uma assinatura. Aqui, um evento "CreateOrder" seria \#enviado \#para a Assinatura \#1 e a Assinatura 3, mas não para a Assinatura 2. Um evento "OrderCompleted" seria \#enviado para \#a Assinatura 2 e a Assinatura 3.

A nuvem do Azure suporta dois serviços de tópicos diferentes: Azure Service Bus Topics e Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Tópicos do Barramento de Serviço do Azure

Sentados em cima do mesmo modelo de mensagem intermediada robusta das filas de ônibus de serviço do Azure são [Tópicos de Ônibus de Serviço Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Um tópico pode receber mensagens de vários editores independentes e enviar mensagens para até 2.000 assinantes. As assinaturas podem ser adicionadas ou removidas dinamicamente em tempo de execução sem parar o sistema ou recriar o tópico.

Muitos recursos avançados das filas de barramento de serviço do Azure também estão disponíveis para tópicos, incluindo [detecção de duplicatas](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) e [suporte a transações.](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) Por padrão, os tópicos do Service Bus são tratados por um único corretor de mensagens e armazenados em um único armazenamento de mensagens. Mas, [o Service Bus Partitioning dimensiona](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) um tópico espalhando-o em muitos corretores de mensagens e lojas de mensagens.

[A entrega de mensagens agendadas](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing) marca uma mensagem com um tempo específico para processamento. A mensagem não aparecerá no tópico antes desse tempo. [O adiamento da mensagem](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral) permite que você adie uma recuperação de uma mensagem para um tempo posterior. Ambos são comumente usados em cenários de processamento de fluxo de trabalho onde as operações são processadas em uma determinada ordem. Você pode adiar o processamento das mensagens recebidas até que o trabalho anterior tenha sido concluído.

Os tópicos de Service Bus são uma tecnologia robusta e comprovada para permitir a publicação/assinatura de comunicação em seus sistemas nativos na nuvem.

### <a name="azure-event-grid"></a>Grade de Eventos do Azure

Enquanto o Azure Service Bus é um corretor de mensagens testado em batalha com um conjunto completo de recursos corporativos, [o Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) é o novo garoto do bloco.

À primeira vista, o Event Grid pode parecer apenas mais um sistema de mensagens baseado em tópicos. No entanto, é diferente em muitos aspectos. Focado em cargas de trabalho orientadas a eventos, ele permite o processamento de eventos em tempo real, a integração profunda do Azure e uma plataforma aberta - tudo em infra-estrutura sem servidor. Ele foi projetado para aplicativos contemporâneos nativos da nuvem e sem servidor

Como um *backplane*centralizado de eventos , ou pipe, event grid reage a eventos dentro dos recursos do Azure e de seus próprios serviços.

As notificações do evento são publicadas em um Event Grid Topic, que, por sua vez, encaminha cada evento para uma assinatura. Os assinantes mapeiam as assinaturas e consomem os eventos. Como o Service Bus, event grid suporta um *modelo de assinante filtrado* onde uma assinatura define regra para os eventos que deseja receber. Event Grid fornece throughput rápido com uma garantia de 10 milhões de eventos por segundo, permitindo entrega quase em tempo real - muito mais do que o Azure Service Bus pode gerar.

Um ponto doce para a Event Grid é sua profunda integração no tecido da infra-estrutura do Azure. Um recurso do Azure, como o Cosmos DB, pode publicar eventos incorporados diretamente para outros recursos interessados do Azure - sem a necessidade de código personalizado. O Event Grid pode publicar eventos a partir de uma assinatura, grupo de recursos ou serviço do Azure, dando aos desenvolvedores controle fino sobre o ciclo de vida dos recursos na nuvem. No entanto, event grid não se limita ao Azure. É uma plataforma aberta que pode consumir eventos HTTP personalizados publicados a partir de aplicativos ou serviços de terceiros e eventos de rota para assinantes externos.

Ao publicar e assinar eventos nativos dos recursos do Azure, nenhuma codificação é necessária. Com uma configuração simples, você pode integrar eventos de um recurso do Azure a outro utilizando encanamento incorporado para Tópicos e Assinaturas. A figura 4-17 mostra a anatomia da Grade de Eventos.

![Anatomia da Grade de Eventos](./media/event-grid-anatomy.png)

**Figura 4-17**. Anatomia da Grade de Eventos

Uma grande diferença entre EventGrid e Service Bus é o padrão de *troca de mensagens*subjacente .

Service Bus implementa um *modelo de atração de* estilo mais antigo no qual o assinante a jusante pesquisa ativamente a assinatura do tópico para novas mensagens. Por outro lado, essa abordagem dá ao assinante controle total do ritmo em que processa as mensagens. Ele controla quando e quantas mensagens processar em qualquer momento. Mensagens não lidas permanecem na assinatura até ser processada. Uma deficiência significativa é a latência entre o momento em que o evento é gerado e a operação de votação que puxa essa mensagem para o assinante para processamento. Além disso, a sobrecarga de votação constante para o próximo evento consome recursos e dinheiro.

EventGrid, no entanto, é diferente. Ele implementa um *modelo de push* no qual os eventos são enviados para os EventHandlers como recebidos, dando uma entrega de eventos quase em tempo real. Também reduz o custo, pois o serviço é acionado apenas quando é necessário consumir um evento – não continuamente como na votação. Dito isto, um manipulador de eventos deve lidar com a carga recebida e fornecer mecanismos de estrangulamento para se proteger de ficar sobrecarregado. Muitos serviços do Azure que consomem esses eventos, como funções do Azure e aplicativos lógicos, fornecem recursos automáticos de autodimensionamento para lidar com cargas aumentadas.  

Event Grid é um serviço de nuvem totalmente gerenciado sem servidor. Ele escala dinamicamente com base no seu tráfego e cobra apenas pelo seu uso real, não pela capacidade pré-comprada. As primeiras 100.000 operações por mês são gratuitas – operações sendo definidas como entrada de eventos (notificações de eventos de entrada), tentativas de entrega de assinatura, chamadas de gerenciamento e filtragem por assunto. Com 99,99% de disponibilidade, a EventGrid garante a entrega de um evento dentro de um período de 24 horas, com funcionalidade de repetição incorporada para entrega mal sucedida. Mensagens não entregues podem ser movidas para uma fila de "letra morta" para resolução.  Ao contrário do Ônibus de Serviço do Azure, o Event Grid é ajustado para um desempenho rápido e não oferece suporte a recursos como mensagens encomendadas, transações e sessões.

### <a name="streaming-messages-in-the-azure-cloud"></a>Mensagens de streaming na nuvem do Azure

A Zure Service Bus e Event Grid fornecem um grande suporte para aplicativos que expõem eventos únicos e discretos, como um novo documento foi inserido em um Cosmos DB. Mas, e se o seu sistema nativo de nuvem precisar processar um *fluxo de eventos relacionados?* [Fluxos de eventos](https://docs.microsoft.com/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems) são mais complexos. Eles são tipicamente ordenados pelo tempo, interrelacionados, e devem ser processados em grupo.

[O Azure Event Hub](https://azure.microsoft.com/services/event-hubs/) é uma plataforma de streaming de dados e serviço de ingestão de eventos que coleta, transforma e armazena eventos. É ajustado para capturar dados de streaming, como notificações contínuas de eventos emitidas a partir de um contexto de telemetria. O serviço é altamente escalável e pode armazenar e [processar milhões de eventos por segundo.](https://docs.microsoft.com/azure/event-hubs/event-hubs-about) Mostrado na Figura 4-18, muitas vezes é uma porta da frente para um pipeline de eventos, desacoplando fluxo de ingestão do consumo de eventos.

![Hub de Eventos do Azure](./media/azure-event-hub.png)

**Figura 4-18**. Hub de Eventos do Azure

O Event Hub suporta baixa latência e retenção de tempo configurável. Ao contrário das filas e tópicos, os Event Hubs mantêm os dados do evento depois de lidos por um consumidor. Esse recurso permite que outros serviços de análise de dados, tanto internos quanto externos, reproduzam os dados para análise suplementar. Os eventos armazenados no hub de eventos só são excluídos após o término do período de retenção, que é de um dia por padrão, mas configurável.

O Event Hub suporta protocolos comuns de publicação de eventos, incluindo HTTPS e AMQP. Também suporta Kafka 1.0. [Os aplicativos Kafka existentes podem se comunicar com](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) o Event Hub usando o protocolo Kafka, fornecendo uma alternativa para gerenciar grandes clusters Kafka. Muitos sistemas nativos em nuvem de código aberto abraçam Kafka.

O Event Hubs implementa o streaming de mensagens através de um [modelo de consumo particionado](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) no qual cada consumidor lê apenas um subconjunto específico, ou partição, do fluxo de mensagens. Esse padrão permite a enorme escala horizontal para processamento de eventos e fornece outros recursos centrados no fluxo que não estão disponíveis em filas e tópicos. Uma partição é uma sequência ordenada de eventos que é mantida em um hub de eventos. À medida que novos eventos chegam, eles são adicionados ao fim desta seqüência.A figura 4-19 mostra particionamento em um Event Hub.

![Particionamento do Event Hub](./media/event-hub-partitioning.png)

**Figura 4-19**. Particionamento do Event Hub

Em vez de ler a partir do mesmo recurso, cada grupo de consumidores lê através de um subconjunto, ou partição, do fluxo de mensagens.

Para aplicativos nativos na nuvem que devem transmitir um grande número de eventos, o Azure Event Hub pode ser uma solução robusta e acessível.

>[!div class="step-by-step"]
>[Próximo](front-end-communication.md)
>[anterior](grpc.md)
