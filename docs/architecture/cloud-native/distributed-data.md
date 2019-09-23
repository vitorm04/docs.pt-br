---
title: Dados distribuídos
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Dados distribuídos para aplicativos nativos de nuvem
ms.date: 06/30/2019
ms.openlocfilehash: 92086c52b02360e90461aea9ad23a2068224e187
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183129"
---
# <a name="distributed-data-for-cloud-native-apps"></a><span data-ttu-id="f4167-103">Dados distribuídos para aplicativos nativos de nuvem</span><span class="sxs-lookup"><span data-stu-id="f4167-103">Distributed data for cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="f4167-104">Ao construir um sistema nativo de nuvem que consiste em muitos microservices independentes, a maneira de pensar sobre as alterações de armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="f4167-104">When constructing a cloud-native system that consists of many independent microservices, the way you think about data storage changes.</span></span>

<span data-ttu-id="f4167-105">Os aplicativos monolíticos tradicionais favorecem um armazenamento de dados centralizado mostrado na Figura 5-1.</span><span class="sxs-lookup"><span data-stu-id="f4167-105">Traditional monolithic applications favor a centralized data store shown in Figure 5-1.</span></span> 

![Banco de dados monolítico único](./media/single-monolithic-database.png)

<span data-ttu-id="f4167-107">**Figura 5-1**.</span><span class="sxs-lookup"><span data-stu-id="f4167-107">**Figure 5-1**.</span></span> <span data-ttu-id="f4167-108">Banco de dados monolítico único</span><span class="sxs-lookup"><span data-stu-id="f4167-108">Single monolithic database</span></span>

<span data-ttu-id="f4167-109">Observe na figura anterior como todos os componentes do aplicativo consomem um único banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="f4167-109">Note in the previous figure how all of the application components consume a single relational database.</span></span>

<span data-ttu-id="f4167-110">Há muitos benefícios para essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="f4167-110">There are many benefits to this approach.</span></span> <span data-ttu-id="f4167-111">É simples consultar dados espalhados por várias tabelas, e é simples implementar [Transações ACID](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) que garantam a consistência dos dados.</span><span class="sxs-lookup"><span data-stu-id="f4167-111">It's straightforward to query data spread across  multiple tables, and it's straightforward to implement [ACID transactions](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) that ensure data consistency.</span></span> <span data-ttu-id="f4167-112">Você sempre acaba com a *consistência imediata*: todas as atualizações de dados ou nenhuma delas.</span><span class="sxs-lookup"><span data-stu-id="f4167-112">You always end up with *immediate consistency*: either all your data updates or none of it does.</span></span>

<span data-ttu-id="f4167-113">Os sistemas nativos de nuvem favorecem uma arquitetura de dados mostrada na Figura 5-2, na qual cada microserviço possui e encapsula seus próprios dados.</span><span class="sxs-lookup"><span data-stu-id="f4167-113">Cloud-native systems favor a data architecture shown in Figure 5-2 in which each microservice owns and encapsulates its own data.</span></span>

![Vários bancos de dados em microserviços](./media/data-across-microservices.png)

<span data-ttu-id="f4167-115">**Figura 5-2**.</span><span class="sxs-lookup"><span data-stu-id="f4167-115">**Figure 5-2**.</span></span> <span data-ttu-id="f4167-116">Vários bancos de dados em microserviços</span><span class="sxs-lookup"><span data-stu-id="f4167-116">Multiple databases across microservices</span></span>

<span data-ttu-id="f4167-117">Observe como, na figura anterior, cada microserviço possui e encapsula o armazenamento de dados de ti e expõe apenas dados para o mundo exterior de sua API pública.</span><span class="sxs-lookup"><span data-stu-id="f4167-117">Note how in the previous figure each microservice owns and encapsulates it data store and only exposes data to the outside world from its public API.</span></span>
 
<span data-ttu-id="f4167-118">Esse modelo permite que cada microserviço evolua independentemente sem a necessidade de coordenar as alterações de esquema de dados com outros microserviços.</span><span class="sxs-lookup"><span data-stu-id="f4167-118">This model enables each microservice to evolve independently without having to coordinate data schema changes with other microservices.</span></span> <span data-ttu-id="f4167-119">Cada microserviço é gratuito para implementar o tipo de armazenamento de dados (banco de dados relacional, banco de dados de documentos, repositório de chave-valor) que melhor atenda às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="f4167-119">Each microservice is free to implement the data store (relational database, document database, key-value store) type that best matches its needs.</span></span> <span data-ttu-id="f4167-120">Em tempo de execução, cada microserviço pode dimensionar seus dados de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="f4167-120">At runtime, each microservice can scale its data accordingly.</span></span> <span data-ttu-id="f4167-121">Isso é mostrado na Figura 5-3:</span><span class="sxs-lookup"><span data-stu-id="f4167-121">This is shown in Figure 5-3:</span></span>

![Persistência de dados poliglota](./media/polyglot-data-persistence.png)

<span data-ttu-id="f4167-123">**Figura 5-3**.</span><span class="sxs-lookup"><span data-stu-id="f4167-123">**Figure 5-3**.</span></span> <span data-ttu-id="f4167-124">Persistência de dados poliglota</span><span class="sxs-lookup"><span data-stu-id="f4167-124">Polyglot data persistence</span></span>

<span data-ttu-id="f4167-125">Observe como, na figura anterior, o catálogo de produtos e os microserviços de inventário adotam bancos de dados relacionais, o microserviço de pedidos, um banco de dados de documentos NoSql e o microserviço do carrinho de compras, que é um repositório de chave-valor externo.</span><span class="sxs-lookup"><span data-stu-id="f4167-125">Note how in the previous figure the product catalog and inventory microservices adopt relational databases, the ordering microservice, a NoSql document database, and the shopping cart microservice, which is an external key-value store.</span></span> <span data-ttu-id="f4167-126">Embora os bancos de dados relacionais permaneçam relevantes para os microserviços com os complexos, eles ganharam uma popularidade considerável, fornecendo a adaptabilidade, pesquisa rápida e alta disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="f4167-126">While relational databases remain relevant for microservices with complex data, NoSQL databases have gained considerable popularity, providing adaptability, fast lookup, and high availability.</span></span> <span data-ttu-id="f4167-127">Sua natureza sem esquema permite que os desenvolvedores se afastem de uma arquitetura de classes de dados tipadas e ORMs que tornam a alteração cara e demorada.</span><span class="sxs-lookup"><span data-stu-id="f4167-127">Their schemaless nature allows developers to move away from an architecture of typed data classes and ORMs that make change expensive and time-consuming.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f4167-128">[Anterior](service-mesh-communication-infrastructure.md)
>[Próximo](data-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="f4167-128">[Previous](service-mesh-communication-infrastructure.md)
[Next](data-patterns.md)</span></span>
