---
title: Como excluir um arquivo no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 536c10070ef51044b801fc6a5805741896586dff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Como excluir um arquivo no Visual Basic
O método `DeleteFile` do objeto `My.Computer.FileSystem` permite a exclusão de um arquivo. As opções oferecidas são: enviar um arquivo excluído para a **Lixeira**, solicitar do usuário uma confirmação de que o arquivo deve ser excluído e o que fazer quando o usuário cancela a operação.  
  
### <a name="to-delete-a-text-file"></a>Excluir um arquivo de texto  
  
-   Use o método `DeleteFile` para excluir o arquivo. O código a seguir demonstra como excluir o arquivo com o nome `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Excluir um arquivo de texto e solicitar do usuário uma confirmação de que o arquivo deve ser excluído  
  
-   Use o método `DeleteFile` para excluir o arquivo, configurando `showUI` para `AllDialogs`. O código a seguir demonstra como excluir o arquivo com o nome `test.txt` e permitir que o usuário confirme se o arquivo deve ser excluído.  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Excluir um arquivo de texto e enviá-lo para a Lixeira  
  
-   Use o método `DeleteFile` para excluir o arquivo, especificando `SendToRecycleBin` para o parâmetro `recycle`. O código a seguir demonstra como excluir o arquivo com o nome `test.txt` e enviá-lo para a **Lixeira**.  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).  
  
-   O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   O arquivo está sendo usado (<xref:System.IO.IOException>).  
  
-   O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
-   O arquivo não existe (<xref:System.IO.FileNotFoundException>).  
  
-   O usuário não tem permissão para excluir o arquivo ou o arquivo é somente leitura (<xref:System.UnauthorizedAccessException>).  
  
-   Há uma situação de confiança parcial na qual o usuário não tem permissões suficientes (<xref:System.Security.SecurityException>).  
  
-   O usuário cancelou a operação e `onUserCancel` está definido como `ThrowException` (<xref:System.OperationCanceledException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.UIOption>  
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>  
 [Como obter a coleção de arquivos em um diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
