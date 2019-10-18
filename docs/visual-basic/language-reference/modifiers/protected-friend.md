---
title: Amigo protegido (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524779"
---
# <a name="protected-friend-visual-basic"></a>Amigo protegido (Visual Basic)

A combinação de palavras-chave `Protected Friend` é um modificador de acesso de membro. Ele confere o acesso [Friend](friend.md) e o acesso [protegido](protected.md) nos elementos declarados, para que eles possam ser acessados de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas. Você pode especificar `Protected Friend` somente em membros de classes; Você não pode aplicar `Protected Friend` aos membros de uma estrutura porque as estruturas não podem ser herdadas.

> [!NOTE]
> No Visual Studio, a seleção de ajuda F1 no `protected friend` fornece ajuda para o [Protected](protected.md) ou o [Friend](friend.md). O IDE escolhe o único token sob o cursor em vez da palavra composta.

## <a name="rules"></a>Regras

**Contexto de declaração.** Você pode usar `Protected Friend` apenas no nível de classe. Isso significa que o contexto de declaração para um elemento de `Protected` deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.

## <a name="see-also"></a>Consulte também

- [Público](../../../visual-basic/language-reference/modifiers/public.md)
- [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Particular Protegido](./private-protected.md)
- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
