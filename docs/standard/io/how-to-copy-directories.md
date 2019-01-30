---
title: 'Como: Copiar diretórios'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57e2b61fb8fef37234dc10885752f92e5f9b1330
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671064"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="e09f8-102">Como: Copiar diretórios</span><span class="sxs-lookup"><span data-stu-id="e09f8-102">How to: Copy directories</span></span>
<span data-ttu-id="e09f8-103">Este tópico demonstra como usar classes de E/S para copiar de forma síncrona o conteúdo de um diretório para outra localização.</span><span class="sxs-lookup"><span data-stu-id="e09f8-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> 

<span data-ttu-id="e09f8-104">Para obter um exemplo de cópia assíncrona de arquivo, confira [E/S assíncrona de arquivo](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="e09f8-104">For an example of asynchronous file copy, see [Asynchronous file I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span> 

<span data-ttu-id="e09f8-105">Este exemplo copia os subdiretórios definindo o `copySubDirs` do método `DirectoryCopy` como `true`.</span><span class="sxs-lookup"><span data-stu-id="e09f8-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="e09f8-106">O método `DirectoryCopy` copia os subdiretórios recursivamente chamando a si próprio em cada subdiretório até não existir nada mais para copiar.</span><span class="sxs-lookup"><span data-stu-id="e09f8-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e09f8-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e09f8-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e09f8-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e09f8-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="e09f8-109">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="e09f8-109">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="e09f8-110">Tarefas comuns de E/S</span><span class="sxs-lookup"><span data-stu-id="e09f8-110">Common I/O tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)
- [<span data-ttu-id="e09f8-111">E/S assíncrona de arquivo</span><span class="sxs-lookup"><span data-stu-id="e09f8-111">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)