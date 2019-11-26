---
title: Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 53f9052555555a5b9dcb038dfee9cd54dc2b4251
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976209"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno

Entre as possíveis causas desse erro estão:  
  
- Um cliente invocou uma propriedade ou um método de um componente fora do processo e tentou passar uma referência a um objeto particular como um dos argumentos.  
  
- Um componente fora do processo chamou um método de retorno de chamada em seu cliente e tentou passar uma referência a um objeto particular.  
  
- Um componente fora do processo tentou passar uma referência a um objeto particular como um argumento de um evento que ele estava gerando.  
  
- Um cliente tentou atribuir uma referência de objeto particular a um `ByRef` argumento de um evento que ele estava manipulando.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Remova a referência.  
  
## <a name="see-also"></a>Consulte também

- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
