---
title: Introdução ao uso do armazenamento de BLOBs do AzureF#
description: Store dados não estruturados na nuvem com o armazenamento de BLOBs do Azure.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e38f58fefa63f922bcb1a78254249a3626bfac43
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981901"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Introdução ao armazenamento de BLOBs do Azure usando F\#

O Armazenamento de Blobs do Azure é um serviço que armazena dados não estruturados na nuvem como objetos/blobs. O Armazenamento de Blobs pode armazenar qualquer tipo de texto ou dados binários, como um documento, um arquivo de mídia ou um instalador de aplicativo. O Armazenamento de Blobs também é conhecido como armazenamento de objeto.

Este artigo mostra como executar tarefas comuns usando o armazenamento de BLOBs. Os exemplos são escritos usando F# usando a biblioteca de cliente de armazenamento do Azure para .NET. Tarefas abordadas incluem como carregar, listar, baixar e excluir blobs.

Para obter uma visão geral conceitual do armazenamento de blob, consulte [o guia do .NET para o armazenamento de BLOBs](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account). Você também precisa sua chave de acesso de armazenamento para esta conta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar um F# Script e iniciar F# interativo

Os exemplos neste artigo podem ser usados em qualquer um uma F# aplicativo ou um F# script. Para criar um F# script, crie um arquivo com o `.fsx` extensão, por exemplo `blobs.fsx`, no seu F# ambiente de desenvolvimento.

Em seguida, use uma [Gerenciador de pacotes](package-management.md) tais como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` e `Microsoft.WindowsAzure.ConfigurationManager` referência e pacotes `WindowsAzure.Storage.dll` e `Microsoft.WindowsAzure.Configuration.dll` em seu script usando um `#r` diretiva.

### <a name="add-namespace-declarations"></a>Adicionar declarações de namespace

Adicione o seguinte `open` as instruções na parte superior do `blobs.fsx` arquivo:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obter a cadeia de conexão

Você precisa de uma cadeia de caracteres de conexão do armazenamento do Azure para este tutorial. Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).

Para o tutorial, você pode inserir a cadeia de conexão no seu script, como este:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

No entanto, isso é **não recomendável** para projetos reais. Sua chave de conta de armazenamento é semelhante para a senha raiz para sua conta de armazenamento. Sempre tenha cuidado para proteger sua chave de conta de armazenamento. Evite distribuí-la a outros usuários, embuti-la, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas. Você pode regenerar a chave usando o Portal do Azure se você acredita que pode ter sido comprometida.

Aplicativos para o real, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração. Para buscar a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Usando o Gerenciador de configuração do Azure é opcional. Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de conexão

Para analisar a cadeia de caracteres de conexão, use:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Isso retorna um `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Criar alguns dados fictícios locais

Antes de começar, crie alguns dados fictícios de locais no diretório do nosso script. Mais tarde você pode carregar esses dados.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Criar o cliente do serviço Blob

O `CloudBlobClient` tipo permite que você recupere contêineres e blobs armazenados no armazenamento de BLOBs. Aqui está uma maneira de criar o cliente do serviço:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Agora você está pronto para escrever um código que lê e grava dados no armazenamento de Blob.

## <a name="create-a-container"></a>Criar um contêiner

Este exemplo mostra como criar um contêiner se ele ainda não existir:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Por padrão, o novo contêiner é privado, o que significa que você deve especificar sua chave de acesso de armazenamento para baixar blobs desse contêiner. Se você quiser tornar os arquivos dentro do contêiner disponíveis a todos, você pode definir o contêiner como público usando o seguinte código:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Qualquer pessoa na Internet pode ver blobs em um contêiner público, mas você pode modificar ou excluí-los somente se você tiver a chave de acesso da conta apropriada ou uma assinatura de acesso compartilhado.

## <a name="upload-a-blob-into-a-container"></a>Carregar um blob em um contêiner

O armazenamento de BLOBs do Azure dá suporte a blobs de blocos e blobs de página. Na maioria dos casos, um blob de blocos é o tipo recomendado.

Para carregar um arquivo em um blob de blocos, obtenha uma referência de contêiner e usá-lo para obter uma referência de blob de bloco. Quando você tiver uma referência de blob, você pode carregar qualquer fluxo de dados nele chamando o `UploadFromFile` método. Esta operação criará o blob se ele anteriormente não existir ou substituí-lo se ele existir.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Listar os blobs em um contêiner

Para listar os blobs em um contêiner, primeiro obtenha uma referência de contêiner. Você pode usar o contêiner `ListBlobs` método para recuperar os blobs e/ou diretórios dentro dele. Para acessar o conjunto avançado de propriedades e métodos para um `IListBlobItem`, você deve convertê-lo em um `CloudBlockBlob`, `CloudPageBlob`, ou `CloudBlobDirectory` objeto. Se o tipo for desconhecido, você pode usar uma verificação de tipo para determinar em qual convertê-lo. O código a seguir demonstra como recuperar e apresentar a URI de cada item no `mydata` contêiner:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Você também pode blobs de nome com informações de caminho em seus nomes. Isso cria uma estrutura de diretório virtual que você pode organizar e percorrer como faria com um sistema de arquivos tradicional. Observe que a estrutura do diretório é virtual apenas - os somente os recursos disponíveis no armazenamento de BLOBs são contêineres e blobs. No entanto, a biblioteca de cliente de armazenamento oferece um `CloudBlobDirectory` objeto para fazer referência a um diretório virtual e simplificar o processo de trabalhar com blobs organizados dessa maneira.

Por exemplo, considere o seguinte conjunto de blobs de blocos em um contêiner denominado `photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*

