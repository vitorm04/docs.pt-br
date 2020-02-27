---
title: Como copiar diretórios
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 132ce0b887f7c314311e294567c546bded9a89a0
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627382"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="b59a9-102">Como copiar diretórios</span><span class="sxs-lookup"><span data-stu-id="b59a9-102">How to: Copy directories</span></span>
<span data-ttu-id="b59a9-103">Este tópico demonstra como usar classes de E/S para copiar de forma síncrona o conteúdo de um diretório para outra localização.</span><span class="sxs-lookup"><span data-stu-id="b59a9-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> 

<span data-ttu-id="b59a9-104">Para obter um exemplo de cópia assíncrona de arquivo, confira [E/S assíncrona de arquivo](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="b59a9-104">For an example of asynchronous file copy, see [Asynchronous file I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span> 

<span data-ttu-id="b59a9-105">Este exemplo copia os subdiretórios definindo o `copySubDirs` do método `DirectoryCopy` como `true`.</span><span class="sxs-lookup"><span data-stu-id="b59a9-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="b59a9-106">O método `DirectoryCopy` copia os subdiretórios recursivamente chamando a si próprio em cada subdiretório até não existir nada mais para copiar.</span><span class="sxs-lookup"><span data-stu-id="b59a9-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b59a9-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b59a9-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="b59a9-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="b59a9-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="b59a9-109">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="b59a9-109">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="b59a9-110">Tarefas comuns de E/S</span><span class="sxs-lookup"><span data-stu-id="b59a9-110">Common I/O tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)
- [<span data-ttu-id="b59a9-111">E/S assíncrona de arquivo</span><span class="sxs-lookup"><span data-stu-id="b59a9-111">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
