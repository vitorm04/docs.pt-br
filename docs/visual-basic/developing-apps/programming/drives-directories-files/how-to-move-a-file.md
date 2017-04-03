---
title: Como mover um arquivo no Visual Basic | Microsoft Docs
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
- files, moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4505e64cdd4a31e133ce2dbbc9ae42c99bdc83a1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-move-a-file-in-visual-basic"></a>Como mover um arquivo no Visual Basic
O método `My.Computer.FileSystem.MoveFile` pode ser utilizado para mover um arquivo para outra pasta. Se a estrutura de destino não existir, ela será criada.  
  
### <a name="to-move-a-file"></a>Mover um arquivo  
  
-   Use o método `MoveFile` para mover o arquivo, especificando o nome de arquivo e o local tanto para o arquivo de origem quanto para o arquivo de destino. Este exemplo move o arquivo de nome `test.txt` de `TestDir1` para `TestDir2`. Observe que o nome do arquivo de destino é especificado mesmo que seja igual ao nome do arquivo de origem.  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Mover um arquivo e renomeá-lo  
  
-   Use o método `MoveFile` para mover o arquivo, especificando o nome de arquivo e o local, o local de destino e o novo nome no local de destino. Este exemplo move o arquivo de nome `test.txt` de `TestDir1` para `TestDir2` e o renomeia como `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de caracteres de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).  
  
-   O caminho não é válido, porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationFileName` é `Nothing` ou uma cadeia de caracteres vazia (<xref:System.ArgumentNullException>).  
  
-   O arquivo de origem não é válido ou não existe (<xref:System.IO.FileNotFoundException>).  
  
-   O caminho combinado aponta para um diretório existente, o arquivo de destino existe e `overwrite` é definido como `False`, um arquivo no diretório de destino com o mesmo nome está em uso ou o usuário não tem permissões suficientes para acessar o arquivo (<xref:System.IO.IOException>).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   `showUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e o usuário cancelou a operação ou um erro não especificado de E/S ocorreu (<xref:System.OperationCanceledException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   O usuário não tiver as permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
-   O usuário não tem a permissão necessária (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>   
 [Como Renomear um Arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)   
 [Como Criar uma Cópia de um Arquivo em um Diretório Diferente](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [Como analisar demarcadores de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
