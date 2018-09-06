---
title: 'Introdução ao armazenamento de BLOBs do Azure usando F #'
description: Store dados não estruturados na nuvem com o armazenamento de BLOBs do Azure.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: ea9dc334ec9c2bcd4a80cc501d4b6634da5f64e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734467"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="d7c82-103">Introdução ao armazenamento de BLOBs do Azure usando F #</span><span class="sxs-lookup"><span data-stu-id="d7c82-103">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="d7c82-104">O Armazenamento de Blobs do Azure é um serviço que armazena dados não estruturados na nuvem como objetos/blobs.</span><span class="sxs-lookup"><span data-stu-id="d7c82-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="d7c82-105">O Armazenamento de Blobs pode armazenar qualquer tipo de texto ou dados binários, como um documento, um arquivo de mídia ou um instalador de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7c82-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="d7c82-106">O Armazenamento de Blobs também é conhecido como armazenamento de objeto.</span><span class="sxs-lookup"><span data-stu-id="d7c82-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="d7c82-107">Este artigo mostra como executar tarefas comuns usando o armazenamento de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="d7c82-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="d7c82-108">Os exemplos são escritos usando F # usando a biblioteca de cliente de armazenamento do Azure para .NET.</span><span class="sxs-lookup"><span data-stu-id="d7c82-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="d7c82-109">Tarefas abordadas incluem como carregar, listar, baixar e excluir blobs.</span><span class="sxs-lookup"><span data-stu-id="d7c82-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="d7c82-110">Para obter uma visão geral conceitual do armazenamento de blob, consulte [o guia do .NET para o armazenamento de BLOBs](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="d7c82-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d7c82-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d7c82-111">Prerequisites</span></span>

<span data-ttu-id="d7c82-112">Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="d7c82-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="d7c82-113">Você também precisa sua chave de acesso de armazenamento para esta conta.</span><span class="sxs-lookup"><span data-stu-id="d7c82-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="d7c82-114">Criar Script de F # e o início da F # interativo</span><span class="sxs-lookup"><span data-stu-id="d7c82-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="d7c82-115">Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #.</span><span class="sxs-lookup"><span data-stu-id="d7c82-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="d7c82-116">Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `blobs.fsx`, em seu ambiente de desenvolvimento do F #.</span><span class="sxs-lookup"><span data-stu-id="d7c82-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="d7c82-117">Em seguida, use uma [Gerenciador de pacotes](package-management.md) tais como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` e `Microsoft.WindowsAzure.ConfigurationManager` referência e pacotes `WindowsAzure.Storage.dll` e `Microsoft.WindowsAzure.Configuration.dll` em seu script usando um `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="d7c82-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="d7c82-118">Adicionar declarações de namespace</span><span class="sxs-lookup"><span data-stu-id="d7c82-118">Add namespace declarations</span></span>

<span data-ttu-id="d7c82-119">Adicione o seguinte `open` as instruções na parte superior do `blobs.fsx` arquivo:</span><span class="sxs-lookup"><span data-stu-id="d7c82-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="d7c82-120">Obter a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="d7c82-120">Get your connection string</span></span>

<span data-ttu-id="d7c82-121">Você precisa de uma cadeia de caracteres de conexão do armazenamento do Azure para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="d7c82-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="d7c82-122">Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="d7c82-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="d7c82-123">Para o tutorial, você pode inserir a cadeia de conexão no seu script, como este:</span><span class="sxs-lookup"><span data-stu-id="d7c82-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="d7c82-124">No entanto, isso é **não recomendável** para projetos reais.</span><span class="sxs-lookup"><span data-stu-id="d7c82-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="d7c82-125">Sua chave de conta de armazenamento é semelhante para a senha raiz para sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d7c82-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="d7c82-126">Sempre tenha cuidado para proteger sua chave de conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d7c82-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="d7c82-127">Evite distribuí-la a outros usuários, embuti-la, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="d7c82-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="d7c82-128">Você pode regenerar a chave usando o Portal do Azure se você acredita que pode ter sido comprometida.</span><span class="sxs-lookup"><span data-stu-id="d7c82-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="d7c82-129">Aplicativos para o real, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d7c82-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="d7c82-130">Para buscar a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="d7c82-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="d7c82-131">Usando o Gerenciador de configuração do Azure é opcional.</span><span class="sxs-lookup"><span data-stu-id="d7c82-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="d7c82-132">Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.</span><span class="sxs-lookup"><span data-stu-id="d7c82-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="d7c82-133">Analisar a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="d7c82-133">Parse the connection string</span></span>

