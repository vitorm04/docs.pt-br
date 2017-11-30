---
title: "O arquivo é muito grande para ser lido em um array de bytes"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bbdb5a4dcaa22ca84428ef28c8838a6d9a0ee1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>O arquivo é muito grande para ser lido em um array de bytes
O tamanho do arquivo que você está tentando ler em uma matriz de bytes excede 4 GB. O `My.Computer.FileSystem.ReadAllBytes` método não pode ler um arquivo que excede esse tamanho.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use um <xref:System.IO.StreamReader> para ler o arquivo. Para obter mais informações, consulte [Noções básicas do .NET Framework arquivo e/s e o sistema de arquivos (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [Access de arquivo com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [Como ler texto a partir de arquivos com um StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
