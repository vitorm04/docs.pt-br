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
# <a name="how-to-copy-directories"></a>Como copiar diretórios
Este exemplo demonstra como usar classes de e/s de forma síncrona, copie o conteúdo de um diretório para outro local. Neste exemplo, o usuário pode especificar se deseja copiar também os subdiretórios. Se as subpastas são copiadas, o método recursivamente esse exemplo copia chamando o próprio em cada subdiretório subsequente até que não há mais para copiar.  
  
 Para obter um exemplo de copiar arquivos de forma assíncrona, consulte [e/s de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)  
 [Tarefas comuns de E/S](../../../docs/standard/io/common-i-o-tasks.md)  
 [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md)
