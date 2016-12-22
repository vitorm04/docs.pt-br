---
title: "Como excluir um arquivo no Visual Basic | Microsoft Docs"
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
  - "Método Delete"
  - "Objeto de arquivo"
  - "Arquivos , excluindo"
  - "Arquivos , manipulando"
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como excluir um arquivo no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O método `DeleteFile` do objeto `My.Computer.FileSystem` permite que você exclua um arquivo.  Entre as opções que ele oferece estão: se deseja enviar o arquivo excluído para a **Recycle Bin**, se deseja perguntar ao usuário para confirmar que o arquivo deve ser excluído, e o que fazer quando o usuário cancelar a operação.  
  
### Para excluir um arquivo de texto  
  
-   Use o método `DeleteFile` para excluir o arquivo.  O código a seguir demonstra como excluir o arquivo chamado `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### Para excluir um arquivo de texto e perguntar aos usuários para confirmar se o arquivo deve ser excluído  
  
-   Use o método `DeleteFile` para excluir o arquivo, definindo `showUI` como `AllDialogs`.  O código a seguir demonstra como excluir o arquivo chamado `test.txt` e permite ao usuário confirmar se o arquivo deve ser excluído.  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### Para excluir um arquivo de texto e enviá\-lo para a Recycle Bin  
  
-   Use o método `DeleteFile` para excluir o arquivo, especificando `SendToRecycleBin` para o parâmetro `recycle`.  O código a seguir demonstra como excluir o arquivo chamado `test.txt` e enviá\-lo para a **Recycle Bin**.  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido para uma das seguintes razões: ele é uma seqüência de comprimento zero, ele contém somente espaços em branco, ele contém caracteres inválidos ou é um caminho de dispositivo \(começa com \\ \\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um arquivo ou nome da pasta no caminho contém dois\-pontos \(:\) ou está em formato inválido \(<xref:System.NotSupportedException>\).  
  
-   O arquivo está em uso \(<xref:System.IO.IOException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
-   O arquivo não existe \(<xref:System.IO.FileNotFoundException>\).  
  
-   O usuário não tem permissão para excluir o arquivo, ou o arquivo é somente para leitura \(<xref:System.UnauthorizedAccessException>\).  
  
-   Uma situação de confiança parcial existe na qual o usuário não tem permissões suficientes \(<xref:System.Security.SecurityException>\).  
  
-   O usuário cancelou a operação e `onUserCancel` é definida como `ThrowException` \(<xref:System.OperationCanceledException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.UIOption>   
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>   
 [Como obter a coleção de arquivos em um diretório](../Topic/How%20to:%20Get%20the%20Collection%20of%20Files%20in%20a%20Directory%20in%20Visual%20Basic.md)