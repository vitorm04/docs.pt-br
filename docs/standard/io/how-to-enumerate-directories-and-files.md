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
helpviewer_keywords: I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: caf9bdec017a5466269ff7fe97be4d0243035b4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enumerate-directories-and-files"></a>Como enumerar diretórios e arquivos
Você pode enumerar diretórios e arquivos usando métodos que retornam uma coleção enumerável de cadeias de caracteres de seus nomes. Você também pode usar os métodos que retornam uma coleção enumerável de <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, ou <xref:System.IO.FileSystemInfo> objetos. Coleções enumeráveis fornecem desempenho melhor que matrizes ao trabalhar com grandes coleções de arquivos e diretórios.  
  
 Você também pode usar coleções enumeráveis obtidas desses métodos para fornecer a <xref:System.Collections.Generic.IEnumerable%601> parâmetro para construtores de coleção de classes, como o <xref:System.Collections.Generic.List%601> classe.  
  
 Se você quiser obter somente os nomes de arquivos ou diretórios, use os métodos de enumeração do <xref:System.IO.Directory> classe. Se você quiser obter outras propriedades de arquivos ou diretórios, use o <xref:System.IO.DirectoryInfo> e <xref:System.IO.FileSystemInfo> classes.  
  
 A tabela a seguir fornece um guia para os métodos que retornam coleções enumeráveis.  
  
|Para enumerar|Coleção enumerável para retornar|Método a ser usado|  
|------------------|-------------------------------------|-------------------|  
|Diretórios|Nomes de diretório|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||Informações de diretório (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Arquivos|Nomes de arquivo|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||Arquivo de informações (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informações do sistema de arquivos|Entradas do arquivo de sistema|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||Informações do sistema de arquivos (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 Embora você pode enumerar imediatamente todos os arquivos nos subdiretórios de um diretório pai usando o <xref:System.IO.SearchOption.AllDirectories> pesquisar opção fornecida pelo <xref:System.IO.SearchOption> enumeração, as exceções de acesso não autorizado (<xref:System.UnauthorizedAccessException>) pode fazer com que a enumeração de pode estar incompleta. Se essas exceções são possíveis, você pode capturá-los e continuar primeiro enumerando diretórios e, em seguida, enumera arquivos.  
  
### <a name="to-enumerate-directory-names"></a>Para enumerar os nomes de diretório  
  
-   Use o <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> método para obter uma lista dos nomes de diretório de nível superior em um caminho especificado.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>Para enumerar os nomes de arquivo em um diretório e subdiretórios  
  
-   Use o <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> método para pesquisar um diretório e (opcionalmente) seus subdiretórios e para obter uma lista de nomes de arquivos que correspondem a um padrão de pesquisa especificados.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>Para enumerar uma coleção de objetos DirectoryInfo  
  
-   Use o <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> método para obter uma coleção de pastas de nível superior.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>Para enumerar uma coleção de objetos FileInfo em todos os diretórios  
  
-   Use o <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> método para obter uma coleção de arquivos que correspondem a um padrão de pesquisa especificada em todos os diretórios. Este exemplo enumera primeiro as pastas de nível superior para capturar exceções de acesso não autorizado possíveis e, em seguida, enumera os arquivos.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
