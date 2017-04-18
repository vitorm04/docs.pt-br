---
title: "Arquivo é muito grande para ser lido em uma matriz de bytes | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6c07096fd2fa99438de8815a7567c4265ec0e3fa
ms.lasthandoff: 03/13/2017

---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>O arquivo é muito grande para ser lido em um array de bytes
O tamanho do arquivo que você está tentando ler em um array de bytes excede 4 GB. O `My.Computer.FileSystem.ReadAllBytes` método não pode ler um arquivo que excede esse tamanho.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use um <xref:System.IO.StreamReader>para ler o arquivo.</xref:System.IO.StreamReader> Para obter mais informações, consulte [Noções básicas do .NET Framework arquivo e/s e o sistema de arquivos (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A></xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>   
 <xref:System.IO.StreamReader></xref:System.IO.StreamReader>   
 [Acesso a arquivos com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)   
 [Como ler texto a partir de arquivos com um StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
