---
title: 'Como: Abrir um arquivo de log e fazer acréscimos a ele'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 921b13e057929d7d6b283b26014a4c1f195f39c9
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674835"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Como: Abrir um arquivo de log e fazer acréscimos a ele
<xref:System.IO.StreamWriter> e <xref:System.IO.StreamReader> gravam caracteres e leem caracteres de fluxos. O exemplo de código a seguir abre o arquivo *log.txt* para a entrada ou cria o arquivo caso ele ainda não exista e acrescenta informações de log ao final do arquivo. Em seguida, o exemplo grava o conteúdo do arquivo na saída padrão para exibição. 

Como alternativa para esse exemplo, você pode armazenar as informações como uma única cadeia de caracteres ou uma matriz de cadeia de caracteres e usar o método <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> ou <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> para obter a mesma funcionalidade.  
  
> [!NOTE]
> Os usuários do Visual Basic podem optar por usar os métodos e propriedades fornecidas pela classe <xref:Microsoft.VisualBasic.Logging.Log> ou pela classe <xref:Microsoft.VisualBasic.FileIO.FileSystem> para criar ou gravar em arquivos de log.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Como: Enumerar diretórios e arquivos](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Como: Ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Como: Ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Como: Gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Como: Ler caracteres de uma cadeia de caracteres](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Como: Gravar caracteres em uma cadeia de caracteres](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
