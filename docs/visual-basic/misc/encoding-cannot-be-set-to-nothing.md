---
title: Codificação não pode ser definida como Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 30b0b4a29fbdf931aa62263b75d1fa946e87b145
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970320"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Codificação não pode ser definida como Nothing
Falha ao tentar ler ou gravar em um arquivo porque o parâmetro `encoding` foi definida como `Nothing` , mas requer um valor válido.  
  
 <xref:System.Text.Encoding> é usado para determinar a codificação a ser usada ao gravar em um arquivo. O padrão é UTF-8.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Forneça um valor válido para o `encoding` parâmetro.  
  
## <a name="see-also"></a>Consulte também

- [Codificações de Arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [Leitura de arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Gravando em arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
