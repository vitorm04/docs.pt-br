---
title: Modo de arquivo inválido
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a>Modo de arquivo inválido
Instruções usadas na manipulação de conteúdo do arquivo devem ser apropriadas para o modo no qual o arquivo foi aberto. Possíveis causas incluem:  
  
-   Um `FilePutObject` ou `FileGetObject` instrução Especifica um arquivo sequencial.  
  
-   Um `Print` declaração especifica um arquivo aberto para um modo de acesso diferente de `Output` ou `Append`.  
  
-   Um `Input` declaração especifica um arquivo aberto para um modo de acesso diferente de`Input`  
  
-   Uma tentativa de gravar em um arquivo somente leitura.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de `FilePutObject` e `FileGetObject` somente referindo-se a arquivos abertos para `Random` ou `Binary` acesso.  
  
-   Certifique-se de `Print` Especifica um arquivo aberto para ou `Output` ou `Append` modo de acesso. Caso contrário, use uma instrução diferente para colocar dados no arquivo ou reabrir o arquivo no modo apropriado.  
  
-   Certifique-se de `Input` Especifica um arquivo aberto para `Input`. Caso contrário, use uma declaração diferente para colocar dados no arquivo ou reabrir o arquivo no modo apropriado.  
  
-   Se você estiver gravando em um arquivo somente leitura, altere o status de leitura/gravação do arquivo ou não tentar gravar nele.  
  
-   Usar a funcionalidade disponível a `My.Computer.FileSystem` objeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [Solução de problemas: lendo e gravando em arquivos de texto](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