<span data-ttu-id="d7c82-134">Para analisar a cadeia de caracteres de conexão, use:</span><span class="sxs-lookup"><span data-stu-id="d7c82-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="d7c82-135">Isso retorna um `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="d7c82-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="d7c82-136">Criar alguns dados fictícios locais</span><span class="sxs-lookup"><span data-stu-id="d7c82-136">Create some local dummy data</span></span>

<span data-ttu-id="d7c82-137">Antes de começar, crie alguns dados fictícios de locais no diretório do nosso script.</span><span class="sxs-lookup"><span data-stu-id="d7c82-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="d7c82-138">Mais tarde você pode carregar esses dados.</span><span class="sxs-lookup"><span data-stu-id="d7c82-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="d7c82-139">Criar o cliente do serviço Blob</span><span class="sxs-lookup"><span data-stu-id="d7c82-139">Create the Blob service client</span></span>

<span data-ttu-id="d7c82-140">O `CloudBlobClient` tipo permite que você recupere contêineres e blobs armazenados no armazenamento de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="d7c82-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="d7c82-141">Aqui está uma maneira de criar o cliente do serviço:</span><span class="sxs-lookup"><span data-stu-id="d7c82-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="d7c82-142">Agora você está pronto para escrever um código que lê e grava dados no armazenamento de Blob.</span><span class="sxs-lookup"><span data-stu-id="d7c82-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="d7c82-143">Criar um contêiner</span><span class="sxs-lookup"><span data-stu-id="d7c82-143">Create a container</span></span>

<span data-ttu-id="d7c82-144">Este exemplo mostra como criar um contêiner se ele ainda não existir:</span><span class="sxs-lookup"><span data-stu-id="d7c82-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="d7c82-145">Por padrão, o novo contêiner é privado, o que significa que você deve especificar sua chave de acesso de armazenamento para baixar blobs desse contêiner.</span><span class="sxs-lookup"><span data-stu-id="d7c82-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="d7c82-146">Se você quiser tornar os arquivos dentro do contêiner disponíveis a todos, você pode definir o contêiner como público usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d7c82-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="d7c82-147">Qualquer pessoa na Internet pode ver blobs em um contêiner público, mas você pode modificar ou excluí-los somente se você tiver a chave de acesso da conta apropriada ou uma assinatura de acesso compartilhado.</span><span class="sxs-lookup"><span data-stu-id="d7c82-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="d7c82-148">Carregar um blob em um contêiner</span><span class="sxs-lookup"><span data-stu-id="d7c82-148">Upload a blob into a container</span></span>

<span data-ttu-id="d7c82-149">O armazenamento de BLOBs do Azure dá suporte a blobs de blocos e blobs de página.</span><span class="sxs-lookup"><span data-stu-id="d7c82-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="d7c82-150">Na maioria dos casos, um blob de blocos é o tipo recomendado.</span><span class="sxs-lookup"><span data-stu-id="d7c82-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="d7c82-151">Para carregar um arquivo em um blob de blocos, obtenha uma referência de contêiner e usá-lo para obter uma referência de blob de bloco.</span><span class="sxs-lookup"><span data-stu-id="d7c82-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="d7c82-152">Quando você tiver uma referência de blob, você pode carregar qualquer fluxo de dados nele chamando o `UploadFromFile` método.</span><span class="sxs-lookup"><span data-stu-id="d7c82-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="d7c82-153">Esta operação criará o blob se ele anteriormente não existir ou substituí-lo se ele existir.</span><span class="sxs-lookup"><span data-stu-id="d7c82-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="d7c82-154">Listar os blobs em um contêiner</span><span class="sxs-lookup"><span data-stu-id="d7c82-154">List the blobs in a container</span></span>

