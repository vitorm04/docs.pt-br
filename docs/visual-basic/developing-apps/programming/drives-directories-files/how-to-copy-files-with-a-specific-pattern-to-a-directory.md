---
title: "Como copiar arquivos com um padr&#227;o espec&#237;fico para um diret&#243;rio no Visual Basic | Microsoft Docs"
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
  - "Método CopyFile, copiando arquivos [Visual Basic]"
  - "arquivos, copiando"
  - "Método CopyFile, copiar arquivos no Visual Basic"
  - "E/s [Visual Basic] Copiando arquivos"
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como copiar arquivos com um padr&#227;o espec&#237;fico para um diret&#243;rio no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> método retorna uma coleção somente leitura de cadeias de caracteres que representa os nomes de caminho para os arquivos. Você pode usar o `wildCards` para especificar um padrão específico.  
  
 Uma coleção vazia é retornada se nenhum arquivo correspondente for encontrado.  
  
 Você pode usar o <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> método para copiar os arquivos para um diretório.  
  
### Para copiar arquivos com um padrão específico para um diretório  
  
1.  Use o `GetFiles` método para retornar a lista de arquivos. Este exemplo retorna todos os arquivos. rtf do diretório especificado.  
  
     [!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]  
  
2.  Use o `CopyFile` método para copiar os arquivos. Este exemplo copia os arquivos para o diretório chamado `testdirectory`.  
  
     [!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]  
  
3.  Feche o `For` instrução com um `Next` instrução.  
  
     [!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]  
  
## Exemplo  
 O exemplo a seguir, que apresenta os trechos acima em sua forma completa, copia todos os arquivos. rtf do diretório especificado para o diretório chamado `testdirectory`.  
  
 [!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]  
  
## Segurança do .NET Framework  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de caracteres de comprimento zero, contém somente espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo \(começa com \\ \\. \\\) \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O diretório não existe \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   O diretório aponta para um arquivo existente \(<xref:System.IO.IOException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um nome de arquivo ou diretório no caminho contém dois\-pontos \(:\) ou está em um formato inválido \(<xref:System.NotSupportedException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\). O usuário não possui permissões necessárias \(<xref:System.UnauthorizedAccessException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>   
 [Como localizar subdiretórios com um padrão específico](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [Solucionando problemas: lendo e gravando em arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [Como obter a coleção de arquivos em um diretório](../Topic/How%20to:%20Get%20the%20Collection%20of%20Files%20in%20a%20Directory%20in%20Visual%20Basic.md)