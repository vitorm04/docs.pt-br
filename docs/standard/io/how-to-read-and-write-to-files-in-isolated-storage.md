---
title: Como ler e gravar em arquivos no armazenamento isolado
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9aecf7aef9023439e145d408e40fb4adf5c0e986
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46586379"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="df479-102">Como ler e gravar em arquivos no armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="df479-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="df479-103">Para ler ou gravar de um arquivo em um armazenamento isolado, use um objeto <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> com um leitor de fluxo (objeto <xref:System.IO.StreamReader>) ou o gravador do fluxo (objeto <xref:System.IO.StreamWriter>).</span><span class="sxs-lookup"><span data-stu-id="df479-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df479-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df479-104">Example</span></span>  
 <span data-ttu-id="df479-105">O exemplo de código a seguir obtém um repositório isolado e verifica se existe um arquivo chamado TestStore.txt no repositório.</span><span class="sxs-lookup"><span data-stu-id="df479-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="df479-106">Se não existir, ele cria o arquivo e grava "Armazenamento Isolado do Hello" no arquivo.</span><span class="sxs-lookup"><span data-stu-id="df479-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="df479-107">Se TestStore.txt já existir, o código de exemplo será lido a partir do arquivo.</span><span class="sxs-lookup"><span data-stu-id="df479-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="df479-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df479-108">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
- <xref:System.IO.FileMode?displayProperty=nameWithType>  
- <xref:System.IO.FileAccess?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader?displayProperty=nameWithType>  
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
- [<span data-ttu-id="df479-109">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="df479-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="df479-110">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="df479-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
