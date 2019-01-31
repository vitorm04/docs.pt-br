---
title: "'<keyword>' só é valido dentro de um método de instância"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: af3bc95e2db88577c7c53e4b58fb60aed8a83453
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267629"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>'\<palavra-chave >' é válido somente dentro de um método de instância
O `Me`, `MyClass`, e `MyBase` palavras-chave se referem a instâncias de classe específica. Você não pode usá-los dentro de um compartilhamento `Function` ou `Sub` procedimento.  
  
 **ID do erro:** BC30043  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova a palavra-chave do procedimento, ou remova o `Shared` palavra-chave da declaração de procedimento.  
  
## <a name="see-also"></a>Consulte também
- [Atribuição de variável do objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
