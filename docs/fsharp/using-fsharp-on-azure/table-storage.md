---
title: 'Introdução ao armazenamento de tabela do Azure usando F #'
description: Armazene dados estruturados na nuvem usando o armazenamento de tabela do Azure ou o banco de dados do Azure Cosmos.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: ac81bc88db1436aa4d5f576da61a90839df04b99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Introdução ao armazenamento de tabela do Azure e a API de tabela de banco de dados do Azure Cosmos usando F # # 

Armazenamento de tabela do Azure é um serviço que armazena dados estruturados de NoSQL na nuvem. Armazenamento de tabela é um repositório de chave/atributo com um design schemaless. Como o armazenamento de tabela é schemaless, é fácil adaptar seus dados conforme as necessidades do seu evolve do aplicativo. Acesso a dados é rápida e econômica para todos os tipos de aplicativos. Armazenamento de tabela normalmente é significativamente menor custo de que SQL tradicional para volumes semelhantes de dados.

Você pode usar o armazenamento de tabela para armazenar conjuntos de dados flexíveis, como dados de usuário para aplicativos web, catálogos de endereços, informações de dispositivo e qualquer outro tipo de metadados que o serviço requer. Você pode armazenar qualquer número de entidades em uma tabela, e uma conta de armazenamento pode conter qualquer número de tabelas, até o limite de capacidade da conta de armazenamento.

Banco de dados do Azure Cosmos fornece a API de tabela para aplicativos que são escritos para o armazenamento de tabela do Azure e que exigem recursos premium, como:

- Distribuição global e completa.
- Produtividade dedicada em todo o mundo.
- Latências de milissegundo dígito no 99th percentual.
- A garantia de alta disponibilidade.
- Secundário a indexação automática.

Aplicativos escritos para o armazenamento de tabela do Azure podem migrar para o banco de dados do Azure Cosmos usando a API de tabela sem alterações de código e tirar proveito dos recursos premium. A API de tabela tem SDKs de cliente disponíveis para .NET, Java, Python e Node.js.

