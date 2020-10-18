---
title: "'<keyword>' só é valido dentro de um método de instância"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: ad39ade294b362b20f2dfb93455445bf41d056cd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163318"
---
# <a name="bc30043-keyword-is-valid-only-within-an-instance-method"></a>BC30043: ' \<keyword> ' é válido somente dentro de um método de instância

As `Me` `MyClass` `MyBase` palavras-chave,, e se referem a instâncias de classe específicas. Você não pode usá-los dentro de um `Function` procedimento compartilhado ou `Sub` .

*ID do erro:** BC30043

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Remova a palavra-chave do procedimento ou remova a `Shared` palavra-chave da declaração do procedimento.

## <a name="see-also"></a>Veja também

- [Atribuição de variável do objeto](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase e MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Noções básicas de herança](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
