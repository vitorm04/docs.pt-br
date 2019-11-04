---
title: Introdução ao armazenamento de Filas do Azure usando F#
description: As filas do Azure fornecem mensagens confiáveis e assíncronas entre os componentes do aplicativo. O Cloud Messaging permite que os componentes do aplicativo sejam dimensionados de forma independente.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: a09cbdd4b995e34177c110ce91b02162bb19dfa8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423853"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Introdução ao armazenamento de filas do Azure usando o F\#

O armazenamento de filas do Azure fornece mensagens de nuvem entre componentes do aplicativo. Na criação de aplicativos para escala, os componentes do aplicativo geralmente são desacoplados, para que possam ser dimensionados de forma independente. O armazenamento de filas fornece mensagens assíncronas para comunicação entre componentes de aplicativos, estejam eles em execução na nuvem, na área de trabalho, em um servidor local ou em um dispositivo móvel. O armazenamento de filas também dá suporte ao gerenciamento de tarefas assíncronas e à criação de fluxos de trabalho

### <a name="about-this-tutorial"></a>Sobre este tutorial

Este tutorial mostra como escrever F# código para algumas tarefas comuns usando o armazenamento de filas do Azure. As tarefas cobertas incluem criar e excluir filas e adicionar, ler e excluir mensagens da fila.

Para obter uma visão geral conceitual do armazenamento de filas, consulte [o guia .net para armazenamento de filas](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Prerequisites

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).
Você também precisará da sua chave de acesso de armazenamento para essa conta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar um F# script e iniciar F# interativo

Os exemplos neste artigo podem ser usados em um F# aplicativo ou um F# script. Para criar um F# script, crie um arquivo com a extensão `.fsx`, por exemplo, `queues.fsx`, em F# seu ambiente de desenvolvimento.

Em seguida, use um [Gerenciador de pacotes](package-management.md) , como [paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) , para instalar o pacote `WindowsAzure.Storage` e referência `WindowsAzure.Storage.dll` em seu script usando uma diretiva `#r`.

### <a name="add-namespace-declarations"></a>Adicionar declarações de namespace

Adicione as seguintes instruções de `open` à parte superior do arquivo de `queues.fsx`:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Obter sua cadeia de conexão

Você precisará de uma cadeia de conexão de armazenamento do Azure para este tutorial. Para obter mais informações sobre cadeias de conexão, consulte [Configurar cadeias de conexão de armazenamento](/azure/storage/storage-configure-connection-string).

Para o tutorial, você inserirá sua cadeia de conexão em seu script, da seguinte maneira:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

No entanto, isso **não é recomendado** para projetos reais. Sua chave de conta de armazenamento é semelhante à senha raiz da sua conta de armazenamento. Sempre tenha cuidado para proteger sua chave de conta de armazenamento. Evite distribuí-lo a outros usuários, embuti-lo em código ou salvá-lo em um arquivo de texto sem formatação que seja acessível para outras pessoas. Você pode regenerar sua chave usando o portal do Azure se acreditar que ele pode ter sido comprometido.

Para aplicativos reais, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração. Para buscar a cadeia de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Usar o Configuration Manager do Azure é opcional. Você também pode usar uma API como o tipo de `ConfigurationManager` do .NET Framework.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de conexão

Para analisar a cadeia de conexão, use:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Isso retornará um `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Criar o cliente serviço Fila

A classe `CloudQueueClient` permite que você recupere filas armazenadas no armazenamento de filas. Aqui está uma maneira de criar o cliente de serviço:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Agora você está pronto para escrever código que lê e grava dados no armazenamento de filas.

## <a name="create-a-queue"></a>Criar uma fila

Este exemplo mostra como criar uma fila, caso ela ainda não exista:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Inserir uma mensagem em uma fila

Para inserir uma mensagem em uma fila existente, primeiro crie uma nova `CloudQueueMessage`. Em seguida, chame o método `AddMessage`. Um `CloudQueueMessage` pode ser criado por meio de uma cadeia de caracteres (em formato UTF-8) ou de uma matriz de `byte`, como esta:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Inspecionar a próxima mensagem

Você pode inspecionar a mensagem na frente de uma fila, sem removê-la da fila, chamando o método `PeekMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Obter a próxima mensagem para processamento

