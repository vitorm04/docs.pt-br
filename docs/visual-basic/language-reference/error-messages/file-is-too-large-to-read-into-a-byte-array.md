---
title: O arquivo é muito grande para ser lido em um array de bytes
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 89459aaf766a70f69008f847dda7ac6e2a1e41d1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874181"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>O arquivo é muito grande para ser lido em um array de bytes

O tamanho do arquivo que você está tentando ler em uma matriz de bytes excede 4 GB. O `My.Computer.FileSystem.ReadAllBytes` método não pode ler um arquivo que exceda esse tamanho.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Use um <xref:System.IO.StreamReader> para ler o arquivo. Para obter mais informações, consulte [noções básicas de .NET Framework e/s de arquivo e o sistema de arquivos (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Access de arquivo com o Visual Basic](../../developing-apps/programming/drives-directories-files/file-access.md)
- [Como: ler texto usando arquivos com um StreamReader](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
