---
title: "Como copiar diretórios"
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
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5602a4e227f3cd17e4a7c9a086bee69d3e3e506
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="707ec-102">Como copiar diretórios</span><span class="sxs-lookup"><span data-stu-id="707ec-102">How to: Copy Directories</span></span>
<span data-ttu-id="707ec-103">Este exemplo demonstra como usar classes de e/s de forma síncrona, copie o conteúdo de um diretório para outro local.</span><span class="sxs-lookup"><span data-stu-id="707ec-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="707ec-104">Neste exemplo, o usuário pode especificar se deseja copiar também os subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="707ec-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="707ec-105">Se as subpastas são copiadas, o método recursivamente esse exemplo copia chamando o próprio em cada subdiretório subsequente até que não há mais para copiar.</span><span class="sxs-lookup"><span data-stu-id="707ec-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="707ec-106">Para obter um exemplo de copiar arquivos de forma assíncrona, consulte [e/s de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="707ec-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="707ec-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="707ec-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="707ec-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="707ec-108">See Also</span></span>  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [<span data-ttu-id="707ec-109">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="707ec-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="707ec-110">Tarefas comuns de E/S</span><span class="sxs-lookup"><span data-stu-id="707ec-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
 [<span data-ttu-id="707ec-111">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="707ec-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
