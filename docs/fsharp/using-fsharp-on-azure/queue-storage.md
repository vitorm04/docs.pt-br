---
title: Introdução ao uso do armazenamento de filas do AzureF#
description: As filas do Azure fornecem uma mensagem assíncrona e confiável entre componentes do aplicativo. Permite que mensagens de nuvem os componentes do aplicativo para dimensionar de modo independente.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 58a46dfe905a32be77a13d11df8f0544546ea0ed
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974270"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Introdução ao armazenamento de filas do Azure usando F\#

O armazenamento de filas do Azure fornece mensagens entre componentes de aplicativos na nuvem. Na criação de aplicativos para escala, componentes de aplicativos geralmente são desassociados, para que possam ser dimensionados independentemente. Armazenamento de filas fornece mensagens assíncronas para a comunicação entre componentes de aplicativos, se eles estão em execução na nuvem, na área de trabalho, em um servidor local ou em um dispositivo móvel. O armazenamento de fila também dá suporte a gerenciamento de tarefas assíncronas e criação de fluxos de trabalho do processo.

### <a name="about-this-tutorial"></a>Sobre este tutorial

Este tutorial mostra como escrever F# código para algumas tarefas comuns usando o armazenamento de filas do Azure. Tarefas abordadas incluem criar e excluir filas e adicionando, ler e excluir mensagens da fila.

Para obter uma visão geral conceitual do armazenamento de filas, consulte [o guia do .NET para o armazenamento de fila](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).
Você também precisará sua chave de acesso de armazenamento para esta conta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar um F# Script e iniciar F# interativo

Os exemplos neste artigo podem ser usados em qualquer um uma F# aplicativo ou um F# script. Para criar um F# script, crie um arquivo com o `.fsx` extensão, por exemplo `queues.fsx`, no seu F# ambiente de desenvolvimento.

Em seguida, use um [Gerenciador de pacotes](package-management.md) tais como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando um `#r`diretiva.

### <a name="add-namespace-declarations"></a>Adicionar declarações de namespace

Adicione o seguinte `open` as instruções na parte superior do `queues.fsx` arquivo:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Obter a cadeia de conexão

Você precisará de uma cadeia de caracteres de conexão do armazenamento do Azure para este tutorial. Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).

Para o tutorial, você irá inserir a cadeia de conexão no seu script, como este:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

No entanto, isso é **não recomendável** para projetos reais. Sua chave de conta de armazenamento é semelhante para a senha raiz para sua conta de armazenamento. Sempre tenha cuidado para proteger sua chave de conta de armazenamento. Evite distribuí-la a outros usuários, embuti-la, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas. Você pode regenerar a chave usando o Portal do Azure se você acredita que pode ter sido comprometida.

Aplicativos para o real, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração. Para buscar a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Usando o Gerenciador de configuração do Azure é opcional. Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de conexão

Para analisar a cadeia de caracteres de conexão, use:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Isso retornará um `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Criar o cliente do serviço fila

O `CloudQueueClient` classe permite que você recupere as filas armazenadas no armazenamento de filas. Aqui está uma maneira de criar o cliente do serviço:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Agora você está pronto para escrever um código que lê e grava dados no armazenamento de fila.

## <a name="create-a-queue"></a>Criar uma fila

Este exemplo mostra como criar uma fila se ela ainda não existir:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Inserir uma mensagem em uma fila

Para inserir uma mensagem em uma fila existente, primeiro crie uma nova `CloudQueueMessage`. Em seguida, chame o `AddMessage` método. Um `CloudQueueMessage` pode ser criada a partir uma cadeia de caracteres (em formato UTF-8) ou um `byte` matriz, como esta:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Espiar a próxima mensagem

Você pode inspecionar a mensagem na frente de uma fila sem removê-la da fila, chamando o `PeekMessage` método.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Obter a próxima mensagem para processamento

Você pode recuperar a mensagem na frente de uma fila para processamento, chamando o `GetMessage` método.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Você posteriormente indica o processamento bem-sucedido da mensagem usando `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Alterar o conteúdo de uma mensagem na fila

Você pode alterar o conteúdo de um mensagem recuperada in-loco na fila. Se a mensagem representa uma tarefa de trabalho, você pode usar esse recurso para atualizar o status da tarefa. O código a seguir atualiza a mensagem da fila com novo conteúdo e define o tempo limite de visibilidade para estender mais 60 segundos. Isso salva o estado do trabalho associado à mensagem e dá ao cliente mais um minuto para continuar trabalhando na mensagem. Você pode usar essa técnica para acompanhar fluxos de trabalho de várias etapas em mensagens em fila, sem ter que recomeçar desde o início, se uma etapa de processamento falhar devido uma falha de hardware ou software. Normalmente, você mantém uma contagem de repetições, e se a mensagem for repetida mais do que algumas vezes, você deve excluí-lo. Isso protege contra uma mensagem que dispara um erro de aplicativo cada vez que ela é processada.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Remover a próxima mensagem da fila

Seu código retira uma mensagem de uma fila em duas etapas. Quando você chama `GetMessage`, você receberá a próxima mensagem em uma fila. Uma mensagem retornada de `GetMessage` torna-se invisível para qualquer outro código que lê mensagens nessa fila. Por padrão, essa mensagem permanece invisível por 30 segundos. Para concluir a remoção da mensagem da fila, você também deve chamar `DeleteMessage`. Esse processo em duas etapas de remover uma mensagem garante que, se seu código falhar ao processar uma mensagem devido à falha de hardware ou software, outra instância do seu código pode receber a mesma mensagem e tente novamente. Seu código chama `DeleteMessage` logo depois que a mensagem foi processada.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Usar fluxos de trabalho assíncronos com APIs comuns de armazenamento de fila

Este exemplo mostra como usar um fluxo de trabalho assíncrono com APIs comuns de armazenamento de fila.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Opções adicionais para remover mensagens da fila

Há duas maneiras de personalizar a recuperação da mensagem de uma fila.
Primeiro, você pode obter um lote de mensagens (até 32). Em segundo lugar, você pode definir um tempo limite de invisibilidade mais longo ou mais curto, permitindo que seu código mais ou menos tempo para processar totalmente cada mensagem. O seguinte exemplo de código usa `GetMessages` para obter 20 mensagens em uma chamada e, em seguida, processa cada mensagem. Ele também define o tempo limite de invisibilidade de cinco minutos para cada mensagem. Observe que os 5 minutos começam para todas as mensagens ao mesmo tempo, portanto, depois de 5 minutos passados desde a chamada para `GetMessages`, todas as mensagens que não tenham sido excluídas se tornarão visíveis novamente.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Obter o comprimento da fila

Você pode obter uma estimativa do número de mensagens em uma fila. O `FetchAttributes` método solicita que o serviço fila recupere os atributos da fila, incluindo a contagem de mensagens. O `ApproximateMessageCount` propriedade retorna o último valor recuperado pelo `FetchAttributes` método, sem chamar o serviço de fila.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Excluir uma fila

Para excluir uma fila e todas as mensagens contidas nela, chame o `Delete` método no objeto de fila.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu os conceitos básicos do armazenamento de filas, siga estes links para saber mais sobre tarefas de armazenamento mais complexas.

- [APIs de armazenamento do Azure para .NET](/dotnet/api/overview/azure/storage)
- [Provedor de tipos de armazenamento do Azure](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog da equipe do armazenamento do Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Configurar cadeias de conexão do armazenamento do Azure](/azure/storage/common/storage-configure-connection-string)
- [Referência da API REST de serviços de armazenamento do Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
