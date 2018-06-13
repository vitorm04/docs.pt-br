---
title: 'Introdução ao armazenamento de fila do Azure usando F #'
description: As filas do Azure fornecem entre componentes de aplicativos de mensagens confiável e assíncrona. Nuvem mensagens habilita os componentes do aplicativo para dimensionada de forma independente.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 14bbc657f965fc262d2a83b1fdf982fe5e75d55e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569406"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Introdução ao armazenamento de fila do Azure usando F # #

Armazenamento de fila do Azure fornece mensagens entre componentes de aplicativos de nuvem. Na criação de aplicativos para a escala, componentes de aplicativos geralmente são separados, para que eles possam ser redimensionados independentemente. Armazenamento de fila fornece mensagens assíncronas para a comunicação entre componentes de aplicativos, quer eles estejam em execução na nuvem, na área de trabalho, em um servidor local ou em um dispositivo móvel. Armazenamento de fila também oferece suporte a tarefas assíncronas de gerenciamento e criação de fluxos de trabalho de processo.

### <a name="about-this-tutorial"></a>Sobre este tutorial

Este tutorial mostra como escrever código F # para algumas tarefas comuns usando o armazenamento de fila do Azure. Tarefas abordadas incluem criando e excluindo filas e adicionar, ler e excluir mensagens da fila.

Para obter uma visão geral conceitual de armazenamento de fila, consulte [o guia do .NET para armazenamento de fila](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).
Você também precisará sua chave de acesso de armazenamento para esta conta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar Script F # e começar a F # interativo

Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #. Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `queues.fsx`, em seu ambiente de desenvolvimento do F #.

Em seguida, use uma [Gerenciador de pacote](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando um `#r`diretiva.

### <a name="add-namespace-declarations"></a>Adicione declarações de namespace

Adicione o seguinte `open` instruções na parte superior do `queues.fsx` arquivo:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Obter a cadeia de conexão

Você precisará de uma cadeia de caracteres de conexão de armazenamento do Azure para este tutorial. Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).

Para o tutorial, você vai inserir sua cadeia de caracteres de conexão no seu script, como este:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

No entanto, isso é **não recomendável** projetos para o real. Sua chave de conta de armazenamento é semelhante para a senha de raiz de sua conta de armazenamento. Sempre tenha cuidado para proteger a chave de conta de armazenamento. Evite distribuí-lo a outros usuários, codificar, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas. Você pode regenerar a chave usando o Portal do Azure se você acredita que ele pode ter sido comprometido.

Aplicativos para o real, a melhor maneira de manter sua cadeia de caracteres de conexão de armazenamento está em um arquivo de configuração. Para obter a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Usando o Gerenciador de configuração do Azure é opcional. Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de caracteres de conexão

Para analisar a cadeia de caracteres de conexão, use:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Isso retornará um `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Criar o cliente do serviço de fila

O `CloudQueueClient` classe permite que você recupere filas armazenadas no armazenamento de fila. Aqui está uma maneira de criar o cliente do serviço:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Agora você está pronto para escrever código que lê e grava dados no armazenamento de fila.

## <a name="create-a-queue"></a>Criar uma fila

Este exemplo mostra como criar uma fila se ela ainda não existir:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Inserir uma mensagem em uma fila

Para inserir uma mensagem em uma fila existente, primeiro crie um novo `CloudQueueMessage`. Em seguida, chame o `AddMessage` método. Um `CloudQueueMessage` podem ser criados de uma cadeia de caracteres (em formato UTF-8) ou um `byte` matriz, como esta:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Espiar a próxima mensagem

Você pode inspecionar a mensagem na frente de uma fila sem removê-la da fila, chamando o `PeekMessage` método.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Obter a próxima mensagem para processamento

Você pode recuperar a mensagem na frente de uma fila para processamento chamando o `GetMessage` método.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Você posteriormente indicar o processamento da mensagem usando `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Alterar o conteúdo de uma mensagem na fila

Você pode alterar o conteúdo de um mensagem recuperada no local na fila. Se a mensagem representa uma tarefa de trabalho, você poderá usar esse recurso para atualizar o status da tarefa. O código a seguir atualiza a mensagem da fila com novo conteúdo e define o tempo limite de visibilidade para estender outro 60 segundos. Isso salva o estado de trabalho associado à mensagem e dá ao cliente outro minuto para continuar a trabalhar na mensagem. Você pode usar essa técnica para rastrear fluxos de trabalho de várias etapas em fila de mensagens, sem a necessidade de recomeçar desde o início, se uma etapa de processamento falhar devido uma falha de hardware ou software. Normalmente, você mantém uma contagem de tentativa e se a mensagem é repetida mais do que algumas vezes, você deve excluí-lo. Isso protege contra uma mensagem que dispara um erro de aplicativo sempre que ela é processada.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Eliminação da fila a próxima mensagem

Seu código eliminação enfileira uma mensagem de uma fila em duas etapas. Quando você chama `GetMessage`, obter a próxima mensagem em uma fila. Uma mensagem retornada de `GetMessage` se torna invisível para qualquer outro código de leitura de mensagens dessa fila. Por padrão, essa mensagem permanece invisível para 30 segundos. Para concluir a remoção de mensagem da fila, você também deve chamar `DeleteMessage`. Esse processo de duas etapas de remoção de uma mensagem garante que, se seu código falhar ao processar uma mensagem devido à falha de hardware ou software, outra instância do seu código pode obter a mesma mensagem de erro e tente novamente. Seu código chama `DeleteMessage` logo depois que a mensagem foi processada.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Usar fluxos de trabalho assíncrono com APIs comuns de armazenamento de fila

Este exemplo mostra como usar um fluxo de trabalho assíncrono com APIs comuns de armazenamento de fila.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Opções adicionais para a eliminação da fila de mensagens

Há duas maneiras que você pode personalizar a recuperação de mensagens de uma fila.
Primeiro, você pode obter um lote de mensagens (até 32). Em seguida, você pode definir um tempo limite de invisibilidade maiores ou menores, permitindo que o seu código mais ou menos tempo para processar completamente cada mensagem. O seguinte exemplo de código usa `GetMessages` obter 20 mensagens em uma chamada e, em seguida, processa cada mensagem. Ele também define o tempo limite de invisibilidade de cinco minutos para cada mensagem. Observe que inicia de cinco minutos para todas as mensagens ao mesmo tempo, após ter de 5 minutos passados desde a chamada para `GetMessages`, qualquer mensagem que não foram excluídas se tornará visível novamente.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Obter o comprimento da fila

Você pode obter uma estimativa do número de mensagens em uma fila. O `FetchAttributes` método solicita que o serviço de fila para recuperar os atributos de fila, incluindo a contagem de mensagens. O `ApproximateMessageCount` propriedade retorna o último valor recuperado pelo `FetchAttributes` método sem chamar o serviço de fila.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Excluir uma fila

Para excluir uma fila e todas as mensagens contidas nela, chame o `Delete` método no objeto de fila.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu as Noções básicas de armazenamento de fila, siga estes links para saber mais sobre as tarefas mais complexas de armazenamento.

- [APIs de armazenamento do Azure para .NET](/dotnet/api/overview/azure/storage)
- [Provedor de tipo de armazenamento do Azure](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog da equipe do armazenamento do Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Configurar cadeias de conexão de armazenamento do Azure](/azure/storage/common/storage-configure-connection-string)
- [Referência da API REST de serviços de armazenamento do Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
