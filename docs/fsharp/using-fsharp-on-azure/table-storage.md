---
title: "Introdução ao armazenamento de tabela do Azure usando F #"
description: "Armazene dados estruturados na nuvem usando o armazenamento de tabela do Azure, um repositório de dados NoSQL."
keywords: "o Visual f #, f #, funcional programação .NET, .NET Core, o Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: 905374a60261b0c2a863edb956943d41ae80f04d
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a>Introdução ao armazenamento de tabela do Azure usando F # #

Armazenamento de tabela do Azure é um serviço que armazena dados estruturados de NoSQL na nuvem. Armazenamento de tabela é um repositório de chave/atributo com um design schemaless. Como o armazenamento de tabela é schemaless, é fácil adaptar seus dados conforme as necessidades do seu evolve do aplicativo. Acesso a dados é rápida e econômica para todos os tipos de aplicativos. Armazenamento de tabela normalmente é significativamente menor custo de que SQL tradicional para volumes semelhantes de dados.

Você pode usar o armazenamento de tabela para armazenar conjuntos de dados flexíveis, como dados de usuário para aplicativos web, catálogos de endereços, informações de dispositivo e qualquer outro tipo de metadados que o serviço requer. Você pode armazenar qualquer número de entidades em uma tabela, e uma conta de armazenamento pode conter qualquer número de tabelas, até o limite de capacidade da conta de armazenamento.

### <a name="about-this-tutorial"></a>Sobre este tutorial

Este tutorial mostra como escrever código F # para fazer algumas tarefas comuns usando o armazenamento de tabela do Azure, incluindo a criação e exclusão de uma tabela e inserindo, atualizando, excluindo e consultar dados de tabela.

Para obter uma visão geral conceitual do armazenamento de tabela, consulte [guia .NET para armazenamento de tabela](/azure/storage/storage-dotnet-how-to-use-tables)

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).
Você também precisará sua chave de acesso de armazenamento para esta conta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar Script F # e começar a F # interativo

Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #. Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `tables.fsx`, em seu ambiente de desenvolvimento do F #.

Em seguida, use uma [Gerenciador de pacote](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando um `#r`diretiva. Fazê-lo novamente para 'Microsoft.WindowsAzure.ConfigurationManager' para obter o namespace Microsoft.Azure.

### <a name="add-namespace-declarations"></a>Adicione declarações de namespace

Adicione o seguinte `open` instruções na parte superior do `tables.fsx` arquivo:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obter a cadeia de conexão

Você precisará de uma cadeia de caracteres de conexão de armazenamento do Azure para este tutorial. Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).

Para o tutorial, você vai inserir sua cadeia de caracteres de conexão no seu script, como este:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

No entanto, isso é **não recomendável** projetos para o real. Sua chave de conta de armazenamento é semelhante para a senha de raiz de sua conta de armazenamento. Sempre tenha cuidado para proteger a chave de conta de armazenamento. Evite distribuí-lo a outros usuários, codificar, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas. Você pode regenerar a chave usando o Portal do Azure se você acredita que ele pode ter sido comprometido.

Aplicativos para o real, a melhor maneira de manter sua cadeia de caracteres de conexão de armazenamento está em um arquivo de configuração. Para obter a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Usando o Gerenciador de configuração do Azure é opcional. Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de caracteres de conexão

