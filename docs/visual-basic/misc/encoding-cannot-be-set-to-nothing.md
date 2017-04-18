---
title: "Codificação não pode ser definida como Nothing | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8787a5cbd5e8610ffa667ae00cd900a43b056f8f
ms.lasthandoff: 03/13/2017

---
# <a name="encoding-cannot-be-set-to-nothing"></a>Codificação não pode ser definida como Nothing
Uma tentativa de ler ou gravar em um arquivo falhou porque o parâmetro `encoding` foi definido como `Nothing` , mas requer um valor válido.  
  
 <xref:System.Text.Encoding>é usado para determinar que codificação usar ao gravar em um arquivo.</xref:System.Text.Encoding> O padrão é UTF-8.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Forneça um valor válido para o `encoding` parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 [Codificações de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)   
 [Leitura de arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Gravando em arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)   
 [Método ReadAllText](http://msdn.microsoft.com/en-us/3a7ac8be-fb1d-4087-bc65-167d6754d57f)   
 [Método WriteAllText](http://msdn.microsoft.com/en-us/f507460c-87d9-4504-b74f-3ff825c7d5c4)
