---
title: Introdução ao armazenamento de Tabelas do Azure usando F#
description: Armazene dados estruturados na nuvem usando o armazenamento de tabelas do Azure ou Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 6833e2264f7543f50b94892b6980140e4bf1cdd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424601"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="0be5c-103">Introdução ao armazenamento de tabelas do Azure e ao Azure Cosmos DB API de Tabela usando F\#</span><span class="sxs-lookup"><span data-stu-id="0be5c-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="0be5c-104">O armazenamento de tabelas do Azure é um serviço que armazena dados NoSQL estruturados na nuvem.</span><span class="sxs-lookup"><span data-stu-id="0be5c-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="0be5c-105">O armazenamento de tabela é um repositório de chave/atributo com um design sem esquema.</span><span class="sxs-lookup"><span data-stu-id="0be5c-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="0be5c-106">Como o armazenamento de tabelas não tem Esquema, é fácil adaptar seus dados à medida que as necessidades de seu aplicativo evoluem.</span><span class="sxs-lookup"><span data-stu-id="0be5c-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="0be5c-107">O acesso aos dados é rápido e econômico para todos os tipos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="0be5c-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="0be5c-108">O armazenamento de tabela normalmente é significativamente menor em relação ao custo do que o SQL tradicional para volumes de dados semelhantes.</span><span class="sxs-lookup"><span data-stu-id="0be5c-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="0be5c-109">Você pode usar o armazenamento de tabelas para armazenar conjuntos de dados flexíveis, como os de usuário para aplicativos Web, catálogos de endereços, informações de dispositivo e qualquer outro tipo de metadados que seu serviço requer.</span><span class="sxs-lookup"><span data-stu-id="0be5c-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="0be5c-110">Você pode armazenar qualquer número de entidades em uma tabela e uma conta de armazenamento pode conter qualquer número de tabelas, até o limite de capacidade da conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0be5c-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="0be5c-111">Azure Cosmos DB fornece a API de Tabela para aplicativos que são escritos para o armazenamento de tabelas do Azure e que exigem recursos premium, como:</span><span class="sxs-lookup"><span data-stu-id="0be5c-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="0be5c-112">Distribuição global pronta para uso.</span><span class="sxs-lookup"><span data-stu-id="0be5c-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="0be5c-113">Taxa de transferência dedicada em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="0be5c-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="0be5c-114">Latências de milissegundos de dígito único no 99 º percentil.</span><span class="sxs-lookup"><span data-stu-id="0be5c-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="0be5c-115">Alta disponibilidade garantida.</span><span class="sxs-lookup"><span data-stu-id="0be5c-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="0be5c-116">Indexação secundária automática.</span><span class="sxs-lookup"><span data-stu-id="0be5c-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="0be5c-117">Os aplicativos escritos para o armazenamento de tabelas do Azure podem migrar para Azure Cosmos DB usando o API de Tabela sem alterações de código e aproveitar os recursos premium.</span><span class="sxs-lookup"><span data-stu-id="0be5c-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="0be5c-118">O API de Tabela tem SDKs de cliente disponíveis para .NET, Java, Python e node. js.</span><span class="sxs-lookup"><span data-stu-id="0be5c-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="0be5c-119">Para obter mais informações, consulte [introdução ao Azure Cosmos DB API de tabela](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="0be5c-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="0be5c-120">Sobre este tutorial</span><span class="sxs-lookup"><span data-stu-id="0be5c-120">About this tutorial</span></span>

<span data-ttu-id="0be5c-121">Este tutorial mostra como escrever F# código para fazer algumas tarefas comuns usando o armazenamento de tabelas do Azure ou o Azure Cosmos DB API de tabela, incluindo a criação e a exclusão de uma tabela e inserção, atualização, exclusão e consulta de dados de tabela.</span><span class="sxs-lookup"><span data-stu-id="0be5c-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0be5c-122">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="0be5c-122">Prerequisites</span></span>

<span data-ttu-id="0be5c-123">Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account) ou [Azure Cosmos DB conta](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="0be5c-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="0be5c-124">Criar um F# script e iniciar F# interativo</span><span class="sxs-lookup"><span data-stu-id="0be5c-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="0be5c-125">Os exemplos neste artigo podem ser usados em um F# aplicativo ou um F# script.</span><span class="sxs-lookup"><span data-stu-id="0be5c-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="0be5c-126">Para criar um F# script, crie um arquivo com a extensão `.fsx`, por exemplo, `tables.fsx`, em F# seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0be5c-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="0be5c-127">Em seguida, use um [Gerenciador de pacotes](package-management.md) , como [paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) , para instalar o pacote `WindowsAzure.Storage` e referência `WindowsAzure.Storage.dll` em seu script usando uma diretiva `#r`.</span><span class="sxs-lookup"><span data-stu-id="0be5c-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="0be5c-128">Faça isso novamente para `Microsoft.WindowsAzure.ConfigurationManager` a fim de obter o namespace Microsoft. Azure.</span><span class="sxs-lookup"><span data-stu-id="0be5c-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="0be5c-129">Adicionar declarações de namespace</span><span class="sxs-lookup"><span data-stu-id="0be5c-129">Add namespace declarations</span></span>

<span data-ttu-id="0be5c-130">Adicione as seguintes instruções `open` à parte superior do arquivo `tables.fsx`:</span><span class="sxs-lookup"><span data-stu-id="0be5c-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="0be5c-131">Obter sua cadeia de conexão de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="0be5c-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="0be5c-132">Se você estiver se conectando ao serviço tabela de armazenamento do Azure, precisará de sua cadeia de conexão para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="0be5c-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="0be5c-133">Você pode copiar a cadeia de conexão do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="0be5c-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="0be5c-134">Para obter mais informações sobre cadeias de conexão, consulte [Configurar cadeias de conexão de armazenamento](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="0be5c-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="0be5c-135">Obter sua cadeia de conexão do Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="0be5c-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="0be5c-136">Se estiver se conectando ao Azure Cosmos DB, você precisará da sua cadeia de conexão para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="0be5c-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="0be5c-137">Você pode copiar a cadeia de conexão do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="0be5c-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="0be5c-138">Na portal do Azure, na sua conta do Cosmos DB, vá para **configurações** > **cadeia de conexão**e clique no botão **copiar** para copiar a cadeia de conexão primária.</span><span class="sxs-lookup"><span data-stu-id="0be5c-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span>

<span data-ttu-id="0be5c-139">Para o tutorial, insira sua cadeia de conexão em seu script, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0be5c-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="0be5c-140">No entanto, isso **não é recomendado** para projetos reais.</span><span class="sxs-lookup"><span data-stu-id="0be5c-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="0be5c-141">Sua chave de conta de armazenamento é semelhante à senha raiz da sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0be5c-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="0be5c-142">Sempre tenha cuidado para proteger sua chave de conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0be5c-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="0be5c-143">Evite distribuí-lo a outros usuários, embuti-lo em código ou salvá-lo em um arquivo de texto sem formatação que seja acessível para outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="0be5c-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="0be5c-144">Você pode regenerar sua chave usando o portal do Azure se acreditar que ele pode ter sido comprometido.</span><span class="sxs-lookup"><span data-stu-id="0be5c-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="0be5c-145">Para aplicativos reais, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0be5c-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="0be5c-146">Para buscar a cadeia de conexão de um arquivo de configuração, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="0be5c-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="0be5c-147">Usar o Configuration Manager do Azure é opcional.</span><span class="sxs-lookup"><span data-stu-id="0be5c-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="0be5c-148">Você também pode usar uma API como o tipo de `ConfigurationManager` do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0be5c-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="0be5c-149">Analisar a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="0be5c-149">Parse the connection string</span></span>

<span data-ttu-id="0be5c-150">Para analisar a cadeia de conexão, use:</span><span class="sxs-lookup"><span data-stu-id="0be5c-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="0be5c-151">Isso retorna um `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="0be5c-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="0be5c-152">Criar o cliente do serviço tabela</span><span class="sxs-lookup"><span data-stu-id="0be5c-152">Create the Table service client</span></span>

<span data-ttu-id="0be5c-153">A classe `CloudTableClient` permite que você recupere tabelas e entidades no armazenamento de tabelas.</span><span class="sxs-lookup"><span data-stu-id="0be5c-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="0be5c-154">Aqui está uma maneira de criar o cliente de serviço:</span><span class="sxs-lookup"><span data-stu-id="0be5c-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="0be5c-155">Agora você está pronto para escrever código que lê dados e grava dados no armazenamento de tabelas.</span><span class="sxs-lookup"><span data-stu-id="0be5c-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="0be5c-156">Criar uma tabela</span><span class="sxs-lookup"><span data-stu-id="0be5c-156">Create a table</span></span>

<span data-ttu-id="0be5c-157">Este exemplo mostra como criar uma tabela se ela ainda não existir:</span><span class="sxs-lookup"><span data-stu-id="0be5c-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="0be5c-158">Adicionar uma entidade a uma tabela</span><span class="sxs-lookup"><span data-stu-id="0be5c-158">Add an entity to a table</span></span>

<span data-ttu-id="0be5c-159">Uma entidade deve ter um tipo que herde de `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="0be5c-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="0be5c-160">Você pode estender `TableEntity` da maneira que desejar, mas seu tipo *deve* ter um construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0be5c-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="0be5c-161">Somente as propriedades que têm `get` e `set` são armazenadas em sua tabela do Azure.</span><span class="sxs-lookup"><span data-stu-id="0be5c-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="0be5c-162">A chave de partição e de linha de uma entidade identifica exclusivamente a entidade na tabela.</span><span class="sxs-lookup"><span data-stu-id="0be5c-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="0be5c-163">As entidades com a mesma chave de partição podem ser consultadas mais rápido do que aquelas com chaves de partição diferentes, mas o uso de chaves de partição diversas permite maior escalabilidade de operações paralelas.</span><span class="sxs-lookup"><span data-stu-id="0be5c-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="0be5c-164">Aqui está um exemplo de um `Customer` que usa o `lastName` como a chave de partição e o `firstName` como a chave de linha.</span><span class="sxs-lookup"><span data-stu-id="0be5c-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="0be5c-165">Agora, adicione `Customer` à tabela.</span><span class="sxs-lookup"><span data-stu-id="0be5c-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="0be5c-166">Para fazer isso, crie um `TableOperation` que é executado na tabela.</span><span class="sxs-lookup"><span data-stu-id="0be5c-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="0be5c-167">Nesse caso, você cria uma operação `Insert`.</span><span class="sxs-lookup"><span data-stu-id="0be5c-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="0be5c-168">Inserir um lote de entidades</span><span class="sxs-lookup"><span data-stu-id="0be5c-168">Insert a batch of entities</span></span>

<span data-ttu-id="0be5c-169">Você pode inserir um lote de entidades em uma tabela usando uma única operação de gravação.</span><span class="sxs-lookup"><span data-stu-id="0be5c-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="0be5c-170">As operações em lote permitem combinar operações em uma única execução, mas têm algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="0be5c-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="0be5c-171">Você pode executar atualizações, exclusões e inserções na mesma operação em lote.</span><span class="sxs-lookup"><span data-stu-id="0be5c-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="0be5c-172">Uma operação em lote pode incluir até 100 entidades.</span><span class="sxs-lookup"><span data-stu-id="0be5c-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="0be5c-173">Todas as entidades em uma operação em lote devem ter a mesma chave de partição.</span><span class="sxs-lookup"><span data-stu-id="0be5c-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="0be5c-174">Embora seja possível executar uma consulta em uma operação em lote, ela deve ser a única operação no lote.</span><span class="sxs-lookup"><span data-stu-id="0be5c-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="0be5c-175">Aqui está um código que combina duas inserções em uma operação em lote:</span><span class="sxs-lookup"><span data-stu-id="0be5c-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="0be5c-176">Recuperar todas as entidades em uma partição</span><span class="sxs-lookup"><span data-stu-id="0be5c-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="0be5c-177">Para consultar uma tabela para todas as entidades em uma partição, use um objeto `TableQuery`.</span><span class="sxs-lookup"><span data-stu-id="0be5c-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="0be5c-178">Aqui, você filtra as entidades em que "Smith" é a chave de partição.</span><span class="sxs-lookup"><span data-stu-id="0be5c-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="0be5c-179">Agora você imprime os resultados:</span><span class="sxs-lookup"><span data-stu-id="0be5c-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="0be5c-180">Recuperar um intervalo de entidades em uma partição</span><span class="sxs-lookup"><span data-stu-id="0be5c-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="0be5c-181">Se você não quiser consultar todas as entidades em uma partição, poderá especificar um intervalo combinando o filtro de chave de partição com um filtro de chave de linha.</span><span class="sxs-lookup"><span data-stu-id="0be5c-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="0be5c-182">Aqui, você usa dois filtros para obter todas as entidades na partição "Smith", em que a chave de linha (primeiro nome) começa com uma letra anterior à "M" no alfabeto.</span><span class="sxs-lookup"><span data-stu-id="0be5c-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="0be5c-183">Agora você imprime os resultados:</span><span class="sxs-lookup"><span data-stu-id="0be5c-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="0be5c-184">Recuperar uma única entidade</span><span class="sxs-lookup"><span data-stu-id="0be5c-184">Retrieve a single entity</span></span>

<span data-ttu-id="0be5c-185">Você pode escrever uma consulta para recuperar uma única entidade específica.</span><span class="sxs-lookup"><span data-stu-id="0be5c-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="0be5c-186">Aqui, você usa um `TableOperation` para especificar o cliente "Ben Smith".</span><span class="sxs-lookup"><span data-stu-id="0be5c-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="0be5c-187">Em vez de uma coleção, você obtém um `Customer`.</span><span class="sxs-lookup"><span data-stu-id="0be5c-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="0be5c-188">A especificação da chave de partição e da chave de linha em uma consulta é a maneira mais rápida de recuperar uma única entidade do serviço tabela.</span><span class="sxs-lookup"><span data-stu-id="0be5c-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="0be5c-189">Agora você imprime os resultados:</span><span class="sxs-lookup"><span data-stu-id="0be5c-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="0be5c-190">Substituir uma entidade</span><span class="sxs-lookup"><span data-stu-id="0be5c-190">Replace an entity</span></span>

<span data-ttu-id="0be5c-191">Para atualizar uma entidade, recupere-a do serviço tabela, modifique o objeto de entidade e salve as alterações de volta no serviço tabela usando uma operação `Replace`.</span><span class="sxs-lookup"><span data-stu-id="0be5c-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="0be5c-192">Isso faz com que a entidade seja totalmente substituída no servidor, a menos que a entidade no servidor tenha sido alterada desde que foi recuperada; nesse caso, a operação falhará.</span><span class="sxs-lookup"><span data-stu-id="0be5c-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="0be5c-193">Essa falha é impedir que seu aplicativo substitua inadvertidamente as alterações de outras fontes.</span><span class="sxs-lookup"><span data-stu-id="0be5c-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="0be5c-194">Inserir ou substituir uma entidade</span><span class="sxs-lookup"><span data-stu-id="0be5c-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="0be5c-195">Às vezes, você não sabe se existe uma entidade na tabela.</span><span class="sxs-lookup"><span data-stu-id="0be5c-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="0be5c-196">E, se tiver, os valores atuais armazenados nela não serão mais necessários.</span><span class="sxs-lookup"><span data-stu-id="0be5c-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="0be5c-197">Você pode usar `InsertOrReplace` para criar a entidade ou substituí-la, se ela existir, independentemente de seu estado.</span><span class="sxs-lookup"><span data-stu-id="0be5c-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="0be5c-198">Consultar um subconjunto de propriedades de entidade</span><span class="sxs-lookup"><span data-stu-id="0be5c-198">Query a subset of entity properties</span></span>

<span data-ttu-id="0be5c-199">Uma consulta de tabela pode recuperar apenas algumas propriedades de uma entidade em vez de todas elas.</span><span class="sxs-lookup"><span data-stu-id="0be5c-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="0be5c-200">Essa técnica, chamada projeção, pode melhorar o desempenho da consulta, especialmente para grandes entidades.</span><span class="sxs-lookup"><span data-stu-id="0be5c-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="0be5c-201">Aqui, você retorna apenas endereços de email usando `DynamicTableEntity` e `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="0be5c-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="0be5c-202">Observe que a projeção não tem suporte no emulador de armazenamento local, portanto, esse código é executado somente quando você está usando uma conta no serviço tabela.</span><span class="sxs-lookup"><span data-stu-id="0be5c-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="0be5c-203">Recuperar entidades em páginas de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="0be5c-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="0be5c-204">Se você estiver lendo um grande número de entidades e quiser processá-las à medida que elas forem recuperadas em vez de esperar que todas elas retornem, você poderá usar uma consulta segmentada.</span><span class="sxs-lookup"><span data-stu-id="0be5c-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="0be5c-205">Aqui, você retorna resultados em páginas usando um fluxo de trabalho assíncrono para que a execução não seja bloqueada enquanto você estiver aguardando um grande conjunto de resultados ser retornado.</span><span class="sxs-lookup"><span data-stu-id="0be5c-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="0be5c-206">Agora você executa essa computação de forma síncrona:</span><span class="sxs-lookup"><span data-stu-id="0be5c-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="0be5c-207">Excluir uma entidade</span><span class="sxs-lookup"><span data-stu-id="0be5c-207">Delete an entity</span></span>

<span data-ttu-id="0be5c-208">Você pode excluir uma entidade depois de recuperá-la.</span><span class="sxs-lookup"><span data-stu-id="0be5c-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="0be5c-209">Assim como a atualização de uma entidade, isso falhará se a entidade tiver sido alterada desde que você a recuperou.</span><span class="sxs-lookup"><span data-stu-id="0be5c-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="0be5c-210">Excluir uma tabela</span><span class="sxs-lookup"><span data-stu-id="0be5c-210">Delete a table</span></span>

<span data-ttu-id="0be5c-211">Você pode excluir uma tabela de uma conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0be5c-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="0be5c-212">Uma tabela que foi excluída não estará disponível para ser recriada por um período de tempo após a exclusão.</span><span class="sxs-lookup"><span data-stu-id="0be5c-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="0be5c-213">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="0be5c-213">Next steps</span></span>

<span data-ttu-id="0be5c-214">Agora que você aprendeu os conceitos básicos do armazenamento de tabelas, siga estes links para saber mais sobre tarefas de armazenamento mais complexas e o Azure Cosmos DB API de Tabela.</span><span class="sxs-lookup"><span data-stu-id="0be5c-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="0be5c-215">Introdução ao Azure Cosmos DB API de Tabela</span><span class="sxs-lookup"><span data-stu-id="0be5c-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="0be5c-216">Referência da biblioteca de cliente de armazenamento para .NET</span><span class="sxs-lookup"><span data-stu-id="0be5c-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="0be5c-217">Provedor de tipo de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="0be5c-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="0be5c-218">Blog da equipe de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="0be5c-218">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="0be5c-219">Configurando cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="0be5c-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
