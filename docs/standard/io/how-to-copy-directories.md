---
title: Como copiar diretórios
description: Consulte como copiar diretórios usando classes de e/s que copiam de forma síncrona o conteúdo de um diretório para outro local.
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
ms.openlocfilehash: 65fe28c90a6cd6f0b3c8c32da19c1d9603900670
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662583"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="8889e-103">Como copiar diretórios</span><span class="sxs-lookup"><span data-stu-id="8889e-103">How to: Copy directories</span></span>
<span data-ttu-id="8889e-104">Este tópico demonstra como usar classes de E/S para copiar de forma síncrona o conteúdo de um diretório para outra localização.</span><span class="sxs-lookup"><span data-stu-id="8889e-104">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="8889e-105">Para obter um exemplo de cópia assíncrona de arquivo, confira [E/S assíncrona de arquivo](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="8889e-105">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="8889e-106">Este exemplo copia os subdiretórios definindo o `copySubDirs` do método `DirectoryCopy` como `true`.</span><span class="sxs-lookup"><span data-stu-id="8889e-106">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="8889e-107">O método `DirectoryCopy` copia os subdiretórios recursivamente chamando a si próprio em cada subdiretório até não existir nada mais para copiar.</span><span class="sxs-lookup"><span data-stu-id="8889e-107">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8889e-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8889e-108">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="8889e-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="8889e-109">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="8889e-110">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="8889e-110">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="8889e-111">Tarefas comuns de E/S</span><span class="sxs-lookup"><span data-stu-id="8889e-111">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="8889e-112">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="8889e-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