<span data-ttu-id="d7c82-155">Para listar os blobs em um contêiner, primeiro obtenha uma referência de contêiner.</span><span class="sxs-lookup"><span data-stu-id="d7c82-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="d7c82-156">Você pode usar o contêiner `ListBlobs` método para recuperar os blobs e/ou diretórios dentro dele.</span><span class="sxs-lookup"><span data-stu-id="d7c82-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="d7c82-157">Para acessar o conjunto avançado de propriedades e métodos para um `IListBlobItem`, você deve convertê-lo em um `CloudBlockBlob`, `CloudPageBlob`, ou `CloudBlobDirectory` objeto.</span><span class="sxs-lookup"><span data-stu-id="d7c82-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="d7c82-158">Se o tipo for desconhecido, você pode usar uma verificação de tipo para determinar em qual convertê-lo.</span><span class="sxs-lookup"><span data-stu-id="d7c82-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="d7c82-159">O código a seguir demonstra como recuperar e apresentar a URI de cada item no `mydata` contêiner:</span><span class="sxs-lookup"><span data-stu-id="d7c82-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="d7c82-160">Você também pode blobs de nome com informações de caminho em seus nomes.</span><span class="sxs-lookup"><span data-stu-id="d7c82-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="d7c82-161">Isso cria uma estrutura de diretório virtual que você pode organizar e percorrer como faria com um sistema de arquivos tradicional.</span><span class="sxs-lookup"><span data-stu-id="d7c82-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="d7c82-162">Observe que a estrutura do diretório é virtual apenas - os somente os recursos disponíveis no armazenamento de BLOBs são contêineres e blobs.</span><span class="sxs-lookup"><span data-stu-id="d7c82-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="d7c82-163">No entanto, a biblioteca de cliente de armazenamento oferece um `CloudBlobDirectory` objeto para fazer referência a um diretório virtual e simplificar o processo de trabalhar com blobs organizados dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="d7c82-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="d7c82-164">Por exemplo, considere o seguinte conjunto de blobs de blocos em um contêiner denominado `photos`:</span><span class="sxs-lookup"><span data-stu-id="d7c82-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="d7c82-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="d7c82-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="d7c82-166">Quando você chama `ListBlobs` em um contêiner (como no exemplo acima), uma listagem hierárquica é retornada.</span><span class="sxs-lookup"><span data-stu-id="d7c82-166">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="d7c82-167">Se ele contiver ambos `CloudBlobDirectory` e `CloudBlockBlob` objetos, que representam os diretórios e blobs no contêiner, respectivamente, em seguida, a saída resultante é semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="d7c82-167">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="d7c82-168">Opcionalmente, você pode definir as `UseFlatBlobListing` parâmetro do `ListBlobs` método `true`.</span><span class="sxs-lookup"><span data-stu-id="d7c82-168">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="d7c82-169">Nesse caso, todos os BLOBs no contêiner é retornado como um `CloudBlockBlob` objeto.</span><span class="sxs-lookup"><span data-stu-id="d7c82-169">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="d7c82-170">A chamada para `ListBlobs` para retornar uma lista simples tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="d7c82-170">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="d7c82-171">e, dependendo do conteúdo atual do seu contêiner, os resultados ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="d7c82-171">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="d7c82-172">Baixar blobs</span><span class="sxs-lookup"><span data-stu-id="d7c82-172">Download blobs</span></span>

