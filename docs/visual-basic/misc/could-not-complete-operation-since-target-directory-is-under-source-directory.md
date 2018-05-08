---
title: Não foi possível concluir a operação porque o diretório de destino está no diretório de origem
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 68217023a980891200c18b5536ef902574d36257
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>Não foi possível concluir a operação porque o diretório de destino está no diretório de origem
Uma operação cíclica falhou. Ciclo de operações cíclicas e, portanto, não é possível concluir. Por exemplo, o objeto A pode tentar herdar do objeto B, que por sua vez, herda do objeto A.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Ao herdar, certifique-se de que não há nenhuma referência cíclica.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../visual-basic/programming-guide/language-features/error-types.md)  
 [Noções básicas de depuração: pontos de interrupção](http://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
