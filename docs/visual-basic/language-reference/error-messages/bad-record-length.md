---
title: "Comprimento de registro inválido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID59
dev_langs:
- VB
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: 8
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
ms.openlocfilehash: a07cb30260eba1b345bcb98b4d92637cc468dcd0
ms.lasthandoff: 03/13/2017

---
# <a name="bad-record-length"></a>Comprimento de registro inválido
Entre as causas possíveis desse erro são:  
  
-   O comprimento de uma variável do Registro especificada em uma `FileGet`, `FileGetObject`, `FilePut` ou `FilePutObject` instrução difere do comprimento especificado na correspondentes `FileOpen` instrução.  
  
-   A variável em uma `FilePut` ou `FilePutObject` instrução é ou inclui uma cadeia de caracteres de comprimento variável.  
  
-   A variável em uma `FilePut` ou `FilePutObject` é ou inclui um `Variant`tipo**.**  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se a soma dos tamanhos das variáveis de comprimento fixo no tipo definido pelo usuário definindo o tipo de registro da variável é o mesmo que o valor indicado no `FileOpen` da instrução `Len` cláusula.  
  
2.  Se a variável em uma `FilePut` ou `FilePutObject` instrução é ou inclui uma cadeia de caracteres de comprimento variável, verifique se a cadeia de caracteres de comprimento variável é pelo menos 2 caracteres menor do que o comprimento do registro especificado no `Len` cláusula do `FileOpen` instrução.  
  
3.  Se a variável em uma `FilePut` ou `FilePutObject` é ou inclui um `Variant` certificar-se de que a cadeia de caracteres de comprimento variável é ao menos 4 bytes menor do que o comprimento do registro especificado no `Len` cláusula do `FileOpen` instrução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A></xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A></xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A></xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A></xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
