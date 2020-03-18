---
title: 'Como: Ler e gravar em um arquivo de dados recém-criado'
ms.date: 01/21/2019
ms.technology: dotnet-standard
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
ms.openlocfilehash: 3772aeeb25d1251a13fde2a0e51a913e5e39eabc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155744"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Como: Ler e gravar em um arquivo de dados recém-criado
As classes <xref:System.IO.BinaryWriter?displayProperty=nameWithType> e <xref:System.IO.BinaryReader?displayProperty=nameWithType> são usadas para gravar e ler dados que não sejam cadeias de caracteres. O exemplo a seguir mostra como criar um fluxo de arquivo vazio, gravar dados nele e ler dados dele.

O exemplo cria um arquivo de dados chamado *Test.data* no diretório atual, cria os objetos <xref:System.IO.BinaryWriter> e <xref:System.IO.BinaryReader> associados e usa o objeto <xref:System.IO.BinaryWriter> para gravar os inteiros de 0 a 10 em *Test.data*, o que deixa o ponteiro de arquivo no final do arquivo. Em seguida, o objeto <xref:System.IO.BinaryReader> define o ponteiro de arquivo novamente para a origem e lê o conteúdo especificado.  
  
> [!NOTE]
> Se *Test.data* já existir no diretório atual, uma exceção <xref:System.IO.IOException> será gerada. Use a opção de modo de arquivo <xref:System.IO.FileMode.Create?displayProperty=nameWithType> em vez de <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> para sempre criar um arquivo sem gerar uma exceção.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Como: Enumerar diretórios e arquivos](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Como: Abrir e anexar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Como: Ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Como: Escrever texto para um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Como: Ler caracteres de uma seqüência](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Como: Escrever caracteres em uma seqüência](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
