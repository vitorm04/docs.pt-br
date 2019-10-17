---
title: Introdução ao armazenamento de Tabelas do Azure usando F#
description: Armazene dados estruturados na nuvem usando o armazenamento de tabelas do Azure ou Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 30ffd5f099dbb8efbf57104a2ade6c26304b7cee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395203"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Introdução ao armazenamento de tabelas do Azure e ao Azure Cosmos DB API de Tabela usando F @ no__t-0

O armazenamento de tabelas do Azure é um serviço que armazena dados NoSQL estruturados na nuvem. O armazenamento de tabela é um repositório de chave/atributo com um design sem esquema. Como o armazenamento de tabelas não tem Esquema, é fácil adaptar seus dados à medida que as necessidades de seu aplicativo evoluem. O acesso aos dados é rápido e econômico para todos os tipos de aplicativos. O armazenamento de tabela normalmente é significativamente menor em relação ao custo do que o SQL tradicional para volumes de dados semelhantes.

Você pode usar o armazenamento de tabelas para armazenar conjuntos de dados flexíveis, como os de usuário para aplicativos Web, catálogos de endereços, informações de dispositivo e qualquer outro tipo de metadados que seu serviço requer. Você pode armazenar qualquer número de entidades em uma tabela e uma conta de armazenamento pode conter qualquer número de tabelas, até o limite de capacidade da conta de armazenamento.

Azure Cosmos DB fornece a API de Tabela para aplicativos que são escritos para o armazenamento de tabelas do Azure e que exigem recursos premium, como:

- Distribuição global pronta para uso.
- Taxa de transferência dedicada em todo o mundo.
- Latências de milissegundos de dígito único no 99 º percentil.
- Alta disponibilidade garantida.
- Indexação secundária automática.

Os aplicativos escritos para o armazenamento de tabelas do Azure podem migrar para Azure Cosmos DB usando o API de Tabela sem alterações de código e aproveitar os recursos premium. O API de Tabela tem SDKs de cliente disponíveis para .NET, Java, Python e node. js.

