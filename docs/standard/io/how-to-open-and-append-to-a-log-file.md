---
title: Como abrir um arquivo de log e acrescentar dados a ele
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
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Como abrir um arquivo de log e acrescentar dados a ele
<xref:System.IO.StreamWriter>e <xref:System.IO.StreamReader> gravar caracteres e ler caracteres de fluxos. O código a seguir exemplo abre o `log.txt` do arquivo de entrada, ou cria o arquivo se ele ainda não existir e acrescenta informações ao final do arquivo. O conteúdo do arquivo, em seguida, é gravado para a saída padrão para exibição. Como alternativa para este exemplo, as informações poderiam ser armazenadas como uma única cadeia de caracteres ou uma matriz de cadeia de caracteres e o <xref:System.IO.File.WriteAllText%2A> ou <xref:System.IO.File.WriteAllLines%2A> método pode ser usado para alcançar a mesma funcionalidade.  
  
> [!NOTE]
>  Usuários do Visual Basic podem optar por usar os métodos e propriedades fornecidas pelo <xref:Microsoft.VisualBasic.Logging.Log> classe ou <xref:Microsoft.VisualBasic.FileIO.FileSystem> classe para criar ou gravar em arquivos de log.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [Como enumerar diretórios e arquivos](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Como ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Como ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Como gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Como ler caracteres de uma cadeia de caracteres](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Como gravar caracteres em uma cadeia de caracteres](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
