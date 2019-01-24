---
title: Codificação não pode ser definida como Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 99dbd1a068cabca7f57b6d5e8dd13e1069aede65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691316"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Codificação não pode ser definida como Nothing
Falha ao tentar ler ou gravar em um arquivo porque o parâmetro `encoding` foi definida como `Nothing` , mas requer um valor válido.  
  
 <xref:System.Text.Encoding> é usado para determinar a codificação a ser usada ao gravar em um arquivo. O padrão é UTF-8.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Forneça um valor válido para o `encoding` parâmetro.  
  
## <a name="see-also"></a>Consulte também
- [Codificações de Arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [Leitura de arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Gravando em arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
