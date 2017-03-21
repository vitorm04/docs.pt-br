---
title: '&quot;Optional&quot; esperado | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30202
- vbc30202
dev_langs:
- VB
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
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
ms.openlocfilehash: 953895a2462610b277dcc01c6b7dede57e331e86
ms.lasthandoff: 03/13/2017

---
# <a name="39optional39-expected"></a>'Optional' esperado
Um argumento opcional na declaração de procedimento é seguido por um argumento necessário. Cada argumento após um argumento opcional também deve ser opcional.  
  
 **ID do erro:** BC30202  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se o argumento destina-se a ser necessários, movê-la para preceder o primeiro argumento opcional na lista de argumentos.  
  
2.  Se o argumento destina-se a ser opcional, use o `Optional` palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Parâmetros Opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
