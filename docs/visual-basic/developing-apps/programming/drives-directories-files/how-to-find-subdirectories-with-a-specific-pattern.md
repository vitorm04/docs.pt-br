---
title: "Como localizar subdiret&#243;rios com um padr&#227;o espec&#237;fico no Visual Basic | Microsoft Docs"
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
  - "pastas, localizando"
  - "correspondência padrão"
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como localizar subdiret&#243;rios com um padr&#227;o espec&#237;fico no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method retorna uma coleção somente leitura de seqüências de caracteres que representa os nomes de caminho para as subpastas em um diretório.  Você pode usar o parâmetro `wildCards` para especificar um padrão.  Se você deseja incluir o conteúdo de subpastas na pesquisa, defina o parâmetro `searchType` como `SearchOption.SearchAllSubDirectories`.  
  
 Uma coleção vazia é retornada se nenhum diretório for encontrado que correspondam ao padrão especificado.  
  
### Para localizar subdiretórios com um padrão específico  
  
-   Use o método `GetDirectories` fornecendo o nome e caminho do diretório que você deseja pesquisar.  O exemplo a seguir retorna todas as pastas da estrutura de diretórios que contêm a palavra "Logs" em seu nome e as adiciona em `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido para uma das seguintes razões: ele é uma seqüência de comprimento zero, ele contém somente espaços em branco, ele contém caracteres inválidos ou é um caminho de dispositivo \(começa com \\ \\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   Um ou mais dos caracteres curinga especificados é `Nothing`, uma sequência vazia, ou contém apenas espaços \(<xref:System.ArgumentNullException>\).  
  
-   `directory` não existe. \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   `directory` aponta para um arquivo existente \(<xref:System.IO.IOException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um arquivo ou nome da pasta no caminho contém dois\-pontos \(:\) ou está em formato inválido \(<xref:System.NotSupportedException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
-   O usuário não possui as permissões necessárias \(<xref:System.UnauthorizedAccessException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>   
 [Como localizar arquivos com um padrão específico](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)