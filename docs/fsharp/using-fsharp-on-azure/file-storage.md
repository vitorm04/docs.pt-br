---
title: "Introdução ao armazenamento de arquivo do Azure usando F #"
description: "Armazenar dados de arquivo na nuvem com o armazenamento de arquivo do Azure e montar o compartilhamento de arquivos da nuvem de uma máquina virtual do Azure (VM) ou de um aplicativo local que executam o Windows."
keywords: "o Visual f #, f #, funcional programação .NET, .NET Core, o Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5c26a0aa-186e-476c-9f87-e0191754579e
ms.openlocfilehash: 66b2503744e9024deac3d6dabea57da4fd393bd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="2f8f4-104">Introdução ao armazenamento de arquivo do Azure usando F #</span><span class="sxs-lookup"><span data-stu-id="2f8f4-104">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="2f8f4-105">Armazenamento de arquivo do Azure é um serviço que oferece a compartilhamentos de arquivos na nuvem usando o padrão [protocolo de bloco de mensagens de servidor (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f8f4-105">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="2f8f4-106">Há suporte para SMB 2.1 e o SMB 3.0.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-106">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="2f8f4-107">Com o armazenamento de arquivo do Azure, você pode migrar aplicativos herdados que dependem de compartilhamentos de arquivos para o Azure rapidamente e sem regravações caras.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-107">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="2f8f4-108">Aplicativos executados em máquinas virtuais do Azure ou serviços de nuvem ou de clientes locais podem montar um compartilhamento de arquivo na nuvem, assim como um aplicativo de desktop monta um compartilhamento SMB típico.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-108">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="2f8f4-109">Qualquer número de componentes de aplicativos pode montar e acessar o compartilhamento de arquivo de armazenamento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-109">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="2f8f4-110">Para obter uma visão geral conceitual de armazenamento de arquivos, consulte [guia .NET para armazenamento de arquivo](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="2f8f4-110">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f8f4-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2f8f4-111">Prerequisites</span></span>

<span data-ttu-id="2f8f4-112">Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="2f8f4-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="2f8f4-113">Você também precisará sua chave de acesso de armazenamento para esta conta.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-113">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="2f8f4-114">Criar Script F # e começar a F # interativo</span><span class="sxs-lookup"><span data-stu-id="2f8f4-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="2f8f4-115">Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="2f8f4-116">Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `files.fsx`, em seu ambiente de desenvolvimento do F #.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-116">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="2f8f4-117">Em seguida, use uma [Gerenciador de pacote](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando um `#r`diretiva.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="2f8f4-118">Adicione declarações de namespace</span><span class="sxs-lookup"><span data-stu-id="2f8f4-118">Add namespace declarations</span></span>

<span data-ttu-id="2f8f4-119">Adicione o seguinte `open` instruções na parte superior do `files.fsx` arquivo:</span><span class="sxs-lookup"><span data-stu-id="2f8f4-119">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="2f8f4-120">Obter a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="2f8f4-120">Get your connection string</span></span>

<span data-ttu-id="2f8f4-121">Você precisará de uma cadeia de caracteres de conexão de armazenamento do Azure para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-121">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="2f8f4-122">Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="2f8f4-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="2f8f4-123">Para o tutorial, você vai inserir sua cadeia de caracteres de conexão no seu script, como este:</span><span class="sxs-lookup"><span data-stu-id="2f8f4-123">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="2f8f4-124">No entanto, isso é **não recomendável** projetos para o real.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="2f8f4-125">Sua chave de conta de armazenamento é semelhante para a senha de raiz de sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="2f8f4-126">Sempre tenha cuidado para proteger a chave de conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="2f8f4-127">Evite distribuí-lo a outros usuários, codificar, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="2f8f4-128">Você pode regenerar a chave usando o Portal do Azure se você acredita que ele pode ter sido comprometido.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="2f8f4-129">Aplicativos para o real, a melhor maneira de manter sua cadeia de caracteres de conexão de armazenamento está em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="2f8f4-130">Para obter a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="2f8f4-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="2f8f4-131">Usando o Gerenciador de configuração do Azure é opcional.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="2f8f4-132">Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="2f8f4-133">Analisar a cadeia de caracteres de conexão</span><span class="sxs-lookup"><span data-stu-id="2f8f4-133">Parse the connection string</span></span>

