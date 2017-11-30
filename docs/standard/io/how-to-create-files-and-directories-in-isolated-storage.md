---
title: "Como criar arquivos e diretórios no armazenamento isolado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="636b6-102">Como criar arquivos e diretórios no armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="636b6-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="636b6-103">Depois de obter um armazenamento isolado, você pode criar pastas e arquivos para armazenar dados.</span><span class="sxs-lookup"><span data-stu-id="636b6-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="636b6-104">Em um repositório, nomes de arquivo e diretório são especificados em relação à raiz do sistema de arquivos virtual.</span><span class="sxs-lookup"><span data-stu-id="636b6-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="636b6-105">Para criar um diretório, use o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> método de instância.</span><span class="sxs-lookup"><span data-stu-id="636b6-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="636b6-106">Se você especificar um subdiretório de um diretório que não existe, ambos os diretórios serão criados.</span><span class="sxs-lookup"><span data-stu-id="636b6-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="636b6-107">Se você especificar um diretório que já existe, o método retorna sem criar um diretório, e nenhuma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="636b6-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="636b6-108">No entanto, se você especificar um nome de diretório que contém caracteres inválidos, uma <xref:System.IO.IsolatedStorage.IsolatedStorageException> exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="636b6-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="636b6-109">Para criar um arquivo, use o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="636b6-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="636b6-110">No sistema operacional Windows, arquivo de armazenamento isolado e diretório nomes diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="636b6-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="636b6-111">Ou seja, se você criar um arquivo chamado `ThisFile.txt`e, em seguida, criar outro arquivo chamado `THISFILE.TXT`, somente um arquivo é criado.</span><span class="sxs-lookup"><span data-stu-id="636b6-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="636b6-112">O nome do arquivo mantém seu capitalização original para fins de exibição.</span><span class="sxs-lookup"><span data-stu-id="636b6-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="636b6-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="636b6-113">Example</span></span>  
 <span data-ttu-id="636b6-114">O exemplo de código a seguir ilustra como criar arquivos e diretórios em um armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="636b6-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="636b6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="636b6-115">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [<span data-ttu-id="636b6-116">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="636b6-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
