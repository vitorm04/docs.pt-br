---
title: Convenção de chamada de DLL inválida
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: f7b0c3a6edbe0b950195306fa66287ff9b209bfe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306612"
---
# <a name="bad-dll-calling-convention"></a>Convenção de chamada de DLL inválida
Argumentos passados para uma biblioteca de vínculo dinâmico (DLL) devem corresponder exatamente aos esperados pela rotina. Convenções de chamada lidam com o número, tipo e ordem dos argumentos. Seu programa pode chamar uma rotina em uma DLL que está sendo passada a um tipo incorreto ou o número de argumentos.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se que todos os tipos de argumento de acordo com aquelas especificadas na declaração da rotina que você está chamando.  
  
2. Verifique se que você estiver passando o mesmo número de argumentos indicado na declaração da rotina que você está chamando.  
  
3. Se a rotina DLL espera argumentos por valor, certifique-se `ByVal` é especificado para esses argumentos na declaração para a rotina.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md)
- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
