---
title: O modificador 'Custom' não é válido em eventos declarados sem tipos delegados explícitos
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: a2277e3778c2c252fd4b1eaeb033d549f041c15c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160627"
---
# <a name="bc31122-custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>BC31122: o modificador ' Custom ' não é válido em eventos declarados sem tipos delegados explícitos

Ao contrário de um evento não personalizado, uma `Custom Event` declaração requer uma `As` cláusula após o nome do evento que especifica explicitamente o tipo delegado para o evento.

 Eventos não personalizados podem ser definidos com uma `As` cláusula e um tipo de delegado explícito, ou com uma lista de parâmetros imediatamente após o nome do evento.

 **ID do erro:** BC31122

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Defina um delegado com a mesma lista de parâmetros que o evento personalizado.

     Por exemplo, se o `Custom Event` foi definido por `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , o delegado correspondente seria o seguinte.

     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]

2. Substitua a lista de parâmetros do evento personalizado por uma `As` cláusula especificando o tipo delegado.

     Continuando com o exemplo, a `Custom Event` declaração seria reescrita da seguinte maneira.

     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]

## <a name="example"></a>Exemplo

 Este exemplo declara um `Custom Event` e especifica a cláusula necessária `As` com um tipo delegate.

 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]

## <a name="see-also"></a>Veja também

- [Instrução Event](../statements/event-statement.md)
- [Instrução Delegate](../statements/delegate-statement.md)
- [Eventos](../../programming-guide/language-features/events/index.md)
