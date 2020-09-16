---
title: Introdução ao armazenamento de Blobs do Azure usando F#
description: Armazene dados não estruturados na nuvem com o armazenamento de BLOBs do Azure.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 0dda2e04f0052823e9ea35051855d677cd19ea92
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548469"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="49bba-103">Introdução ao armazenamento de BLOBs do Azure usando o F\#</span><span class="sxs-lookup"><span data-stu-id="49bba-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="49bba-104">O Armazenamento de Blobs do Azure é um serviço que armazena dados não estruturados na nuvem como objetos/blobs.</span><span class="sxs-lookup"><span data-stu-id="49bba-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="49bba-105">O Armazenamento de Blobs pode conter qualquer tipo de texto ou de dados binários, como um documento, um arquivo de mídia ou um instalador de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bba-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="49bba-106">O Armazenamento de Blobs também é chamado de armazenamento de objeto.</span><span class="sxs-lookup"><span data-stu-id="49bba-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="49bba-107">Este artigo mostra como executar tarefas comuns usando o armazenamento de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="49bba-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="49bba-108">Os exemplos são escritos usando F # usando a biblioteca de cliente de armazenamento do Azure para .NET.</span><span class="sxs-lookup"><span data-stu-id="49bba-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="49bba-109">As tarefas abordadas incluem como carregar, listar, baixar e excluir BLOBs.</span><span class="sxs-lookup"><span data-stu-id="49bba-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="49bba-110">Para obter uma visão geral conceitual do armazenamento de BLOBs, consulte [o guia .net para armazenamento de BLOBs](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span><span class="sxs-lookup"><span data-stu-id="49bba-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49bba-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="49bba-111">Prerequisites</span></span>

<span data-ttu-id="49bba-112">Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/common/storage-account-create).</span><span class="sxs-lookup"><span data-stu-id="49bba-112">To use this guide, you must first [create an Azure storage account](/azure/storage/common/storage-account-create).</span></span> <span data-ttu-id="49bba-113">Você também precisa da sua chave de acesso de armazenamento para essa conta.</span><span class="sxs-lookup"><span data-stu-id="49bba-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="49bba-114">Criar um script F # e iniciar o F# Interativo</span><span class="sxs-lookup"><span data-stu-id="49bba-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="49bba-115">Os exemplos neste artigo podem ser usados em um aplicativo F # ou em um script F #.</span><span class="sxs-lookup"><span data-stu-id="49bba-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="49bba-116">Para criar um script F #, crie um arquivo com a `.fsx` extensão, por exemplo `blobs.fsx` , em seu ambiente de desenvolvimento em F #.</span><span class="sxs-lookup"><span data-stu-id="49bba-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="49bba-117">Em seguida, use um [Gerenciador de pacotes](package-management.md) , como [paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) , para instalar os `WindowsAzure.Storage` pacotes e a `Microsoft.WindowsAzure.ConfigurationManager` referência e `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` em seu script usando uma `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="49bba-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="49bba-118">Adicionar declarações do namespace</span><span class="sxs-lookup"><span data-stu-id="49bba-118">Add namespace declarations</span></span>

<span data-ttu-id="49bba-119">Adicione as seguintes instruções `open` à parte superior do arquivo `blobs.fsx`:</span><span class="sxs-lookup"><span data-stu-id="49bba-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="49bba-120">Obter a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="49bba-120">Get your connection string</span></span>