Para obter mais informações, consulte [Introdução à API de tabela de banco de dados do Azure Cosmos](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>Sobre este tutorial

Este tutorial mostra como escrever código F # para fazer algumas tarefas comuns usando o armazenamento de tabela do Azure ou a API do Azure Cosmos banco de dados tabela, incluindo a criação e exclusão de uma tabela e inserindo, atualizando, excluindo e consultar dados de tabela.

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account) ou [conta de banco de dados do Azure Cosmos](https://azure.microsoft.com/try/cosmosdb/).


## <a name="create-an-f-script-and-start-f-interactive"></a>Criar Script F # e começar a F # interativo

Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #. Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `tables.fsx`, em seu ambiente de desenvolvimento do F #.

Em seguida, use uma [Gerenciador de pacote](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando um `#r`diretiva. Fazê-lo novamente para `Microsoft.WindowsAzure.ConfigurationManager` para obter o namespace Microsoft.Azure.

### <a name="add-namespace-declarations"></a>Adicione declarações de namespace

Adicione o seguinte `open` instruções na parte superior do `tables.fsx` arquivo:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Obter a cadeia de caracteres de conexão de armazenamento do Azure

Se você estiver se conectando ao serviço de tabela de armazenamento do Azure, você precisará de sua cadeia de caracteres de conexão para este tutorial. Você pode copiar a cadeia de caracteres de conexão do portal do Azure. Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Obter sua cadeia de caracteres de conexão do banco de dados do Azure Cosmos

Se você estiver se conectando ao banco de dados do Azure Cosmos, você precisará de sua cadeia de caracteres de conexão para este tutorial. Você pode copiar a cadeia de caracteres de conexão do portal do Azure. No portal do Azure, na sua conta do banco de dados do Cosmos, vá para **configurações** > **cadeia de caracteres de Conexão**e clique no **cópia** botão Copiar sua Conexão primária Cadeia de caracteres. 

Para o tutorial, insira a cadeia de conexão no seu script, como o exemplo a seguir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

No entanto, isso é **não recomendável** projetos para o real. Sua chave de conta de armazenamento é semelhante para a senha de raiz de sua conta de armazenamento. Sempre tenha cuidado para proteger a chave de conta de armazenamento. Evite distribuí-lo a outros usuários, codificar, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas. Você pode regenerar a chave usando o Portal do Azure se você acredita que ele pode ter sido comprometido.

Aplicativos para o real, a melhor maneira de manter sua cadeia de caracteres de conexão de armazenamento está em um arquivo de configuração. Para obter a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Usando o Gerenciador de configuração do Azure é opcional. Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de caracteres de conexão

Para analisar a cadeia de caracteres de conexão, use:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Isso retorna um `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Criar o cliente do serviço de tabela

O `CloudTableClient` classe permite que você recupere tabelas e entidades no armazenamento de tabela. Aqui está uma maneira de criar o cliente do serviço:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Agora você está pronto para escrever código que lê e grava dados no armazenamento de tabela.

### <a name="create-a-table"></a>Criar uma tabela

Este exemplo mostra como criar uma tabela se ela ainda não existir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Adicionar uma entidade a uma tabela

Uma entidade deve ter um tipo que herda de `TableEntity`. Você pode estender `TableEntity` de maneira que desejar, mas seu tipo *deve* tem um construtor sem parâmetros. Somente as propriedades que têm ambos `get` e `set` são armazenados na tabela do Azure.

Partição de uma entidade e a chave de linha identificam exclusivamente a entidade na tabela. Entidades com a mesma chave de partição podem ser consultadas com mais rapidez do que aquelas com diferentes chaves de partição, mas usar chaves de partição diversas permite maior escalabilidade de operações paralelas.

Aqui está um exemplo de um `Customer` que usa o `lastName` como a chave de partição e o `firstName` como a chave de linha.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Agora adicione `Customer` à tabela. Para fazer isso, crie um `TableOperation` que é executado na tabela. Nesse caso, você cria um `Insert` operação.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Inserir um lote de entidades

Você pode inserir um lote de entidades em uma tabela usando uma única operação de gravação. Operações em lote permitem combinar as operações em uma única execução, mas eles têm algumas restrições:

- Você pode executar atualizações, exclusões e insere na mesma operação em lote.
- Uma operação em lote pode incluir até 100 entidades.
- Todas as entidades em uma operação de lote devem ter a mesma chave de partição.
- Embora seja possível executar uma consulta em uma operação em lote, ele deve ser a única operação em lote.

Este é o código que combina dois inserções em uma operação em lote:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Recuperar todas as entidades em uma partição

Para consultar uma tabela para todas as entidades em uma partição, use um `TableQuery` objeto. Aqui, você filtrar para entidades onde "Smith" é a chave de partição.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Agora é possível imprimir os resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Recuperar um intervalo de entidades em uma partição

Se você não quiser consultar todas as entidades em uma partição, você pode especificar um intervalo, combinando o filtro chave de partição com um filtro de linha de chave. Aqui, você usa dois filtros para obter todas as entidades na partição "Smith" onde a chave de linha (nome) começa com uma letra anteriores "M" no alfabeto.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Agora é possível imprimir os resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Recuperar uma única entidade

Você pode escrever uma consulta para recuperar uma entidade única e específica. Aqui, você usa um `TableOperation` para especificar o cliente "Ben Smith". Em vez de uma coleção, você obtém um `Customer`. Especificar a chave de partição e a chave de linha em uma consulta é a maneira mais rápida para recuperar uma única entidade de serviço tabela.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Agora é possível imprimir os resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a>Substituir uma entidade

Para atualizar uma entidade, recuperá-lo do serviço de tabela, modifique o objeto de entidade e, em seguida, salvar as alterações de volta para o serviço tabela usando um `Replace` operação. Isso faz com que a entidade a ser totalmente substituídos no servidor, a menos que a entidade do servidor foi alterado desde que foi recuperada, caso em que a operação falhará. Essa falha é para impedir que seu aplicativo inadvertidamente substituir alterações de outras fontes.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Inserir ou substituir uma entidade

Às vezes, você não sabe se existe uma entidade na tabela. E, em caso afirmativo, os valores atuais armazenados nela não são mais necessários. Você pode usar `InsertOrReplace` para criar a entidade ou substituí-lo se ele existir, independentemente de seu estado.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Consultar um subconjunto das propriedades de entidade

Uma consulta de tabela pode recuperar apenas algumas propriedades de uma entidade em vez de todos eles. Essa técnica, chamada de projeção, pode melhorar o desempenho, especialmente para grandes entidades. Aqui, você retornar endereços de email somente usando `DynamicTableEntity` e `EntityResolver`. Observe que projeção não é suportada no emulador de armazenamento local, para que este código seja executado somente quando você estiver usando uma conta do serviço de tabela.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Recuperar entidades nas páginas de forma assíncrona

Se você está lendo um grande número de entidades e deseja processá-las conforme eles são recuperados em vez de esperar todos eles retornar, você pode usar uma consulta segmentada. Aqui, você retorna resultados em páginas usando um fluxo de trabalho assíncrono para que a execução não é bloqueada enquanto você está esperando um grande conjunto de resultados a serem retornados.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Você executar esse cálculo síncrona:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Excluir uma entidade

Você pode excluir uma entidade após recuperá-lo. Com a atualização de uma entidade, isso pode falhar se a entidade foi alterado desde que foi recuperado.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Excluir uma tabela

Você pode excluir uma tabela de uma conta de armazenamento. Uma tabela que foi excluída estará disponível para ser recriado por um período de tempo após a exclusão.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu as Noções básicas de armazenamento de tabela, siga estes links para saber mais sobre as tarefas mais complexas de armazenamento e a API de tabela de banco de dados do Azure Cosmos.

- [Introdução à API de tabela do banco de dados do Cosmos do Azure](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Biblioteca de cliente de armazenamento para a referência do .NET](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Provedor de tipo de armazenamento do Azure](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog da equipe do armazenamento do Azure](http://blogs.msdn.com/b/windowsazurestorage/)
- [Configurando cadeias de caracteres de Conexão](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [Introdução ao armazenamento de tabela do Azure no .NET](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
