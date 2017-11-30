---
title: Como ler e gravar em arquivos no armazenamento isolado
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
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8d733efc3d70070dd12f55c651033e97d1792c38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="026c8-102">Como ler e gravar em arquivos no armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="026c8-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="026c8-103">Para ler ou gravar um arquivo em um armazenamento isolado, use um <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> objeto com um leitor de fluxo (<xref:System.IO.StreamReader> objeto) ou o gravador do fluxo (<xref:System.IO.StreamWriter> objeto).</span><span class="sxs-lookup"><span data-stu-id="026c8-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="026c8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="026c8-104">Example</span></span>  
 <span data-ttu-id="026c8-105">O exemplo de código a seguir obtém um armazenamento isolado e verifica se existe um arquivo chamado TestStore no repositório.</span><span class="sxs-lookup"><span data-stu-id="026c8-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="026c8-106">Se não existir, ele cria o arquivo e grava "Hello isolado Storage" no arquivo.</span><span class="sxs-lookup"><span data-stu-id="026c8-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="026c8-107">Se TestStore já existir, o código de exemplo lê a partir do arquivo.</span><span class="sxs-lookup"><span data-stu-id="026c8-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="026c8-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="026c8-108">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 <xref:System.IO.FileMode?displayProperty=nameWithType>  
 <xref:System.IO.FileAccess?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader?displayProperty=nameWithType>  
 <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
 [<span data-ttu-id="026c8-109">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="026c8-109">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="026c8-110">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="026c8-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
