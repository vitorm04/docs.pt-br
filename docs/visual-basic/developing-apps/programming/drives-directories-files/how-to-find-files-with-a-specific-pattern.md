---
title: "Como localizar arquivos com um padr&#227;o espec&#237;fico no Visual Basic | Microsoft Docs"
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
  - "Arquivos , localizando"
  - "correspondência padrão"
  - "padrões, correspondência"
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como localizar arquivos com um padr&#227;o espec&#237;fico no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O método de <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> retorna uma coleção somente leitura de cadeias de caracteres que representam os nomes de caminho para os arquivos.  Você pode usar o parâmetro `wildCards` para especificar um padrão específico.  Se você deseja incluir o subpastas na pesquisa, defina o parâmetro `searchType` como `SearchOption.SearchAllSubDirectories`.  
  
 Uma coleção vazia é retornada se nenhum arquivo que corresponda ao padrão especificado for encontrado.  
  
> [!NOTE]
>  Para obter informações sobre retornar uma lista de arquivo usando a classe de `DirectoryInfo` de namespace de `System.IO` , consulte <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### Para localizar arquivos com um padrão especificado  
  
-   Use o método `GetFiles` fornecendo o nome e caminho do diretório que você deseja pesquisar e especificando o padrão.  O exemplo a seguir retorna todos os arquivos com a extensão `.dll` no diretório e os adiciona à `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-files-with-a-specific-pattern_1.vb)]  
  
## Segurança do .NET Framework  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos motivos a seguir: é uma cadeia de caracteres de comprimento zero, contém somente espaço em branco, contém caracteres inválidos, ou é um caminho de dispositivo \(começa com \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `directory` não existe. \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   `directory` aponta para um arquivo existente \(<xref:System.IO.IOException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um arquivo ou nome da pasta no caminho contém dois\-pontos \(:\) ou está em formato inválido \(<xref:System.NotSupportedException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
-   O usuário não possui as permissões necessárias \(<xref:System.UnauthorizedAccessException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>   
 [Como localizar subdiretórios com um padrão específico](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [Solucionando problemas: lendo e gravando em arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [Como obter a coleção de arquivos em um diretório](../Topic/How%20to:%20Get%20the%20Collection%20of%20Files%20in%20a%20Directory%20in%20Visual%20Basic.md)