---
title: 'Introdução ao armazenamento de tabelas do Azure usando F #'
description: Store dados estruturados na nuvem usando o armazenamento de tabela do Azure ou Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 2d793ba8653833ff384f1824e303b08e05aba69b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519529"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Introdução ao armazenamento de tabelas do Azure e a API de tabela do Azure Cosmos DB usando F # # 

Armazenamento de tabela do Azure é um serviço que armazena dados NoSQL estruturados na nuvem. Armazenamento de tabelas é um repositório de chaves/atributos com um design sem esquema. Como o armazenamento de tabela é sem esquema, é fácil adaptar seus dados conforme as necessidades do seu aplicativo evoluem. Acesso a dados é rápido e econômico para todos os tipos de aplicativos. Armazenamento de tabela normalmente é significativamente mais baixo custo que o SQL tradicional para volumes de dados semelhantes.

Você pode usar o armazenamento de tabela para armazenar conjuntos de dados flexíveis, como dados de usuário para aplicativos web, catálogos de endereços, informações de dispositivo e qualquer outro tipo de metadados que o serviço requer. Você pode armazenar qualquer número de entidades em uma tabela e uma conta de armazenamento pode conter qualquer número de tabelas, até o limite de capacidade da conta de armazenamento.

O Azure Cosmos DB fornece a API de tabela para aplicativos que são escritos para o armazenamento de tabela do Azure e que exigem recursos premium como:

- Distribuição global turnkey.
- Taxa de transferência dedicada em todo o mundo.
- Latências de milissegundo de único dígito no 99 º percentil.
- Garantia de alta disponibilidade.
- Indexação secundária automática.

Aplicativos escritos para o armazenamento de tabela do Azure podem migrar para o Azure Cosmos DB usando a API de tabela sem alterações no código e tirar proveito dos recursos premium. A API de tabela tem SDKs de cliente disponíveis para .NET, Java, Python e Node. js.

Para obter mais informações, consulte [Introdução à API de tabela do Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>Sobre este tutorial

Este tutorial mostra como escrever código em F # para fazer algumas tarefas comuns usando o armazenamento de tabela do Azure ou a API tabela do Azure Cosmos DB, incluindo a criação e exclusão de uma tabela e inserindo, atualizando, excluindo e consultar dados de tabela.

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account) ou [conta do Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).


## <a name="create-an-f-script-and-start-f-interactive"></a>Criar Script de F # e o início da F # interativo

Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #. Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `tables.fsx`, em seu ambiente de desenvolvimento do F #.

Em seguida, use um [Gerenciador de pacotes](package-management.md) tais como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando um `#r`diretiva. Fazê-lo novamente para `Microsoft.WindowsAzure.ConfigurationManager` para obter o namespace Microsoft.Azure.

### <a name="add-namespace-declarations"></a>Adicionar declarações de namespace

Adicione o seguinte `open` as instruções na parte superior do `tables.fsx` arquivo:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Obter a cadeia de conexão do armazenamento do Azure

Se você estiver se conectando ao serviço de tabela de armazenamento do Azure, você precisará de sua cadeia de caracteres de conexão para este tutorial. Você pode copiar a cadeia de conexão do portal do Azure. Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Obter a cadeia de conexão do Azure Cosmos DB

Se você estiver se conectando ao Azure Cosmos DB, você precisará de sua cadeia de caracteres de conexão para este tutorial. Você pode copiar a cadeia de conexão do portal do Azure. No portal do Azure, na sua conta do Cosmos DB, acesse **as configurações** > **cadeia de caracteres de Conexão**e clique no **cópia** botão para copiar sua Conexão primária Cadeia de caracteres. 

Para o tutorial, insira sua cadeia de conexão no seu script, como o exemplo a seguir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

No entanto, isso é **não recomendável** para projetos reais. Sua chave de conta de armazenamento é semelhante para a senha raiz para sua conta de armazenamento. Sempre tenha cuidado para proteger sua chave de conta de armazenamento. Evite distribuí-la a outros usuários, embuti-la, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas. Você pode regenerar a chave usando o Portal do Azure se você acredita que pode ter sido comprometida.

Aplicativos para o real, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração. Para buscar a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Usando o Gerenciador de configuração do Azure é opcional. Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de conexão

