---
title: Instrução não é válida dentro de um método / lambda
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: 994cafc44a37d16d0f70caec560f530c6a836ec0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841557"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>A instrução não é válida dentro de um método/lambda de várias linhas
A instrução não é válida dentro de um `Sub`, `Function`, propriedade `Get`, ou a propriedade `Set` procedimento. Algumas instruções podem ser colocadas no nível de módulo ou classe. Outros, como `Option Strict`, deve estar no nível de namespace e preceder todas as outras declarações.  
  
 **ID do erro:** BC30024  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova a instrução do procedimento.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)
