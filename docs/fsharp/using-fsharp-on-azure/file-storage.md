---
title: Introdução ao armazenamento de Arquivos do Azure usando F#
description: Armazene dados de arquivos na nuvem com o armazenamento de Arquivos do Azure e monte seu compartilhamento de arquivos na nuvem de uma VM (máquina virtual) do Azure ou de um aplicativo local que executa o Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 04bee82fd9d3c652cd99b9c951880f6ba89610ee
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548456"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="ed627-103">Introdução ao armazenamento de arquivos do Azure usando o F\#</span><span class="sxs-lookup"><span data-stu-id="ed627-103">Get started with Azure File storage using F\#</span></span>

<span data-ttu-id="ed627-104">O armazenamento de arquivos do Azure é um serviço que oferece compartilhamentos de arquivos na nuvem usando o [protocolo SMB (Server Message Block)](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview)padrão.</span><span class="sxs-lookup"><span data-stu-id="ed627-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview).</span></span> <span data-ttu-id="ed627-105">Há suporte ao SMB 2.1 e ao 3.0 SMB.</span><span class="sxs-lookup"><span data-stu-id="ed627-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="ed627-106">Com o armazenamento de Arquivos do Azure, você pode migrar aplicativos herdados que dependem de compartilhamentos de arquivos para o Azure rapidamente e sem regravações caras.</span><span class="sxs-lookup"><span data-stu-id="ed627-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="ed627-107">Os aplicativos executados em máquinas virtuais do Azure ou serviços de nuvem ou em clientes locais podem montar um compartilhamento de arquivos na nuvem, exatamente como um aplicativo de desktop monta um compartilhamento SMB típico.</span><span class="sxs-lookup"><span data-stu-id="ed627-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="ed627-108">Qualquer quantidade de componentes de aplicativos pode montar e acessar o compartilhamento de armazenamento de arquivos simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="ed627-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="ed627-109">Para obter uma visão geral conceitual do armazenamento de arquivos, consulte [o guia .net para armazenamento de arquivos](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="ed627-109">For a conceptual overview of file storage, see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ed627-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ed627-110">Prerequisites</span></span>

<span data-ttu-id="ed627-111">Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="ed627-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="ed627-112">Você também precisará da sua chave de acesso de armazenamento para essa conta.</span><span class="sxs-lookup"><span data-stu-id="ed627-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="ed627-113">Criar um script F # e iniciar o F# Interativo</span><span class="sxs-lookup"><span data-stu-id="ed627-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="ed627-114">Os exemplos neste artigo podem ser usados em um aplicativo F # ou em um script F #.</span><span class="sxs-lookup"><span data-stu-id="ed627-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="ed627-115">Para criar um script F #, crie um arquivo com a `.fsx` extensão, por exemplo `files.fsx` , em seu ambiente de desenvolvimento em F #.</span><span class="sxs-lookup"><span data-stu-id="ed627-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="ed627-116">Em seguida, use um [Gerenciador de pacotes](package-management.md) , como [paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) , para instalar o `WindowsAzure.Storage` pacote e a referência `WindowsAzure.Storage.dll` em seu script usando uma `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="ed627-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="ed627-117">Adicionar declarações do namespace</span><span class="sxs-lookup"><span data-stu-id="ed627-117">Add namespace declarations</span></span>

<span data-ttu-id="ed627-118">Adicione as seguintes instruções `open` à parte superior do arquivo `files.fsx`:</span><span class="sxs-lookup"><span data-stu-id="ed627-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="ed627-119">Obter a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="ed627-119">Get your connection string</span></span>

