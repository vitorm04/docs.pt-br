---
title: As instruções '#Region' e '#End Region' não são válidas dentro dos corpos/lambdas de várias linhas do método
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: e3147b6192f54ce85d0fecd6b67f7d80f6281b54
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870887"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>As instruções '#Region' e '#End Region' não são válidas dentro dos corpos/lambdas de várias linhas do método

O `#Region` bloco deve ser declarado em um nível de classe, módulo ou namespace. Uma região recolhível pode incluir um ou mais procedimentos, mas não pode começar ou terminar dentro de um procedimento.  
  
 **ID do erro:** BC32025  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se o procedimento anterior foi encerrado corretamente com `End Function` uma `End Sub` instrução ou.  
  
2. Verifique se as `#Region` `#End Region` diretivas e estão no mesmo bloco de código.  
  
## <a name="see-also"></a>Confira também

- [#Region diretiva](../directives/region-directive.md)
