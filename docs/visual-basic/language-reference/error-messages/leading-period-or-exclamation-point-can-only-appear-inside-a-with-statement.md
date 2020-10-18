---
title: "'.' ou '!' à esquerda só podem aparecer dentro de uma instrução 'With'"
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 4ff273d5930fe58a5bccf0f4f4c10e971d777d01
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162499"
---
# <a name="bc30157-leading--or--can-only-appear-inside-a-with-statement"></a>BC30157: '. ' ou '! ' à esquerda só podem aparecer dentro de uma instrução ' with '

Um período (.) ou ponto de exclamação (!) que não está dentro de um `With` bloco ocorre sem uma expressão à esquerda. O acesso de membro ( `.` ) e o acesso de membro de dicionário ( `!` ) exigem uma expressão especificando o elemento que contém o membro. Isso deve aparecer imediatamente à esquerda do acessador ou como o destino de um `With` bloco que contém o acesso de membro.

 **ID do erro:** BC30157

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Verifique se o `With` bloco está formatado corretamente.

2. Se não houver nenhum `With` bloco, adicione uma expressão à esquerda do acessador que é avaliada como um elemento definido que contém o membro.

## <a name="see-also"></a>Veja também

- [Caracteres especiais no código](../../programming-guide/program-structure/special-characters-in-code.md)
- [Instrução With...End With](../statements/with-end-with-statement.md)
