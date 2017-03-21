---
title: "Constantes devem ser do tipo intrínseco ou enumerado, não uma classe, estrutura, parâmetro de tipo ou tipo de matriz | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
dev_langs:
- VB
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 12
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
ms.openlocfilehash: 7063c9b374dd14c5771b816002f5f55965be68dd
ms.lasthandoff: 03/13/2017

---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz
Você tentou declarar uma constante como uma classe, estrutura ou tipo de matriz, ou como um parâmetro de tipo definido por um tipo genérico.  
  
 Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.  
  
 **ID do erro:** BC30424  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declare a constante como um intrínseco ou `Enum` tipo.  
  
2.  Uma constante pode também ser um valor especial como `True`, `False`, ou `Nothing`. O compilador considera esses valores predefinidos como do tipo intrínseco apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Constantes e enumerações](../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)
