---
title: Tipos de referência – Referência em C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744523"
---
# <a name="reference-types-c-reference"></a>Tipos de referência (Referência em C#)

Há dois tipos em C#: tipos de referência e valor. Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados. Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável. Com tipos de valor, cada variável tem sua própria cópia dos dados e as operações em uma variável não podem afetar a outra (exceto no caso das variáveis de parâmetros in, ref e out. Confira o modificador de parâmetro [in](in-parameter-modifier.md), [ref](ref.md) e [out](out-parameter-modifier.md)).

 As seguintes palavras-chaves são usadas para declarar tipos de referência:

- [class](class.md)

- [Interface](interface.md)

- [Delegado](../builtin-types/reference-types.md)

 O C# também oferece os seguintes tipos de referência internos:

- [dinâmico](../builtin-types/reference-types.md)

- [Objeto](../builtin-types/reference-types.md)

- [String](../builtin-types/reference-types.md)

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [Palavras-chave do C#](index.md)
- [Tipos de Ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos de valor](../builtin-types/value-types.md)
