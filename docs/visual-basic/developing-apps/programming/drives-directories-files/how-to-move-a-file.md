---
title: Como mover um arquivo
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 29c64a7a81028d47bf489212e6d8faec5e8dda75
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335365"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Como mover um arquivo no Visual Basic

O método `My.Computer.FileSystem.MoveFile` pode ser utilizado para mover um arquivo para outra pasta. Se a estrutura de destino não existir, ela será criada.  
  
### <a name="to-move-a-file"></a>Mover um arquivo  
  
- Use o método `MoveFile` para mover o arquivo, especificando o nome de arquivo e o local tanto para o arquivo de origem quanto para o arquivo de destino. Este exemplo move o arquivo de nome `test.txt` de `TestDir1` para `TestDir2`. Observe que o nome do arquivo de destino é especificado mesmo que seja igual ao nome do arquivo de origem.  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Mover um arquivo e renomeá-lo  
  
- Use o método `MoveFile` para mover o arquivo, especificando o nome de arquivo e o local, o local de destino e o novo nome no local de destino. Este exemplo move o arquivo de nome `test.txt` de `TestDir1` para `TestDir2` e o renomeia como `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a>Programação Robusta  

 As seguintes condições podem causar uma exceção:  
  
- O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).  
  
- O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
- `destinationFileName` é `Nothing` ou é uma cadeia de caracteres vazia (<xref:System.ArgumentNullException>).  
  
- O arquivo de origem não é válido ou não existe (<xref:System.IO.FileNotFoundException>).  
  
- O caminho combinado aponta para um diretório existente, o arquivo de destino existe e `overwrite` é definido como `False`, um arquivo no diretório de destino com o mesmo nome está sendo usado ou o usuário não tem permissões suficientes para acessar o arquivo (<xref:System.IO.IOException>).  
  
- Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
- `showUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e o usuário cancelou a operação ou ocorre um erro de E/S não especificado (<xref:System.OperationCanceledException>).  
  
- O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
- O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
- O usuário não tem a permissão necessária (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Como renomear um arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [Como criar uma cópia de um arquivo em um diretório diferente](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Como analisar demarcadores de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
