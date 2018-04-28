---
title: 'Introdução ao armazenamento de tabela do Azure usando F #'
description: Armazene dados estruturados na nuvem usando o armazenamento de tabela do Azure ou o banco de dados do Azure Cosmos.
author: sylvanc
ms.author: phcart
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 50721ca44bbae5c52984b08a30bc87507fbf063d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="ea1c8-103">Introdução ao armazenamento de tabela do Azure e a API de tabela de banco de dados do Azure Cosmos usando F #</span><span class="sxs-lookup"><span data-stu-id="ea1c8-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="ea1c8-104">Armazenamento de tabela do Azure é um serviço que armazena dados estruturados de NoSQL na nuvem.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="ea1c8-105">Armazenamento de tabela é um repositório de chave/atributo com um design schemaless.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="ea1c8-106">Como o armazenamento de tabela é schemaless, é fácil adaptar seus dados conforme as necessidades do seu evolve do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="ea1c8-107">Acesso a dados é rápida e econômica para todos os tipos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="ea1c8-108">Armazenamento de tabela normalmente é significativamente menor custo de que SQL tradicional para volumes semelhantes de dados.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="ea1c8-109">Você pode usar o armazenamento de tabela para armazenar conjuntos de dados flexíveis, como dados de usuário para aplicativos web, catálogos de endereços, informações de dispositivo e qualquer outro tipo de metadados que o serviço requer.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="ea1c8-110">Você pode armazenar qualquer número de entidades em uma tabela, e uma conta de armazenamento pode conter qualquer número de tabelas, até o limite de capacidade da conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="ea1c8-111">Banco de dados do Azure Cosmos fornece a API de tabela para aplicativos que são escritos para o armazenamento de tabela do Azure e que exigem recursos premium, como:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="ea1c8-112">Distribuição global e completa.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="ea1c8-113">Produtividade dedicada em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="ea1c8-114">Latências de milissegundo dígito no 99th percentual.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="ea1c8-115">A garantia de alta disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="ea1c8-116">Secundário a indexação automática.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="ea1c8-117">Aplicativos escritos para o armazenamento de tabela do Azure podem migrar para o banco de dados do Azure Cosmos usando a API de tabela sem alterações de código e tirar proveito dos recursos premium.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="ea1c8-118">A API de tabela tem SDKs de cliente disponíveis para .NET, Java, Python e Node.js.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="ea1c8-119">Para obter mais informações, consulte [Introdução à API de tabela de banco de dados do Azure Cosmos](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="ea1c8-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="ea1c8-120">Sobre este tutorial</span><span class="sxs-lookup"><span data-stu-id="ea1c8-120">About this tutorial</span></span>

<span data-ttu-id="ea1c8-121">Este tutorial mostra como escrever código F # para fazer algumas tarefas comuns usando o armazenamento de tabela do Azure ou a API do Azure Cosmos banco de dados tabela, incluindo a criação e exclusão de uma tabela e inserindo, atualizando, excluindo e consultar dados de tabela.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea1c8-122">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ea1c8-122">Prerequisites</span></span>