<span data-ttu-id="49bba-121">Você precisa de uma cadeia de conexão de armazenamento do Azure para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="49bba-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="49bba-122">Para obter mais informações sobre cadeias de conexão, consulte [Configurar cadeias de conexão de armazenamento](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="49bba-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="49bba-123">Para o tutorial, insira a cadeia de conexão em seu script, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="49bba-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="49bba-124">No entanto, isso **não é recomendado** para projetos reais.</span><span class="sxs-lookup"><span data-stu-id="49bba-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="49bba-125">Sua chave de conta de armazenamento é semelhante para a senha raiz da sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="49bba-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="49bba-126">Sempre tenha cuidado para proteger a chave de sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="49bba-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="49bba-127">Evite distribuí-la a outros usuários, embuti-la no código ou salvá-lo em um arquivo de texto sem formatação que esteja acessível a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="49bba-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="49bba-128">Você pode regenerar sua chave usando o portal do Azure se acreditar que ele pode ter sido comprometido.</span><span class="sxs-lookup"><span data-stu-id="49bba-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="49bba-129">Para aplicativos reais, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="49bba-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="49bba-130">Para buscar a cadeia de conexão de um arquivo de configuração, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="49bba-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="49bba-131">O uso do Gerenciador de Configurações do Azure é opcional.</span><span class="sxs-lookup"><span data-stu-id="49bba-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="49bba-132">Você também pode usar uma API como o tipo de .NET Framework `ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="49bba-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="49bba-133">Analisar a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="49bba-133">Parse the connection string</span></span>

<span data-ttu-id="49bba-134">Para analisar a cadeia de conexão, use:</span><span class="sxs-lookup"><span data-stu-id="49bba-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="49bba-135">Isso retorna um `CloudStorageAccount` .</span><span class="sxs-lookup"><span data-stu-id="49bba-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="49bba-136">Criar alguns dados fictícios locais</span><span class="sxs-lookup"><span data-stu-id="49bba-136">Create some local dummy data</span></span>

<span data-ttu-id="49bba-137">Antes de começar, crie alguns dados locais fictícios no diretório do nosso script.</span><span class="sxs-lookup"><span data-stu-id="49bba-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="49bba-138">Posteriormente, você carregará esses dados.</span><span class="sxs-lookup"><span data-stu-id="49bba-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="49bba-139">Criar o cliente do serviço Blob</span><span class="sxs-lookup"><span data-stu-id="49bba-139">Create the Blob service client</span></span>

<span data-ttu-id="49bba-140">O `CloudBlobClient` tipo permite que você recupere contêineres e blobs armazenados no armazenamento de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="49bba-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="49bba-141">Veja uma maneira de criar o cliente de serviço:</span><span class="sxs-lookup"><span data-stu-id="49bba-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="49bba-142">Agora você está pronto para escrever um código que lê e grava dados no Armazenamento de Blobs.</span><span class="sxs-lookup"><span data-stu-id="49bba-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="49bba-143">Criar um contêiner</span><span class="sxs-lookup"><span data-stu-id="49bba-143">Create a container</span></span>

<span data-ttu-id="49bba-144">Este exemplo mostra como criar um contêiner caso ele ainda não exista:</span><span class="sxs-lookup"><span data-stu-id="49bba-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="49bba-145">Por padrão, o novo contêiner é privado, o que significa que você deve especificar sua chave de acesso de armazenamento para baixar blobs desse contêiner.</span><span class="sxs-lookup"><span data-stu-id="49bba-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="49bba-146">Para disponibilizar os arquivos do contêiner para todos, você pode definir o contêiner como público usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="49bba-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="49bba-147">Qualquer pessoa na Internet pode ver os blobs em um contêiner público, mas você só poderá modificá-los ou excluí-los se tiver a chave de acesso ou a assinatura de acesso compartilhado adequada.</span><span class="sxs-lookup"><span data-stu-id="49bba-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="49bba-148">Carregar um blob em um contêiner</span><span class="sxs-lookup"><span data-stu-id="49bba-148">Upload a blob into a container</span></span>

<span data-ttu-id="49bba-149">O Armazenamento de Blob do Azure oferece suporte a blobs de blocos e a blobs de páginas.</span><span class="sxs-lookup"><span data-stu-id="49bba-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="49bba-150">Na maioria dos casos, um blob de blocos é o tipo recomendado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="49bba-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="49bba-151">Para carregar um arquivo em um blob de blocos, obtenha uma referência de contêiner e use-a para obter uma referência de blob de blocos.</span><span class="sxs-lookup"><span data-stu-id="49bba-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="49bba-152">Depois de ter uma referência de BLOB, você pode carregar qualquer fluxo de dados para ele chamando o `UploadFromFile` método.</span><span class="sxs-lookup"><span data-stu-id="49bba-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="49bba-153">Essa operação criará o blob se ele não existir anteriormente ou substituirá-o se existir.</span><span class="sxs-lookup"><span data-stu-id="49bba-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="49bba-154">Listar os blobs em um contêiner</span><span class="sxs-lookup"><span data-stu-id="49bba-154">List the blobs in a container</span></span>

