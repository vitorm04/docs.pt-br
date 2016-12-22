---
title: "Como anexar a arquivos de texto no Visual Basic | Microsoft Docs"
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
  - "E/S [Visual Basic], anexando a arquivos"
  - "E/S [Visual Basic], Método My.Computer.FileSystem.WriteAllText"
  - "E/S [Visual Basic], Método WriteAllText"
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como anexar a arquivos de texto no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> método pode ser usado para acrescentar a um arquivo de texto, especificando que o `append` parâmetro for definido como `True`.  
  
### Anexar em um arquivo de texto  
  
-   Use o método `WriteAllText`, especificando o arquivo de destino e a sequência de caracteres a ser anexada e definindo o parâmetro `append` para `True`.  
  
     Este exemplo grava a sequência de caracteres `"This is a test string."` para o arquivo chamado `Testfile.txt`.  
  
     [!CODE [VbFileIOWrite#6](../CodeSnippet/VS_Snippets_VBCSharp/VbFileIOWrite#6)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido para uma das seguintes razões: ele é uma seqüência de comprimento zero, ele contém somente espaços em branco, ele contém caracteres inválidos ou é um caminho de dispositivo \(começa com \\ \\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `File` aponta para um caminho que não existe \(<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>\).  
  
-   O arquivo está em uso por outro processo, ou ocorre um erro de I\/O \(<xref:System.IO.IOException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois\-pontos \(:\) ou está em um formato inválido \(<xref:System.NotSupportedException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 [Gravando em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)