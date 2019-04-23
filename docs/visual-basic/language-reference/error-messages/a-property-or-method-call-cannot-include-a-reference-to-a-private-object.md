---
title: Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 04124ca044ad8dbff58f85230d7e10ea336d41e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341463"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
Entre as causas possíveis desse erro são:  
  
-   Um cliente chamou uma propriedade ou método de um componente fora do processo e tentou passar uma referência a um objeto particular como um dos argumentos.  
  
-   Um componente fora do processo chamou um método de retorno de chamada em seu cliente e tentou passar uma referência a um objeto particular.  
  
-   Um componente fora do processo tentou passar uma referência a um objeto particular como um argumento de um evento que ele estava gerando.  
  
-   Um cliente tentou atribuir uma referência de objeto particular para um `ByRef` argumento de um evento que estava tratando.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Remova a referência.  
  
## <a name="see-also"></a>Consulte também

- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
