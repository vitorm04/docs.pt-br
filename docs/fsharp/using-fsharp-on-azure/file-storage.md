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
ms.openlocfilehash: 5e1f6914acad5ae8c7148a7238e2d1d6a8ca5867
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Introdução ao armazenamento de arquivo do Azure usando F # #

Armazenamento de arquivo do Azure é um serviço que oferece a compartilhamentos de arquivos na nuvem usando o padrão [protocolo de bloco de mensagens de servidor (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Há suporte para SMB 2.1 e o SMB 3.0. Com o armazenamento de arquivo do Azure, você pode migrar aplicativos herdados que dependem de compartilhamentos de arquivos para o Azure rapidamente e sem regravações caras. Aplicativos executados em máquinas virtuais do Azure ou serviços de nuvem ou de clientes locais podem montar um compartilhamento de arquivo na nuvem, assim como um aplicativo de desktop monta um compartilhamento SMB típico. Qualquer número de componentes de aplicativos pode montar e acessar o compartilhamento de arquivo de armazenamento simultaneamente.

Para obter uma visão geral conceitual de armazenamento de arquivos, consulte [guia .NET para armazenamento de arquivo](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).
Você também precisará sua chave de acesso de armazenamento para esta conta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar Script F # e começar a F # interativo

Os exemplos neste artigo podem ser usados em um aplicativo do F # ou um script F #. Para criar um script F #, crie um arquivo com o `.fsx` extensão, por exemplo `files.fsx`, em seu ambiente de desenvolvimento do F #.

Em seguida, use uma [Gerenciador de pacote](package-management.md) como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando um `#r`diretiva.

### <a name="add-namespace-declarations"></a>Adicione declarações de namespace

Adicione o seguinte `open` instruções na parte superior do `files.fsx` arquivo:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obter a cadeia de conexão

Você precisará de uma cadeia de caracteres de conexão de armazenamento do Azure para este tutorial. Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).

Para o tutorial, você vai inserir sua cadeia de caracteres de conexão no seu script, como este:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

No entanto, isso é **não recomendável** projetos para o real. Sua chave de conta de armazenamento é semelhante para a senha de raiz de sua conta de armazenamento. Sempre tenha cuidado para proteger a chave de conta de armazenamento. Evite distribuí-lo a outros usuários, codificar, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas. Você pode regenerar a chave usando o Portal do Azure se você acredita que ele pode ter sido comprometido.

Aplicativos para o real, a melhor maneira de manter sua cadeia de caracteres de conexão de armazenamento está em um arquivo de configuração. Para obter a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Usando o Gerenciador de configuração do Azure é opcional. Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de caracteres de conexão

Para analisar a cadeia de caracteres de conexão, use:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Isso retornará um `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Criar o cliente de serviços de arquivo

O `CloudFileClient` tipo permite que você use programaticamente os arquivos armazenados no armazenamento de arquivo. Aqui está uma maneira de criar o cliente do serviço:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Agora você está pronto para escrever código que lê e grava dados no armazenamento de arquivo.

## <a name="create-a-file-share"></a>Criar um compartilhamento de arquivos

Este exemplo mostra como criar um compartilhamento de arquivos se ele ainda não existir:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Criar um diretório raiz e um subdiretório

Aqui, você pode obter o diretório raiz e obter um subdiretório da raiz. Criar ambos se ainda não existirem.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Carregue o texto como um arquivo

Este exemplo mostra como carregar um arquivo de texto.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Baixar um arquivo para uma cópia local do arquivo

Aqui você baixar o arquivo que acabou de criar, acrescentando o conteúdo em um arquivo local.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Definir o tamanho máximo para um compartilhamento de arquivos

O exemplo a seguir mostra como verificar o uso atual para um compartilhamento e como definir uma cota para o compartilhamento. `FetchAttributes` deve ser chamado para popular um compartilhamento `Properties`, e `SetProperties` para propagar as alterações locais para o armazenamento de arquivo do Azure.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Gerar uma assinatura de acesso compartilhado para um arquivo ou compartilhamento de arquivos

Você pode gerar uma assinatura de acesso compartilhado (SAS) para um compartilhamento de arquivos ou para um arquivo individual. Você também pode criar uma política de acesso compartilhado em um compartilhamento de arquivos para gerenciar assinaturas de acesso compartilhado. Criar uma política de acesso compartilhado é recomendada, pois ele fornece um meio de revogar a SAS se ela deve ser comprometida.

Aqui, você cria um compartilhado política em um compartilhamento de acesso e, em seguida, use essa política para fornecer as restrições para uma SAS em um arquivo no compartilhamento.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Para obter mais informações sobre como criar e usar assinaturas de acesso compartilhado, consulte [assinaturas usando de acesso compartilhado (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) e [criar e usar uma SAS com armazenamento de Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Copiar arquivos

Você pode copiar um arquivo para outro arquivo ou para um blob ou um blob em um arquivo. Se você estiver copiando um blob para um arquivo ou um arquivo em um blob, você *deve* usar uma assinatura de acesso compartilhado (SAS) para autenticar o objeto de origem, mesmo se você estiver copiando dentro da mesma conta de armazenamento.

### <a name="copy-a-file-to-another-file"></a>Copiar um arquivo para outro arquivo

Aqui, você deve copiar um arquivo para outro arquivo no mesmo compartilhamento. Como essa operação de cópia copia entre arquivos na mesma conta de armazenamento, você pode usar a autenticação de chave compartilhada para executar a cópia.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Copiar um arquivo para um blob

Aqui, você pode criar um arquivo e copie-o para um blob dentro da mesma conta de armazenamento. Criar uma SAS para o arquivo de origem, o serviço usa para autenticar o acesso ao arquivo de origem durante a operação de cópia.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Você pode copiar um blob em um arquivo da mesma maneira. Se o objeto de origem for um blob, em seguida, crie uma SAS para autenticar o acesso ao blob durante a operação de cópia.

## <a name="troubleshooting-file-storage-using-metrics"></a>Uso de métricas de armazenamento de arquivos de solução de problemas

Análise de armazenamento do Azure oferece suporte a métricas para armazenamento de arquivos. Com dados de métricas, você pode rastrear solicitações e diagnosticar problemas.

Você pode habilitar as métricas para o armazenamento de arquivos do [Portal do Azure](https://portal.azure.com), ou você pode fazer isso no F # como este:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Próximas etapas

Consulte esses links para obter mais informações sobre o armazenamento de arquivo do Azure.

### <a name="conceptual-articles-and-videos"></a>Vídeos e artigos conceituais

- [Armazenamento de arquivos do Azure: sistema de arquivos de uma nuvem ininterrupto SMB para Windows e Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Como usar o armazenamento de arquivos do Azure com Linux](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Ferramentas de suporte para armazenamento de arquivo

- [Usando o PowerShell do Azure com o armazenamento do Azure](/azure/storage/storage-powershell-guide-full)
- [Como usar AzCopy com armazenamento do Microsoft Azure](/azure/storage/storage-use-azcopy)
- [Usando a CLI do Azure com o armazenamento do Azure](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Referência

- [Biblioteca de cliente de armazenamento para a referência do .NET](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Referência da API REST de serviços de arquivo](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Postagens de blog

- [Armazenamento de arquivo do Azure agora está disponível](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Armazenamento de arquivos do Azure dentro](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Introdução ao serviço de arquivo do Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Conexões persistentes aos arquivos do Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