<span data-ttu-id="ea1c8-123">Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account) ou [conta de banco de dados do Azure Cosmos](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="ea1c8-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="ea1c8-124">Criar Script F # e começar a F # interativo</span><span class="sxs-lookup"><span data-stu-id="ea1c8-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="ea1c8-125">Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="ea1c8-126">Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `tables.fsx`, em seu ambiente de desenvolvimento do F #.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="ea1c8-127">Em seguida, use uma [Gerenciador de pacote](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando um `#r`diretiva.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="ea1c8-128">Fazê-lo novamente para `Microsoft.WindowsAzure.ConfigurationManager` para obter o namespace Microsoft.Azure.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="ea1c8-129">Adicione declarações de namespace</span><span class="sxs-lookup"><span data-stu-id="ea1c8-129">Add namespace declarations</span></span>

<span data-ttu-id="ea1c8-130">Adicione o seguinte `open` instruções na parte superior do `tables.fsx` arquivo:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="ea1c8-131">Obter a cadeia de caracteres de conexão de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="ea1c8-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="ea1c8-132">Se você estiver se conectando ao serviço de tabela de armazenamento do Azure, você precisará de sua cadeia de caracteres de conexão para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="ea1c8-133">Você pode copiar a cadeia de caracteres de conexão do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="ea1c8-134">Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="ea1c8-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="ea1c8-135">Obter sua cadeia de caracteres de conexão do banco de dados do Azure Cosmos</span><span class="sxs-lookup"><span data-stu-id="ea1c8-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="ea1c8-136">Se você estiver se conectando ao banco de dados do Azure Cosmos, você precisará de sua cadeia de caracteres de conexão para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="ea1c8-137">Você pode copiar a cadeia de caracteres de conexão do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="ea1c8-138">No portal do Azure, na sua conta do banco de dados do Cosmos, vá para **configurações** > **cadeia de caracteres de Conexão**e clique no **cópia** botão Copiar sua Conexão primária Cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="ea1c8-139">Para o tutorial, insira a cadeia de conexão no seu script, como o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="ea1c8-140">No entanto, isso é **não recomendável** projetos para o real.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="ea1c8-141">Sua chave de conta de armazenamento é semelhante para a senha de raiz de sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="ea1c8-142">Sempre tenha cuidado para proteger a chave de conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="ea1c8-143">Evite distribuí-lo a outros usuários, codificar, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="ea1c8-144">Você pode regenerar a chave usando o Portal do Azure se você acredita que ele pode ter sido comprometido.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="ea1c8-145">Aplicativos para o real, a melhor maneira de manter sua cadeia de caracteres de conexão de armazenamento está em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="ea1c8-146">Para obter a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="ea1c8-147">Usando o Gerenciador de configuração do Azure é opcional.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="ea1c8-148">Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="ea1c8-149">Analisar a cadeia de caracteres de conexão</span><span class="sxs-lookup"><span data-stu-id="ea1c8-149">Parse the connection string</span></span>

<span data-ttu-id="ea1c8-150">Para analisar a cadeia de caracteres de conexão, use:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="ea1c8-151">Isso retorna um `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="ea1c8-152">Criar o cliente do serviço de tabela</span><span class="sxs-lookup"><span data-stu-id="ea1c8-152">Create the Table service client</span></span>

<span data-ttu-id="ea1c8-153">O `CloudTableClient` classe permite que você recupere tabelas e entidades no armazenamento de tabela.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="ea1c8-154">Aqui está uma maneira de criar o cliente do serviço:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="ea1c8-155">Agora você está pronto para escrever código que lê e grava dados no armazenamento de tabela.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="ea1c8-156">Criar uma tabela</span><span class="sxs-lookup"><span data-stu-id="ea1c8-156">Create a table</span></span>

<span data-ttu-id="ea1c8-157">Este exemplo mostra como criar uma tabela se ela ainda não existir:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="ea1c8-158">Adicionar uma entidade a uma tabela</span><span class="sxs-lookup"><span data-stu-id="ea1c8-158">Add an entity to a table</span></span>

<span data-ttu-id="ea1c8-159">Uma entidade deve ter um tipo que herda de `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="ea1c8-160">Você pode estender `TableEntity` de maneira que desejar, mas seu tipo *deve* tem um construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="ea1c8-161">Somente as propriedades que têm ambos `get` e `set` são armazenados na tabela do Azure.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="ea1c8-162">Partição de uma entidade e a chave de linha identificam exclusivamente a entidade na tabela.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="ea1c8-163">Entidades com a mesma chave de partição podem ser consultadas com mais rapidez do que aquelas com diferentes chaves de partição, mas usar chaves de partição diversas permite maior escalabilidade de operações paralelas.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="ea1c8-164">Aqui está um exemplo de um `Customer` que usa o `lastName` como a chave de partição e o `firstName` como a chave de linha.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="ea1c8-165">Agora adicione `Customer` à tabela.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="ea1c8-166">Para fazer isso, crie um `TableOperation` que é executado na tabela.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="ea1c8-167">Nesse caso, você cria um `Insert` operação.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="ea1c8-168">Inserir um lote de entidades</span><span class="sxs-lookup"><span data-stu-id="ea1c8-168">Insert a batch of entities</span></span>

<span data-ttu-id="ea1c8-169">Você pode inserir um lote de entidades em uma tabela usando uma única operação de gravação.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="ea1c8-170">Operações em lote permitem combinar as operações em uma única execução, mas eles têm algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="ea1c8-171">Você pode executar atualizações, exclusões e insere na mesma operação em lote.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="ea1c8-172">Uma operação em lote pode incluir até 100 entidades.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="ea1c8-173">Todas as entidades em uma operação de lote devem ter a mesma chave de partição.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="ea1c8-174">Embora seja possível executar uma consulta em uma operação em lote, ele deve ser a única operação em lote.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="ea1c8-175">Este é o código que combina dois inserções em uma operação em lote:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="ea1c8-176">Recuperar todas as entidades em uma partição</span><span class="sxs-lookup"><span data-stu-id="ea1c8-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="ea1c8-177">Para consultar uma tabela para todas as entidades em uma partição, use um `TableQuery` objeto.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="ea1c8-178">Aqui, você filtrar para entidades onde "Smith" é a chave de partição.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="ea1c8-179">Agora é possível imprimir os resultados:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="ea1c8-180">Recuperar um intervalo de entidades em uma partição</span><span class="sxs-lookup"><span data-stu-id="ea1c8-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="ea1c8-181">Se você não quiser consultar todas as entidades em uma partição, você pode especificar um intervalo, combinando o filtro chave de partição com um filtro de linha de chave.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="ea1c8-182">Aqui, você usa dois filtros para obter todas as entidades na partição "Smith" onde a chave de linha (nome) começa com uma letra anteriores "M" no alfabeto.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="ea1c8-183">Agora é possível imprimir os resultados:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="ea1c8-184">Recuperar uma única entidade</span><span class="sxs-lookup"><span data-stu-id="ea1c8-184">Retrieve a single entity</span></span>

<span data-ttu-id="ea1c8-185">Você pode escrever uma consulta para recuperar uma entidade única e específica.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="ea1c8-186">Aqui, você usa um `TableOperation` para especificar o cliente "Ben Smith".</span><span class="sxs-lookup"><span data-stu-id="ea1c8-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="ea1c8-187">Em vez de uma coleção, você obtém um `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="ea1c8-188">Especificar a chave de partição e a chave de linha em uma consulta é a maneira mais rápida para recuperar uma única entidade de serviço tabela.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="ea1c8-189">Agora é possível imprimir os resultados:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="ea1c8-190">Substituir uma entidade</span><span class="sxs-lookup"><span data-stu-id="ea1c8-190">Replace an entity</span></span>

<span data-ttu-id="ea1c8-191">Para atualizar uma entidade, recuperá-lo do serviço de tabela, modifique o objeto de entidade e, em seguida, salvar as alterações de volta para o serviço tabela usando um `Replace` operação.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="ea1c8-192">Isso faz com que a entidade a ser totalmente substituídos no servidor, a menos que a entidade do servidor foi alterado desde que foi recuperada, caso em que a operação falhará.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="ea1c8-193">Essa falha é para impedir que seu aplicativo inadvertidamente substituir alterações de outras fontes.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="ea1c8-194">Inserir ou substituir uma entidade</span><span class="sxs-lookup"><span data-stu-id="ea1c8-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="ea1c8-195">Às vezes, você não sabe se existe uma entidade na tabela.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="ea1c8-196">E, em caso afirmativo, os valores atuais armazenados nela não são mais necessários.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="ea1c8-197">Você pode usar `InsertOrReplace` para criar a entidade ou substituí-lo se ele existir, independentemente de seu estado.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="ea1c8-198">Consultar um subconjunto das propriedades de entidade</span><span class="sxs-lookup"><span data-stu-id="ea1c8-198">Query a subset of entity properties</span></span>

<span data-ttu-id="ea1c8-199">Uma consulta de tabela pode recuperar apenas algumas propriedades de uma entidade em vez de todos eles.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="ea1c8-200">Essa técnica, chamada de projeção, pode melhorar o desempenho, especialmente para grandes entidades.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="ea1c8-201">Aqui, você retornar endereços de email somente usando `DynamicTableEntity` e `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="ea1c8-202">Observe que projeção não é suportada no emulador de armazenamento local, para que este código seja executado somente quando você estiver usando uma conta do serviço de tabela.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="ea1c8-203">Recuperar entidades nas páginas de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="ea1c8-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="ea1c8-204">Se você está lendo um grande número de entidades e deseja processá-las conforme eles são recuperados em vez de esperar todos eles retornar, você pode usar uma consulta segmentada.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="ea1c8-205">Aqui, você retorna resultados em páginas usando um fluxo de trabalho assíncrono para que a execução não é bloqueada enquanto você está esperando um grande conjunto de resultados a serem retornados.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="ea1c8-206">Você executar esse cálculo síncrona:</span><span class="sxs-lookup"><span data-stu-id="ea1c8-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="ea1c8-207">Excluir uma entidade</span><span class="sxs-lookup"><span data-stu-id="ea1c8-207">Delete an entity</span></span>

<span data-ttu-id="ea1c8-208">Você pode excluir uma entidade após recuperá-lo.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="ea1c8-209">Com a atualização de uma entidade, isso pode falhar se a entidade foi alterado desde que foi recuperado.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="ea1c8-210">Excluir uma tabela</span><span class="sxs-lookup"><span data-stu-id="ea1c8-210">Delete a table</span></span>

<span data-ttu-id="ea1c8-211">Você pode excluir uma tabela de uma conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="ea1c8-212">Uma tabela que foi excluída estará disponível para ser recriado por um período de tempo após a exclusão.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="ea1c8-213">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ea1c8-213">Next steps</span></span>

<span data-ttu-id="ea1c8-214">Agora que você aprendeu as Noções básicas de armazenamento de tabela, siga estes links para saber mais sobre as tarefas mais complexas de armazenamento e a API de tabela de banco de dados do Azure Cosmos.</span><span class="sxs-lookup"><span data-stu-id="ea1c8-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="ea1c8-215">Introdução à API de tabela do banco de dados do Cosmos do Azure</span><span class="sxs-lookup"><span data-stu-id="ea1c8-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="ea1c8-216">Biblioteca de cliente de armazenamento para a referência do .NET</span><span class="sxs-lookup"><span data-stu-id="ea1c8-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="ea1c8-217">Provedor de tipo de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="ea1c8-217">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="ea1c8-218">Blog da equipe do armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="ea1c8-218">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="ea1c8-219">Configurando cadeias de caracteres de Conexão</span><span class="sxs-lookup"><span data-stu-id="ea1c8-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="ea1c8-220">Introdução ao armazenamento de tabela do Azure no .NET</span><span class="sxs-lookup"><span data-stu-id="ea1c8-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
