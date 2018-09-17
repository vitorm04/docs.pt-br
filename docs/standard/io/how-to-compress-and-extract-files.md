---
title: Como compactar e extrair arquivos
ms.date: 06/06/2018
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
ms.openlocfilehash: 669936d15cfe1ea125ed36ffdfcfd093b6aacbe1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45687628"
---
# <a name="how-to-compress-and-extract-files"></a>Como compactar e extrair arquivos

O namespace <xref:System.IO.Compression> contém os seguintes tipos para compactar e descompactar arquivos e fluxos. Você também pode usar esses tipos para ler e modificar o conteúdo de um arquivo compactado:

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

Os exemplos a seguir mostram algumas das funções que você pode executar ao trabalhar com arquivos compactados.

## <a name="example-1---create-and-extract-a-zip-file"></a>Exemplo 1 - Criar e extrair um arquivo .zip

O exemplo a seguir mostra como criar e extrair um arquivo compactado que tenha uma extensão de nome de arquivo .zip usando a classe <xref:System.IO.Compression.ZipFile>. Ele compacta o conteúdo de uma pasta em um novo arquivo .zip e extrai o conteúdo para uma nova pasta. Para usar a classe <xref:System.IO.Compression.ZipFile>, você deve fazer referência ao assembly `System.IO.Compression.FileSystem` em seu projeto.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a>Exemplo 2 - Extrair extensões de arquivo específicas

O exemplo a seguir mostra como iterar pelo conteúdo de um arquivo .zip e extrair os arquivos que tenham uma extensão .txt. Ele usa a classe <xref:System.IO.Compression.ZipArchive> para acessar um arquivo .zip existente, e a classe <xref:System.IO.Compression.ZipArchiveEntry> para inspecionar as entradas individuais no arquivo compactado. Ele usa um método de extensão (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) para o objeto <xref:System.IO.Compression.ZipArchiveEntry>. O método de extensão está disponível na classe <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>. Para usar a classe <xref:System.IO.Compression.ZipFileExtensions>, você deve fazer referência ao assembly `System.IO.Compression.FileSystem` em seu projeto.

> [!IMPORTANT]
> Ao descompactar os arquivos, você deve procurar caminhos de arquivos maliciosos que possam escapar do diretório em que deseja descompactar. Isso é conhecido como um ataque de passagem de caminho.

O exemplo a seguir demonstra como verificar caminhos de arquivos maliciosos e fornece uma maneira segura de descompactar:

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a>Exemplo 3 - Adicionar um novo arquivo para um arquivo. zip existente

O exemplo a seguir usa a classe <xref:System.IO.Compression.ZipArchive> para acessar um arquivo .zip existente, e adiciona um novo arquivo ao arquivo compactado. O novo arquivo é compactado quando você o adiciona ao arquivo .zip.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a>Exemplo 4 - Compactar e descompactar um diretório de arquivos .gz

Você também pode usar as classes <xref:System.IO.Compression.GZipStream> e <xref:System.IO.Compression.DeflateStream> para compactar e descompactar dados. Elas usam o mesmo algoritmo de compactação. Objetos <xref:System.IO.Compression.GZipStream> compactados que são gravados em um arquivo que tem uma extensão .gz podem ser descompactados usando várias ferramentas comuns, além dos métodos fornecidos por <xref:System.IO.Compression.GZipStream>. O exemplo a seguir mostra como compactar e descompactar um diretório de arquivos usando a classe <xref:System.IO.Compression.GZipStream>:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Consulte também

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
