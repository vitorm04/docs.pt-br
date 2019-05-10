---
title: "'<keyword>' só é valido dentro de um método de instância"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 8ec1e704815ee10cb98d8cc20fb5982ee4b92832
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662006"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>'\<palavra-chave >' é válido somente dentro de um método de instância
O `Me`, `MyClass`, e `MyBase` palavras-chave se referem a instâncias de classe específica. Você não pode usá-los dentro de um compartilhamento `Function` ou `Sub` procedimento.  
  
 **ID do erro:** BC30043  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a palavra-chave do procedimento, ou remova o `Shared` palavra-chave da declaração de procedimento.  
  
## <a name="see-also"></a>Consulte também

- [Atribuição de variável do objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
