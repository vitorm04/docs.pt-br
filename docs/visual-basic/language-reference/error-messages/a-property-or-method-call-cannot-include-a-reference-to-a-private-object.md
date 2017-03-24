---
title: "Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou como um valor de retorno | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID98
dev_langs:
- VB
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9a1f49ecd5ace71e5084105a348976a03ab32952
ms.lasthandoff: 03/13/2017

---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
Entre as causas possíveis desse erro são:  
  
-   Um cliente chamou uma propriedade ou método de um componente fora de processo e tentou passar uma referência a um objeto particular como um dos argumentos.  
  
-   Um componente fora de processo chamou um método de retorno de chamada no seu cliente e tentou passar uma referência a um objeto particular.  
  
-   Um componente fora de processo tentou passar uma referência a um objeto particular como um argumento de um evento que ele estava lançando.  
  
-   Um cliente tentou atribuir uma referência de objeto particular para um `ByRef` argumento de um evento que ele estava tratando.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Remova a referência.  
  
## <a name="see-also"></a>Consulte também  
 [Privado](../../../visual-basic/language-reference/modifiers/private.md)