<span data-ttu-id="d7c82-173">Para baixar blobs, primeiro recupere uma referência de blob e, em seguida, chamar o `DownloadToStream` método.</span><span class="sxs-lookup"><span data-stu-id="d7c82-173">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="d7c82-174">O exemplo a seguir usa o `DownloadToStream` método para transferir o conteúdo do blob para um objeto de fluxo que você pode persistir em um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="d7c82-174">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="d7c82-175">Você também pode usar o `DownloadToStream` método para baixar o conteúdo de um blob como uma cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="d7c82-175">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="d7c82-176">Excluir blobs</span><span class="sxs-lookup"><span data-stu-id="d7c82-176">Delete blobs</span></span>

<span data-ttu-id="d7c82-177">Para excluir um blob, primeiro obtenha uma referência de blob e, em seguida, chame o `Delete` método nele.</span><span class="sxs-lookup"><span data-stu-id="d7c82-177">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="d7c82-178">Listar blobs em páginas de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="d7c82-178">List blobs in pages asynchronously</span></span>

<span data-ttu-id="d7c82-179">Se você está listando uma grande quantidade de blobs, ou você deseja controlar o número de resultados retornados em uma operação de listagem, você pode listar os blobs em páginas de resultados.</span><span class="sxs-lookup"><span data-stu-id="d7c82-179">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="d7c82-180">Este exemplo mostra como retornar resultados nas páginas de forma assíncrona, para que a execução não fique bloqueada enquanto espera para retornar um grande conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="d7c82-180">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="d7c82-181">Este exemplo mostra um listagem de blob simples, mas você também pode realizar uma listagem hierárquica, definindo o `useFlatBlobListing` parâmetro do `ListBlobsSegmentedAsync` método `false`.</span><span class="sxs-lookup"><span data-stu-id="d7c82-181">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="d7c82-182">O exemplo define um método assíncrono, usando um `async` bloco.</span><span class="sxs-lookup"><span data-stu-id="d7c82-182">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="d7c82-183">O ``let!`` palavra-chave suspende a execução do método de exemplo até que a tarefa de listagem seja concluída.</span><span class="sxs-lookup"><span data-stu-id="d7c82-183">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="d7c82-184">Agora, podemos usar essa rotina assíncrona da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="d7c82-184">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="d7c82-185">Primeiro, você carregar alguns dados fictícios (usando o arquivo local criado anteriormente neste tutorial).</span><span class="sxs-lookup"><span data-stu-id="d7c82-185">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="d7c82-186">Agora, chame a rotina.</span><span class="sxs-lookup"><span data-stu-id="d7c82-186">Now, call the routine.</span></span> <span data-ttu-id="d7c82-187">Você usa `Async.RunSynchronously` para forçar a execução da operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="d7c82-187">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="d7c82-188">Gravando em um blob de acréscimo</span><span class="sxs-lookup"><span data-stu-id="d7c82-188">Writing to an append blob</span></span>

