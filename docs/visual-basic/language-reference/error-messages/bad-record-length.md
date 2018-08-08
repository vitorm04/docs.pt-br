---
title: Comprimento de registro inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: b4b311e2eb504c485772091ed126b3beb71729cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585964"
---
# <a name="bad-record-length"></a>Comprimento de registro inválido
Entre as causas possíveis desse erro são:  
  
-   O comprimento de uma variável do Registro especificada em uma `FileGet`, `FileGetObject`, `FilePut` ou `FilePutObject` instrução é diferente do que o comprimento especificado em correspondente `FileOpen` instrução.  
  
-   A variável em uma `FilePut` ou `FilePutObject` instrução é ou inclui uma cadeia de caracteres de comprimento variável.  
  
-   A variável em uma `FilePut` ou `FilePutObject` é ou inclui um `Variant` tipo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se a soma dos tamanhos das variáveis de comprimento fixo no tipo definido pelo usuário definindo o tipo de registro da variável é o mesmo que o valor indicado no `FileOpen` da instrução `Len` cláusula.  
  
2.  Se a variável em uma `FilePut` ou `FilePutObject` instrução é ou inclui uma cadeia de caracteres de comprimento variável, verifique se a cadeia de caracteres de comprimento variável é pelo menos 2 caracteres menor do que o comprimento do registro especificado no `Len` cláusula do `FileOpen` instrução.  
  
3.  Se a variável em uma `FilePut` ou `FilePutObject` é ou inclui um `Variant` certificar-se de que a cadeia de caracteres de comprimento variável é menor do que o comprimento do registro especificado em pelo menos 4 bytes a `Len` cláusula do `FileOpen` instrução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
