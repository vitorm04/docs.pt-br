---
title: "Como ler e gravar em um arquivo de dados recém-criado"
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
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b547f2c85495a497e5fc384f9a2ea44de7bf861c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Como ler e gravar em um arquivo de dados recém-criado
O <xref:System.IO.BinaryWriter> e <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes são usadas para gravar e ler dados, em vez de cadeias de caracteres. O exemplo a seguir demonstra como gravar e ler dados de um fluxo de arquivo novo e vazio chamado `Test.data`. Depois de criar o arquivo de dados no diretório atual, associado <xref:System.IO.BinaryWriter> e <xref:System.IO.BinaryReader> objetos são criados e o <xref:System.IO.BinaryWriter> objeto é usado para gravar os inteiros de 0 a 10 para `Test.data`, que deixa o ponteiro do arquivo no final do arquivo. Depois de definir o ponteiro de arquivo para a origem, o <xref:System.IO.BinaryReader> objeto lê o conteúdo especificado.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Se `Test.data` já existe no diretório atual, um <xref:System.IO.IOException> exceção será lançada. Use a opção de modo de arquivo <xref:System.IO.FileMode.Create?displayProperty=nameWithType> quando você inicializar o fluxo de arquivos para sempre criar um novo arquivo sem lançar uma exceção.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryWriter>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
 <xref:System.IO.SeekOrigin>  
 [Como enumerar diretórios e arquivos](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Como abrir e acrescentar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Como ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Como gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Como ler caracteres de uma cadeia de caracteres](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Como gravar caracteres em uma cadeia de caracteres](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
