---
title: 'Introdução ao armazenamento de BLOBs do Azure usando F #'
description: Armazene dados não estruturados em nuvem com o armazenamento de BLOBs do Azure.
keywords: 'o Visual f #, f #, funcional programação .NET, .NET Core, o Azure'
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c5b74a4f-dcd1-4849-930c-904b6c8a04e1
ms.openlocfilehash: 14ccba36638c724536793a6a589cf1c0a6186eeb
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="042d4-104">Introdução ao armazenamento de BLOBs do Azure usando F #</span><span class="sxs-lookup"><span data-stu-id="042d4-104">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="042d4-105">O Armazenamento de Blobs do Azure é um serviço que armazena dados não estruturados na nuvem como objetos/blobs.</span><span class="sxs-lookup"><span data-stu-id="042d4-105">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="042d4-106">O Armazenamento de Blobs pode armazenar qualquer tipo de texto ou dados binários, como um documento, um arquivo de mídia ou um instalador de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="042d4-106">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="042d4-107">O Armazenamento de Blobs também é conhecido como armazenamento de objeto.</span><span class="sxs-lookup"><span data-stu-id="042d4-107">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="042d4-108">Este artigo mostra como executar tarefas comuns usando o armazenamento de Blob.</span><span class="sxs-lookup"><span data-stu-id="042d4-108">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="042d4-109">Os exemplos são escritos usando F # usando a biblioteca de cliente de armazenamento do Azure para .NET.</span><span class="sxs-lookup"><span data-stu-id="042d4-109">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="042d4-110">As tarefas abordadas incluem como carregar, listar, baixar e excluir blobs.</span><span class="sxs-lookup"><span data-stu-id="042d4-110">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="042d4-111">Para obter uma visão geral conceitual do armazenamento de blob, consulte [o guia do .NET para armazenamento de blob](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="042d4-111">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="042d4-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="042d4-112">Prerequisites</span></span>

<span data-ttu-id="042d4-113">Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="042d4-113">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="042d4-114">Você também precisará sua chave de acesso de armazenamento para esta conta.</span><span class="sxs-lookup"><span data-stu-id="042d4-114">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="042d4-115">Criar Script F # e começar a F # interativo</span><span class="sxs-lookup"><span data-stu-id="042d4-115">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="042d4-116">Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #.</span><span class="sxs-lookup"><span data-stu-id="042d4-116">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="042d4-117">Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `blobs.fsx`, em seu ambiente de desenvolvimento do F #.</span><span class="sxs-lookup"><span data-stu-id="042d4-117">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="042d4-118">Em seguida, use uma [Gerenciador de pacote](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` e `Microsoft.WindowsAzure.ConfigurationManager` pacotes e referência `WindowsAzure.Storage.dll` e `Microsoft.WindowsAzure.Configuration.dll` em seu script usando um `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="042d4-118">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="042d4-119">Adicione declarações de namespace</span><span class="sxs-lookup"><span data-stu-id="042d4-119">Add namespace declarations</span></span>

<span data-ttu-id="042d4-120">Adicione o seguinte `open` instruções na parte superior do `blobs.fsx` arquivo:</span><span class="sxs-lookup"><span data-stu-id="042d4-120">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="042d4-121">Obter a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="042d4-121">Get your connection string</span></span>

