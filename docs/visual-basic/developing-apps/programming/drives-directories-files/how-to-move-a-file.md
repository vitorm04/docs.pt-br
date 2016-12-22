---
title: "Como mover um arquivo no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arquivos, movendo"
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como mover um arquivo no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O `My.Computer.FileSystem.MoveFile` método pode ser usado para mover um arquivo para outra pasta. Se a estrutura de destino não existir, ele será criado.  
  
### Para mover um arquivo  
  
-   Use o `MoveFile` método para mover o arquivo, especificando o nome do arquivo e o local para o arquivo de origem e o arquivo de destino. Este exemplo move o arquivo chamado `test.txt` de `TestDir1` para `TestDir2`. Observe que o nome do arquivo de destino é especificado mesmo que seja o mesmo que o nome do arquivo de origem.  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### Para mover um arquivo e renomeá\-lo  
  
-   Use o `MoveFile` método para mover o arquivo, especificando o nome do arquivo de origem e local, o local de destino e o novo nome no local de destino. Este exemplo move o arquivo chamado `test.txt` de `TestDir1` para `TestDir2` e renomeia o arquivo `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de caracteres de comprimento zero, contém somente espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo \(começa com \\ \\. \\\) \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `destinationFileName` é `Nothing` ou uma cadeia de caracteres vazia \(<xref:System.ArgumentNullException>\).  
  
-   O arquivo de origem não é válido ou não existe \(<xref:System.IO.FileNotFoundException>\).  
  
-   O caminho combinado aponta para um diretório existente, o arquivo de destino existe e `overwrite` é definido como `False`, um arquivo no diretório de destino com o mesmo nome está em uso, ou o usuário não tem permissões suficientes para acessar o arquivo \(<xref:System.IO.IOException>\).  
  
-   Um nome de arquivo ou diretório no caminho contém dois\-pontos \(:\) ou está em um formato inválido \(<xref:System.NotSupportedException>\).  
  
-   `showUI` é definido como `True`, `onUserCancel` é definido como `ThrowException`, e o usuário cancelou a operação ou ocorre um erro de e\/s não especificado \(<xref:System.OperationCanceledException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
-   O usuário não tem permissão necessária \(<xref:System.UnauthorizedAccessException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>   
 [Como renomear um arquivo](../Topic/How%20to:%20Rename%20a%20File%20in%20Visual%20Basic.md)   
 [Como criar uma cópia de um arquivo em um diretório diferente](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [Como analisar caminhos de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)