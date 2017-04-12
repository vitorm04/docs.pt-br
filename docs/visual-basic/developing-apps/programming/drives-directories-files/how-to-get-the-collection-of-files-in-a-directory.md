---
title: "Como obter a coleção de arquivos em um diretório no Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- folders, working with
- files, accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5b36baee302db0214844e0553473a05603090f1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Como obter a coleção de arquivos em um diretório no Visual Basic
As sobrecargas do método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> retornam uma coleção de cadeias de caracteres somente leitura que representam os nomes dos arquivos em um diretório:  
  
-   Use a sobrecarga <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> para uma pesquisa de arquivo simples em um diretório especificado, sem pesquisar em subdiretórios.  
  
-   Use a sobrecarga <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> para especificar opções adicionais para a sua pesquisa. É possível usar o parâmetro `wildCards` para especificar um padrão de busca. Para incluir subdiretórios na pesquisa, defina o parâmetro `searchType` como <xref:Microsoft.VisualBasic.FileIO.SearchOption?displayProperty=fullName>.  
  
 Uma coleção vazia é retornada se nenhum arquivo correspondente ao padrão especificado for encontrado.  
  
### <a name="to-list-files-in-a-directory"></a>Listar arquivos em um diretório  
  
-   Use uma das sobrecargas de método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName>, fornecendo o nome e o caminho do diretório a ser pesquisado no parâmetro `directory`. O exemplo a seguir retorna todos os arquivos no diretório e os inclui na `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de caracteres de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).  
  
-   O caminho não é válido, porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O `directory` não existe (<xref:System.IO.DirectoryNotFoundException>).  
  
-   O `directory` aponta para um arquivo existente (<xref:System.IO.IOException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   O usuário não tiver as permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
-   O usuário não tem as permissões necessárias (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>   
 [Como localizar arquivos com um padrão específico](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)   
 [Como localizar subdiretórios com um padrão específico](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)

