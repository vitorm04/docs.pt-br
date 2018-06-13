---
title: Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 1f36526eab1bc0964bf89398b6e0f3e74d09fdc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583819"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
Entre as causas possíveis desse erro são:  
  
-   Um cliente chamou uma propriedade ou método de um componente fora de processo e tentou passar uma referência a um objeto particular como um dos argumentos.  
  
-   Um componente fora do processo chamou um método de retorno de chamada no seu cliente e tentou passar uma referência a um objeto particular.  
  
-   Um componente fora de processo tentou passar uma referência a um objeto particular como um argumento de um evento que ele estava lançando.  
  
-   Um cliente tentou atribuir uma referência de objeto particular para um `ByRef` argumento de um evento que ele estava tratando.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Remova a referência.  
  
## <a name="see-also"></a>Consulte também  
 [Privado](../../../visual-basic/language-reference/modifiers/private.md)
