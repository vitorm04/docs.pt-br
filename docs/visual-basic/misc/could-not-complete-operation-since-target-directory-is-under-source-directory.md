---
title: Não foi possível concluir a operação, pois o diretório de destino está sob o diretório de origem
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 253e7ff1d457827a2e1cb9f64eae4bfa971a3798
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645867"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>Não foi possível concluir a operação, pois o diretório de destino está sob o diretório de origem
Uma operação cíclica falhou. Ciclo de operações cíclicas e, portanto, não pode ser concluída. Por exemplo, o objeto A pode tentar herdar do objeto B, que por sua vez herda de objeto A.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Ao herdar, certifique-se de que não há nenhuma referência cíclica.  
  
## <a name="see-also"></a>Consulte também
- [Tipos de Erro](../../visual-basic/programming-guide/language-features/error-types.md)
- [Noções básicas de depuração: Pontos de interrupção](https://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