Para obter mais informações, consulte [introdução ao Azure Cosmos DB API de tabela](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>Sobre este tutorial

Este tutorial mostra como escrever F# código para fazer algumas tarefas comuns usando o armazenamento de tabelas do Azure ou o Azure Cosmos DB API de tabela, incluindo a criação e a exclusão de uma tabela e inserção, atualização, exclusão e consulta de dados de tabela.

## <a name="prerequisites"></a>Prerequisites

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account) ou [Azure Cosmos DB conta](https://azure.microsoft.com/try/cosmosdb/).

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar um F# script e iniciar F# interativo

Os exemplos neste artigo podem ser usados em um F# aplicativo ou um F# script. Para criar um F# script, crie um arquivo com a extensão `.fsx`, por exemplo, `tables.fsx`, em F# seu ambiente de desenvolvimento.

Em seguida, use um [Gerenciador de pacotes](package-management.md) , como [paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) , para instalar o pacote `WindowsAzure.Storage` e referência `WindowsAzure.Storage.dll` em seu script usando uma diretiva `#r`. Faça isso novamente para `Microsoft.WindowsAzure.ConfigurationManager` a fim de obter o namespace Microsoft. Azure.

### <a name="add-namespace-declarations"></a>Adicionar declarações de namespace

Adicione as seguintes instruções `open` à parte superior do arquivo `tables.fsx`:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Obter sua cadeia de conexão de armazenamento do Azure

Se você estiver se conectando ao serviço tabela de armazenamento do Azure, precisará de sua cadeia de conexão para este tutorial. Você pode copiar a cadeia de conexão do portal do Azure. Para obter mais informações sobre cadeias de conexão, consulte [Configurar cadeias de conexão de armazenamento](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Obter sua cadeia de conexão do Azure Cosmos DB

Se estiver se conectando ao Azure Cosmos DB, você precisará da sua cadeia de conexão para este tutorial. Você pode copiar a cadeia de conexão do portal do Azure. Na portal do Azure, na sua conta do Cosmos DB, vá para **configurações** > **cadeia de conexão**e clique no botão **copiar** para copiar a cadeia de conexão primária. 

Para o tutorial, insira sua cadeia de conexão em seu script, como no exemplo a seguir:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

No entanto, isso **não é recomendado** para projetos reais. Sua chave de conta de armazenamento é semelhante à senha raiz da sua conta de armazenamento. Sempre tenha cuidado para proteger sua chave de conta de armazenamento. Evite distribuí-lo a outros usuários, embuti-lo em código ou salvá-lo em um arquivo de texto sem formatação que seja acessível para outras pessoas. Você pode regenerar sua chave usando o portal do Azure se acreditar que ele pode ter sido comprometido.

Para aplicativos reais, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração. Para buscar a cadeia de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Usar o Configuration Manager do Azure é opcional. Você também pode usar uma API como o tipo de `ConfigurationManager` do .NET Framework.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de conexão

Para analisar a cadeia de conexão, use:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Isso retorna um `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Criar o cliente do serviço tabela

A classe `CloudTableClient` permite que você recupere tabelas e entidades no armazenamento de tabelas. Aqui está uma maneira de criar o cliente de serviço:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Agora você está pronto para escrever código que lê dados e grava dados no armazenamento de tabelas.

### <a name="create-a-table"></a>Criar uma tabela

Este exemplo mostra como criar uma tabela se ela ainda não existir:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Adicionar uma entidade a uma tabela

Uma entidade deve ter um tipo que herde de `TableEntity`. Você pode estender `TableEntity` da maneira que desejar, mas seu tipo *deve* ter um construtor sem parâmetros. Somente as propriedades que têm `get` e `set` são armazenadas em sua tabela do Azure.

A chave de partição e de linha de uma entidade identifica exclusivamente a entidade na tabela. As entidades com a mesma chave de partição podem ser consultadas mais rápido do que aquelas com chaves de partição diferentes, mas o uso de chaves de partição diversas permite maior escalabilidade de operações paralelas.

Aqui está um exemplo de um `Customer` que usa o `lastName` como a chave de partição e o `firstName` como a chave de linha.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Agora, adicione `Customer` à tabela. Para fazer isso, crie um `TableOperation` que é executado na tabela. Nesse caso, você cria uma operação `Insert`.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Inserir um lote de entidades

Você pode inserir um lote de entidades em uma tabela usando uma única operação de gravação. As operações em lote permitem combinar operações em uma única execução, mas têm algumas restrições:

- Você pode executar atualizações, exclusões e inserções na mesma operação em lote.
- Uma operação em lote pode incluir até 100 entidades.
- Todas as entidades em uma operação em lote devem ter a mesma chave de partição.
- Embora seja possível executar uma consulta em uma operação em lote, ela deve ser a única operação no lote.

Aqui está um código que combina duas inserções em uma operação em lote:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Recuperar todas as entidades em uma partição

Para consultar uma tabela para todas as entidades em uma partição, use um objeto `TableQuery`. Aqui, você filtra as entidades em que "Smith" é a chave de partição.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Agora você imprime os resultados:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Recuperar um intervalo de entidades em uma partição

Se você não quiser consultar todas as entidades em uma partição, poderá especificar um intervalo combinando o filtro de chave de partição com um filtro de chave de linha. Aqui, você usa dois filtros para obter todas as entidades na partição "Smith", em que a chave de linha (primeiro nome) começa com uma letra anterior à "M" no alfabeto.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Agora você imprime os resultados:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Recuperar uma única entidade

Você pode escrever uma consulta para recuperar uma única entidade específica. Aqui, você usa um `TableOperation` para especificar o cliente "Ben Smith". Em vez de uma coleção, você obtém um `Customer`. A especificação da chave de partição e da chave de linha em uma consulta é a maneira mais rápida de recuperar uma única entidade do serviço tabela.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Agora você imprime os resultados:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>Substituir uma entidade

Para atualizar uma entidade, recupere-a do serviço tabela, modifique o objeto de entidade e salve as alterações de volta no serviço tabela usando uma operação `Replace`. Isso faz com que a entidade seja totalmente substituída no servidor, a menos que a entidade no servidor tenha sido alterada desde que foi recuperada; nesse caso, a operação falhará. Essa falha é impedir que seu aplicativo substitua inadvertidamente as alterações de outras fontes.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Inserir ou substituir uma entidade

Às vezes, você não sabe se existe uma entidade na tabela. E, se tiver, os valores atuais armazenados nela não serão mais necessários. Você pode usar `InsertOrReplace` para criar a entidade ou substituí-la, se ela existir, independentemente de seu estado.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Consultar um subconjunto de propriedades de entidade

Uma consulta de tabela pode recuperar apenas algumas propriedades de uma entidade em vez de todas elas. Essa técnica, chamada projeção, pode melhorar o desempenho da consulta, especialmente para grandes entidades. Aqui, você retorna apenas endereços de email usando `DynamicTableEntity` e `EntityResolver`. Observe que a projeção não tem suporte no emulador de armazenamento local, portanto, esse código é executado somente quando você está usando uma conta no serviço tabela.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Recuperar entidades em páginas de forma assíncrona

Se você estiver lendo um grande número de entidades e quiser processá-las à medida que elas forem recuperadas em vez de esperar que todas elas retornem, você poderá usar uma consulta segmentada. Aqui, você retorna resultados em páginas usando um fluxo de trabalho assíncrono para que a execução não seja bloqueada enquanto você estiver aguardando um grande conjunto de resultados ser retornado.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Agora você executa essa computação de forma síncrona:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Excluir uma entidade

Você pode excluir uma entidade depois de recuperá-la. Assim como a atualização de uma entidade, isso falhará se a entidade tiver sido alterada desde que você a recuperou.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Excluir uma tabela

Você pode excluir uma tabela de uma conta de armazenamento. Uma tabela que foi excluída não estará disponível para ser recriada por um período de tempo após a exclusão.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu os conceitos básicos do armazenamento de tabelas, siga estes links para saber mais sobre tarefas de armazenamento mais complexas e o Azure Cosmos DB API de Tabela.

- [Introdução ao Azure Cosmos DB API de Tabela](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Referência da biblioteca de cliente de armazenamento para .NET](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [Provedor de tipo de armazenamento do Azure](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog da equipe de armazenamento do Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Configurando cadeias de conexão](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
