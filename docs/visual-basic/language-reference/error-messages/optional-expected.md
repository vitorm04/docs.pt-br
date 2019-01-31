---
title: "'Optional' esperado"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 0ad0d0890b73103a0678b13409a24190329d37d4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266314"
---
# <a name="optional-expected"></a>'Optional' esperado
Um argumento opcional em uma declaração de procedimento é seguido por um argumento obrigatório. Cada argumento após um argumento opcional também deve ser opcional.  
  
 **ID do erro:** BC30202  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se o argumento deve ser necessária, movê-la para preceder o primeiro argumento opcional na lista de argumentos.  
  
2.  Se o argumento deve ser opcional, use o `Optional` palavra-chave.  
  
## <a name="see-also"></a>Consulte também
- [Parâmetros Opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
