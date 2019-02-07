---
title: 'Como: Compactar e extrair arquivos'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a4ea4c32f5b73b283a5982f16e55a4d078171c1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254997"
---
# <a name="how-to-compress-and-extract-files"></a>Como: Compactar e extrair arquivos

O namespace <xref:System.IO.Compression> contém os seguintes tipos para compactar e descompactar arquivos e fluxos. Use também esses tipos para ler e modificar o conteúdo de um arquivo compactado.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Os exemplos a seguir mostram algumas das operações que você pode executar com arquivos compactados.

## <a name="example-1-create-and-extract-a-zip-file"></a>Exemplo 1: Criar e extrair um arquivo .zip

O exemplo a seguir mostra como criar e extrair um arquivo *.zip* compactado usando a classe <xref:System.IO.Compression.ZipFile>. O exemplo compacta o conteúdo de uma pasta em um novo arquivo *.zip* e extrai o zip para uma nova pasta. 

Para executar a amostra, crie uma pasta *Iniciar* na pasta do programa e popule-a com arquivos a serem zipados. 

Se você receber o erro de build "O nome 'ZipFile' não existe no contexto atual", adicione uma referência ao assembly `System.IO.Compression.FileSystem` ao projeto.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Exemplo 2: Extrair extensões de arquivo específicas

O próximo exemplo itera pelo conteúdo de um arquivo *.zip* existente e extrai os arquivos que têm uma extensão *.txt*. Ele usa a classe <xref:System.IO.Compression.ZipArchive> para acessar o zip e a classe <xref:System.IO.Compression.ZipArchiveEntry> para inspecionar as entradas individuais. O método de extensão <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> para o objeto <xref:System.IO.Compression.ZipArchiveEntry> está disponível na classe <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>. 

Para executar a amostra, coloque um arquivo *.zip* chamado *result.zip* na pasta do programa. Quando solicitado, forneça um nome de pasta na qual extrair. 

Se você receber o erro de build "O nome 'ZipFile' não existe no contexto atual", adicione uma referência ao assembly `System.IO.Compression.FileSystem` ao projeto.

Se você receber o erro "O tipo 'ZipArchive' é definido em um assembly que não é referenciado", adicione uma referência ao `System.IO.Compression` assembly ao projeto. 

> [!IMPORTANT]
> Ao descompactar os arquivos, você precisa procurar caminhos de arquivos maliciosos que possam escapar do diretório no qual deseja descompactar. Isso é conhecido como um ataque de passagem de caminho. O exemplo a seguir demonstra como verificar caminhos de arquivos maliciosos e fornece uma maneira segura de descompactação.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Exemplo 3: Adicionar um arquivo a um zip existente

O exemplo a seguir usa a classe <xref:System.IO.Compression.ZipArchive> para acessar um arquivo *.zip* existente e adiciona um arquivo a ele. O novo arquivo é compactado quando você o adiciona ao zip existente.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Exemplo 4: Compactar e descompactar arquivos .gz

Você também pode usar as classes <xref:System.IO.Compression.GZipStream> e <xref:System.IO.Compression.DeflateStream> para compactar e descompactar dados. Elas usam o mesmo algoritmo de compactação. Você pode descompactar objetos <xref:System.IO.Compression.GZipStream> que são gravados em um arquivo *.gz* usando muitas ferramentas comuns. O exemplo a seguir mostra como compactar e descompactar um diretório de arquivos usando a classe <xref:System.IO.Compression.GZipStream>:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Consulte também

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
