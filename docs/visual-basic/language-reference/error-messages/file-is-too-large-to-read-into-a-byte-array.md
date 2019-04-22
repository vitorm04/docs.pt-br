---
title: O arquivo é muito grande para ser lido em um array de bytes
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 0c7d35e08eeb42e35c4c40e47434a64393d829b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831508"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="cf99c-102">O arquivo é muito grande para ser lido em um array de bytes</span><span class="sxs-lookup"><span data-stu-id="cf99c-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="cf99c-103">O tamanho do arquivo que você está tentando ler em uma matriz de bytes excede 4 GB.</span><span class="sxs-lookup"><span data-stu-id="cf99c-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="cf99c-104">O `My.Computer.FileSystem.ReadAllBytes` método não é possível ler um arquivo que excede esse tamanho.</span><span class="sxs-lookup"><span data-stu-id="cf99c-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cf99c-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cf99c-105">To correct this error</span></span>  
  
-   <span data-ttu-id="cf99c-106">Use um <xref:System.IO.StreamReader> para ler o arquivo.</span><span class="sxs-lookup"><span data-stu-id="cf99c-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="cf99c-107">Para obter mais informações, consulte [Noções básicas do .NET Framework/s de arquivo e o sistema de arquivos (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="cf99c-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf99c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf99c-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="cf99c-109">Access de arquivo com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf99c-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="cf99c-110">Como: Ler texto de arquivos com um StreamReader</span><span class="sxs-lookup"><span data-stu-id="cf99c-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
