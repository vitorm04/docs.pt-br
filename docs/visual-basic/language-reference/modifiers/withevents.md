---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: c2dcb044d04099c51f57d82a8bc08f0932bf3542
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875426"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)

Especifica que uma ou mais variáveis de membro declaradas se referem a uma instância de uma classe que pode gerar eventos.

## <a name="remarks"></a>Comentários

Quando uma variável é definida usando `WithEvents` , você pode especificar declarativamente que um método manipule os eventos da variável usando a `Handles` palavra-chave.

Você pode usar `WithEvents` somente no nível de classe ou de módulo. Isso significa que o contexto de declaração para uma `WithEvents` variável deve ser uma classe ou um módulo e não pode ser um arquivo de origem, namespace, estrutura ou procedimento.

Você não pode usar `WithEvents` em um membro de estrutura.

Você pode declarar apenas variáveis individuais, e não matrizes, com `WithEvents` .

## <a name="rules"></a>Regras

**Tipos de elemento.** Você deve declarar `WithEvents` variáveis para serem variáveis de objeto para que elas possam aceitar instâncias de classe. No entanto, você não pode declará-las como `Object` . Você deve declará-los como a classe específica que pode gerar os eventos.

O `WithEvents` modificador pode ser usado neste contexto: [instrução Dim](../statements/dim-statement.md)

## <a name="example"></a>Exemplo

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Confira também

- [Alças](../statements/handles-clause.md)
- [Palavras-chave](../keywords/index.md)
- [Eventos](../../programming-guide/language-features/events/index.md)