<span data-ttu-id="49bba-155">Para listar blobs em um contêiner, primeiro obtenha uma referência ao contêiner.</span><span class="sxs-lookup"><span data-stu-id="49bba-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="49bba-156">Em seguida, você pode usar o `ListBlobs` método do contêiner para recuperar os BLOBs e/ou diretórios dentro dele.</span><span class="sxs-lookup"><span data-stu-id="49bba-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="49bba-157">Para acessar o rico conjunto de propriedades e métodos para um retornado `IListBlobItem` , você deve convertê-lo em um `CloudBlockBlob` `CloudPageBlob` objeto, ou `CloudBlobDirectory` .</span><span class="sxs-lookup"><span data-stu-id="49bba-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="49bba-158">Se o tipo for desconhecido, você poderá usar uma verificação de tipo para determinar no qual convertê-lo.</span><span class="sxs-lookup"><span data-stu-id="49bba-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="49bba-159">O código a seguir demonstra como recuperar e apresentar a saída do URI de cada item no contêiner `mydata` :</span><span class="sxs-lookup"><span data-stu-id="49bba-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="49bba-160">Você também pode nomear BLOBs com informações de caminho em seus nomes.</span><span class="sxs-lookup"><span data-stu-id="49bba-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="49bba-161">Isso cria uma estrutura de diretório virtual que você pode organizar e percorrer como faria com um sistema de arquivos tradicional.</span><span class="sxs-lookup"><span data-stu-id="49bba-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="49bba-162">Observe que a estrutura do diretório é virtual apenas - os somente os recursos disponíveis no armazenamento de Blob são contêineres e blobs.</span><span class="sxs-lookup"><span data-stu-id="49bba-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="49bba-163">No entanto, a biblioteca de cliente de armazenamento oferece um `CloudBlobDirectory` objeto para se referir a um diretório virtual e simplificar o processo de trabalho com blobs que são organizados dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="49bba-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="49bba-164">Por exemplo, considere o seguinte conjunto de blobs de blocos em um contêiner chamado `photos`:</span><span class="sxs-lookup"><span data-stu-id="49bba-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="49bba-165">*photo1.jpg*</span><span class="sxs-lookup"><span data-stu-id="49bba-165">*photo1.jpg*</span></span>\
<span data-ttu-id="49bba-166">*2015/arquitetura/description.txt*</span><span class="sxs-lookup"><span data-stu-id="49bba-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="49bba-167">*2015/arquitetura/photo3.jpg*</span><span class="sxs-lookup"><span data-stu-id="49bba-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="49bba-168">*2015/arquitetura/photo4.jpg*</span><span class="sxs-lookup"><span data-stu-id="49bba-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="49bba-169">*2016/arquitetura/photo5.jpg*</span><span class="sxs-lookup"><span data-stu-id="49bba-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="49bba-170">*2016/arquitetura/photo6.jpg*</span><span class="sxs-lookup"><span data-stu-id="49bba-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="49bba-171">*2016/arquitetura/description.txt*</span><span class="sxs-lookup"><span data-stu-id="49bba-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="49bba-172">*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="49bba-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="49bba-173">Quando você chama `ListBlobs` em um contêiner (como no exemplo acima), uma listagem hierárquica é retornada.</span><span class="sxs-lookup"><span data-stu-id="49bba-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="49bba-174">Se ele contiver ambos os `CloudBlobDirectory` `CloudBlockBlob` objetos e, representando os diretórios e blobs no contêiner, respectivamente, a saída resultante será semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="49bba-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="49bba-175">Opcionalmente, você pode definir o `UseFlatBlobListing` parâmetro do `ListBlobs` método como `true` .</span><span class="sxs-lookup"><span data-stu-id="49bba-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="49bba-176">Nesse caso, cada blob no contêiner é retornado como um `CloudBlockBlob` objeto.</span><span class="sxs-lookup"><span data-stu-id="49bba-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="49bba-177">A chamada para `ListBlobs` para retornar uma listagem simples é parecida com esta:</span><span class="sxs-lookup"><span data-stu-id="49bba-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="49bba-178">e, dependendo do conteúdo atual do seu contêiner, os resultados têm a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="49bba-178">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="49bba-179">Baixar blobs</span><span class="sxs-lookup"><span data-stu-id="49bba-179">Download blobs</span></span>

