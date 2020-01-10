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
ms.openlocfilehash: 223e83a5ff6a73825985ec4e3b6b601fb196fe5e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707894"
---
# <a name="how-to-copy-directories"></a>Como copiar diretórios
Este tópico demonstra como usar classes de E/S para copiar de forma síncrona o conteúdo de um diretório para outra localização. 

Para obter um exemplo de cópia assíncrona de arquivo, confira [E/S assíncrona de arquivo](../../../docs/standard/io/asynchronous-file-i-o.md). 

Este exemplo copia os subdiretórios definindo o `copySubDirs` do método `DirectoryCopy` como `true`. O método `DirectoryCopy` copia os subdiretórios recursivamente chamando a si próprio em cada subdiretório até não existir nada mais para copiar.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
- [Tarefas comuns de E/S](../../../docs/standard/io/common-i-o-tasks.md)
- [E/S assíncrona de arquivo](../../../docs/standard/io/asynchronous-file-i-o.md)
