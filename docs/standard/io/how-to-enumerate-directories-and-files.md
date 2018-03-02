---
title: "Como enumerar diretórios e arquivos"
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
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d0f22853210144881e49c4192ea38a5c3e57cda
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enumerate-directories-and-files"></a>Como enumerar diretórios e arquivos
Você pode enumerar diretórios e arquivos usando métodos que retornam uma coleção enumerável de cadeias de caracteres de seus nomes. Você também pode usar os métodos que retornam uma coleção enumerável de objetos <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo> ou <xref:System.IO.FileSystemInfo>. Coleções enumeráveis fornecem um desempenho melhor do que matrizes ao trabalhar com coleções grandes de arquivos e diretórios.  
  
 Você também pode usar coleções enumeráveis obtidas desses métodos para fornecer o parâmetro <xref:System.Collections.Generic.IEnumerable%601> para construtores de classes de coleção, como a classe <xref:System.Collections.Generic.List%601>.  
  
 Se você quiser obter somente os nomes de arquivos ou diretórios, use os métodos de enumeração da classe <xref:System.IO.Directory>. Se você quiser obter outras propriedades de arquivos ou diretórios, use as classes <xref:System.IO.DirectoryInfo> e <xref:System.IO.FileSystemInfo>.  
  
 A tabela a seguir fornece um guia para os métodos que retornam coleções enumeráveis.  
  
|Para enumerar|Coleção enumerável a retornar|Método a ser usado|  
|------------------|-------------------------------------|-------------------|  
|Diretórios|Nomes de diretório|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||Informações de diretório (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Arquivos|Nomes de arquivo|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||Informações do arquivo (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informações do sistema de arquivos|Entradas do sistema de arquivos|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||Informações do sistema de arquivos (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 Embora você possa enumerar imediatamente todos os arquivos nos subdiretórios de um diretório pai usando a opção de pesquisa <xref:System.IO.SearchOption.AllDirectories> fornecida pela enumeração <xref:System.IO.SearchOption>, as exceções de acesso não autorizado (<xref:System.UnauthorizedAccessException>) podem fazer com que a enumeração fique incompleta. Se essas exceções forem possíveis, você poderá capturá-las e continuar enumerando primeiros os diretórios e, depois, enumerando os arquivos.  
  
### <a name="to-enumerate-directory-names"></a>Para enumerar os nomes de diretório  
  
-   Use o método <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> para obter uma lista dos nomes de diretório de nível superior em um caminho especificado.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>Para enumerar os nomes de arquivo em um diretório e subdiretórios  
  
-   Use o método <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> para pesquisar um diretório e (opcionalmente) seus subdiretórios, e para obter uma lista de nomes de arquivos que correspondem a um padrão de pesquisa especificado.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>Para enumerar uma coleção de objetos DirectoryInfo  
  
-   Use o método <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> para obter uma coleção de diretórios de nível superior.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>Para enumerar uma coleção de objetos FileInfo em todos os diretórios  
  
-   Use o método <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> para obter uma coleção de arquivos que correspondem a um padrão de pesquisa especificado em todos os diretórios. Este exemplo enumera primeiro os diretórios de nível superior para capturar possíveis exceções de acesso não autorizado e, em seguida, enumera os arquivos.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
