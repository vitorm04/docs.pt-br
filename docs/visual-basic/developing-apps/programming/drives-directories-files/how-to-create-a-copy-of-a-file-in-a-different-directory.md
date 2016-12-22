---
title: "Como criar uma c&#243;pia de um arquivo em um diret&#243;rio diferente no Visual Basic | Microsoft Docs"
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
  - "Método CopyFile, copiando arquivos no Visual Basic"
  - "Arquivos , copiando"
  - "E/S [Visual Basic], copiando arquivos"
  - "Método My.Computer.FileSystem.CopyFile, copiando arquivos [Visual Basic]"
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar uma c&#243;pia de um arquivo em um diret&#243;rio diferente no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O método `My.Computer.FileSystem.CopyFile` permite que você copie arquivos.  Seus parâmetros fornecem a capacidade de sobrescrever arquivos existentes, renomiar o arquivo, mostrar o andamento da operação e permitir que o usuário cancele a operação.  
  
### Para copiar um arquivo de texto para outra pasta  
  
-   Use o método `CopyFile` para copiar um arquivo, especificando um arquivo de origem e o diretório de destino.  O parâmetro `overwrite` permite que você especifique se deseja ou não substituir arquivos existentes.  Os exemplos de código a seguir demonstram como usar `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido para um dos seguintes motivos: é uma seqüência de comprimento zero, ele contém somente espaço em branco, ele contém caracteres inválidos ou é um caminho dispositivo \(começa com \\ \\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   O sistema não pôde recuperar o caminho absoluto \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O arquivo de origem não é válido ou não existe \(<xref:System.IO.FileNotFoundException>\).  
  
-   O caminho combinado aponta para uma pasta existente \(<xref:System.IO.IOException>\).  
  
-   O arquivo de destino existe e `overwrite` é definida como `False` \(<xref:System.IO.IOException>\).  
  
-   O usuário não tem permissões suficientes para acessar o arquivo \(<xref:System.IO.IOException>\).  
  
-   Um arquivo na pasta de destino com o mesmo nome está em uso \(<xref:System.IO.IOException>\).  
  
-   Um arquivo ou nome da pasta no caminho contém dois\-pontos \(:\) ou está em formato inválido \(<xref:System.NotSupportedException>\).  
  
-   `ShowUI` está definida como `True`, \(`onUserCancel`\) está definida como  `ThrowException`, e o usuário cancelou a operação \(<xref:System.OperationCanceledException>\).  
  
-   `ShowUI` está definida como `True`, `onUserCancel` está definida como `ThrowException`, e ocorre um erro de E\/S não especificado \(<xref:System.OperationCanceledException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   O usuário não tem permissão necessária \(<xref:System.UnauthorizedAccessException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 [Como copiar arquivos com um padrão específico para um diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)   
 [Como criar uma cópia de um arquivo no mesmo diretório](../Topic/How%20to:%20Create%20a%20Copy%20of%20a%20File%20in%20the%20Same%20Directory%20in%20Visual%20Basic.md)   
 [Como copiar um diretório para outro diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [Como renomear um arquivo](../Topic/How%20to:%20Rename%20a%20File%20in%20Visual%20Basic.md)