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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 462fd547c754c250f8f89838da03afbad879144b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="88522-102">O arquivo é muito grande para ser lido em um array de bytes</span><span class="sxs-lookup"><span data-stu-id="88522-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="88522-103">O tamanho do arquivo que você está tentando ler em um array de bytes excede 4 GB.</span><span class="sxs-lookup"><span data-stu-id="88522-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="88522-104">O `My.Computer.FileSystem.ReadAllBytes` método não pode ler um arquivo que excede esse tamanho.</span><span class="sxs-lookup"><span data-stu-id="88522-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88522-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="88522-105">To correct this error</span></span>  
  
-   <span data-ttu-id="88522-106">Use um <xref:System.IO.StreamReader>para ler o arquivo.</xref:System.IO.StreamReader></span><span class="sxs-lookup"><span data-stu-id="88522-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="88522-107">Para obter mais informações, consulte [Noções básicas do .NET Framework arquivo e/s e o sistema de arquivos (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="88522-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88522-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88522-108">See Also</span></span>  
 <span data-ttu-id="88522-109"><xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A></xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A></span><span class="sxs-lookup"><span data-stu-id="88522-109"><xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A></span></span>   
 <span data-ttu-id="88522-110"><xref:System.IO.StreamReader></xref:System.IO.StreamReader></span><span class="sxs-lookup"><span data-stu-id="88522-110"><xref:System.IO.StreamReader></span></span>   
<span data-ttu-id="88522-111"> [Acesso a arquivos com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md) </span><span class="sxs-lookup"><span data-stu-id="88522-111"> [File Access with Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md) </span></span>  
<span data-ttu-id="88522-112"> [Como ler texto a partir de arquivos com um StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)</span><span class="sxs-lookup"><span data-stu-id="88522-112"> [How to: Read Text from Files with a StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)</span></span>
