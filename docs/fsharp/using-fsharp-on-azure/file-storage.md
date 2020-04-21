---
title: Introdução ao armazenamento de Arquivos do Azure usando F#
description: Armazene dados de arquivos na nuvem com o armazenamento de Arquivos do Azure e monte seu compartilhamento de arquivos na nuvem de uma VM (máquina virtual) do Azure ou de um aplicativo local que executa o Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 1b38ee53f2f73f7b7f4ee12f712f487cb726d41e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739597"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="2379e-103">Comece com o armazenamento de arquivos Do Azure usando F\#</span><span class="sxs-lookup"><span data-stu-id="2379e-103">Get started with Azure File storage using F\#</span></span>

<span data-ttu-id="2379e-104">O armazenamento de Arquivos do Azure é um serviço que oferece compartilhamentos de arquivos na nuvem usando o [Protocolo SMB](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)padrão.</span><span class="sxs-lookup"><span data-stu-id="2379e-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="2379e-105">Há suporte ao SMB 2.1 e ao 3.0 SMB.</span><span class="sxs-lookup"><span data-stu-id="2379e-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="2379e-106">Com o armazenamento de Arquivos do Azure, você pode migrar aplicativos herdados que dependem de compartilhamentos de arquivos para o Azure rapidamente e sem regravações caras.</span><span class="sxs-lookup"><span data-stu-id="2379e-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="2379e-107">Os aplicativos executados em máquinas virtuais do Azure ou serviços de nuvem ou em clientes locais podem montar um compartilhamento de arquivos na nuvem, exatamente como um aplicativo de desktop monta um compartilhamento SMB típico.</span><span class="sxs-lookup"><span data-stu-id="2379e-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="2379e-108">Qualquer quantidade de componentes de aplicativos pode montar e acessar o compartilhamento de armazenamento de arquivos simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="2379e-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="2379e-109">Para obter uma visão geral conceitual do armazenamento de arquivos, consulte [o guia .NET para armazenamento de arquivos](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="2379e-109">For a conceptual overview of file storage, see [the .NET guide for file storage](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2379e-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2379e-110">Prerequisites</span></span>

