---
title: "Classes derivadas não podem elevar eventos de classe base | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
dev_langs:
- VB
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: 9
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
ms.openlocfilehash: cc146caf49e714fd58edfbe3bb267a532dc13f98
ms.lasthandoff: 03/13/2017

---
# <a name="derived-classes-cannot-raise-base-class-events"></a>As classes derivadas não podem acionar eventos de classe base
Um evento pode ser gerado apenas do espaço de declaração na qual ela é declarada. Portanto, uma classe não pode disparar eventos de qualquer outra classe, até mesmo uma da qual ela é derivada.  
  
 **ID do erro:** BC30029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mova o `Event` instrução ou o `RaiseEvent` instrução para que estejam na mesma classe.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
