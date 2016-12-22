---
title: "Como criar um diret&#243;rio no Visual Basic | Microsoft Docs"
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
  - "diretórios [Visual Basic], criando"
  - "pastas [Visual Basic], criando"
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar um diret&#243;rio no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Use o método `CreateDirectory` do objeto `My.Computer.FileSystem` para criar diretórios.  
  
 Se o diretório já existir, nenhuma exceção é lançada.  
  
### Para criar um diretório  
  
-   Use o método `CreateDirectory` especificando o caminho completo da localidade onde o diretório deve ser criado.  Este exemplo cria o diretório `NewDirectory` no `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O nome do diretório é incorreto.  Por exemplo, ele contém caracteres ilegais ou apenas espaços em branco \(<xref:System.ArgumentException>\).  
  
-   A pasta pai da pasta a ser criada é somente leitura \(<xref:System.IO.IOException>\).  
  
-   O nome do diretório é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O nome do diretório é muito longo \(<xref:System.IO.PathTooLongException>\).  
  
-   O nome do diretório é um dois\-pontos ": " \(<xref:System.NotSupportedException>\).  
  
-   O usuário não tem permissão para criar a pasta \(<xref:System.UnauthorizedAccessException>\).  
  
-   O usuário não possui permissões em uma situação de confiança parcial \(<xref:System.Security.SecurityException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>   
 [Criando, excluindo e movendo arquivos e diretórios](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)