<span data-ttu-id="042d4-122">Você precisa de uma cadeia de caracteres de conexão de armazenamento do Azure para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="042d4-122">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="042d4-123">Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="042d4-123">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="042d4-124">Para o tutorial, você pode inserir sua cadeia de caracteres de conexão no seu script, como este:</span><span class="sxs-lookup"><span data-stu-id="042d4-124">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="042d4-125">No entanto, isso é **não recomendável** projetos para o real.</span><span class="sxs-lookup"><span data-stu-id="042d4-125">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="042d4-126">Sua chave de conta de armazenamento é semelhante para a senha de raiz de sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="042d4-126">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="042d4-127">Sempre tenha cuidado para proteger a chave de conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="042d4-127">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="042d4-128">Evite distribuí-lo a outros usuários, codificar, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="042d4-128">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="042d4-129">Você pode regenerar a chave usando o Portal do Azure se você acredita que ele pode ter sido comprometido.</span><span class="sxs-lookup"><span data-stu-id="042d4-129">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="042d4-130">Aplicativos para o real, a melhor maneira de manter sua cadeia de caracteres de conexão de armazenamento está em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="042d4-130">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="042d4-131">Para obter a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="042d4-131">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="042d4-132">Usando o Gerenciador de configuração do Azure é opcional.</span><span class="sxs-lookup"><span data-stu-id="042d4-132">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="042d4-133">Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.</span><span class="sxs-lookup"><span data-stu-id="042d4-133">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="042d4-134">Analisar a cadeia de caracteres de conexão</span><span class="sxs-lookup"><span data-stu-id="042d4-134">Parse the connection string</span></span>

