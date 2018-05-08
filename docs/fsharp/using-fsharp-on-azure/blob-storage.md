---
title: 'Introdução ao armazenamento de BLOBs do Azure usando F #'
description: Armazene dados não estruturados em nuvem com o armazenamento de BLOBs do Azure.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 3ab08154bd374896fce777c7c373204c9048b65c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Introdução ao armazenamento de BLOBs do Azure usando F # #

O Armazenamento de Blobs do Azure é um serviço que armazena dados não estruturados na nuvem como objetos/blobs. O Armazenamento de Blobs pode armazenar qualquer tipo de texto ou dados binários, como um documento, um arquivo de mídia ou um instalador de aplicativo. O Armazenamento de Blobs também é conhecido como armazenamento de objeto.

Este artigo mostra como executar tarefas comuns usando o armazenamento de Blob. Os exemplos são escritos usando F # usando a biblioteca de cliente de armazenamento do Azure para .NET. As tarefas abordadas incluem como carregar, listar, baixar e excluir blobs.

Para obter uma visão geral conceitual do armazenamento de blob, consulte [o guia do .NET para armazenamento de blob](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account). Você também precisará sua chave de acesso de armazenamento para esta conta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar Script F # e começar a F # interativo

Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #. Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `blobs.fsx`, em seu ambiente de desenvolvimento do F #.

Em seguida, use uma [Gerenciador de pacote](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` e `Microsoft.WindowsAzure.ConfigurationManager` pacotes e referência `WindowsAzure.Storage.dll` e `Microsoft.WindowsAzure.Configuration.dll` em seu script usando um `#r` diretiva.

### <a name="add-namespace-declarations"></a>Adicione declarações de namespace

Adicione o seguinte `open` instruções na parte superior do `blobs.fsx` arquivo:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obter a cadeia de conexão

Você precisa de uma cadeia de caracteres de conexão de armazenamento do Azure para este tutorial. Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).

Para o tutorial, você pode inserir sua cadeia de caracteres de conexão no seu script, como este:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

No entanto, isso é **não recomendável** projetos para o real. Sua chave de conta de armazenamento é semelhante para a senha de raiz de sua conta de armazenamento. Sempre tenha cuidado para proteger a chave de conta de armazenamento. Evite distribuí-lo a outros usuários, codificar, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas. Você pode regenerar a chave usando o Portal do Azure se você acredita que ele pode ter sido comprometido.

Aplicativos para o real, a melhor maneira de manter sua cadeia de caracteres de conexão de armazenamento está em um arquivo de configuração. Para obter a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Usando o Gerenciador de configuração do Azure é opcional. Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de caracteres de conexão

Para analisar a cadeia de caracteres de conexão, use:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Isso retorna um `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Criar alguns dados fictícios locais

Antes de começar, crie alguns dados fictícios de locais no diretório do nosso script. Mais tarde você carregar esses dados.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Criar o cliente do serviço Blob

O `CloudBlobClient` tipo permite que você recupere contêineres e blobs armazenados no armazenamento de Blob. Aqui está uma maneira de criar o cliente do serviço:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Agora você está pronto para escrever código que lê e grava dados no armazenamento de Blob.

## <a name="create-a-container"></a>Criar um contêiner

Este exemplo mostra como criar um contêiner se ele ainda não existir:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Por padrão, o novo contêiner é privado, o que significa que você deve especificar a chave de acesso de armazenamento para baixar blobs desse contêiner. Se você quiser disponibilizar os arquivos dentro do contêiner a todos os usuários, você pode definir o contêiner pública usando o seguinte código:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Qualquer pessoa na Internet pode ver os blobs em um contêiner público, mas você pode modificar ou excluí-los somente se você tiver a chave de acesso da conta apropriada ou uma assinatura de acesso compartilhado.

## <a name="upload-a-blob-into-a-container"></a>Carregar um blob em um contêiner

Armazenamento de BLOBs do Azure oferece suporte a blobs de blocos e blobs de página. Na maioria dos casos, um blob de bloco é o tipo recomendado para usar.

Para carregar um arquivo para um blob de bloco, obtenha uma referência de contêiner e usá-lo para obter uma referência de blob de bloco. Quando você tem uma referência de blob, você pode carregar qualquer fluxo de dados a ele ao chamar o `UploadFromFile` método. Essa operação cria o blob se ele anteriormente não existe ou substituí-lo se ele existir.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Listar os blobs em um contêiner

Para listar os blobs em um contêiner, primeiro obtenha uma referência de contêiner. Você pode usar o contêiner `ListBlobs` método para recuperar os blobs e/ou diretórios dentro dele. Para acessar um conjunto sofisticado de propriedades e métodos para uma retornado `IListBlobItem`, você deve convertê-lo para um `CloudBlockBlob`, `CloudPageBlob`, ou `CloudBlobDirectory` objeto. Se o tipo é desconhecido, você pode usar uma verificação de tipo para determinar qual converter a. O código a seguir demonstra como recuperar e o URI de cada item de saída de `mydata` contêiner:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Você também pode blobs de nome com informações de caminho em seus nomes. Isso cria uma estrutura de diretório virtual que você pode organizar e percorrer como faria com um sistema de arquivos tradicional. Observe que a estrutura de diretório é somente virtual - os somente os recursos disponíveis no armazenamento de Blob são contêineres e blobs. No entanto, a biblioteca de cliente de armazenamento oferece uma `CloudBlobDirectory` objeto para fazer referência a um diretório virtual e simplificar o processo de trabalho com blobs são organizados dessa maneira.

Por exemplo, considere o seguinte conjunto de blobs de bloco em um contêiner denominado `photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*