<span data-ttu-id="2f8f4-134">Para analisar a cadeia de caracteres de conexão, use:</span><span class="sxs-lookup"><span data-stu-id="2f8f4-134">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="2f8f4-135">Isso retornará um `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-135">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="2f8f4-136">Criar o cliente de serviços de arquivo</span><span class="sxs-lookup"><span data-stu-id="2f8f4-136">Create the File service client</span></span>

<span data-ttu-id="2f8f4-137">O `CloudFileClient` tipo permite que você use programaticamente os arquivos armazenados no armazenamento de arquivo.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-137">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="2f8f4-138">Aqui está uma maneira de criar o cliente do serviço:</span><span class="sxs-lookup"><span data-stu-id="2f8f4-138">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="2f8f4-139">Agora você está pronto para escrever código que lê e grava dados no armazenamento de arquivo.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-139">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="2f8f4-140">Criar um compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="2f8f4-140">Create a file share</span></span>

<span data-ttu-id="2f8f4-141">Este exemplo mostra como criar um compartilhamento de arquivos se ele ainda não existir:</span><span class="sxs-lookup"><span data-stu-id="2f8f4-141">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="2f8f4-142">Criar um diretório raiz e um subdiretório</span><span class="sxs-lookup"><span data-stu-id="2f8f4-142">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="2f8f4-143">Aqui, você pode obter o diretório raiz e obter um subdiretório da raiz.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-143">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="2f8f4-144">Criar ambos se ainda não existirem.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-144">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="2f8f4-145">Carregue o texto como um arquivo</span><span class="sxs-lookup"><span data-stu-id="2f8f4-145">Upload text as a file</span></span>

<span data-ttu-id="2f8f4-146">Este exemplo mostra como carregar um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-146">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="2f8f4-147">Baixar um arquivo para uma cópia local do arquivo</span><span class="sxs-lookup"><span data-stu-id="2f8f4-147">Download a file to a local copy of the file</span></span>

<span data-ttu-id="2f8f4-148">Aqui você baixar o arquivo que acabou de criar, acrescentando o conteúdo em um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-148">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="2f8f4-149">Definir o tamanho máximo para um compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="2f8f4-149">Set the maximum size for a file share</span></span>

<span data-ttu-id="2f8f4-150">O exemplo a seguir mostra como verificar o uso atual para um compartilhamento e como definir uma cota para o compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-150">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="2f8f4-151">`FetchAttributes`deve ser chamado para popular um compartilhamento `Properties`, e `SetProperties` para propagar as alterações locais para o armazenamento de arquivo do Azure.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-151">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="2f8f4-152">Gerar uma assinatura de acesso compartilhado para um arquivo ou compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="2f8f4-152">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="2f8f4-153">Você pode gerar uma assinatura de acesso compartilhado (SAS) para um compartilhamento de arquivos ou para um arquivo individual.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-153">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="2f8f4-154">Você também pode criar uma política de acesso compartilhado em um compartilhamento de arquivos para gerenciar assinaturas de acesso compartilhado.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-154">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="2f8f4-155">Criar uma política de acesso compartilhado é recomendada, pois ele fornece um meio de revogar a SAS se ela deve ser comprometida.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-155">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="2f8f4-156">Aqui, você cria um compartilhado política em um compartilhamento de acesso e, em seguida, use essa política para fornecer as restrições para uma SAS em um arquivo no compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-156">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="2f8f4-157">Para obter mais informações sobre como criar e usar assinaturas de acesso compartilhado, consulte [assinaturas usando de acesso compartilhado (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) e [criar e usar uma SAS com armazenamento de Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="2f8f4-157">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="2f8f4-158">Copiar arquivos</span><span class="sxs-lookup"><span data-stu-id="2f8f4-158">Copy files</span></span>

<span data-ttu-id="2f8f4-159">Você pode copiar um arquivo para outro arquivo ou para um blob ou um blob em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-159">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="2f8f4-160">Se você estiver copiando um blob para um arquivo ou um arquivo em um blob, você *deve* usar uma assinatura de acesso compartilhado (SAS) para autenticar o objeto de origem, mesmo se você estiver copiando dentro da mesma conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-160">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="2f8f4-161">Copiar um arquivo para outro arquivo</span><span class="sxs-lookup"><span data-stu-id="2f8f4-161">Copy a file to another file</span></span>

<span data-ttu-id="2f8f4-162">Aqui, você deve copiar um arquivo para outro arquivo no mesmo compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-162">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="2f8f4-163">Como essa operação de cópia copia entre arquivos na mesma conta de armazenamento, você pode usar a autenticação de chave compartilhada para executar a cópia.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-163">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="2f8f4-164">Copiar um arquivo para um blob</span><span class="sxs-lookup"><span data-stu-id="2f8f4-164">Copy a file to a blob</span></span>

<span data-ttu-id="2f8f4-165">Aqui, você pode criar um arquivo e copie-o para um blob dentro da mesma conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-165">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="2f8f4-166">Criar uma SAS para o arquivo de origem, o serviço usa para autenticar o acesso ao arquivo de origem durante a operação de cópia.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-166">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="2f8f4-167">Você pode copiar um blob em um arquivo da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-167">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="2f8f4-168">Se o objeto de origem for um blob, em seguida, crie uma SAS para autenticar o acesso ao blob durante a operação de cópia.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-168">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="2f8f4-169">Uso de métricas de armazenamento de arquivos de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="2f8f4-169">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="2f8f4-170">Análise de armazenamento do Azure oferece suporte a métricas para armazenamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-170">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="2f8f4-171">Com dados de métricas, você pode rastrear solicitações e diagnosticar problemas.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-171">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="2f8f4-172">Você pode habilitar as métricas para o armazenamento de arquivos do [Portal do Azure](https://portal.azure.com), ou você pode fazer isso no F # como este:</span><span class="sxs-lookup"><span data-stu-id="2f8f4-172">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="2f8f4-173">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2f8f4-173">Next steps</span></span>

<span data-ttu-id="2f8f4-174">Consulte esses links para obter mais informações sobre o armazenamento de arquivo do Azure.</span><span class="sxs-lookup"><span data-stu-id="2f8f4-174">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="2f8f4-175">Vídeos e artigos conceituais</span><span class="sxs-lookup"><span data-stu-id="2f8f4-175">Conceptual articles and videos</span></span>

- [<span data-ttu-id="2f8f4-176">Armazenamento de arquivos do Azure: sistema de arquivos de uma nuvem ininterrupto SMB para Windows e Linux</span><span class="sxs-lookup"><span data-stu-id="2f8f4-176">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="2f8f4-177">Como usar o armazenamento de arquivos do Azure com Linux</span><span class="sxs-lookup"><span data-stu-id="2f8f4-177">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="2f8f4-178">Ferramentas de suporte para armazenamento de arquivo</span><span class="sxs-lookup"><span data-stu-id="2f8f4-178">Tooling support for File storage</span></span>

- [<span data-ttu-id="2f8f4-179">Usando o PowerShell do Azure com o armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="2f8f4-179">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="2f8f4-180">Como usar AzCopy com armazenamento do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2f8f4-180">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="2f8f4-181">Usando a CLI do Azure com o armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="2f8f4-181">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="2f8f4-182">Referência</span><span class="sxs-lookup"><span data-stu-id="2f8f4-182">Reference</span></span>

- [<span data-ttu-id="2f8f4-183">Biblioteca de cliente de armazenamento para a referência do .NET</span><span class="sxs-lookup"><span data-stu-id="2f8f4-183">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="2f8f4-184">Referência da API REST de serviços de arquivo</span><span class="sxs-lookup"><span data-stu-id="2f8f4-184">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="2f8f4-185">Postagens de blog</span><span class="sxs-lookup"><span data-stu-id="2f8f4-185">Blog posts</span></span>

- [<span data-ttu-id="2f8f4-186">Armazenamento de arquivo do Azure agora está disponível</span><span class="sxs-lookup"><span data-stu-id="2f8f4-186">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="2f8f4-187">Armazenamento de arquivos do Azure dentro</span><span class="sxs-lookup"><span data-stu-id="2f8f4-187">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="2f8f4-188">Introdução ao serviço de arquivo do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2f8f4-188">Introducing Microsoft Azure File Service</span></span>](http://blogs.msdn.com/b/windowsazurestorage/archive/2014/05/12/introducing-microsoft-azure-file-service.aspx)
- [<span data-ttu-id="2f8f4-189">Conexões persistentes aos arquivos do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2f8f4-189">Persisting connections to Microsoft Azure Files</span></span>](http://blogs.msdn.com/b/windowsazurestorage/archive/2014/05/27/persisting-connections-to-microsoft-azure-files.aspx)
