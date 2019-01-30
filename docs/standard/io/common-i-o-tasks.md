---
title: Tarefas comuns de E/S
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac2b0eafa64b809d2b40ac6471806dc9ab3c8c53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609623"
---
# <a name="common-io-tasks"></a>Tarefas comuns de E/S
O namespace <xref:System.IO> fornece várias classes que permitem que várias ações, como leitura e gravação, sejam realizadas em arquivos, diretórios e fluxos. Para obter mais informações, confira [E/S de arquivo e fluxo](../../../docs/standard/io/index.md).  
  
## <a name="common-file-tasks"></a>Tarefas comuns de arquivos  
  
|Para fazer isso...|Veja o exemplo neste tópico...|  
|-------------------|--------------------------------------|  
|Criar um arquivo de texto|Método <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType><br /><br /> Método <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType><br /><br /> Método <xref:System.IO.File.Create%2A?displayProperty=nameWithType><br /><br /> Método <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType>|  
|Gravar em um arquivo de texto|[Como: Gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)<br /><br /> [Como: Escrever um arquivo de texto (C++/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Ler de um arquivo de texto|[Como: Ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|Anexar texto em um arquivo|[Como: Abrir um arquivo de log e fazer acréscimos a ele](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)<br /><br /> Método <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType><br /><br /> Método <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType>|  
|Renomear ou mover um arquivo|Método <xref:System.IO.File.Move%2A?displayProperty=nameWithType><br /><br /> Método <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Excluir um arquivo|Método <xref:System.IO.File.Delete%2A?displayProperty=nameWithType><br /><br /> Método <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType>|  
|Copiar um arquivo|Método <xref:System.IO.File.Copy%2A?displayProperty=nameWithType><br /><br /> Método <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType>|  
|Obter o tamanho de um arquivo|Propriedade <xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType>|  
|Obter os atributos de um arquivo|Método <xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType>|  
|Definir os atributos de um arquivo|Método <xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType>|  
|Determinar se um arquivo existe|Método <xref:System.IO.File.Exists%2A?displayProperty=nameWithType>|  
|Ler de um arquivo binário|[Como: Ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Gravar em um arquivo binário|[Como: Ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Recuperar uma extensão de nome de arquivo|Método <xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType>|  
|Recuperar o caminho totalmente qualificado de um arquivo|Método <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>|  
|Recuperar o nome e a extensão do arquivo de um caminho|Método <xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType>|  
|Alterar a extensão de um arquivo|Método <xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType>|  
  
## <a name="common-directory-tasks"></a>Tarefas comuns de diretório  
  
|Para fazer isso...|Veja o exemplo neste tópico...|  
|-------------------|--------------------------------------|  
|Acessar um arquivo em uma pasta especial, como Meus Documentos|[Como: Gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|Criar um diretório|Método <xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType><br /><br /> Propriedade <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType>|  
|Criar um subdiretório|Método <xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType>|  
|Renomear ou mover um diretório|Método <xref:System.IO.Directory.Move%2A?displayProperty=nameWithType><br /><br /> Método <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Copiar um diretório|[Como: Copiar diretórios](../../../docs/standard/io/how-to-copy-directories.md)|  
|Excluir um diretório|Método <xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType><br /><br /> Método <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType>|  
|Ver os arquivos e subdiretórios em um diretório|[Como: Enumerar diretórios e arquivos](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)|  
|Descobrir o tamanho de um diretório|Classe <xref:System.IO.Directory?displayProperty=nameWithType>|  
|Determinar se um diretório existe|Método <xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Consulte também

- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
- [Compondo fluxos](../../../docs/standard/io/composing-streams.md)
- [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md)
