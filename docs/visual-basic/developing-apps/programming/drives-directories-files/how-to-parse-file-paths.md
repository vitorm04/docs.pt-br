---
title: "Como analisar caminhos de arquivo no Visual Basic | Microsoft Docs"
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
  - "nomes de arquivos, analisando [Visual Basic]"
  - "análise de caminhos de arquivo [Visual Basic]"
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como analisar caminhos de arquivo no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.FileIO.FileSystem> object oferece uma série de métodos úteis ao analisar os caminhos de arquivo.  
  
-   O <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> método utiliza dois caminhos e retorna um caminho combinado corretamente formatado.  
  
-   O <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> método retorna o caminho absoluto do pai do caminho fornecido.  
  
-   O <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> método retorna um <xref:System.IO.FileInfo> objeto que pode ser consultado para determinar propriedades do arquivo, como seu nome e caminho.  
  
 Não tome decisões sobre o conteúdo do arquivo com base na extensão de nome de arquivo. Por exemplo, o arquivo Form1. vb pode não ser um arquivo de origem Visual Basic.  
  
### Para determinar o nome e o caminho do arquivo  
  
-   Use o <xref:System.IO.FileInfo.DirectoryName%2A> e <xref:System.IO.FileInfo.Name%2A> Propriedades do <xref:System.IO.FileInfo> objeto para determinar o nome e o caminho do arquivo. Este exemplo determina o nome e o caminho e os exibe.  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### Para combinar o nome de um arquivo e diretório para criar o caminho completo  
  
-   Use o `CombinePath` All, fornecendo o diretório e o nome. Este exemplo usa as cadeias de caracteres `folderPath` e `fileName` criado no exemplo anterior, as combina e exibe o resultado.  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>   
 <xref:System.IO.FileInfo>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>   
 [Como obter a coleção de arquivos em um diretório](../Topic/How%20to:%20Get%20the%20Collection%20of%20Files%20in%20a%20Directory%20in%20Visual%20Basic.md)