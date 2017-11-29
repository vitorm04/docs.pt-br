---
title: "Como localizar arquivos com um padrão específico no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce37e7241eb33c3d4f18355d3b5375e0de95b28f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Como localizar arquivos com um padrão específico no Visual Basic
O método <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> retorna uma coleção somente leitura de cadeias de caracteres que representam os nomes de caminho para os arquivos. É possível usar o parâmetro `wildCards` para especificar um padrão específico. Para incluir subdiretórios na pesquisa, configure o parâmetro `searchType` para `SearchOption.SearchAllSubDirectories`.  
  
 Uma coleção vazia é retornada se nenhum arquivo correspondente ao padrão especificado for encontrado.  
  
> [!NOTE]
>  Para saber mais sobre como retornar uma lista de arquivos usando a classe `DirectoryInfo` do namespace `System.IO`, confira <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Localizar arquivos com um padrão específico  
  
-   Use o método `GetFiles`, fornecendo o nome e o caminho do diretório a ser pesquisado e especificando o padrão. O exemplo a seguir retorna todos os arquivos com a extensão `.dll` no diretório e os adiciona a `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-files-with-a-specific-pattern_1.vb)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).  
  
-   O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `directory` não existe (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` aponta para um arquivo existente (<xref:System.IO.IOException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
-   O usuário não possui as permissões necessárias (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>  
 [Como localizar subdiretórios com um padrão específico](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [Solução de problemas: lendo e gravando em arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [Como obter a coleção de arquivos em um diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