Quando você chama `ListBlobs` em um contêiner (como o exemplo acima), uma lista hierárquica é retornada. Se ele contém ambos `CloudBlobDirectory` e `CloudBlockBlob` objetos, representando os diretórios e blobs no contêiner, respectivamente, em seguida, a saída resultante é semelhante a este:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Opcionalmente, você pode definir o `UseFlatBlobListing` parâmetro o `ListBlobs` método `true`. Nesse caso, cada blob no contêiner é retornado como um `CloudBlockBlob` objeto. A chamada para `ListBlobs` para retornar uma lista simples tem esta aparência:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

e, dependendo do conteúdo atual do seu contêiner, os resultados ter esta aparência:

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a>Baixar blobs

Para baixar blobs, primeiro recuperar uma referência de blob e, em seguida, chamar o `DownloadToStream` método. O exemplo a seguir usa o `DownloadToStream` método para transferir o conteúdo do blob para um objeto de fluxo, em seguida, você pode persistir para um arquivo local.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Você também pode usar o `DownloadToStream` método para baixar o conteúdo de um blob como uma cadeia de caracteres de texto.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Exclua os blobs

Para excluir um blob, primeiro obter uma referência de blob e, em seguida, chamar o `Delete` método nele.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Listar blobs em páginas de forma assíncrona

Se estiver listando um grande número de blobs ou para controlar o número de resultados de que retorno em uma operação de listagem, você pode listar blobs em páginas de resultados. Este exemplo mostra como retornar resultados nas páginas de forma assíncrona, para que a execução não está bloqueada enquanto aguarda para retornar um grande conjunto de resultados.

Este exemplo mostra uma simples listagem do blob, mas você também pode executar uma lista hierárquica, definindo o `useFlatBlobListing` parâmetro o `ListBlobsSegmentedAsync` método `false`.

O exemplo define um método assíncrono, usando um `async` bloco. O ``let!`` palavra-chave suspende a execução do método exemplo até que a lista de conclusão da tarefa.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Agora, podemos usar esta rotina assíncrona da seguinte maneira. Primeiro, carregue alguns dados fictícios (usando o arquivo local criado anteriormente neste tutorial).

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Agora, chame a rotina. Você usa ``Async.RunSynchronously`` para forçar a execução da operação assíncrona.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Gravar um blob de acréscimo

Um blob de acréscimo é otimizado para operações de acréscimo, como o registro em log. Como um blob de bloco, um blob de acréscimo é composto por blocos, mas quando você adiciona um novo bloco a um blob de acréscimo, ele sempre é adicionado ao final do blob. Você não pode atualizar ou excluir um bloco existente em um blob de acréscimo. As IDs do bloco para um blob de acréscimo não são expostos como eles são para um blob de bloco.

Cada bloco em um blob de acréscimo pode ter um tamanho diferente, até um máximo de 4 MB, e um blob de acréscimo pode incluir até 50.000 blocos. O tamanho máximo de um blob de acréscimo, portanto, é um pouco mais de 195 GB (4 MB X 50.000 blocos).

