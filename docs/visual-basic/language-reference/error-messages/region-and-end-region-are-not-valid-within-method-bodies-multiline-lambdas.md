---
title: "Instruções '#Region' e ' #End' não são válidas dentro de corpos / lambdas de método"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: deef3de645040d7c3d95b1a6c8a25fcf10de881b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842701"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>As instruções '#Region' e '#End Region' não são válidas dentro dos corpos/lambdas de várias linhas do método
O `#Region` bloco deve ser declarado em um nível de classe, módulo ou namespace. Uma região recolhível pode incluir um ou mais procedimentos, mas ele não pode começar ou terminar dentro de um procedimento.  
  
 **ID do erro:** BC32025  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que o procedimento anterior é encerrado corretamente com um `End Function` ou `End Sub` instrução.  
  
2.  Certifique-se de que o `#Region` e `#End Region` diretivas estão no mesmo bloco de código.  
  
## <a name="see-also"></a>Consulte também

- [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