Para analisar a cadeia de caracteres de conexão, use:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Isso retorna um `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Criar o cliente do serviço de tabela

O `CloudTableClient` classe permite que você recupere as tabelas e entidades no armazenamento de tabela. Aqui está uma maneira de criar o cliente do serviço:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Agora você está pronto para escrever um código que lê e grava dados no armazenamento de tabela.

### <a name="create-a-table"></a>Criar uma tabela

Este exemplo mostra como criar uma tabela se ela ainda não existir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Adicionar uma entidade a uma tabela

Uma entidade deve ter um tipo que herda de `TableEntity`. Você pode estender `TableEntity` na maneira que desejar, mas seu tipo *deve* tem um construtor sem parâmetros. Somente as propriedades que têm ambos `get` e `set` são armazenados na tabela do Azure.

Partição de uma entidade e a chave de linha identificam exclusivamente a entidade na tabela. Entidades com a mesma chave de partição podem ser consultadas mais rápido do que aquelas com chaves de partição diferentes, mas usar chaves de partição diferentes permite uma escalabilidade maior de operações paralelas.

Aqui está um exemplo de uma `Customer` que usa o `lastName` como a chave de partição e o `firstName` como a chave de linha.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Agora, adicione `Customer` à tabela. Para fazer isso, crie um `TableOperation` que é executado na tabela. Nesse caso, você cria um `Insert` operação.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Inserir um lote de entidades

Você pode inserir um lote de entidades em uma tabela usando uma única operação de gravação. Operações em lote que você combine operações em uma única execução, mas eles têm algumas restrições:

- Você pode executar atualizações, exclusões e inserções na mesma operação em lote.
- Uma operação em lote pode incluir até 100 entidades.
- Todas as entidades em uma operação em lote devem ter a mesma chave de partição.
- Embora seja possível executar uma consulta em uma operação em lote, ele deve ser a única operação no lote.

Aqui está um código que combina duas inserções em uma operação em lote:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Recuperar todas as entidades em uma partição

Para consultar uma tabela de todas as entidades em uma partição, use um `TableQuery` objeto. Aqui, você filtrar para entidades onde "Smith" é a chave de partição.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Agora é possível imprimir os resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Recuperar um intervalo de entidades em uma partição

Se não desejar consultar todas as entidades em uma partição, você pode especificar um intervalo combinando o filtro de chave de partição com um filtro de chave de linha. Aqui, você usa dois filtros para obter todas as entidades na partição "Smith" em que a chave de linha (nome) começa com uma letra anterior a "M" no alfabeto.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Agora é possível imprimir os resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Recuperar uma única entidade

Você pode escrever uma consulta para recuperar uma entidade única e específica. Aqui, você usa um `TableOperation` para especificar o cliente "Ben Smith". Em vez de uma coleção, você recebe um `Customer`. Especificar a chave de partição e a chave de linha em uma consulta é a maneira mais rápida de recuperar uma única entidade de serviço tabela.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Agora é possível imprimir os resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a>Substituir uma entidade

Para atualizar uma entidade, recuperá-la do serviço tabela, modificar o objeto de entidade e, em seguida, salve as alterações de volta para o serviço tabela usando um `Replace` operação. Isso faz com que a entidade seja totalmente substituída no servidor, a menos que a entidade no servidor foi alterado desde que foi recuperada, caso em que a operação falhará. Essa falha ocorre impedir que seu aplicativo substitua inadvertidamente as alterações de outras fontes.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Inserir ou substituir uma entidade

Às vezes, você não sabe se uma entidade existe na tabela. E, em caso afirmativo, os valores atuais armazenados nela não são mais necessários. Você pode usar `InsertOrReplace` para criar a entidade ou substituí-lo se ele existir, independentemente de seu estado.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Consultar um subconjunto de propriedades da entidade

Uma consulta de tabela pode recuperar apenas algumas propriedades de uma entidade em vez de todos eles. Essa técnica, chamada projeção, pode melhorar o desempenho, especialmente para grandes entidades. Aqui, você retornar endereços de email só utilizam `DynamicTableEntity` e `EntityResolver`. Observe que projeção não é suportada no emulador de armazenamento local, portanto, esse código é executado somente quando você estiver usando uma conta no serviço tabela.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Recuperar entidades nas páginas de forma assíncrona

Se você estiver lendo um grande número de entidades, e você deseja processá-los conforme eles são recuperados em vez de aguardar que eles todos retornar, você pode usar uma consulta segmentada. Aqui, retornar resultados em páginas usando um fluxo de trabalho assíncronos, para que a execução não fique bloqueada enquanto espera para um grande conjunto de resultados a serem retornados.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Agora você executar esse cálculo sincronicamente:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Excluir uma entidade

Você pode excluir uma entidade depois que você recuperou. Assim como acontece com a atualização de uma entidade, isso falhará se a entidade tiver sido alterado desde que você recuperou a ele.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Excluir uma tabela

Você pode excluir uma tabela de uma conta de armazenamento. Uma tabela que foi excluída estará disponível para ser recriada por um período de tempo após a exclusão.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu os conceitos básicos do armazenamento de tabela, siga estes links para saber mais sobre as tarefas mais complexas de armazenamento e a API de tabela do Azure Cosmos DB.

- [Introdução ao Azure Cosmos DB API de tabela](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Biblioteca de cliente de armazenamento para a referência do .NET](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Provedor de tipos de armazenamento do Azure](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog da equipe do armazenamento do Azure](https://blogs.msdn.com/b/windowsazurestorage/)
- [Configurando cadeias de caracteres de Conexão](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [Introdução ao armazenamento de tabela do Azure no .NET](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
