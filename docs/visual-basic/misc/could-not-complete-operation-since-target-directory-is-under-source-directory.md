---
title: Não foi possível concluir a operação, pois o diretório de destino está sob o diretório de origem
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: f53ad664b341d4db803dee1f0f008c3918d13d93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970112"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>Não foi possível concluir a operação, pois o diretório de destino está sob o diretório de origem
Uma operação cíclica falhou. Ciclo de operações cíclicas e, portanto, não pode ser concluída. Por exemplo, o objeto A pode tentar herdar do objeto B, que por sua vez herda de objeto A.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Ao herdar, certifique-se de que não há nenhuma referência cíclica.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Erro](../../visual-basic/programming-guide/language-features/error-types.md)
- [Usar pontos de interrupção no depurador do Visual Studio](/visualstudio/debugger/using-breakpoints)
