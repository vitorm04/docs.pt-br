---
title: Introdução ao armazenamento de arquivos do Azure usando F#
description: Store dados de arquivos na nuvem com o armazenamento de arquivos do Azure e montar o compartilhamento de arquivos de nuvem de uma máquina virtual do Azure (VM) ou de um aplicativo local que executa o Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e772da5f81d2e6827295d0dfe150934a415eb3bb
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "33569337"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Introdução ao armazenamento de arquivos do Azure usando F# #

O armazenamento de arquivos do Azure é um serviço que oferece compartilhamentos de arquivos na nuvem usando o padrão [protocolo de bloco de mensagens de servidor (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Há suporte para SMB 2.1 e SMB 3.0. Com o armazenamento de arquivos do Azure, você pode migrar aplicativos herdados que dependem de compartilhamentos de arquivo para o Azure rapidamente e sem regravações caras. Aplicativos em execução em máquinas virtuais do Azure ou serviços de nuvem ou de clientes locais podem montar um compartilhamento de arquivos na nuvem, exatamente como um aplicativo de desktop monta um compartilhamento SMB típico. Qualquer número de componentes de aplicativos pode, em seguida, montar e acessar o compartilhamento de armazenamento de arquivos simultaneamente.

Para obter uma visão geral conceitual de armazenamento de arquivos, consulte [o guia do .NET para o armazenamento de arquivos](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Pré-requisitos

Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).
Você também precisará sua chave de acesso de armazenamento para esta conta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Criar Script de F# e o início da F# interativo

Os exemplos neste artigo podem ser usados em um aplicativo do F# ou um script F#. Para criar um script F#, crie um arquivo com o `.fsx` extensão, por exemplo `files.fsx`, em seu ambiente de desenvolvimento do F#.

Em seguida, use um [Gerenciador de pacotes](package-management.md) tais como [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) para instalar o `WindowsAzure.Storage` pacote e referência `WindowsAzure.Storage.dll` em seu script usando um `#r`diretiva.

### <a name="add-namespace-declarations"></a>Adicionar declarações de namespace

Adicione o seguinte `open` as instruções na parte superior do `files.fsx` arquivo:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obter a cadeia de conexão

Você precisará de uma cadeia de caracteres de conexão do armazenamento do Azure para este tutorial. Para obter mais informações sobre cadeias de caracteres de conexão, consulte [configurar cadeias de Conexão de armazenamento](/azure/storage/storage-configure-connection-string).

Para o tutorial, você irá inserir a cadeia de conexão no seu script, como este:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

No entanto, isso é **não recomendável** para projetos reais. Sua chave de conta de armazenamento é semelhante para a senha raiz para sua conta de armazenamento. Sempre tenha cuidado para proteger sua chave de conta de armazenamento. Evite distribuí-la a outros usuários, embuti-la, ou salvá-la em um arquivo de texto sem formatação que é acessível a outras pessoas. Você pode regenerar a chave usando o Portal do Azure se você acredita que pode ter sido comprometida.

Aplicativos para o real, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração. Para buscar a cadeia de caracteres de conexão de um arquivo de configuração, você pode fazer isso:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Usando o Gerenciador de configuração do Azure é opcional. Você também pode usar uma API como o .NET Framework `ConfigurationManager` tipo.

### <a name="parse-the-connection-string"></a>Analisar a cadeia de conexão

Para analisar a cadeia de caracteres de conexão, use:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Isso retornará um `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Criar o cliente do serviço de arquivo

O `CloudFileClient` tipo lhe permite usar arquivos armazenados no armazenamento de arquivos de forma programática. Aqui está uma maneira de criar o cliente do serviço:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Agora você está pronto para escrever um código que lê e grava dados no armazenamento de arquivo.

## <a name="create-a-file-share"></a>Criar um compartilhamento de arquivos

Este exemplo mostra como criar um compartilhamento de arquivo se ele ainda não existir:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Criar um diretório raiz e um subdiretório

Aqui, você pode obter o diretório raiz e obtenha um subdiretório do diretório da raiz. Criar ambos se ainda não existirem.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Carregue o texto como um arquivo

Este exemplo mostra como carregar texto como um arquivo.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Baixar um arquivo para uma cópia local do arquivo

Aqui você baixar o arquivo que acabou de criar, acrescentar o conteúdo em um arquivo local.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Definir o tamanho máximo para um compartilhamento de arquivos

O exemplo a seguir mostra como verificar o uso atual para um compartilhamento e como definir a cota para o compartilhamento. `FetchAttributes` deve ser chamado para preencher um compartilhamento `Properties`, e `SetProperties` para propagar as alterações locais para o armazenamento de arquivos do Azure.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Gerar uma assinatura de acesso compartilhado para um arquivo ou compartilhamento de arquivos

Você pode gerar uma assinatura de acesso compartilhado (SAS) para um compartilhamento de arquivos ou para um arquivo individual. Você também pode criar uma política de acesso compartilhado em um compartilhamento de arquivos para gerenciar assinaturas de acesso compartilhado. Criar uma política de acesso compartilhado é recomendada, pois ele fornece um meio de revogar a SAS se ele for comprometido.

Aqui, você cria um compartilhamento em um compartilhamento de política de acesso e, em seguida, usar essa política para fornecer as restrições de um SAS em um arquivo no compartilhamento.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Para obter mais informações sobre como criar e usar assinaturas de acesso compartilhado, consulte [assinaturas usando de acesso compartilhado (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) e [criar e usar uma SAS com o armazenamento de BLOBs](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Copiar arquivos

Você pode copiar um arquivo para outro arquivo ou para um blob ou um blob em um arquivo. Se você estiver copiando um blob em um arquivo ou um arquivo em um blob, você *deve* usar uma assinatura de acesso compartilhado (SAS) para autenticar o objeto de origem, mesmo se você estiver copiando dentro da mesma conta de armazenamento.

### <a name="copy-a-file-to-another-file"></a>Copiar um arquivo para outro arquivo

Aqui, você copia um arquivo para outro arquivo no mesmo compartilhamento. Como essa operação de cópia copia entre arquivos na mesma conta de armazenamento, você pode usar a autenticação de chave compartilhada para executar a cópia.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Copiar um arquivo para um blob

Aqui, você cria um arquivo e copie-o para um blob dentro da mesma conta de armazenamento. Você cria uma SAS para o arquivo de origem, o serviço usa para autenticar o acesso ao arquivo de origem durante a operação de cópia.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Você pode copiar um blob em um arquivo da mesma maneira. Se o objeto de origem for um blob, em seguida, crie uma SAS para autenticar o acesso ao blob durante a operação de cópia.

## <a name="troubleshooting-file-storage-using-metrics"></a>Solução de problemas usando métricas de armazenamento de arquivos

Análise de armazenamento do Azure dá suporte a métricas para armazenamento de arquivos. Com dados de métricas, você pode rastrear solicitações e diagnosticar problemas.

Você pode habilitar métricas para armazenamento de arquivos dos [Portal do Azure](https://portal.azure.com), ou você pode fazê-lo no F# como este:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Próximas etapas

Consulte estes links para obter mais informações sobre o armazenamento de arquivos do Azure.

### <a name="conceptual-articles-and-videos"></a>Artigos e vídeos conceituais

- [Armazenamento de arquivos do Azure: sistema de arquivos de SMB de nuvem ininterrupto para Windows e Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Como usar o armazenamento de arquivos do Azure com Linux](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Suporte a ferramentas para o armazenamento de arquivos

- [Usando o PowerShell do Azure com o armazenamento do Azure](/azure/storage/storage-powershell-guide-full)
- [Como usar o AzCopy com o armazenamento do Microsoft Azure](/azure/storage/storage-use-azcopy)
- [Usando a CLI do Azure com o armazenamento do Azure](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Referência

- [Biblioteca de cliente de armazenamento para a referência do .NET](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Referência da API REST do serviço de arquivo](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Postagens de blog

- [O armazenamento de arquivos do Azure agora está geralmente disponível](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Armazenamento de arquivos do Azure por dentro](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Introdução ao serviço de arquivo do Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Persistindo conexões para arquivos do Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
