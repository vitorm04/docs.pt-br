---
title: '&#39;&lt;palavra-chave&gt; &#39; é válido somente dentro de um método de instância'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 2d9e26aa7dccf1b9c6390a20a59b10a0d248969d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a>&#39;&lt;palavra-chave&gt; &#39; é válido somente dentro de um método de instância
O `Me`, `MyClass`, e `MyBase` palavras-chave se referem a instâncias de classe específica. Você não pode usá-las dentro de um compartilhado `Function` ou `Sub` procedimento.  
  
 **ID do erro:** BC30043  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova a palavra-chave do procedimento, ou remova o `Shared` palavra-chave da declaração de procedimento.  
  
## <a name="see-also"></a>Consulte também  
 [Atribuição de variável do objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
