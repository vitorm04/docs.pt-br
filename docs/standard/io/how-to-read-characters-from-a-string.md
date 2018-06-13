---
title: Como ler caracteres de uma cadeia de caracteres
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2e128f1011b6daa5c0e8b62252c8adc3175586c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572769"
---
# <a name="how-to-read-characters-from-a-string"></a>Como ler caracteres de uma cadeia de caracteres
Os exemplos de código a seguir mostram como ler caracteres de forma síncrona e assíncrona de uma cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 Este exemplo lê 13 caracteres de forma síncrona de uma cadeia de caracteres, armazena-os em uma matriz e exibe esses caracteres. Em seguida, lê os caracteres restantes na cadeia de caracteres, armazena-os na matriz, começando pelo sexto elemento, e exibe o conteúdo da matriz.  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a>Exemplo  
 O próximo exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz. Ele grava de maneira assíncrona cada caractere alfabético ou espaço em branco em uma linha separada, seguida de uma quebra de linha para um controle <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.StringReader>  
 <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
 [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [NIB: Como criar uma listagem de diretório](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [Como ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Como abrir e acrescentar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Como ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Como gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Como gravar caracteres em uma cadeia de caracteres](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