<span data-ttu-id="2379e-111">Para usar este guia, primeiro você deve [criar uma conta de armazenamento Azure](https://docs.microsoft.com/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="2379e-111">To use this guide, you must first [create an Azure storage account](https://docs.microsoft.com/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="2379e-112">Você também precisará da sua chave de acesso de armazenamento para esta conta.</span><span class="sxs-lookup"><span data-stu-id="2379e-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="2379e-113">Crie um script F# e inicie f# interativo</span><span class="sxs-lookup"><span data-stu-id="2379e-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="2379e-114">As amostras deste artigo podem ser usadas em um aplicativo F# ou em um script F#.</span><span class="sxs-lookup"><span data-stu-id="2379e-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="2379e-115">Para criar um script F#, `.fsx` crie um `files.fsx`arquivo com a extensão, por exemplo, no seu ambiente de desenvolvimento F#.</span><span class="sxs-lookup"><span data-stu-id="2379e-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="2379e-116">Em seguida, use um [gerenciador de pacotes](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) ou `#r` [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando uma diretiva.</span><span class="sxs-lookup"><span data-stu-id="2379e-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="2379e-117">Adicionar declarações do namespace</span><span class="sxs-lookup"><span data-stu-id="2379e-117">Add namespace declarations</span></span>

<span data-ttu-id="2379e-118">Adicione as seguintes instruções `open` à parte superior do arquivo `files.fsx`:</span><span class="sxs-lookup"><span data-stu-id="2379e-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="2379e-119">Obter sua cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="2379e-119">Get your connection string</span></span>

<span data-ttu-id="2379e-120">Você precisará de uma seqüência de conexão Azure Storage para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="2379e-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="2379e-121">Para obter mais informações sobre strings de conexão, consulte [Configure Storage Connection Strings](https://docs.microsoft.com/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="2379e-121">For more information about connection strings, see [Configure Storage Connection Strings](https://docs.microsoft.com/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="2379e-122">Para o tutorial, você digitará sua seqüência de conexão no seu script, assim:</span><span class="sxs-lookup"><span data-stu-id="2379e-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="2379e-123">No entanto, isso não é **recomendado** para projetos reais.</span><span class="sxs-lookup"><span data-stu-id="2379e-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="2379e-124">Sua chave de conta de armazenamento é semelhante para a senha raiz da sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2379e-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="2379e-125">Sempre tenha cuidado para proteger a chave de sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2379e-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="2379e-126">Evite distribuí-la a outros usuários, embuti-la no código ou salvá-lo em um arquivo de texto sem formatação que esteja acessível a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="2379e-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="2379e-127">Você pode regenerar sua chave usando o portal Azure se você acredita que pode ter sido comprometida.</span><span class="sxs-lookup"><span data-stu-id="2379e-127">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="2379e-128">Para aplicativos reais, a melhor maneira de manter sua seqüência de conexão de armazenamento está em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2379e-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="2379e-129">Para buscar a seqüência de conexões de um arquivo de configuração, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="2379e-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="2379e-130">O uso do Gerenciador de Configurações do Azure é opcional.</span><span class="sxs-lookup"><span data-stu-id="2379e-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="2379e-131">Você também pode usar uma API, como `ConfigurationManager` o tipo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2379e-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="2379e-132">Analisar a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="2379e-132">Parse the connection string</span></span>

<span data-ttu-id="2379e-133">Para analisar a seqüência de conexões, use:</span><span class="sxs-lookup"><span data-stu-id="2379e-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="2379e-134">Isso vai `CloudStorageAccount`devolver um.</span><span class="sxs-lookup"><span data-stu-id="2379e-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="2379e-135">Criar o cliente de serviço de arquivo</span><span class="sxs-lookup"><span data-stu-id="2379e-135">Create the File service client</span></span>

<span data-ttu-id="2379e-136">O `CloudFileClient` tipo permite que você use programaticamente arquivos armazenados no armazenamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="2379e-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="2379e-137">Veja uma maneira de criar o cliente de serviço:</span><span class="sxs-lookup"><span data-stu-id="2379e-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="2379e-138">Agora você está pronto para escrever código que lê dados e grava dados para armazenamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="2379e-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="2379e-139">Criar um compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="2379e-139">Create a file share</span></span>

<span data-ttu-id="2379e-140">Este exemplo mostra como criar um compartilhamento de arquivos se ele ainda não existir:</span><span class="sxs-lookup"><span data-stu-id="2379e-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="2379e-141">Crie um diretório raiz e um subdiretório</span><span class="sxs-lookup"><span data-stu-id="2379e-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="2379e-142">Aqui, você começa o diretório raiz e obter um subdiretório da raiz.</span><span class="sxs-lookup"><span data-stu-id="2379e-142">Here, you get the root directory and get a subdirectory of the root.</span></span> <span data-ttu-id="2379e-143">Você cria ambos se eles já não existem.</span><span class="sxs-lookup"><span data-stu-id="2379e-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="2379e-144">Carregar texto como um arquivo</span><span class="sxs-lookup"><span data-stu-id="2379e-144">Upload text as a file</span></span>

<span data-ttu-id="2379e-145">Este exemplo mostra como carregar texto como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2379e-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="2379e-146">Baixe um arquivo para uma cópia local do arquivo</span><span class="sxs-lookup"><span data-stu-id="2379e-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="2379e-147">Aqui você baixa o arquivo que acabou de criar, anexando o conteúdo a um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="2379e-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="2379e-148">Definir o tamanho máximo de um compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="2379e-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="2379e-149">O exemplo a seguir mostra como verificar o uso atual de um compartilhamento e como definir a cota para o compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="2379e-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="2379e-150">`FetchAttributes`devem ser chamados para preencher `Properties`uma `SetProperties` parte e propagar alterações locais no armazenamento de arquivos do Azure.</span><span class="sxs-lookup"><span data-stu-id="2379e-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="2379e-151">Gerar uma assinatura de acesso compartilhado para um arquivo ou compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="2379e-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="2379e-152">Você pode gerar uma SAS (assinatura de acesso compartilhado) para um compartilhamento de arquivo ou para um arquivo individual.</span><span class="sxs-lookup"><span data-stu-id="2379e-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="2379e-153">Você também pode criar uma política de acesso compartilhado em um compartilhamento de arquivos para gerenciar assinaturas de acesso compartilhado.</span><span class="sxs-lookup"><span data-stu-id="2379e-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="2379e-154">Recomendamos a criação de uma política de acesso compartilhado, pois ela fornece um meio de revogar o SAS se ele for comprometido.</span><span class="sxs-lookup"><span data-stu-id="2379e-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="2379e-155">Aqui, você cria uma política de acesso compartilhado em um compartilhamento e, em seguida, usa essa política para fornecer as restrições para um SAS em um arquivo no compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="2379e-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="2379e-156">Para saber mais sobre como criar e usar as assinaturas de acesso compartilhado, confira [Como usar SAS (Assinaturas de Acesso Compartilhado)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) e [Criar e usar uma SAS com o Armazenamento de Blobs](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="2379e-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="2379e-157">Copiar arquivos</span><span class="sxs-lookup"><span data-stu-id="2379e-157">Copy files</span></span>

<span data-ttu-id="2379e-158">Você pode copiar um arquivo para outro arquivo ou para uma bolha, ou uma bolha para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2379e-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="2379e-159">Se você estiver copiando uma bolha para um arquivo ou um arquivo para uma bolha, você *deve* usar uma assinatura de acesso compartilhado (SAS) para autenticar o objeto de origem, mesmo se você estiver copiando dentro da mesma conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2379e-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="2379e-160">Copiar um arquivo para outro arquivo</span><span class="sxs-lookup"><span data-stu-id="2379e-160">Copy a file to another file</span></span>

<span data-ttu-id="2379e-161">Aqui, você copia um arquivo para outro arquivo no mesmo compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="2379e-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="2379e-162">Como essa operação de cópia realiza a cópia entre arquivos na mesma conta de armazenamento, você pode usar a autenticação de Chave compartilhada para executar a cópia.</span><span class="sxs-lookup"><span data-stu-id="2379e-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="2379e-163">Copiar um arquivo em um blob</span><span class="sxs-lookup"><span data-stu-id="2379e-163">Copy a file to a blob</span></span>

<span data-ttu-id="2379e-164">Aqui, você cria um arquivo e o copia para uma bolha dentro da mesma conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2379e-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="2379e-165">Você cria um SAS para o arquivo de origem, que o serviço usa para autenticar o acesso ao arquivo de origem durante a operação de cópia.</span><span class="sxs-lookup"><span data-stu-id="2379e-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="2379e-166">Você pode copiar um blob em um arquivo da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="2379e-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="2379e-167">Se o objeto de origem for um blob, crie uma SAS para autenticar o acesso ao blob durante a operação de cópia.</span><span class="sxs-lookup"><span data-stu-id="2379e-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="2379e-168">Solucionando problemas de armazenamento de arquivos usando métricas</span><span class="sxs-lookup"><span data-stu-id="2379e-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="2379e-169">O Azure Storage Analytics suporta métricas para armazenamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="2379e-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="2379e-170">Com dados de métricas, você pode rastrear solicitações e diagnosticar problemas.</span><span class="sxs-lookup"><span data-stu-id="2379e-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="2379e-171">Você pode habilitar métricas para armazenamento de arquivos a partir do [portal Azure,](https://portal.azure.com)ou pode fazê-lo a partir de F# assim:</span><span class="sxs-lookup"><span data-stu-id="2379e-171">You can enable metrics for File storage from the [Azure portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="2379e-172">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2379e-172">Next steps</span></span>

<span data-ttu-id="2379e-173">Para obter mais informações sobre o armazenamento de arquivos do Azure, consulte esses links.</span><span class="sxs-lookup"><span data-stu-id="2379e-173">For more information about Azure File storage, see these links.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="2379e-174">Artigos e vídeos conceituais</span><span class="sxs-lookup"><span data-stu-id="2379e-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="2379e-175">Armazenamento de Arquivos do Azure: um sistema de arquivos SMB de nuvem ininterrupto SMB para Windows e Linux</span><span class="sxs-lookup"><span data-stu-id="2379e-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="2379e-176">Como usar o Armazenamento de Arquivos do Azure com o Linux</span><span class="sxs-lookup"><span data-stu-id="2379e-176">How to use Azure File Storage with Linux</span></span>](https://docs.microsoft.com/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="2379e-177">Suporte de ferramentas para o armazenamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="2379e-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="2379e-178">Usando o PowerShell do Azure com o Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="2379e-178">Using Azure PowerShell with Azure Storage</span></span>](https://docs.microsoft.com/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="2379e-179">Como usar o AzCopy com o Armazenamento do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2379e-179">How to use AzCopy with Microsoft Azure Storage</span></span>](https://docs.microsoft.com/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="2379e-180">Criar, baixar e listar blobs com a CLI do Azure</span><span class="sxs-lookup"><span data-stu-id="2379e-180">Create, download, and list blobs with Azure CLI</span></span>](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="2379e-181">Referência</span><span class="sxs-lookup"><span data-stu-id="2379e-181">Reference</span></span>

- [<span data-ttu-id="2379e-182">Referência à Biblioteca de Cliente de Armazenamento para .NET</span><span class="sxs-lookup"><span data-stu-id="2379e-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="2379e-183">Referência à API REST do serviço de arquivos</span><span class="sxs-lookup"><span data-stu-id="2379e-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="2379e-184">Postagens no blog</span><span class="sxs-lookup"><span data-stu-id="2379e-184">Blog posts</span></span>

- [<span data-ttu-id="2379e-185">O Armazenamento de arquivos do Azure agora está disponível ao público geral</span><span class="sxs-lookup"><span data-stu-id="2379e-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="2379e-186">Armazenamento de arquivos do Azure</span><span class="sxs-lookup"><span data-stu-id="2379e-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [<span data-ttu-id="2379e-187">Apresentando o serviço de arquivo do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2379e-187">Introducing Microsoft Azure File Service</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [<span data-ttu-id="2379e-188">Persistindo conexões para arquivos do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2379e-188">Persisting connections to Microsoft Azure Files</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
