---
title: "Como Localizar Subdiretórios com um Padrão Específico no Visual Basic | Microsoft Docs"
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
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
caps.latest.revision: 16
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3fc7683c6629e2d94f3acb670810c6632efec094
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Como localizar subdiretórios com um padrão específico no Visual Basic
O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> retorna uma coleção somente leitura de cadeias de caracteres que representam os nomes de caminho para os subdiretórios em um diretório. É possível usar o parâmetro `wildCards` para especificar um padrão específico. Caso deseje incluir os conteúdos dos subdiretórios na pesquisa, defina o parâmetro `searchType` para `SearchOption.SearchAllSubDirectories`.  
  
 Uma coleção vazia será retornada se nenhum diretório correspondente ao padrão especificado for encontrado.  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a>Localizar subdiretórios com um padrão específico  
  
-   Use o método `GetDirectories`, fornecendo o nome e o caminho do diretório a ser pesquisado. O exemplo a seguir retorna todos os diretórios na estrutura de diretório que contém a palavra “Logs” em seu nome e as adiciona a `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).  
  
-   O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Um ou mais dos caracteres curinga especificados é `Nothing`, uma cadeia de caracteres vazia ou contém somente espaços (<xref:System.ArgumentNullException>).  
  
-   `directory` não existe (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` aponta para um arquivo existente (<xref:System.IO.IOException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
-   O usuário não possui as permissões necessárias (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>   
 [Como localizar arquivos com um padrão específico](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
