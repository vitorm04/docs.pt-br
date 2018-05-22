---
title: Friend protegido (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/18/2018
---
# <a name="protected-friend-visual-basic"></a>Friend protegido (Visual Basic)

O `Protected Friend` combinação de palavra-chave é um modificador de acesso de membro. Ele confere ambos [Friend](friend.md) acesso e [protegidos](protected.md) acesso os elementos declarados, para que eles são acessíveis de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas. Você pode especificar `Protected Friend` somente em membros de classes; não é possível aplicar `Protected Friend` para membros de uma estrutura como estruturas não podem ser herdadas.

> [!NOTE]
> No Visual Studio, selecionando Ajuda F1 em `protected friend` fornece ajuda para o [protegido](protected.md) ou [friend](friend.md). O IDE adota o token único sob o cursor em vez da palavra composta.

## <a name="rules"></a>Regras

- **Contexto de declaração.** Você pode usar `Protected Friend` somente no nível de classe. Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento. 


## <a name="see-also"></a>Consulte também

[Público](../../../visual-basic/language-reference/modifiers/public.md)  
[Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Privado](../../../visual-basic/language-reference/modifiers/private.md)  
[Privado protegido](./private-protected.md)   
[Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
