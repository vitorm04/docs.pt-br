---
title: Convenção de chamada de DLL inválida
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a>Convenção de chamada de DLL inválida
Argumentos passados para uma biblioteca de vínculo dinâmico (DLL) devem corresponder exatamente àqueles esperado pela rotina. Convenções de chamada lidam com número, tipo e ordem dos argumentos. Seu programa pode chamar uma rotina em uma DLL que está sendo passada o tipo incorreto ou o número de argumentos.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se que todos os tipos de argumento de acordo com aquelas especificadas na declaração de rotina que você está chamando.  
  
2.  Verifique se que você estiver passando o mesmo número de argumentos indicado na declaração de rotina que você está chamando.  
  
3.  Se a rotina DLL espera argumentos por valor, certifique-se de `ByVal` é especificado para esses argumentos na declaração para a rotina.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
