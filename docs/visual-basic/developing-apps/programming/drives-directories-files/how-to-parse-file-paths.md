---
title: Como Analisar Demarcadores de Arquivo no Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- file names, parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a23fb13e99e94d6fa144c82edffca7afaaef96b3
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Como analisar demarcadores de arquivo no Visual Basic
O objeto <xref:Microsoft.VisualBasic.FileIO.FileSystem> oferece uma série de métodos úteis ao analisar os caminhos de arquivo.  
  
-   O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> usa dois caminhos e retorna um caminho combinado formatado corretamente.  
  
-   O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> retorna o caminho absoluto do pai do caminho fornecido.  
  
-   O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> retorna um objeto <xref:System.IO.FileInfo> que pode ser consultado para determinar as propriedades do arquivo, como seu nome e caminho.  
  
 Não tome decisões sobre os conteúdos do arquivo com base na extensão de nome de arquivo. Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Determinar o nome e o caminho de um arquivo  
  
-   Use as propriedades <xref:System.IO.FileInfo.DirectoryName%2A> e <xref:System.IO.FileInfo.Name%2A> do objeto <xref:System.IO.FileInfo> para determinar o nome e o caminho do arquivo. Este exemplo determina o nome e o caminho e os exibe.  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Combinar o nome e o diretório de um arquivo para criar o caminho completo  
  
-   Use o método `CombinePath`, fornecendo o diretório e o nome. Este exemplo usa as cadeias de caracteres `folderPath` e `fileName`, criadas no exemplo anterior, as combina e exibe o resultado.  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>   
 <xref:System.IO.FileInfo>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>   
 [Como obter a coleção de arquivos em um diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
