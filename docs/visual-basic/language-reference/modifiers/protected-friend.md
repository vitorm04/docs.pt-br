---
title: Friend protegido (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 331c63dc290d4096e8158f265ee869b47743a273
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151769"
---
# <a name="protected-friend-visual-basic"></a>Friend protegido (Visual Basic)

A combinação de palavras-chave `Protected Friend` é um modificador de acesso de membro. Ele confere ambos [amigo](friend.md) acesso e [protegido](protected.md) acesso os elementos declarados, portanto, eles são acessíveis de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas. Você pode especificar `Protected Friend` somente em membros de classes; não é possível aplicar `Protected Friend` aos membros de uma estrutura porque as estruturas não podem ser herdadas.

> [!NOTE]
> No Visual Studio, selecionando a Ajuda de F1 na `protected friend` fornece ajuda para o [protegidos](protected.md) ou [amigo](friend.md). O IDE escolherá o token único sob o cursor em vez da palavra composta.

## <a name="rules"></a>Regras

- **Contexto da declaração.** Você pode usar `Protected Friend` somente no nível de classe. Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, estrutura, módulo ou procedimento. 

## <a name="see-also"></a>Consulte também

- [Público](../../../visual-basic/language-reference/modifiers/public.md)
- [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Particular](../../../visual-basic/language-reference/modifiers/private.md)
- [Privado protegido](./private-protected.md)
- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
