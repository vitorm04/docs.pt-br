---
title: O ordinal não é válido
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 28f78161e14604c1f59872801855ccc918faec58
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299248"
---
# <a name="ordinal-is-not-valid"></a>O ordinal não é válido
A chamada para uma biblioteca de vínculo dinâmico (DLL) indicado para usar um número em vez de um nome de procedimento, usando o `#num` sintaxe. Esse erro tem as seguintes causas possíveis:  
  
-   Uma tentativa de converter o `#num` expressão a um ordinal falhou.  
  
-   O `#num` especificado não especificar qualquer função na DLL.  
  
-   Uma biblioteca de tipos tem uma declaração inválida, resultando no uso interno de um número ordinal inválido.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se que a expressão representa um número válido, ou chame o procedimento por nome.  
  
2. Certifique-se de `#num` identifica uma função válida na DLL.  
  
3. Isole a causa do problema comentando o código de chamada de procedimento. Gravar um `Declare` instrução para o procedimento e relatar o problema para o fornecedor da biblioteca de tipo.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
