---
title: Introdução ao armazenamento de Blobs do Azure usando F#
description: Armazene dados não estruturados na nuvem com o armazenamento de BLOBs do Azure.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: c765f38cba7642e813a5966d3b7754c5ce45abbd
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107116"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Introdução ao armazenamento de BLOBs do Azure usando o F\#

O Armazenamento de Blobs do Azure é um serviço que armazena dados não estruturados na nuvem como objetos/blobs. O Armazenamento de Blobs pode armazenar qualquer tipo de texto ou dados binários, como um documento, um arquivo de mídia ou um instalador de aplicativo. O Armazenamento de Blobs também é conhecido como armazenamento de objeto.

Este artigo mostra como executar tarefas comuns usando o armazenamento de BLOBs. Os exemplos são escritos usando F# o uso da biblioteca de cliente de armazenamento do Azure para .net. As tarefas abordadas incluem como carregar, listar, baixar e excluir BLOBs.

Para obter uma visão geral conceitual do armazenamento de BLOBs, consulte [o guia .net para armazenamento de BLOBs](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account). Você também precisa da sua chave de acesso de armazenamento para essa conta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar um F# script e iniciar F# interativo

Os exemplos neste artigo podem ser usados em um F# aplicativo ou um F# script. Para criar um F# script, crie um arquivo com a `.fsx` extensão, por exemplo `blobs.fsx`, em seu F# ambiente de desenvolvimento.

Em seguida, use um [Gerenciador de pacotes](package-management.md) , como [paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) , `WindowsAzure.Storage` para instalar os pacotes `WindowsAzure.Storage.dll` e `Microsoft.WindowsAzure.Configuration.dll` `Microsoft.WindowsAzure.ConfigurationManager` a referência e em seu `#r` script usando uma diretiva.

### <a name="add-namespace-declarations"></a>Adicionar declarações de namespace

Adicione as seguintes `open` instruções à parte superior `blobs.fsx` do arquivo:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obter sua cadeia de conexão

Você precisa de uma cadeia de conexão de armazenamento do Azure para este tutorial. Para obter mais informações sobre cadeias de conexão, consulte [Configurar cadeias de conexão de armazenamento](/azure/storage/storage-configure-connection-string).

Para o tutorial, insira a cadeia de conexão em seu script, da seguinte maneira:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

No entanto, isso **não é recomendado** para projetos reais. Sua chave de conta de armazenamento é semelhante à senha raiz da sua conta de armazenamento. Sempre tenha cuidado para proteger sua chave de conta de armazenamento. Evite distribuí-lo a outros usuários, embuti-lo em código ou salvá-lo em um arquivo de texto sem formatação que seja acessível para outras pessoas. Você pode regenerar sua chave usando o portal do Azure se acreditar que ele pode ter sido comprometido.

Para aplicativos reais, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração. Para buscar a cadeia de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Usar o Configuration Manager do Azure é opcional. Você também pode usar uma API como o `ConfigurationManager` tipo de .NET Framework.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de conexão

