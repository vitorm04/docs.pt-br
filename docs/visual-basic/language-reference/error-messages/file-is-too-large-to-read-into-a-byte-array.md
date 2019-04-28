---
title: O arquivo é muito grande para ser lido em um array de bytes
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 0c7d35e08eeb42e35c4c40e47434a64393d829b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800874"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>O arquivo é muito grande para ser lido em um array de bytes
O tamanho do arquivo que você está tentando ler em uma matriz de bytes excede 4 GB. O `My.Computer.FileSystem.ReadAllBytes` método não é possível ler um arquivo que excede esse tamanho.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Use um <xref:System.IO.StreamReader> para ler o arquivo. Para obter mais informações, consulte [Noções básicas do .NET Framework/s de arquivo e o sistema de arquivos (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Access de arquivo com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [Como: Ler texto de arquivos com um StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