Para analisar a cadeia de caracteres de conexão, use:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Isso retornará um `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Criar o cliente do serviço de tabela

O `CloudTableClient` classe permite que você recupere tabelas e entidades armazenadas no armazenamento de tabela. Aqui está uma maneira de criar o cliente do serviço:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Agora você está pronto para escrever código que lê e grava dados no armazenamento de tabela.

## <a name="create-a-table"></a>Criar uma tabela

Este exemplo mostra como criar uma tabela se ela ainda não existir:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a>Adicionar uma entidade a uma tabela

Uma entidade deve ter um tipo que herda de `TableEntity`. Você pode estender `TableEntity` de maneira que desejar, mas seu tipo *deve* tem um construtor sem parâmetros. Somente as propriedades que têm ambos `get` e `set` será armazenado na tabela do Azure.

Partição de uma entidade e a chave de linha identificam exclusivamente a entidade na tabela. Entidades com a mesma chave de partição podem ser consultadas com mais rapidez do que aquelas com diferentes chaves de partição, mas usar chaves de partição diversas permite maior escalabilidade de operações paralelas.

Aqui está um exemplo de um `Customer` que usa o `lastName` como a chave de partição e o `firstName` como a chave de linha.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Agora vamos adicionar nossa `Customer` à tabela. Para fazer isso, você cria um `TableOperation` que será executado na tabela. Nesse caso, você cria um `Insert` operação.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a>Inserir um lote de entidades

Você pode inserir um lote de entidades em uma tabela usando uma única operação de gravação. Operações em lote permitem combinar as operações em uma única execução, mas eles têm algumas restrições:

- Você pode executar atualizações, exclusões e insere na mesma operação em lote.
- Uma operação em lote pode incluir até 100 entidades.
- Todas as entidades em uma operação de lote devem ter a mesma chave de partição.
- Embora seja possível executar uma consulta em uma operação em lote, ele deve ser a única operação em lote.

Este é o código que combina dois inserções em uma operação em lote:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a>Recuperar todas as entidades em uma partição

Para consultar uma tabela para todas as entidades em uma partição, use um `TableQuery` objeto. Aqui, você filtrar para entidades em que "Buster" é a chave de partição.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

Agora é possível imprimir os resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a>Recuperar um intervalo de entidades em uma partição

Se você não quiser consultar todas as entidades em uma partição, você pode especificar um intervalo, combinando o filtro chave de partição com um filtro de linha de chave. Aqui, você usa dois filtros para obter todas as entidades na partição "Buster" onde a chave de linha (nome) começa com uma letra anteriores "M" no alfabeto.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Agora é possível imprimir os resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a>Recuperar uma única entidade

Você pode escrever uma consulta para recuperar uma entidade única e específica. Aqui, você usa um `TableOperation` para especificar o cliente "Larry Buster". Em vez de uma coleção, você obtém um `Customer`. Especificar a chave de partição e a chave de linha em uma consulta é a maneira mais rápida para recuperar uma única entidade de serviço tabela.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Agora é possível imprimir os resultados:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a>Substituir uma entidade

Para atualizar uma entidade, recuperá-lo do serviço de tabela, modifique o objeto de entidade e, em seguida, salvar as alterações de volta para o serviço tabela usando um `Replace` operação. Isso faz com que a entidade a ser totalmente substituídos no servidor, a menos que a entidade do servidor foi alterado desde que foi recuperada, caso em que a operação falhará. Essa falha é para impedir que seu aplicativo inadvertidamente substituir alterações de outras fontes.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a>Inserir ou substituir uma entidade

Às vezes, você não sabe se a entidade existir na tabela ou não. E, em caso afirmativo, os valores atuais armazenados nela não são mais necessários. Você pode usar `InsertOrReplace` para criar a entidade ou substituí-lo se ele existir, independentemente de seu estado.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a>Consultar um subconjunto das propriedades de entidade

Uma consulta de tabela pode recuperar apenas algumas propriedades de uma entidade em vez de todos eles. Essa técnica, chamada de projeção, pode melhorar o desempenho, especialmente para grandes entidades. Aqui, você retornar endereços de email somente usando `DynamicTableEntity` e `EntityResolver`. Observe que projeção não é suportada no emulador de armazenamento local, para que este código seja executado somente quando você estiver usando uma conta do serviço de tabela.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a>Recuperar entidades nas páginas de forma assíncrona

Se você está lendo um grande número de entidades e deseja processá-las conforme eles são recuperados em vez de esperar todos eles retornar, você pode usar uma consulta segmentada. Aqui, você retorna resultados em páginas usando um fluxo de trabalho assíncrono para que a execução não é bloqueada enquanto você está esperando um grande conjunto de resultados a serem retornados.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

Você executar esse cálculo síncrona:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a>Excluir uma entidade

Você pode excluir uma entidade após recuperá-lo. Com a atualização de uma entidade, isso irá falhar se a entidade foi alterado desde que foi recuperado.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a>Excluir uma tabela

Você pode excluir uma tabela de uma conta de armazenamento. Uma tabela que foi excluída estará disponível para ser recriado por um período de tempo após a exclusão.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu as Noções básicas de armazenamento de tabela, siga estes links para saber mais sobre as tarefas mais complexas de armazenamento:

- [APIs de armazenamento do Azure para .NET](/dotnet/api/overview/azure/storage)
- [Provedor de tipo de armazenamento do Azure](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog da equipe do armazenamento do Azure](https://blogs.msdn.microsoft.com/b/windowsazurestorage/)
- [Configurar cadeias de conexão de armazenamento do Azure](/azure/storage/common/storage-configure-connection-string)
- [Introdução ao armazenamento de tabela do Azure no .NET](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)
