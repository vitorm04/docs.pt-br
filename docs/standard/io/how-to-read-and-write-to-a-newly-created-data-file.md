---
title: 'Como: ler e gravar em um arquivo de dados recém-criado'
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
ms.openlocfilehash: 0bb06f42542d6acb3214fd4a1a3ca5c54f7caab2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706693"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Como: ler e gravar em um arquivo de dados recém-criado
As classes <xref:System.IO.BinaryWriter?displayProperty=nameWithType> e <xref:System.IO.BinaryReader?displayProperty=nameWithType> são usadas para gravar e ler dados que não sejam cadeias de caracteres. O exemplo a seguir mostra como criar um fluxo de arquivo vazio, gravar dados nele e ler dados dele. 

O exemplo cria um arquivo de dados chamado *Test.data* no diretório atual, cria os objetos <xref:System.IO.BinaryWriter> e <xref:System.IO.BinaryReader> associados e usa o objeto <xref:System.IO.BinaryWriter> para gravar os inteiros de 0 a 10 em *Test.data*, o que deixa o ponteiro de arquivo no final do arquivo. Em seguida, o objeto <xref:System.IO.BinaryReader> define o ponteiro de arquivo novamente para a origem e lê o conteúdo especificado.  
  
> [!NOTE]
> Se *Test.data* já existir no diretório atual, uma exceção <xref:System.IO.IOException> será gerada. Use a opção de modo de arquivo <xref:System.IO.FileMode.Create?displayProperty=nameWithType> em vez de <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> para sempre criar um arquivo sem gerar uma exceção.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Como: enumerar diretórios e arquivos](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Como: abrir e anexar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Como: ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Como: gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Como: ler caracteres de uma cadeia de caracteres](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Como: gravar caracteres em uma cadeia de caracteres](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
