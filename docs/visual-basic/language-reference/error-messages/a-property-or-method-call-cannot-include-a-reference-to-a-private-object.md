---
title: Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cce2bc67beb7e4ac0664b5b7240f5eb3ea0204f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