O exemplo a seguir cria um novo blob de acréscimo e acrescenta alguns dados a ele, com uma simulação de uma operação de log simples.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Consulte [Compreendendo Blobs de bloco, Blobs de página e Blobs de acréscimo](https://msdn.microsoft.com/library/azure/ee691964.aspx) para obter mais informações sobre as diferenças entre os três tipos de blobs.

## <a name="concurrent-access"></a>Acesso simultâneo

Para dar suporte a acesso simultâneo a um blob de vários clientes ou várias instâncias do processo, você pode usar **ETags** ou **concessões**.

* **ETag** -fornece uma maneira de detectar que o blob ou contêiner foi modificado por outro processo

* **Concessão** -fornece uma maneira de obter exclusivo, renovável, gravação ou exclusão acesso a um blob para um período de tempo

Para obter mais informações, consulte [gerenciamento de simultaneidade no armazenamento do Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Contêineres de nomenclatura

Cada blob no armazenamento do Azure deve residir em um contêiner. O contêiner faz parte do nome do blob. Por exemplo, `mydata` é o nome do contêiner esses URIs do blob de exemplo:

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Um nome de contêiner deve ser um nome DNS válido, em conformidade com as regras de nomenclatura a seguir:

1. Os nomes de contêiner devem começar com uma letra ou número e podem conter apenas letras, números e o caractere de traço (-).
1. Cada caractere de traço (-) deve ser imediatamente precedido e seguido por uma letra ou número; traços consecutivos não são permitidos em nomes de contêiner.
1. Todas as letras em um nome de contêiner devem estar em minúsculas.
1. Nomes de contêiner devem ter de 3 a 63 caracteres.

Observe que o nome de um contêiner deve sempre ser minúsculas. Se você incluir uma letra maiuscula em um nome de contêiner ou viola o regras de nomenclatura do contêiner, você poderá receber um erro 400 (solicitação incorreta).

## <a name="managing-security-for-blobs"></a>Gerenciamento de segurança para blobs

Por padrão, o armazenamento do Azure mantém seus dados seguros, limitando o acesso ao proprietário da conta, que está em posse das chaves de acesso de conta. Quando você precisa compartilhar dados blob em sua conta de armazenamento, é importante fazer isso sem comprometer a segurança de suas chaves de acesso da conta. Além disso, você pode criptografar os dados de blob para garantir que ele é seguro vai através da rede e no armazenamento do Azure.

### <a name="controlling-access-to-blob-data"></a>Controlando o acesso a dados de blob

Por padrão, os dados de blob na conta de armazenamento são acessíveis somente para o proprietário da conta de armazenamento. Autenticar solicitações em relação ao armazenamento de Blob exige a chave de acesso de conta por padrão. No entanto, você talvez queira disponibilizar determinados dados de blob para outros usuários.

Para obter detalhes sobre como controlar o acesso ao armazenamento de blob, consulte [o guia de .NET para a seção de armazenamento de blob no controle de acesso](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).


### <a name="encrypting-blob-data"></a>Criptografia de dados de blob

Armazenamento do Azure oferece suporte à criptografia de dados de blob no cliente e no servidor.

Para obter detalhes sobre como criptografar dados blob, consulte [guia .NET para a seção de armazenamento de blob em criptografia](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu as Noções básicas do armazenamento de Blob, siga estes links para obter mais informações.

### <a name="tools"></a>Ferramentas
- [F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) um F # tipo de provedor que pode ser usado para explorar os ativos de Blob, tabela e fila de armazenamento do Azure e aplicar facilmente operações CRUD neles.
- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) uma API de F # para usar o serviço de armazenamento de tabela do Microsoft Azure
- [Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) é um aplicativo autônomo gratuito da Microsoft que lhe permite trabalhar visualmente com dados de armazenamento do Azure no Windows, OS X e Linux.

### <a name="blob-storage-reference"></a>Referência do armazenamento de blob

- [APIs de armazenamento do Azure para .NET](/dotnet/api/overview/azure/storage)
- [Referência da API REST de serviços de armazenamento do Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Guias de relacionados

- [Introdução ao armazenamento de BLOBs do Azure em c#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Transferência de dados com o utilitário de linha de comando AzCopy no Windows](/azure/storage/common/storage-use-azcopy)
- [Transferência de dados com o utilitário de linha de comando AzCopy no Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Configurar cadeias de conexão de armazenamento do Azure](/azure/storage/common/storage-configure-connection-string)
- [Blog da equipe do armazenamento do Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