<span data-ttu-id="49bba-180">Para baixar BLOBs, primeiro recupere uma referência de BLOB e, em seguida, chame o `DownloadToStream` método.</span><span class="sxs-lookup"><span data-stu-id="49bba-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="49bba-181">O exemplo a seguir usa o `DownloadToStream` método para transferir o conteúdo do blob para um objeto de fluxo que você pode persistir em um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="49bba-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="49bba-182">Você também pode usar o `DownloadToStream` método para baixar o conteúdo de um blob como uma cadeia de texto.</span><span class="sxs-lookup"><span data-stu-id="49bba-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="49bba-183">Excluir blobs</span><span class="sxs-lookup"><span data-stu-id="49bba-183">Delete blobs</span></span>

<span data-ttu-id="49bba-184">Para excluir um blob, primeiro obtenha uma referência de BLOB e, em seguida, chame o `Delete` método nele.</span><span class="sxs-lookup"><span data-stu-id="49bba-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="49bba-185">Listar blobs em páginas de maneira assíncrona</span><span class="sxs-lookup"><span data-stu-id="49bba-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="49bba-186">Se você está listando uma grande quantidade de blobs ou se deseja controlar o número de resultados retornados em uma operação de listagem, pode listar os blobs em páginas de resultados.</span><span class="sxs-lookup"><span data-stu-id="49bba-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="49bba-187">Este exemplo mostra como retornar resultados em páginas de forma assíncrona, para que a execução não fique bloqueada enquanto espera para retornar um grande conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="49bba-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="49bba-188">Este exemplo mostra uma listagem de blob simples, mas você também pode executar uma listagem hierárquica, definindo o `useFlatBlobListing` parâmetro do `ListBlobsSegmentedAsync` método como `false` .</span><span class="sxs-lookup"><span data-stu-id="49bba-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="49bba-189">O exemplo define um método assíncrono, usando um `async` bloco.</span><span class="sxs-lookup"><span data-stu-id="49bba-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="49bba-190">A ``let!`` palavra-chave suspende a execução do método de exemplo até que a tarefa de listagem seja concluída.</span><span class="sxs-lookup"><span data-stu-id="49bba-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="49bba-191">Agora podemos usar essa rotina assíncrona da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="49bba-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="49bba-192">Primeiro, você carrega alguns dados fictícios (usando o arquivo local criado anteriormente neste tutorial).</span><span class="sxs-lookup"><span data-stu-id="49bba-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="49bba-193">Agora, chame a rotina.</span><span class="sxs-lookup"><span data-stu-id="49bba-193">Now, call the routine.</span></span> <span data-ttu-id="49bba-194">Você usa `Async.RunSynchronously` para forçar a execução da operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="49bba-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="49bba-195">Gravar um blob de acréscimo</span><span class="sxs-lookup"><span data-stu-id="49bba-195">Writing to an append blob</span></span>

