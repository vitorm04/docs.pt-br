---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350749"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Especifica que uma ou mais variáveis de membro declaradas se referem a uma instância de uma classe que pode gerar eventos.

## <a name="remarks"></a>Comentários

Quando uma variável é definida usando `WithEvents`, você pode especificar declarativamente que um método manipule os eventos da variável usando a palavra-chave `Handles`.

Você pode usar `WithEvents` somente no nível de classe ou módulo. Isso significa que o contexto de declaração para uma variável de `WithEvents` deve ser uma classe ou um módulo e não pode ser um arquivo de origem, namespace, estrutura ou procedimento.

Você não pode usar `WithEvents` em um membro de estrutura.

Você pode declarar apenas variáveis individuais, e não matrizes, com `WithEvents`.

## <a name="rules"></a>Regras

**Tipos de elemento.** Você deve declarar `WithEvents` variáveis para serem variáveis de objeto para que elas possam aceitar instâncias de classe. No entanto, você não pode declará-las como `Object`. Você deve declará-los como a classe específica que pode gerar os eventos.

O modificador de `WithEvents` pode ser usado neste contexto: [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)

## <a name="example"></a>Exemplo

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Consulte também

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