Você pode recuperar a mensagem na frente de uma fila para processamento chamando o método `GetMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Posteriormente, você indicará o processamento bem-sucedido da mensagem usando `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Alterar o conteúdo de uma mensagem em fila

Você pode alterar o conteúdo de uma mensagem recuperada in-loco na fila. Se a mensagem representar uma tarefa de trabalho, você poderá usar esse recurso para atualizar o status da tarefa de trabalho. O código a seguir atualiza a mensagem da fila com novo conteúdo e define o tempo limite de visibilidade para estender outros 60 segundos. Isso salva o estado do trabalho associado à mensagem e dá ao cliente outro minuto para continuar a trabalhar na mensagem. Você poderia usar essa técnica para rastrear fluxos de trabalho de várias etapas em mensagens de fila, sem precisar começar desde o início se uma etapa de processamento falhar devido a uma falha de hardware ou de software. Normalmente, você manteria uma contagem de repetições também e, se a mensagem for repetida mais do que um número de vezes, você a excluiria. Isso protege contra uma mensagem que dispara um erro de aplicativo cada vez que é processado.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Remover a próxima mensagem da fila

Seu código retira a fila de uma mensagem de uma fila em duas etapas. Ao chamar `GetMessage`, você receberá a próxima mensagem em uma fila. Uma mensagem retornada de `GetMessage` torna-se invisível para qualquer outra mensagem de leitura de código dessa fila. Por padrão, essa mensagem permanece invisível por 30 segundos. Para concluir a remoção da mensagem da fila, você também deve chamar `DeleteMessage`. Esse processo de duas etapas para remover uma mensagem garante que, se o código não processar uma mensagem devido a uma falha de hardware ou de software, outra instância do seu código poderá obter a mesma mensagem e tentar novamente. Seu código chama `DeleteMessage` logo após a mensagem ser processada.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Usar fluxos de trabalho assíncronos com APIs de armazenamento de fila comuns

Este exemplo mostra como usar um fluxo de trabalho assíncrono com APIs de armazenamento de fila comuns.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Opções adicionais para a remoção de mensagens da fila

Há duas maneiras de personalizar a recuperação de mensagens de uma fila.
Primeiro, você pode obter um lote de mensagens (até 32). Em segundo lugar, você pode definir um tempo limite de invisibilidade mais longo ou mais curto, permitindo que seu código tenha mais ou menos tempo para processar totalmente cada mensagem. O exemplo de código a seguir usa `GetMessages` para obter 20 mensagens em uma chamada e, em seguida, processa cada mensagem. Ele também define o tempo limite de invisibilidade para cinco minutos para cada mensagem. Observe que os 5 minutos começam para todas as mensagens ao mesmo tempo, portanto, depois de 5 minutos desde a chamada para `GetMessages`, todas as mensagens que não foram excluídas ficarão visíveis novamente.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Obter o comprimento da fila

Você pode obter uma estimativa do número de mensagens em uma fila. O método `FetchAttributes` solicita que o serviço Fila recupere os atributos da fila, incluindo a contagem de mensagens. A propriedade `ApproximateMessageCount` retorna o último valor recuperado pelo método `FetchAttributes`, sem chamar o serviço Fila.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Excluir uma fila

Para excluir uma fila e todas as mensagens contidas nela, chame o método `Delete` no objeto Queue.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu os conceitos básicos do armazenamento de filas, siga estes links para saber mais sobre tarefas de armazenamento mais complexas.

- [APIs de armazenamento do Azure para .NET](/dotnet/api/overview/azure/storage)
- [Provedor de tipo de armazenamento do Azure](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog da equipe de armazenamento do Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Configurar cadeias de conexão do armazenamento do Azure](/azure/storage/common/storage-configure-connection-string)
- [Referência da API REST dos serviços de armazenamento do Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