<span data-ttu-id="49bba-196">Um blob de acréscimo é otimizado para operações de acréscimo, como o registro em log.</span><span class="sxs-lookup"><span data-stu-id="49bba-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="49bba-197">Como um blob de blocos, um blob de acréscimo é composto por blocos; no entanto, quando você adiciona um novo bloco a um blob de acréscimo, ele sempre é acrescentado ao fim do blob.</span><span class="sxs-lookup"><span data-stu-id="49bba-197">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="49bba-198">Não é possível atualizar ou excluir um bloco existente em um blob de acréscimo.</span><span class="sxs-lookup"><span data-stu-id="49bba-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="49bba-199">As IDs de bloco de um blob de acréscimo não ficam expostas como em um blob de blocos.</span><span class="sxs-lookup"><span data-stu-id="49bba-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="49bba-200">Cada bloco em um blob de acréscimo pode ter um tamanho diferente, até no máximo 4 MB, e um blob de acréscimo pode incluir no máximo 50.000 blocos.</span><span class="sxs-lookup"><span data-stu-id="49bba-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="49bba-201">O tamanho máximo de um blob de acréscimo, portanto, é de pouco mais de 195 GB (4 MB x 50.000 blocos).</span><span class="sxs-lookup"><span data-stu-id="49bba-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="49bba-202">O exemplo a seguir cria um novo BLOB de acréscimo e acrescenta alguns dados a ele, simulando uma operação de log simples.</span><span class="sxs-lookup"><span data-stu-id="49bba-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="49bba-203">Para saber mais sobre as diferenças entre os três tipos de blobs, confira [Noções gerais sobre blobs de blocos, blobs de páginas e blobs de acréscimo](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) .</span><span class="sxs-lookup"><span data-stu-id="49bba-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="49bba-204">Acesso simultâneo</span><span class="sxs-lookup"><span data-stu-id="49bba-204">Concurrent access</span></span>

<span data-ttu-id="49bba-205">Para suportar o acesso simultâneo a uma blob por meio de vários clientes ou várias instâncias do processo, você pode usar **ETags** ou **concessões**.</span><span class="sxs-lookup"><span data-stu-id="49bba-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

- <span data-ttu-id="49bba-206">**Etag** – fornece uma maneira de detectar se o blob ou o contêiner foi modificado por outro processo</span><span class="sxs-lookup"><span data-stu-id="49bba-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