<span data-ttu-id="042d4-135">Para analisar a cadeia de caracteres de conexão, use:</span><span class="sxs-lookup"><span data-stu-id="042d4-135">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="042d4-136">Isso retorna um `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="042d4-136">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="042d4-137">Criar alguns dados fictícios locais</span><span class="sxs-lookup"><span data-stu-id="042d4-137">Create some local dummy data</span></span>

<span data-ttu-id="042d4-138">Antes de começar, crie alguns dados fictícios de locais no diretório do nosso script.</span><span class="sxs-lookup"><span data-stu-id="042d4-138">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="042d4-139">Mais tarde você carregar esses dados.</span><span class="sxs-lookup"><span data-stu-id="042d4-139">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="042d4-140">Criar o cliente do serviço Blob</span><span class="sxs-lookup"><span data-stu-id="042d4-140">Create the Blob service client</span></span>

<span data-ttu-id="042d4-141">O `CloudBlobClient` tipo permite que você recupere contêineres e blobs armazenados no armazenamento de Blob.</span><span class="sxs-lookup"><span data-stu-id="042d4-141">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="042d4-142">Aqui está uma maneira de criar o cliente do serviço:</span><span class="sxs-lookup"><span data-stu-id="042d4-142">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="042d4-143">Agora você está pronto para escrever código que lê e grava dados no armazenamento de Blob.</span><span class="sxs-lookup"><span data-stu-id="042d4-143">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="042d4-144">Criar um contêiner</span><span class="sxs-lookup"><span data-stu-id="042d4-144">Create a container</span></span>

<span data-ttu-id="042d4-145">Este exemplo mostra como criar um contêiner se ele ainda não existir:</span><span class="sxs-lookup"><span data-stu-id="042d4-145">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="042d4-146">Por padrão, o novo contêiner é privado, o que significa que você deve especificar a chave de acesso de armazenamento para baixar blobs desse contêiner.</span><span class="sxs-lookup"><span data-stu-id="042d4-146">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="042d4-147">Se você quiser disponibilizar os arquivos dentro do contêiner a todos os usuários, você pode definir o contêiner pública usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="042d4-147">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="042d4-148">Qualquer pessoa na Internet pode ver os blobs em um contêiner público, mas você pode modificar ou excluí-los somente se você tiver a chave de acesso da conta apropriada ou uma assinatura de acesso compartilhado.</span><span class="sxs-lookup"><span data-stu-id="042d4-148">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="042d4-149">Carregar um blob em um contêiner</span><span class="sxs-lookup"><span data-stu-id="042d4-149">Upload a blob into a container</span></span>

<span data-ttu-id="042d4-150">Armazenamento de BLOBs do Azure oferece suporte a blobs de blocos e blobs de página.</span><span class="sxs-lookup"><span data-stu-id="042d4-150">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="042d4-151">Na maioria dos casos, um blob de bloco é o tipo recomendado para usar.</span><span class="sxs-lookup"><span data-stu-id="042d4-151">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="042d4-152">Para carregar um arquivo para um blob de bloco, obtenha uma referência de contêiner e usá-lo para obter uma referência de blob de bloco.</span><span class="sxs-lookup"><span data-stu-id="042d4-152">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="042d4-153">Quando você tem uma referência de blob, você pode carregar qualquer fluxo de dados a ele ao chamar o `UploadFromFile` método.</span><span class="sxs-lookup"><span data-stu-id="042d4-153">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="042d4-154">Essa operação cria o blob se ele anteriormente não existe ou substituí-lo se ele existir.</span><span class="sxs-lookup"><span data-stu-id="042d4-154">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="042d4-155">Listar os blobs em um contêiner</span><span class="sxs-lookup"><span data-stu-id="042d4-155">List the blobs in a container</span></span>

<span data-ttu-id="042d4-156">Para listar os blobs em um contêiner, primeiro obtenha uma referência de contêiner.</span><span class="sxs-lookup"><span data-stu-id="042d4-156">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="042d4-157">Você pode usar o contêiner `ListBlobs` método para recuperar os blobs e/ou diretórios dentro dele.</span><span class="sxs-lookup"><span data-stu-id="042d4-157">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="042d4-158">Para acessar um conjunto sofisticado de propriedades e métodos para uma retornado `IListBlobItem`, você deve convertê-lo para um `CloudBlockBlob`, `CloudPageBlob`, ou `CloudBlobDirectory` objeto.</span><span class="sxs-lookup"><span data-stu-id="042d4-158">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="042d4-159">Se o tipo é desconhecido, você pode usar uma verificação de tipo para determinar qual converter a.</span><span class="sxs-lookup"><span data-stu-id="042d4-159">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="042d4-160">O código a seguir demonstra como recuperar e o URI de cada item de saída de `mydata` contêiner:</span><span class="sxs-lookup"><span data-stu-id="042d4-160">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="042d4-161">Você também pode blobs de nome com informações de caminho em seus nomes.</span><span class="sxs-lookup"><span data-stu-id="042d4-161">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="042d4-162">Isso cria uma estrutura de diretório virtual que você pode organizar e percorrer como faria com um sistema de arquivos tradicional.</span><span class="sxs-lookup"><span data-stu-id="042d4-162">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="042d4-163">Observe que a estrutura de diretório é somente virtual - os somente os recursos disponíveis no armazenamento de Blob são contêineres e blobs.</span><span class="sxs-lookup"><span data-stu-id="042d4-163">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="042d4-164">No entanto, a biblioteca de cliente de armazenamento oferece uma `CloudBlobDirectory` objeto para fazer referência a um diretório virtual e simplificar o processo de trabalho com blobs são organizados dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="042d4-164">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="042d4-165">Por exemplo, considere o seguinte conjunto de blobs de bloco em um contêiner denominado `photos`:</span><span class="sxs-lookup"><span data-stu-id="042d4-165">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="042d4-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="042d4-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="042d4-167">Quando você chama `ListBlobs` em um contêiner (como o exemplo acima), uma lista hierárquica é retornada.</span><span class="sxs-lookup"><span data-stu-id="042d4-167">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="042d4-168">Se ele contém ambos `CloudBlobDirectory` e `CloudBlockBlob` objetos, representando os diretórios e blobs no contêiner, respectivamente, em seguida, a saída resultante é semelhante a este:</span><span class="sxs-lookup"><span data-stu-id="042d4-168">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="042d4-169">Opcionalmente, você pode definir o `UseFlatBlobListing` parâmetro o `ListBlobs` método `true`.</span><span class="sxs-lookup"><span data-stu-id="042d4-169">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="042d4-170">Nesse caso, cada blob no contêiner é retornado como um `CloudBlockBlob` objeto.</span><span class="sxs-lookup"><span data-stu-id="042d4-170">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="042d4-171">A chamada para `ListBlobs` para retornar uma lista simples tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="042d4-171">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="042d4-172">e, dependendo do conteúdo atual do seu contêiner, os resultados ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="042d4-172">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="042d4-173">Baixar blobs</span><span class="sxs-lookup"><span data-stu-id="042d4-173">Download blobs</span></span>

<span data-ttu-id="042d4-174">Para baixar blobs, primeiro recuperar uma referência de blob e, em seguida, chamar o `DownloadToStream` método.</span><span class="sxs-lookup"><span data-stu-id="042d4-174">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="042d4-175">O exemplo a seguir usa o `DownloadToStream` método para transferir o conteúdo do blob para um objeto de fluxo, em seguida, você pode persistir para um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="042d4-175">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="042d4-176">Você também pode usar o `DownloadToStream` método para baixar o conteúdo de um blob como uma cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="042d4-176">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="042d4-177">Exclua os blobs</span><span class="sxs-lookup"><span data-stu-id="042d4-177">Delete blobs</span></span>

<span data-ttu-id="042d4-178">Para excluir um blob, primeiro obter uma referência de blob e, em seguida, chamar o `Delete` método nele.</span><span class="sxs-lookup"><span data-stu-id="042d4-178">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="042d4-179">Listar blobs em páginas de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="042d4-179">List blobs in pages asynchronously</span></span>

<span data-ttu-id="042d4-180">Se estiver listando um grande número de blobs ou para controlar o número de resultados de que retorno em uma operação de listagem, você pode listar blobs em páginas de resultados.</span><span class="sxs-lookup"><span data-stu-id="042d4-180">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="042d4-181">Este exemplo mostra como retornar resultados nas páginas de forma assíncrona, para que a execução não está bloqueada enquanto aguarda para retornar um grande conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="042d4-181">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="042d4-182">Este exemplo mostra uma simples listagem do blob, mas você também pode executar uma lista hierárquica, definindo o `useFlatBlobListing` parâmetro o `ListBlobsSegmentedAsync` método `false`.</span><span class="sxs-lookup"><span data-stu-id="042d4-182">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="042d4-183">O exemplo define um método assíncrono, usando um `async` bloco.</span><span class="sxs-lookup"><span data-stu-id="042d4-183">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="042d4-184">O ``let!`` palavra-chave suspende a execução do método exemplo até que a lista de conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="042d4-184">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="042d4-185">Agora, podemos usar esta rotina assíncrona da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="042d4-185">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="042d4-186">Primeiro, carregue alguns dados fictícios (usando o arquivo local criado anteriormente neste tutorial).</span><span class="sxs-lookup"><span data-stu-id="042d4-186">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="042d4-187">Agora, chame a rotina.</span><span class="sxs-lookup"><span data-stu-id="042d4-187">Now, call the routine.</span></span> <span data-ttu-id="042d4-188">Você usa ``Async.RunSynchronously`` para forçar a execução da operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="042d4-188">You use ``Async.RunSynchronously`` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="042d4-189">Gravar um blob de acréscimo</span><span class="sxs-lookup"><span data-stu-id="042d4-189">Writing to an append blob</span></span>

<span data-ttu-id="042d4-190">Um blob de acréscimo é otimizado para operações de acréscimo, como o registro em log.</span><span class="sxs-lookup"><span data-stu-id="042d4-190">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="042d4-191">Como um blob de bloco, um blob de acréscimo é composto por blocos, mas quando você adiciona um novo bloco a um blob de acréscimo, ele sempre é adicionado ao final do blob.</span><span class="sxs-lookup"><span data-stu-id="042d4-191">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="042d4-192">Você não pode atualizar ou excluir um bloco existente em um blob de acréscimo.</span><span class="sxs-lookup"><span data-stu-id="042d4-192">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="042d4-193">As IDs do bloco para um blob de acréscimo não são expostos como eles são para um blob de bloco.</span><span class="sxs-lookup"><span data-stu-id="042d4-193">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="042d4-194">Cada bloco em um blob de acréscimo pode ter um tamanho diferente, até um máximo de 4 MB, e um blob de acréscimo pode incluir até 50.000 blocos.</span><span class="sxs-lookup"><span data-stu-id="042d4-194">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="042d4-195">O tamanho máximo de um blob de acréscimo, portanto, é um pouco mais de 195 GB (4 MB X 50.000 blocos).</span><span class="sxs-lookup"><span data-stu-id="042d4-195">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="042d4-196">O exemplo a seguir cria um novo blob de acréscimo e acrescenta alguns dados a ele, com uma simulação de uma operação de log simples.</span><span class="sxs-lookup"><span data-stu-id="042d4-196">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="042d4-197">Consulte [Compreendendo Blobs de bloco, Blobs de página e Blobs de acréscimo](https://msdn.microsoft.com/library/azure/ee691964.aspx) para obter mais informações sobre as diferenças entre os três tipos de blobs.</span><span class="sxs-lookup"><span data-stu-id="042d4-197">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="042d4-198">Acesso simultâneo</span><span class="sxs-lookup"><span data-stu-id="042d4-198">Concurrent access</span></span>

<span data-ttu-id="042d4-199">Para dar suporte a acesso simultâneo a um blob de vários clientes ou várias instâncias do processo, você pode usar **ETags** ou **concessões**.</span><span class="sxs-lookup"><span data-stu-id="042d4-199">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="042d4-200">**ETag** -fornece uma maneira de detectar que o blob ou contêiner foi modificado por outro processo</span><span class="sxs-lookup"><span data-stu-id="042d4-200">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="042d4-201">**Concessão** -fornece uma maneira de obter exclusivo, renovável, gravação ou exclusão acesso a um blob para um período de tempo</span><span class="sxs-lookup"><span data-stu-id="042d4-201">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="042d4-202">Para obter mais informações, consulte [gerenciamento de simultaneidade no armazenamento do Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="042d4-202">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="042d4-203">Contêineres de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="042d4-203">Naming containers</span></span>

<span data-ttu-id="042d4-204">Cada blob no armazenamento do Azure deve residir em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="042d4-204">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="042d4-205">O contêiner faz parte do nome do blob.</span><span class="sxs-lookup"><span data-stu-id="042d4-205">The container forms part of the blob name.</span></span> <span data-ttu-id="042d4-206">Por exemplo, `mydata` é o nome do contêiner esses URIs do blob de exemplo:</span><span class="sxs-lookup"><span data-stu-id="042d4-206">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="042d4-207">Um nome de contêiner deve ser um nome DNS válido, em conformidade com as regras de nomenclatura a seguir:</span><span class="sxs-lookup"><span data-stu-id="042d4-207">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="042d4-208">Os nomes de contêiner devem começar com uma letra ou número e podem conter apenas letras, números e o caractere de traço (-).</span><span class="sxs-lookup"><span data-stu-id="042d4-208">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="042d4-209">Cada caractere de traço (-) deve ser imediatamente precedido e seguido por uma letra ou número; traços consecutivos não são permitidos em nomes de contêiner.</span><span class="sxs-lookup"><span data-stu-id="042d4-209">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="042d4-210">Todas as letras em um nome de contêiner devem estar em minúsculas.</span><span class="sxs-lookup"><span data-stu-id="042d4-210">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="042d4-211">Nomes de contêiner devem ter de 3 a 63 caracteres.</span><span class="sxs-lookup"><span data-stu-id="042d4-211">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="042d4-212">Observe que o nome de um contêiner deve sempre ser minúsculas.</span><span class="sxs-lookup"><span data-stu-id="042d4-212">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="042d4-213">Se você incluir uma letra maiuscula em um nome de contêiner ou viola o regras de nomenclatura do contêiner, você poderá receber um erro 400 (solicitação incorreta).</span><span class="sxs-lookup"><span data-stu-id="042d4-213">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="042d4-214">Gerenciamento de segurança para blobs</span><span class="sxs-lookup"><span data-stu-id="042d4-214">Managing security for blobs</span></span>

<span data-ttu-id="042d4-215">Por padrão, o armazenamento do Azure mantém seus dados seguros, limitando o acesso ao proprietário da conta, que está em posse das chaves de acesso de conta.</span><span class="sxs-lookup"><span data-stu-id="042d4-215">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="042d4-216">Quando você precisa compartilhar dados blob em sua conta de armazenamento, é importante fazer isso sem comprometer a segurança de suas chaves de acesso da conta.</span><span class="sxs-lookup"><span data-stu-id="042d4-216">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="042d4-217">Além disso, você pode criptografar os dados de blob para garantir que ele é seguro vai através da rede e no armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="042d4-217">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="042d4-218">Controlando o acesso a dados de blob</span><span class="sxs-lookup"><span data-stu-id="042d4-218">Controlling access to blob data</span></span>

<span data-ttu-id="042d4-219">Por padrão, os dados de blob na conta de armazenamento são acessíveis somente para o proprietário da conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="042d4-219">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="042d4-220">Autenticar solicitações em relação ao armazenamento de Blob exige a chave de acesso de conta por padrão.</span><span class="sxs-lookup"><span data-stu-id="042d4-220">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="042d4-221">No entanto, você talvez queira disponibilizar determinados dados de blob para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="042d4-221">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="042d4-222">Para obter detalhes sobre como controlar o acesso ao armazenamento de blob, consulte [o guia de .NET para a seção de armazenamento de blob no controle de acesso](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span><span class="sxs-lookup"><span data-stu-id="042d4-222">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="042d4-223">Criptografia de dados de blob</span><span class="sxs-lookup"><span data-stu-id="042d4-223">Encrypting blob data</span></span>

<span data-ttu-id="042d4-224">Armazenamento do Azure oferece suporte à criptografia de dados de blob no cliente e no servidor.</span><span class="sxs-lookup"><span data-stu-id="042d4-224">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="042d4-225">Para obter detalhes sobre como criptografar dados blob, consulte [guia .NET para a seção de armazenamento de blob em criptografia](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span><span class="sxs-lookup"><span data-stu-id="042d4-225">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="042d4-226">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="042d4-226">Next steps</span></span>

<span data-ttu-id="042d4-227">Agora que você aprendeu as Noções básicas do armazenamento de Blob, siga estes links para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="042d4-227">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="042d4-228">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="042d4-228">Tools</span></span>
- <span data-ttu-id="042d4-229">[F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) um F # tipo de provedor que pode ser usado para explorar os ativos de Blob, tabela e fila de armazenamento do Azure e aplicar facilmente operações CRUD neles.</span><span class="sxs-lookup"><span data-stu-id="042d4-229">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="042d4-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) uma API de F # para usar o serviço de armazenamento de tabela do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="042d4-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="042d4-231">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) é um aplicativo autônomo gratuito da Microsoft que lhe permite trabalhar visualmente com dados de armazenamento do Azure no Windows, OS X e Linux.</span><span class="sxs-lookup"><span data-stu-id="042d4-231">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="042d4-232">Referência do armazenamento de blob</span><span class="sxs-lookup"><span data-stu-id="042d4-232">Blob storage reference</span></span>

- [<span data-ttu-id="042d4-233">APIs de armazenamento do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="042d4-233">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="042d4-234">Referência da API REST de serviços de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="042d4-234">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="042d4-235">Guias de relacionados</span><span class="sxs-lookup"><span data-stu-id="042d4-235">Related guides</span></span>

- [<span data-ttu-id="042d4-236">Introdução ao armazenamento de BLOBs do Azure em c#</span><span class="sxs-lookup"><span data-stu-id="042d4-236">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="042d4-237">Transferência de dados com o utilitário de linha de comando AzCopy no Windows</span><span class="sxs-lookup"><span data-stu-id="042d4-237">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="042d4-238">Transferência de dados com o utilitário de linha de comando AzCopy no Linux</span><span class="sxs-lookup"><span data-stu-id="042d4-238">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="042d4-239">Configurar cadeias de conexão de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="042d4-239">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="042d4-240">Blog da equipe do armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="042d4-240">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