Quando você chama `ListBlobs` em um contêiner (como no exemplo acima), uma listagem hierárquica é retornada. Se ele contiver ambos `CloudBlobDirectory` e `CloudBlockBlob` objetos, que representam os diretórios e blobs no contêiner, respectivamente, em seguida, a saída resultante é semelhante a esta:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Opcionalmente, você pode definir as `UseFlatBlobListing` parâmetro do `ListBlobs` método `true`. Nesse caso, todos os BLOBs no contêiner é retornado como um `CloudBlockBlob` objeto. A chamada para `ListBlobs` para retornar uma lista simples tem esta aparência:

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

Para baixar blobs, primeiro recupere uma referência de blob e, em seguida, chamar o `DownloadToStream` método. O exemplo a seguir usa o `DownloadToStream` método para transferir o conteúdo do blob para um objeto de fluxo que você pode persistir em um arquivo local.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Você também pode usar o `DownloadToStream` método para baixar o conteúdo de um blob como uma cadeia de caracteres de texto.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Excluir blobs

Para excluir um blob, primeiro obtenha uma referência de blob e, em seguida, chame o `Delete` método nele.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Listar blobs em páginas de forma assíncrona

Se você está listando uma grande quantidade de blobs, ou você deseja controlar o número de resultados retornados em uma operação de listagem, você pode listar os blobs em páginas de resultados. Este exemplo mostra como retornar resultados nas páginas de forma assíncrona, para que a execução não fique bloqueada enquanto espera para retornar um grande conjunto de resultados.

Este exemplo mostra um listagem de blob simples, mas você também pode realizar uma listagem hierárquica, definindo o `useFlatBlobListing` parâmetro do `ListBlobsSegmentedAsync` método `false`.

O exemplo define um método assíncrono, usando um `async` bloco. O ``let!`` palavra-chave suspende a execução do método de exemplo até que a tarefa de listagem seja concluída.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Agora, podemos usar essa rotina assíncrona da seguinte maneira. Primeiro, você carregar alguns dados fictícios (usando o arquivo local criado anteriormente neste tutorial).

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Agora, chame a rotina. Você usa `Async.RunSynchronously` para forçar a execução da operação assíncrona.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Gravando em um blob de acréscimo

Um blob de acréscimo é otimizado para operações de acréscimo, como registro em log. Como um blob de blocos, um blob de acréscimo é composto por blocos, mas quando você adiciona um novo bloco para um blob de acréscimo, ele sempre é acrescentado ao final do blob. Você não pode atualizar ou excluir um bloco existente em um blob de acréscimo. As IDs de bloco para um blob de acréscimo não são expostos como são para um blob de blocos.

Cada bloco em um blob de acréscimo pode ter um tamanho diferente, até um máximo de 4 MB, e um blob de acréscimo pode incluir no máximo 50.000 blocos. O tamanho máximo de um blob de acréscimo, portanto, é um pouco mais de 195 GB (4 MB X 50.000 blocos).

