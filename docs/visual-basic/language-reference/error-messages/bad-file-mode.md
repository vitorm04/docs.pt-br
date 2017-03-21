---
title: "Modo de arquivo inválido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID54
dev_langs:
- VB
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 61afdb0f23d0ae8343aa8bab087fbd4656021413
ms.lasthandoff: 03/13/2017

---
# <a name="bad-file-mode"></a>Modo de arquivo inválido
Instruções usadas para manipular o conteúdo do arquivo devem ser apropriadas para o modo no qual o arquivo foi aberto. Possíveis causas incluem:  
  
-   A `FilePutObject` ou `FileGetObject` declaração especifica um arquivo sequencial.  
  
-   A `Print` declaração especifica um arquivo aberto para um modo de acesso diferente de `Output` ou `Append`.  
  
-   Um `Input` declaração especifica um arquivo aberto para um modo de acesso diferente de`Input`  
  
-   Uma tentativa de gravar em um arquivo somente leitura.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de `FilePutObject` e `FileGetObject` estão se referindo apenas a arquivos abertos para `Random` ou `Binary` acesso.  
  
-   Certifique-se de `Print` Especifica um arquivo aberto para ou `Output` ou `Append` modo de acesso. Caso contrário, use uma declaração diferente para colocar dados no arquivo ou reabra o arquivo no modo apropriado.  
  
-   Certifique-se de `Input` Especifica um arquivo aberto para `Input`. Caso contrário, use uma declaração diferente para colocar dados no arquivo ou reabra o arquivo no modo apropriado.  
  
-   Se você estiver escrevendo em um arquivo somente leitura, alterar o status de leitura/gravação do arquivo ou não tentar gravar nele.  
  
-   Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem></xref:Microsoft.VisualBasic.FileSystem>   
 [Solução de problemas: lendo e gravando em arquivos de texto](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