<span data-ttu-id="d7c82-189">Um blob de acréscimo é otimizado para operações de acréscimo, como registro em log.</span><span class="sxs-lookup"><span data-stu-id="d7c82-189">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="d7c82-190">Como um blob de blocos, um blob de acréscimo é composto por blocos, mas quando você adiciona um novo bloco para um blob de acréscimo, ele sempre é acrescentado ao final do blob.</span><span class="sxs-lookup"><span data-stu-id="d7c82-190">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="d7c82-191">Você não pode atualizar ou excluir um bloco existente em um blob de acréscimo.</span><span class="sxs-lookup"><span data-stu-id="d7c82-191">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="d7c82-192">As IDs de bloco para um blob de acréscimo não são expostos como são para um blob de blocos.</span><span class="sxs-lookup"><span data-stu-id="d7c82-192">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="d7c82-193">Cada bloco em um blob de acréscimo pode ter um tamanho diferente, até um máximo de 4 MB, e um blob de acréscimo pode incluir no máximo 50.000 blocos.</span><span class="sxs-lookup"><span data-stu-id="d7c82-193">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="d7c82-194">O tamanho máximo de um blob de acréscimo, portanto, é um pouco mais de 195 GB (4 MB X 50.000 blocos).</span><span class="sxs-lookup"><span data-stu-id="d7c82-194">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="d7c82-195">O exemplo a seguir cria um novo blob de acréscimo e acrescenta alguns dados a ele, simulando uma operação de registro em log simples.</span><span class="sxs-lookup"><span data-stu-id="d7c82-195">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="d7c82-196">Ver [Compreendendo Blobs de blocos, Blobs de páginas e Blobs de acréscimo](https://msdn.microsoft.com/library/azure/ee691964.aspx) para obter mais informações sobre as diferenças entre os três tipos de blobs.</span><span class="sxs-lookup"><span data-stu-id="d7c82-196">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="d7c82-197">Acesso simultâneo</span><span class="sxs-lookup"><span data-stu-id="d7c82-197">Concurrent access</span></span>

<span data-ttu-id="d7c82-198">Para dar suporte a acesso simultâneo em um blob de vários clientes ou várias instâncias do processo, você pode usar **ETags** ou **concessões**.</span><span class="sxs-lookup"><span data-stu-id="d7c82-198">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="d7c82-199">**ETag** -fornece uma maneira de detectar que o contêiner ou blob foi modificado por outro processo</span><span class="sxs-lookup"><span data-stu-id="d7c82-199">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="d7c82-200">**Concessão** -fornece uma maneira exclusivo e renovável, gravar ou excluir o acesso a um blob para um período de tempo</span><span class="sxs-lookup"><span data-stu-id="d7c82-200">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="d7c82-201">Para obter mais informações, consulte [Gerenciando a simultaneidade no armazenamento do Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="d7c82-201">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="d7c82-202">Contêineres de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="d7c82-202">Naming containers</span></span>

<span data-ttu-id="d7c82-203">Todos os BLOBs no armazenamento do Azure devem residir em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="d7c82-203">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="d7c82-204">O contêiner faz parte do nome do blob.</span><span class="sxs-lookup"><span data-stu-id="d7c82-204">The container forms part of the blob name.</span></span> <span data-ttu-id="d7c82-205">Por exemplo, `mydata` é o nome do contêiner em que esses URIs do blob de exemplo:</span><span class="sxs-lookup"><span data-stu-id="d7c82-205">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="d7c82-206">Um nome de contêiner deve ser um nome DNS válido, em conformidade com as regras de nomenclatura a seguir:</span><span class="sxs-lookup"><span data-stu-id="d7c82-206">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="d7c82-207">Os nomes de contêiner devem começar com uma letra ou número e podem conter apenas letras, números e o caractere traço (-).</span><span class="sxs-lookup"><span data-stu-id="d7c82-207">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="d7c82-208">Cada caractere traço (-) deve ser imediatamente precedido e seguido por uma letra ou número; traços consecutivos não são permitidos em nomes de contêiner.</span><span class="sxs-lookup"><span data-stu-id="d7c82-208">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="d7c82-209">Todas as letras de um nome de contêiner devem estar em minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d7c82-209">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="d7c82-210">Os nomes de contêiner devem ter de 3 a 63 caracteres.</span><span class="sxs-lookup"><span data-stu-id="d7c82-210">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="d7c82-211">Observe que o nome de um contêiner deve sempre estar em minúsculo.</span><span class="sxs-lookup"><span data-stu-id="d7c82-211">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="d7c82-212">Se você incluir uma letra maiuscula em um nome de contêiner ou viola o regras de nomenclatura do contêiner, você poderá receber um erro 400 (solicitação incorreta).</span><span class="sxs-lookup"><span data-stu-id="d7c82-212">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="d7c82-213">Gerenciar a segurança de blobs</span><span class="sxs-lookup"><span data-stu-id="d7c82-213">Managing security for blobs</span></span>

<span data-ttu-id="d7c82-214">Por padrão, o armazenamento do Azure mantém seus dados seguros limitando o acesso ao proprietário da conta, que está em posse das chaves de acesso de conta.</span><span class="sxs-lookup"><span data-stu-id="d7c82-214">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="d7c82-215">Quando você precisa compartilhar dados de blob em sua conta de armazenamento, é importante fazer isso sem comprometer a segurança de suas chaves de acesso da conta.</span><span class="sxs-lookup"><span data-stu-id="d7c82-215">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="d7c82-216">Além disso, você pode criptografar dados de blob para garantir que eles fiquem seguros durante a transmissão e no armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7c82-216">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="d7c82-217">Controlando o acesso a dados de blob</span><span class="sxs-lookup"><span data-stu-id="d7c82-217">Controlling access to blob data</span></span>

<span data-ttu-id="d7c82-218">Por padrão, os dados de blob em sua conta de armazenamento são acessíveis somente para o proprietário da conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d7c82-218">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="d7c82-219">Autenticando solicitações no armazenamento de BLOBs requer a chave de acesso de conta por padrão.</span><span class="sxs-lookup"><span data-stu-id="d7c82-219">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="d7c82-220">No entanto, você talvez queira disponibilizar determinados dados de blob para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="d7c82-220">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="d7c82-221">Para obter detalhes sobre como controlar o acesso ao armazenamento de blob, consulte [o guia do .NET para a seção de armazenamento de blob no controle de acesso](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span><span class="sxs-lookup"><span data-stu-id="d7c82-221">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="d7c82-222">Criptografia de dados de blob</span><span class="sxs-lookup"><span data-stu-id="d7c82-222">Encrypting blob data</span></span>

<span data-ttu-id="d7c82-223">O armazenamento do Azure dá suporte à criptografia de dados de blob no cliente e no servidor.</span><span class="sxs-lookup"><span data-stu-id="d7c82-223">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="d7c82-224">Para obter detalhes sobre a criptografia de dados de blob, consulte [o guia do .NET para a seção de armazenamento de blob na criptografia de](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span><span class="sxs-lookup"><span data-stu-id="d7c82-224">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d7c82-225">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d7c82-225">Next steps</span></span>

<span data-ttu-id="d7c82-226">Agora que você aprendeu os conceitos básicos do armazenamento de BLOBs, siga estes links para saber mais.</span><span class="sxs-lookup"><span data-stu-id="d7c82-226">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="d7c82-227">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="d7c82-227">Tools</span></span>
- <span data-ttu-id="d7c82-228">[F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) um tipo de provedor de F # que pode ser usado para explorar os ativos de Blob, tabela e fila de armazenamento do Azure e aplicar facilmente operações CRUD neles.</span><span class="sxs-lookup"><span data-stu-id="d7c82-228">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="d7c82-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) uma API de F # para usar o serviço de armazenamento de tabela do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="d7c82-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="d7c82-230">[Azure Storage Explorer MASE (Microsoft)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) é um aplicativo autônomo gratuito da Microsoft que permite trabalhar visualmente com dados do armazenamento do Azure no Windows, OS X e Linux.</span><span class="sxs-lookup"><span data-stu-id="d7c82-230">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="d7c82-231">Referência do armazenamento de blob</span><span class="sxs-lookup"><span data-stu-id="d7c82-231">Blob storage reference</span></span>

- [<span data-ttu-id="d7c82-232">APIs de armazenamento do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="d7c82-232">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="d7c82-233">Referência da API REST de serviços de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="d7c82-233">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="d7c82-234">Guias de relacionados</span><span class="sxs-lookup"><span data-stu-id="d7c82-234">Related guides</span></span>

- [<span data-ttu-id="d7c82-235">Introdução ao armazenamento de BLOBs do Azure em c#</span><span class="sxs-lookup"><span data-stu-id="d7c82-235">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="d7c82-236">Transferir dados com o utilitário de linha de comando do AzCopy no Windows</span><span class="sxs-lookup"><span data-stu-id="d7c82-236">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="d7c82-237">Transferir dados com o utilitário de linha de comando do AzCopy no Linux</span><span class="sxs-lookup"><span data-stu-id="d7c82-237">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="d7c82-238">Configurar cadeias de conexão do armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="d7c82-238">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="d7c82-239">Blog da equipe do armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="d7c82-239">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
