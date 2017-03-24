---
title: "Convenção de chamada de DLL incorreta | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
dev_langs:
- VB
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
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
ms.openlocfilehash: e9e8ba99adf240f05451c18c13aa54ace15a7d39
ms.lasthandoff: 03/13/2017

---
# <a name="bad-dll-calling-convention"></a>Convenção de chamada de DLL inválida
Argumentos passados para uma biblioteca de vínculo dinâmico (DLL) devem corresponder exatamente àqueles esperado pela rotina. Convenções de chamada lidam com número, tipo e ordem dos argumentos. Seu programa pode ser chamando uma rotina em uma DLL que é passada a tipo errado ou o número de argumentos.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se que todos os tipos de argumento de acordo com aquelas especificadas na declaração de rotina que você está chamando.  
  
2.  Verifique se que você está passando o mesmo número de argumentos indicado na declaração de rotina que você está chamando.  
  
3.  Se a rotina DLL espera argumentos por valor, certifique-se `ByVal` é especificado para esses argumentos na declaração para a rotina.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md)   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
