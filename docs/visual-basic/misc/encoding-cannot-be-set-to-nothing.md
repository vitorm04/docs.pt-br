---
title: "Codificação não pode ser definida como Nothing"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42baef6e0634849004290dce3db32e47f103282d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Codificação não pode ser definida como Nothing
Falha na tentativa de ler ou gravar em um arquivo porque o parâmetro `encoding` foi definida como `Nothing` , mas requer um valor válido.  
  
 <xref:System.Text.Encoding>é usado para determinar que codificação usar ao gravar em um arquivo. O padrão é UTF-8.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Forneça um valor válido para o `encoding` parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 [Codificações de Arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 [Leitura de arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Gravando em arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)  
 [WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
