---
title: "O arquivo &#233; muito grande para ser lido em um array de bytes | Microsoft Docs"
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
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O arquivo &#233; muito grande para ser lido em um array de bytes
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O tamanho do arquivo que você está tentando ler em um array de bytes excede 4 GB.  O método `My.Computer.FileSystem.ReadAllBytes` não pode ler um arquivo que excede esse tamanho.  
  
### Para corrigir este erro  
  
-   Use um <xref:System.IO.StreamReader> para ler o arquivo.  Para obter mais informações, consulte [Noções básicas de E\/S de arquivo do .NET Framework e o sistema de arquivos \(Visual Basic\)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>   
 <xref:System.IO.StreamReader>   
 [Access de arquivo com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)   
 [Como ler texto a partir de arquivos com um StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)