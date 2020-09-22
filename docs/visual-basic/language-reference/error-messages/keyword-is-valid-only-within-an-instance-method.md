---
title: "'<keyword>' só é valido dentro de um método de instância"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: af436b8fd57ff0d2747c766a64af175760931009
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873899"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>'\<keyword>' só é valido dentro de um método de instância

As `Me` `MyClass` `MyBase` palavras-chave,, e se referem a instâncias de classe específicas. Você não pode usá-los dentro de um `Function` procedimento compartilhado ou `Sub` .  
  
 **ID do erro:** BC30043  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a palavra-chave do procedimento ou remova a `Shared` palavra-chave da declaração do procedimento.  
  
## <a name="see-also"></a>Confira também

- [Atribuição de variável do objeto](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase e MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Noções básicas de herança](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