- <span data-ttu-id="49bba-207">**Concessão** – fornece acesso exclusivo e renovável para a gravação ou a exclusão de um blob por determinado período</span><span class="sxs-lookup"><span data-stu-id="49bba-207">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="49bba-208">Para obter mais informações, consulte [Gerenciando a simultaneidade no armazenamento do Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="49bba-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="49bba-209">Contêineres de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="49bba-209">Naming containers</span></span>

<span data-ttu-id="49bba-210">Todos os blobs no armazenamento do Azure devem residir em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="49bba-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="49bba-211">O contêiner faz parte do nome do blob.</span><span class="sxs-lookup"><span data-stu-id="49bba-211">The container forms part of the blob name.</span></span> <span data-ttu-id="49bba-212">Por exemplo, `mydata` é o nome do contêiner nesses URIs do blob de exemplo:</span><span class="sxs-lookup"><span data-stu-id="49bba-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

<span data-ttu-id="49bba-213">Um nome de contêiner deve ser um nome DNS válido e estar em conformidade com as seguintes regras de nomenclatura:</span><span class="sxs-lookup"><span data-stu-id="49bba-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="49bba-214">Os nomes de contêiner devem começar com uma letra ou número e podem conter apenas letras, números e o caractere traço (-).</span><span class="sxs-lookup"><span data-stu-id="49bba-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="49bba-215">Cada caractere traço (-) deve ser imediatamente precedido e seguido por uma letra ou número. Não são permitidos traços consecutivos em nomes de contêiner.</span><span class="sxs-lookup"><span data-stu-id="49bba-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="49bba-216">Todas as letras do nome de um contêiner devem ser minúsculas.</span><span class="sxs-lookup"><span data-stu-id="49bba-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="49bba-217">Os nomes de contêiner devem ter de 3 a 63 caracteres.</span><span class="sxs-lookup"><span data-stu-id="49bba-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="49bba-218">Observe que o nome de um contêiner deve sempre estar em minúsculas.</span><span class="sxs-lookup"><span data-stu-id="49bba-218">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="49bba-219">Se você incluir uma letra maiúscula em um nome de contêiner ou de alguma forma violar as regras de nomenclatura do contêiner, você receberá um erro 400 (solicitação incorreta).</span><span class="sxs-lookup"><span data-stu-id="49bba-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="49bba-220">Gerenciamento da segurança de blobs</span><span class="sxs-lookup"><span data-stu-id="49bba-220">Managing security for blobs</span></span>

<span data-ttu-id="49bba-221">Por padrão, o Armazenamento do Azure mantém seus dados seguros limitando o acesso ao proprietário da conta, que possui as chaves de acesso à conta.</span><span class="sxs-lookup"><span data-stu-id="49bba-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="49bba-222">Quando você precisa compartilhar dados de blob em sua conta de armazenamento, é importante fazer isso sem comprometer a segurança de suas chaves de acesso à conta.</span><span class="sxs-lookup"><span data-stu-id="49bba-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="49bba-223">Além disso, você pode criptografar os dados de blob para garantir que eles fiquem seguros durante a transmissão e no Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="49bba-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="49bba-224">Controle do acesso a dados de blob</span><span class="sxs-lookup"><span data-stu-id="49bba-224">Controlling access to blob data</span></span>

<span data-ttu-id="49bba-225">Por padrão, os dados de blob em sua conta de armazenamento só podem ser acessados pelo proprietário da conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="49bba-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="49bba-226">A autenticação de solicitações no Armazenamento de Blobs requer a chave de acesso da conta, por padrão.</span><span class="sxs-lookup"><span data-stu-id="49bba-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="49bba-227">No entanto, talvez você queira disponibilizar determinados dados de BLOB para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="49bba-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="49bba-228">Criptografia de dados de blobs</span><span class="sxs-lookup"><span data-stu-id="49bba-228">Encrypting blob data</span></span>

<span data-ttu-id="49bba-229">O armazenamento do Azure dá suporte à criptografia de dados de blob no cliente e no servidor.</span><span class="sxs-lookup"><span data-stu-id="49bba-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="49bba-230">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="49bba-230">Next steps</span></span>

<span data-ttu-id="49bba-231">Agora que você aprendeu os conceitos básicos do armazenamento de Blobs, siga estes links para saber mais.</span><span class="sxs-lookup"><span data-stu-id="49bba-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="49bba-232">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="49bba-232">Tools</span></span>

- <span data-ttu-id="49bba-233">[AzureStorageTypeProvider F #](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="49bba-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="49bba-234">Um provedor de tipo F # que pode ser usado para explorar os ativos de armazenamento de BLOB, tabela e fila do Azure e aplicar facilmente as operações CRUD neles.</span><span class="sxs-lookup"><span data-stu-id="49bba-234">An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="49bba-235">[FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="49bba-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="49bba-236">Uma API F # para usar Microsoft Azure serviço de armazenamento de tabelas</span><span class="sxs-lookup"><span data-stu-id="49bba-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="49bba-237">[Gerenciador de Armazenamento do Microsoft Azure (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="49bba-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="49bba-238">Um aplicativo autônomo e gratuito da Microsoft que permite que você trabalhe visualmente com os dados do armazenamento do Azure no Windows, no OS X e no Linux.</span><span class="sxs-lookup"><span data-stu-id="49bba-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="49bba-239">Referência do Armazenamento de Blobs</span><span class="sxs-lookup"><span data-stu-id="49bba-239">Blob storage reference</span></span>

- [<span data-ttu-id="49bba-240">APIs do Armazenamento do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="49bba-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="49bba-241">Referência de API REST dos Serviços de Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="49bba-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/)

### <a name="related-guides"></a><span data-ttu-id="49bba-242">Guias relacionados</span><span class="sxs-lookup"><span data-stu-id="49bba-242">Related guides</span></span>

- [<span data-ttu-id="49bba-243">Exemplos de armazenamento de Blobs do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="49bba-243">Azure Blob Storage Samples for .NET</span></span>](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="49bba-244">Introdução ao AzCopy</span><span class="sxs-lookup"><span data-stu-id="49bba-244">Get started with AzCopy</span></span>](/azure/storage/common/storage-use-azcopy-v10)
- [<span data-ttu-id="49bba-245">Configurar cadeias de conexão do Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="49bba-245">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="49bba-246">Blog da equipe de Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="49bba-246">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="49bba-247">Início rápido: usar o .NET para criar um blob no armazenamento de objetos</span><span class="sxs-lookup"><span data-stu-id="49bba-247">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
