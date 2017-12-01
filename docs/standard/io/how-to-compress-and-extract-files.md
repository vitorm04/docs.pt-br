---
title: Como compactar e extrair arquivos
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
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22a95ce18b602d4e329499c5d36557213e08a8b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compress-and-extract-files"></a>Como compactar e extrair arquivos
O <xref:System.IO.Compression> namespace contém os tipos a seguir para compactar e descompactar os arquivos e fluxos. Você também pode usar esses tipos para ler e modificar o conteúdo de um arquivo compactado:  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 Os exemplos a seguir mostram algumas das funções que você pode executar ao trabalhar com arquivos compactados.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar e extrair um arquivo compactado com uma extensão de nome de arquivo. zip usando o <xref:System.IO.Compression.ZipFile> classe. Compacta o conteúdo de uma pasta em um novo arquivo. zip e extrai o conteúdo para uma nova pasta. Para usar o <xref:System.IO.Compression.ZipFile> classe, você deve fazer referência a `System.IO.Compression.FileSystem` assembly em seu projeto.  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como percorrer o conteúdo de um arquivo. zip e extraia os arquivos que têm uma extensão. txt. Ele usa o <xref:System.IO.Compression.ZipArchive> classe para acessar um arquivo. zip existente e o <xref:System.IO.Compression.ZipArchiveEntry> classe para inspecionar as entradas individuais no arquivo compactado. Ele usa um método de extensão (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) para o <xref:System.IO.Compression.ZipArchiveEntry> objeto. O método de extensão está disponível na <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> classe. Para usar o <xref:System.IO.Compression.ZipFileExtensions> classe, você deve fazer referência a `System.IO.Compression.FileSystem` assembly em seu projeto.  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.IO.Compression.ZipArchive> de classe para acessar um arquivo. zip existente e adiciona um novo arquivo para o arquivo compactado. O novo arquivo obtém compactado quando você adicioná-lo para o arquivo. zip.  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a>Exemplo  
 Você também pode usar o <xref:System.IO.Compression.GZipStream> e <xref:System.IO.Compression.DeflateStream> classes para compactar e descompactar dados. Eles usam o mesmo algoritmo de compactação. Compactado <xref:System.IO.Compression.GZipStream> objetos que são gravados em um arquivo que tem uma extensão de .gz podem ser descompactados usando várias ferramentas comuns, além dos métodos fornecidos pelo <xref:System.IO.Compression.GZipStream>. Este exemplo mostra como compactar e descompactar um diretório de arquivos usando o <xref:System.IO.Compression.GZipStream> classe.  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
