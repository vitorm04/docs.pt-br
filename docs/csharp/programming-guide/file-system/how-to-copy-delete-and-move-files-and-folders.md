---
title: 'Como: copiar, excluir e mover arquivos e pastas – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 609e14141538543c9318efbd4899ec16967cc23f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972060"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Como: copiar, excluir e mover arquivos e pastas (Guia de Programação em C#)
Os exemplos a seguir mostram como copiar, mover e excluir arquivos e pastas de maneira síncrona usando as classes <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType> e <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> do namespace <xref:System.IO?displayProperty=nameWithType>. Esses exemplos não fornecem uma barra de progresso ou qualquer outra interface do usuário. Se você quiser fornecer uma caixa de diálogo de progresso padrão, confira [Como fornecer uma caixa de diálogo de progresso para operações de arquivo](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> para fornecer eventos que permitirão que você calcule o progresso ao operar em vários arquivos. Outra abordagem é usar a invocação de plataforma para invocar os métodos relacionados ao arquivo relevantes no Shell do Windows. Para obter informações sobre como executar essas operações de arquivo de forma assíncrona, consulte [E/S de arquivo assíncrona](../../../standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como copiar arquivos e diretórios.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como mover arquivos e diretórios.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como excluir arquivos e diretórios.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO?displayProperty=nameWithType>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Sistema de arquivos e o Registro (Guia de Programação em C#)](index.md)
- [Como: fornecer uma caixa de diálogo de progresso para operações de arquivo](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [E/S de arquivo e de fluxo](../../../standard/io/index.md)
- [Tarefas comuns de E/S](../../../standard/io/common-i-o-tasks.md)