O exemplo a seguir cria um novo blob de acréscimo e acrescenta alguns dados a ele, simulando uma operação de registro em log simples.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Ver [Compreendendo Blobs de blocos, Blobs de páginas e Blobs de acréscimo](https://msdn.microsoft.com/library/azure/ee691964.aspx) para obter mais informações sobre as diferenças entre os três tipos de blobs.

## <a name="concurrent-access"></a>Acesso simultâneo

Para dar suporte a acesso simultâneo em um blob de vários clientes ou várias instâncias do processo, você pode usar **ETags** ou **concessões**.

* **ETag** -fornece uma maneira de detectar que o contêiner ou blob foi modificado por outro processo

* **Concessão** -fornece uma maneira exclusivo e renovável, gravar ou excluir o acesso a um blob para um período de tempo

Para obter mais informações, consulte [Gerenciando a simultaneidade no armazenamento do Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Contêineres de nomenclatura

Todos os BLOBs no armazenamento do Azure devem residir em um contêiner. O contêiner faz parte do nome do blob. Por exemplo, `mydata` é o nome do contêiner em que esses URIs do blob de exemplo:

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Um nome de contêiner deve ser um nome DNS válido, em conformidade com as regras de nomenclatura a seguir:

1. Os nomes de contêiner devem começar com uma letra ou número e podem conter apenas letras, números e o caractere traço (-).
1. Cada caractere traço (-) deve ser imediatamente precedido e seguido por uma letra ou número; traços consecutivos não são permitidos em nomes de contêiner.
1. Todas as letras de um nome de contêiner devem estar em minúsculas.
1. Os nomes de contêiner devem ter de 3 a 63 caracteres.

Observe que o nome de um contêiner deve sempre estar em minúsculo. Se você incluir uma letra maiuscula em um nome de contêiner ou viola o regras de nomenclatura do contêiner, você poderá receber um erro 400 (solicitação incorreta).

## <a name="managing-security-for-blobs"></a>Gerenciar a segurança de blobs

Por padrão, o armazenamento do Azure mantém seus dados seguros limitando o acesso ao proprietário da conta, que está em posse das chaves de acesso de conta. Quando você precisa compartilhar dados de blob em sua conta de armazenamento, é importante fazer isso sem comprometer a segurança de suas chaves de acesso da conta. Além disso, você pode criptografar dados de blob para garantir que eles fiquem seguros durante a transmissão e no armazenamento do Azure.

### <a name="controlling-access-to-blob-data"></a>Controlando o acesso a dados de blob

Por padrão, os dados de blob em sua conta de armazenamento são acessíveis somente para o proprietário da conta de armazenamento. Autenticando solicitações no armazenamento de BLOBs requer a chave de acesso de conta por padrão. No entanto, você talvez queira disponibilizar determinados dados de blob para outros usuários.

### <a name="encrypting-blob-data"></a>Criptografia de dados de blob

O armazenamento do Azure dá suporte à criptografia de dados de blob no cliente e no servidor.

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu os conceitos básicos do armazenamento de BLOBs, siga estes links para saber mais.

### <a name="tools"></a>Ferramentas

- [F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Um F# provedor de tipo que pode ser usado para explorar os ativos de Blob, tabela e fila de armazenamento do Azure e aplicar facilmente operações CRUD neles.

- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
Um F# API para usar o serviço de armazenamento de tabela do Microsoft Azure

- [Microsoft Azure Storage Explorer MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Um aplicativo autônomo gratuito da Microsoft que permite trabalhar visualmente com dados do armazenamento do Azure no Windows, OS X e Linux.

### <a name="blob-storage-reference"></a>Referência do armazenamento de blob

- [APIs de armazenamento do Azure para .NET](/dotnet/api/overview/azure/storage)
- [Referência da API REST de serviços de armazenamento do Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Guias de relacionados

- [Introdução ao armazenamento de BLOBs do Azure em c#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Transferir dados com o utilitário de linha de comando do AzCopy no Windows](/azure/storage/common/storage-use-azcopy)
- [Transferir dados com o utilitário de linha de comando do AzCopy no Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Configurar cadeias de conexão do armazenamento do Azure](/azure/storage/common/storage-configure-connection-string)
- [Blog da equipe do armazenamento do Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Início Rápido: Usar o .NET para criar um blob no armazenamento de objeto](/azure/storage/blobs/storage-quickstart-blobs-dotnet)