<span data-ttu-id="ed627-120">Você precisará de uma cadeia de conexão de armazenamento do Azure para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="ed627-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="ed627-121">Para obter mais informações sobre cadeias de conexão, consulte [Configurar cadeias de conexão de armazenamento](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="ed627-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="ed627-122">Para o tutorial, você inserirá sua cadeia de conexão em seu script, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ed627-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="ed627-123">No entanto, isso **não é recomendado** para projetos reais.</span><span class="sxs-lookup"><span data-stu-id="ed627-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="ed627-124">Sua chave de conta de armazenamento é semelhante para a senha raiz da sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ed627-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="ed627-125">Sempre tenha cuidado para proteger a chave de sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ed627-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="ed627-126">Evite distribuí-la a outros usuários, embuti-la no código ou salvá-lo em um arquivo de texto sem formatação que esteja acessível a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="ed627-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="ed627-127">Você pode regenerar sua chave usando o portal do Azure se acreditar que ele pode ter sido comprometido.</span><span class="sxs-lookup"><span data-stu-id="ed627-127">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="ed627-128">Para aplicativos reais, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ed627-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="ed627-129">Para buscar a cadeia de conexão de um arquivo de configuração, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="ed627-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="ed627-130">O uso do Gerenciador de Configurações do Azure é opcional.</span><span class="sxs-lookup"><span data-stu-id="ed627-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="ed627-131">Você também pode usar uma API como o tipo de .NET Framework `ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="ed627-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="ed627-132">Analisar a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="ed627-132">Parse the connection string</span></span>

<span data-ttu-id="ed627-133">Para analisar a cadeia de conexão, use:</span><span class="sxs-lookup"><span data-stu-id="ed627-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="ed627-134">Isso retornará um `CloudStorageAccount` .</span><span class="sxs-lookup"><span data-stu-id="ed627-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="ed627-135">Criar o cliente do serviço de arquivo</span><span class="sxs-lookup"><span data-stu-id="ed627-135">Create the File service client</span></span>

<span data-ttu-id="ed627-136">O `CloudFileClient` tipo permite que você use programaticamente arquivos armazenados no armazenamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="ed627-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="ed627-137">Veja uma maneira de criar o cliente de serviço:</span><span class="sxs-lookup"><span data-stu-id="ed627-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="ed627-138">Agora você está pronto para escrever código que lê e grava dados no armazenamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="ed627-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="ed627-139">Criar um compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="ed627-139">Create a file share</span></span>

<span data-ttu-id="ed627-140">Este exemplo mostra como criar um compartilhamento de arquivos se ele ainda não existir:</span><span class="sxs-lookup"><span data-stu-id="ed627-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="ed627-141">Criar um diretório raiz e um subdiretório</span><span class="sxs-lookup"><span data-stu-id="ed627-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="ed627-142">Aqui, você obtém o diretório raiz e Obtém um subdiretório da raiz.</span><span class="sxs-lookup"><span data-stu-id="ed627-142">Here, you get the root directory and get a subdirectory of the root.</span></span> <span data-ttu-id="ed627-143">Você cria ambos se eles ainda não existirem.</span><span class="sxs-lookup"><span data-stu-id="ed627-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="ed627-144">Carregar texto como um arquivo</span><span class="sxs-lookup"><span data-stu-id="ed627-144">Upload text as a file</span></span>

<span data-ttu-id="ed627-145">Este exemplo mostra como carregar texto como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ed627-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="ed627-146">Baixar um arquivo para uma cópia local do arquivo</span><span class="sxs-lookup"><span data-stu-id="ed627-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="ed627-147">Aqui você baixa o arquivo recém-criado, acrescentando o conteúdo a um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="ed627-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="ed627-148">Definir o tamanho máximo de um compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="ed627-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="ed627-149">O exemplo a seguir mostra como verificar o uso atual de um compartilhamento e como definir a cota para o compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="ed627-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="ed627-150">`FetchAttributes` deve ser chamado para preencher um compartilhamento `Properties` e `SetProperties` para propagar alterações locais para o armazenamento de arquivos do Azure.</span><span class="sxs-lookup"><span data-stu-id="ed627-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="ed627-151">Gerar uma assinatura de acesso compartilhado para um arquivo ou compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="ed627-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="ed627-152">Você pode gerar uma SAS (assinatura de acesso compartilhado) para um compartilhamento de arquivo ou para um arquivo individual.</span><span class="sxs-lookup"><span data-stu-id="ed627-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="ed627-153">Você também pode criar uma política de acesso compartilhado em um compartilhamento de arquivos para gerenciar assinaturas de acesso compartilhado.</span><span class="sxs-lookup"><span data-stu-id="ed627-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="ed627-154">Recomendamos a criação de uma política de acesso compartilhado, pois ela fornece um meio de revogar o SAS se ele for comprometido.</span><span class="sxs-lookup"><span data-stu-id="ed627-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="ed627-155">Aqui, você cria uma política de acesso compartilhado em um compartilhamento e, em seguida, usa essa política para fornecer as restrições para uma SAS em um arquivo no compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="ed627-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="ed627-156">Para saber mais sobre como criar e usar as assinaturas de acesso compartilhado, confira [Como usar SAS (Assinaturas de Acesso Compartilhado)](/azure/storage/storage-dotnet-shared-access-signature-part-1) e [Criar e usar uma SAS com o Armazenamento de Blobs](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="ed627-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="ed627-157">Copiar arquivos</span><span class="sxs-lookup"><span data-stu-id="ed627-157">Copy files</span></span>

<span data-ttu-id="ed627-158">Você pode copiar um arquivo para outro arquivo ou para um blob, ou um blob para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ed627-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="ed627-159">Se você estiver copiando um blob para um arquivo ou um arquivo para um blob, *deverá* usar uma SAS (assinatura de acesso compartilhado) para autenticar o objeto de origem, mesmo que você esteja copiando dentro da mesma conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ed627-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="ed627-160">Copiar um arquivo para outro arquivo</span><span class="sxs-lookup"><span data-stu-id="ed627-160">Copy a file to another file</span></span>

<span data-ttu-id="ed627-161">Aqui, você copia um arquivo para outro arquivo no mesmo compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="ed627-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="ed627-162">Como essa operação de cópia realiza a cópia entre arquivos na mesma conta de armazenamento, você pode usar a autenticação de Chave compartilhada para executar a cópia.</span><span class="sxs-lookup"><span data-stu-id="ed627-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="ed627-163">Copiar um arquivo em um blob</span><span class="sxs-lookup"><span data-stu-id="ed627-163">Copy a file to a blob</span></span>

<span data-ttu-id="ed627-164">Aqui, você cria um arquivo e o copia para um blob dentro da mesma conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ed627-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="ed627-165">Você cria uma SAS para o arquivo de origem, que o serviço usa para autenticar o acesso ao arquivo de origem durante a operação de cópia.</span><span class="sxs-lookup"><span data-stu-id="ed627-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="ed627-166">Você pode copiar um blob em um arquivo da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="ed627-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="ed627-167">Se o objeto de origem for um blob, crie uma SAS para autenticar o acesso ao blob durante a operação de cópia.</span><span class="sxs-lookup"><span data-stu-id="ed627-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="ed627-168">Solucionando problemas de armazenamento de arquivos usando métricas</span><span class="sxs-lookup"><span data-stu-id="ed627-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="ed627-169">O Análise de Armazenamento do Azure dá suporte a métricas para armazenamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="ed627-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="ed627-170">Com dados de métricas, você pode rastrear solicitações e diagnosticar problemas.</span><span class="sxs-lookup"><span data-stu-id="ed627-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="ed627-171">Você pode habilitar as métricas para o armazenamento de arquivos do [portal do Azure](https://portal.azure.com)ou pode fazer isso em F # como este:</span><span class="sxs-lookup"><span data-stu-id="ed627-171">You can enable metrics for File storage from the [Azure portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="ed627-172">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ed627-172">Next steps</span></span>

<span data-ttu-id="ed627-173">Para obter mais informações sobre o armazenamento de arquivos do Azure, consulte esses links.</span><span class="sxs-lookup"><span data-stu-id="ed627-173">For more information about Azure File storage, see these links.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="ed627-174">Artigos e vídeos conceituais</span><span class="sxs-lookup"><span data-stu-id="ed627-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="ed627-175">Armazenamento de Arquivos do Azure: um sistema de arquivos SMB de nuvem ininterrupto SMB para Windows e Linux</span><span class="sxs-lookup"><span data-stu-id="ed627-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="ed627-176">Como usar o Armazenamento de Arquivos do Azure com o Linux</span><span class="sxs-lookup"><span data-stu-id="ed627-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="ed627-177">Suporte de ferramentas para o armazenamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="ed627-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="ed627-178">Usando o PowerShell do Azure com o Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="ed627-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="ed627-179">Como usar o AzCopy com o Armazenamento do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="ed627-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="ed627-180">Criar, baixar e listar blobs com a CLI do Azure</span><span class="sxs-lookup"><span data-stu-id="ed627-180">Create, download, and list blobs with Azure CLI</span></span>](/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="ed627-181">Referência</span><span class="sxs-lookup"><span data-stu-id="ed627-181">Reference</span></span>

- [<span data-ttu-id="ed627-182">Referência à Biblioteca de Cliente de Armazenamento para .NET</span><span class="sxs-lookup"><span data-stu-id="ed627-182">Storage Client Library for .NET reference</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="ed627-183">Referência à API REST do serviço de arquivos</span><span class="sxs-lookup"><span data-stu-id="ed627-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="ed627-184">Postagens no blog</span><span class="sxs-lookup"><span data-stu-id="ed627-184">Blog posts</span></span>

- [<span data-ttu-id="ed627-185">O Armazenamento de arquivos do Azure agora está disponível ao público geral</span><span class="sxs-lookup"><span data-stu-id="ed627-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="ed627-186">Dentro do armazenamento de arquivos do Azure</span><span class="sxs-lookup"><span data-stu-id="ed627-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [<span data-ttu-id="ed627-187">Apresentando o serviço de arquivo do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="ed627-187">Introducing Microsoft Azure File Service</span></span>](/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [<span data-ttu-id="ed627-188">Persistindo conexões para arquivos do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="ed627-188">Persisting connections to Microsoft Azure Files</span></span>](/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
