---
title: "Como ler a partir de arquivos bin&#225;rios no Visual Basic | Microsoft Docs"
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
  - "arquivos binários, lendo de"
  - "E/S [Visual Basic], lendo de arquivos binários"
  - "Objeto My.Computer.FileSystem, lendo de arquivos binários"
  - "Método ReadAllBytes, lendo de arquivos binários"
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ler a partir de arquivos bin&#225;rios no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O objeto `My.Computer.FileSystem` fornece o método `ReadAllBytes` para leitura de arquivos binários.  
  
### Para ler de um arquivo binário  
  
-   Use o método `ReadAllBytes` que retorna o conteúdo de um arquivo como uma matriz de bytes.  Este exemplo lê a partir do arquivo `C:/Documents and Settings/selfportrait.jpg`.  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_1.vb)]  
  
-   Para arquivos binários grandes, você pode usar o <xref:System.IO.FileStream.Read%2A> método da <xref:System.IO.FileStream> o objeto para ler o arquivo apenas uma quantidade especificada por vez.  Você pode limitar a quantidade do arquivo é carregado na memória para cada operação de leitura.  O exemplo de código a seguir copia um arquivo e permite que o chamador especificar quanto do arquivo é lido na memória por operação de leitura.  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_2.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por uma das razões a seguir: ele é uma sequência de comprimento zero, ele contém somente espaço em branco, ele contém caracteres inválidos, ou é um caminho de dispositivo \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O arquivo não existe \(<xref:System.IO.FileNotFoundException>\).  
  
-   O arquivo está em uso por outro processo, ou ocorre um erro de I\/O \(<xref:System.IO.IOException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois\-pontos \(:\) ou está em um formato inválido \(<xref:System.NotSupportedException>\).  
  
-   Não há memória suficiente para gravar a sequência de caracteres no buffer \(<xref:System.OutOfMemoryException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
 Não faça decisões sobre o conteúdo do arquivo com base no nome do arquivo.  Por exemplo, o arquivo Form1.vb pode não ser um arquivo fonte do Visual Basic.  
  
 Verifique todas as entradas antes de usar os dados no seu aplicativo.  O conteúdo do arquivo pode não ser esperado e métodos para ler o arquivo podem falhar.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [Lendo a partir de arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Como ler a partir de arquivos de texto com vários formatos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Armazenando dados e lendo a partir da Área de Transferência](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)