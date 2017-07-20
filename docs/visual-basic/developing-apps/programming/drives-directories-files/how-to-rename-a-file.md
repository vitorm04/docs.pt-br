---
title: Como renomear um arquivo no Visual Basic | Microsoft Docs
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
- I/O [Visual Basic], renaming files
- files, renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: 21
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
ms.openlocfilehash: a090fa8df6347a98b5c971c26664e6dd1098a594
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Como renomear um arquivo no Visual Basic
Use o método `RenameFile` do objeto `My.Computer.FileSystem` para renomear um arquivo, fornecendo o local atual, o nome de arquivo e o novo nome de arquivo. Esse método não pode ser usado para mover um arquivo. Use o método `MoveFile` para mover e renomear o arquivo.  
  
### <a name="to-rename-a-file"></a>Para renomear um arquivo  
  
-   Use o método `My.Computer.FileSystem.RenameFile` para renomear um arquivo. Este exemplo renomeia o arquivo chamado `Test.txt` para `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código do IntelliSense. No selecionador de trecho de código, o trecho está localizado em **Sistema de Arquivos – Processando Unidades, Pastas e Arquivos**. Para obter mais informações, consulte [Trechos de Código](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
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
 [Como Criar uma Cópia de um Arquivo no Mesmo Diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)   
 [Como criar uma cópia de um arquivo em um diretório diferente](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