Para analisar a cadeia de conexão, use:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Isso retorna um `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Criar alguns dados fictícios locais

Antes de começar, crie alguns dados locais fictícios no diretório do nosso script. Posteriormente, você carregará esses dados.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Criar o cliente do serviço blob

O `CloudBlobClient` tipo permite que você recupere contêineres e blobs armazenados no armazenamento de BLOBs. Aqui está uma maneira de criar o cliente de serviço:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Agora você está pronto para escrever código que lê dados e grava dados no armazenamento de BLOBs.

## <a name="create-a-container"></a>Criar um contêiner

Este exemplo mostra como criar um contêiner se ele ainda não existir:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Por padrão, o novo contêiner é privado, o que significa que você deve especificar sua chave de acesso de armazenamento para baixar BLOBs desse contêiner. Se desejar disponibilizar os arquivos dentro do contêiner para todos, você poderá definir o contêiner como público usando o seguinte código:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Qualquer pessoa na Internet pode ver BLOBs em um contêiner público, mas você pode modificá-los ou excluí-los somente se tiver a chave de acesso da conta apropriada ou uma assinatura de acesso compartilhado.

## <a name="upload-a-blob-into-a-container"></a>Carregar um blob em um contêiner

O armazenamento de BLOBs do Azure dá suporte a blobs de blocos e blobs de páginas. Na maioria dos casos, um blob de blocos é o tipo recomendado a ser usado.

Para carregar um arquivo em um blob de blocos, obtenha uma referência de contêiner e use-o para obter uma referência de blob de blocos. Depois de ter uma referência de BLOB, você pode carregar qualquer fluxo de dados para ele chamando o `UploadFromFile` método. Essa operação criará o blob se ele não existir anteriormente ou substituirá-o se existir.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Listar os BLOBs em um contêiner

Para listar os BLOBs em um contêiner, primeiro obtenha uma referência de contêiner. Em seguida, você pode usar o `ListBlobs` método do contêiner para recuperar os BLOBs e/ou diretórios dentro dele. Para acessar o rico conjunto de propriedades e métodos para um retornado `IListBlobItem`, você deve convertê-lo `CloudBlockBlob`em `CloudPageBlob`um objeto `CloudBlobDirectory` , ou. Se o tipo for desconhecido, você poderá usar uma verificação de tipo para determinar para qual convertê-lo. O código a seguir demonstra como recuperar e gerar a saída do URI de cada item `mydata` no contêiner:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Você também pode nomear BLOBs com informações de caminho em seus nomes. Isso cria uma estrutura de diretório virtual que você pode organizar e percorrer como faria com um sistema de arquivos tradicional. Observe que a estrutura de diretório é virtual somente-os únicos recursos disponíveis no armazenamento de BLOBs são contêineres e blobs. No entanto, a biblioteca de cliente `CloudBlobDirectory` de armazenamento oferece um objeto para se referir a um diretório virtual e simplificar o processo de trabalho com blobs que são organizados dessa maneira.

Por exemplo, considere o seguinte conjunto de blobs de blocos em um contêiner `photos`chamado:

*photo1.jpg*\
*2015/architecture/description.txt*\
*2015/architecture/photo3.jpg*\
*2015/architecture/photo4.jpg*\
*2016/architecture/photo5.jpg*\
*2016/architecture/photo6.jpg*\
*2016/architecture/description.txt*\
*2016/photo7.jpg*\

Quando você chama `ListBlobs` em um contêiner (como no exemplo acima), uma listagem hierárquica é retornada. Se ele contiver `CloudBlobDirectory` ambos `CloudBlockBlob` os objetos e, representando os diretórios e blobs no contêiner, respectivamente, a saída resultante será semelhante a esta:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Opcionalmente, você pode definir o `UseFlatBlobListing` parâmetro `ListBlobs` do método como `true`. Nesse caso, cada blob no contêiner é retornado como um `CloudBlockBlob` objeto. A chamada para `ListBlobs` para retornar uma listagem simples é parecida com esta:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

e, dependendo do conteúdo atual do seu contêiner, os resultados têm a seguinte aparência:

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

## <a name="download-blobs"></a>Baixar BLOBs

Para baixar BLOBs, primeiro recupere uma referência de BLOB e, em `DownloadToStream` seguida, chame o método. O exemplo a seguir usa `DownloadToStream` o método para transferir o conteúdo do blob para um objeto de fluxo que você pode persistir em um arquivo local.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Você também pode usar o `DownloadToStream` método para baixar o conteúdo de um blob como uma cadeia de texto.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Excluir BLOBs

Para excluir um blob, primeiro obtenha uma referência de BLOB e, em `Delete` seguida, chame o método nele.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Listar BLOBs em páginas de forma assíncrona

Se você estiver listando um grande número de BLOBs ou se quiser controlar o número de resultados retornados em uma operação de listagem, poderá listar os BLOBs em páginas de resultados. Este exemplo mostra como retornar resultados em páginas de forma assíncrona, para que a execução não seja bloqueada enquanto aguarda para retornar um grande conjunto de resultados.

Este exemplo mostra uma listagem de blob simples, mas você também pode executar uma listagem hierárquica, definindo o `useFlatBlobListing` parâmetro `ListBlobsSegmentedAsync` do método como `false`.

O exemplo define um método assíncrono, usando um `async` bloco. A ``let!`` palavra-chave suspende a execução do método de exemplo até que a tarefa de listagem seja concluída.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Agora podemos usar essa rotina assíncrona da seguinte maneira. Primeiro, você carrega alguns dados fictícios (usando o arquivo local criado anteriormente neste tutorial).

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Agora, chame a rotina. Você usa `Async.RunSynchronously` para forçar a execução da operação assíncrona.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Gravando em um blob de acréscimo

Um blob de acréscimo é otimizado para operações de acréscimo, como registro em log. Como um blob de blocos, um blob de acréscimo é composto por blocos, mas quando você adiciona um novo bloco a um blob de acréscimo, ele é sempre acrescentado ao final do blob. Você não pode atualizar ou excluir um bloco existente em um blob de acréscimo. As IDs de bloco para um blob de acréscimo não são expostas como são para um blob de blocos.

Cada bloco em um blob de acréscimo pode ter um tamanho diferente, até um máximo de 4 MB, e um blob de acréscimo pode incluir um máximo de 50.000 blocos. O tamanho máximo de um blob de acréscimo é, portanto, um pouco mais que 195 GB (4 MB X 50.000 blocos).

O exemplo a seguir cria um novo BLOB de acréscimo e acrescenta alguns dados a ele, simulando uma operação de log simples.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Consulte [noções básicas sobre blobs de blocos, blobs de páginas e blobs de acréscimo](https://msdn.microsoft.com/library/azure/ee691964.aspx) para obter mais informações sobre as diferenças entre os três tipos de BLOBs.

## <a name="concurrent-access"></a>Acesso simultâneo

Para dar suporte ao acesso simultâneo a um blob de vários clientes ou várias instâncias de processo, você pode usar ETags ou concessões.

- **ETag** – fornece uma maneira de detectar que o BLOB ou o contêiner foi modificado por outro processo

- **Concessão** -fornece uma maneira de obter acesso exclusivo, renovável, gravar ou excluir a um blob por um período de tempo

Para obter mais informações, consulte Gerenciando a [simultaneidade no armazenamento do Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Contêineres de nomenclatura

Cada blob no armazenamento do Azure deve residir em um contêiner. O contêiner faz parte do nome do blob. Por exemplo, `mydata` é o nome do contêiner nesses URIs de blob de exemplo:

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Um nome de contêiner deve ser um nome DNS válido, em conformidade com as seguintes regras de nomenclatura:

1. Os nomes de contêiner devem começar com uma letra ou número e podem conter apenas letras, números e o caractere de traço (-).
1. Cada caractere de traço (-) deve ser imediatamente precedido e seguido por uma letra ou número; traços consecutivos não são permitidos em nomes de contêiner.
1. Todas as letras em um nome de contêiner devem estar em minúsculas.
1. Os nomes de contêiner devem ter de 3 a 63 caracteres de comprimento.

Observe que o nome de um contêiner deve estar sempre em minúsculas. Se você incluir uma letra maiúscula em um nome de contêiner ou violar as regras de nomenclatura de contêiner, poderá receber um erro 400 (solicitação inadequada).

## <a name="managing-security-for-blobs"></a>Gerenciando a segurança para BLOBs

Por padrão, o armazenamento do Azure mantém seus dados seguros limitando o acesso ao proprietário da conta, que está em posse das chaves de acesso da conta. Quando você precisar compartilhar dados de BLOB em sua conta de armazenamento, é importante fazer isso sem comprometer a segurança de suas chaves de acesso de conta. Além disso, você pode criptografar dados de BLOB para garantir que ele esteja seguro passando pela conexão e no armazenamento do Azure.

### <a name="controlling-access-to-blob-data"></a>Controlando o acesso a dados de BLOB

Por padrão, os dados de BLOB em sua conta de armazenamento são acessíveis somente para o proprietário da conta de armazenamento. A autenticação de solicitações no armazenamento de BLOBs requer a chave de acesso da conta por padrão. No entanto, talvez você queira disponibilizar determinados dados de BLOB para outros usuários.

### <a name="encrypting-blob-data"></a>Criptografando dados de BLOB

O armazenamento do Azure dá suporte à criptografia de dados de blob no cliente e no servidor.

## <a name="next-steps"></a>Próximas etapas

Agora que você aprendeu os conceitos básicos do armazenamento de BLOBs, siga estes links para saber mais.

### <a name="tools"></a>Ferramentas

- [F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Um F# provedor de tipos que pode ser usado para explorar os ativos de armazenamento de BLOB, tabela e fila do Azure e aplicar facilmente as operações CRUD neles.

- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
Uma F# API para usar Microsoft Azure serviço de armazenamento de tabelas

- [Gerenciador de Armazenamento do Microsoft Azure (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Um aplicativo autônomo e gratuito da Microsoft que permite que você trabalhe visualmente com os dados do armazenamento do Azure no Windows, no OS X e no Linux.

### <a name="blob-storage-reference"></a>Referência de armazenamento de BLOBs

- [APIs de armazenamento do Azure para .NET](/dotnet/api/overview/azure/storage)
- [Referência da API REST dos serviços de armazenamento do Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Guias relacionados

- [Introdução com o armazenamento de BLOBs do Azure noC#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Transferir dados com o utilitário de linha de comando AzCopy no Windows](/azure/storage/common/storage-use-azcopy)
- [Transferir dados com o utilitário de linha de comando AzCopy no Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Configurar cadeias de conexão do armazenamento do Azure](/azure/storage/common/storage-configure-connection-string)
- [Blog da equipe de armazenamento do Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Início Rápido: Use o .NET para criar um blob no armazenamento de objetos](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
