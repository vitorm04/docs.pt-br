---
title: "Como gravar em arquivos bin&#225;rios no Visual Basic | Microsoft Docs"
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
  - "arquivos binários, gravando em Visual Basic"
  - "Arquivos , acesso binário"
  - "Método WriteAllBytes"
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como gravar em arquivos bin&#225;rios no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> método grava dados em um arquivo binário.  Se o parâmetro `append` for `True`, ele irá acrescentar os dados para o arquivo; caso contrário, dados no arquivo são substituídos.  
  
 Se o caminho especificado excluindo o nome de arquivo não for válido, uma exceção <xref:System.IO.DirectoryNotFoundException> será acionada.  Se o caminho é válido, mas o arquivo não existir, o arquivo será criado.  
  
### Para Gravar em um arquivo binário.  
  
-   Use o método `WriteAllBytes`, fornecendo o caminho do arquivo e nome e os bytes a serem gravados.  Este exemplo acrescenta a matriz de dados `CustomerData` para o arquivo chamado `CollectedData.dat`.  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## Programação robusta  
 As seguintes condições podem criar uma exceção:  
  
-   O caminho não é válido por uma das razões a seguir: ele é uma sequência de comprimento zero, ou ele contém somente espaço em branco, ele contém caracteres inválidos.  \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `File` aponta para um caminho que não existe \(<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>\).  
  
-   O arquivo está em uso por outro processo, ou ocorre um erro de I\/O \(<xref:System.IO.IOException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois\-pontos \(:\) ou está em um formato inválido \(<xref:System.NotSupportedException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [Como gravar texto em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)