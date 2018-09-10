---
title: Como copiar diretórios
ms.date: 03/30/2017
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
ms.openlocfilehash: 6f2c2fbd58b10af80a2a233cbd4211befe2dbd33
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216048"
---
# <a name="how-to-copy-directories"></a>Como copiar diretórios
Este exemplo demonstra como usar classes de E/S para copiar de forma síncrona o conteúdo de um diretório para outro local. Nesse exemplo, o usuário pode especificar se deseja copiar também os subdiretórios. Se os subdiretórios forem copiadas, o método nesse exemplo as copiará recursivamente chamando a si próprio em cada subdiretório subsequente até que não haja mais nada para copiar.  
  
 Para obter um exemplo de como copiar arquivos de forma assíncrona, confira [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO.FileInfo>  
- <xref:System.IO.DirectoryInfo>  
- <xref:System.IO.FileStream>  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)  
- [Tarefas comuns de E/S](../../../docs/standard/io/common-i-o-tasks.md)  
- [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md)
