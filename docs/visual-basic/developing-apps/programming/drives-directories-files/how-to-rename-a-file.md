---
title: Como renomear um arquivo no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34316fabf63959389eee498a6063ac7c9a7b320a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Como renomear um arquivo no Visual Basic
Use o método `RenameFile` do objeto `My.Computer.FileSystem` para renomear um arquivo, fornecendo o local atual, o nome de arquivo e o novo nome de arquivo. Esse método não pode ser usado para mover um arquivo. Use o método `MoveFile` para mover e renomear o arquivo.  
  
### <a name="to-rename-a-file"></a>Para renomear um arquivo  
  
-   Use o método `My.Computer.FileSystem.RenameFile` para renomear um arquivo. Este exemplo renomeia o arquivo chamado `Test.txt` para `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código do IntelliSense. No selecionador de trecho de código, o trecho está localizado em **Sistema de Arquivos – Processando Unidades, Pastas e Arquivos**. Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).  
  
-   `newName` contém informações de caminho (<xref:System.ArgumentException>).  
  
-   O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `newName` é `Nothing` ou é uma cadeia de caracteres vazia (<xref:System.ArgumentNullException>).  
  
-   O arquivo de origem não é válido ou não existe (<xref:System.IO.FileNotFoundException>).  
  
-   Há um arquivo ou diretório existente com o nome especificado em `newName` (<xref:System.IO.IOException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
-   O usuário não tem a permissão necessária (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>  
 [Como mover um arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)  
 [Criando, excluindo e movendo arquivos e diretórios](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 [Como criar uma cópia de um arquivo no mesmo diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [Como criar uma cópia de um arquivo em um diretório diferente](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
