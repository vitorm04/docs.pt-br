---
title: '##error – Referência de C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: cc1e0640886e3f3c1c74a54f64961a56c8b030e4
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812361"
---
# <a name="error-c-reference"></a>#error (Referência de C#)

`#error` permite gerar um erro definido pelo usuário [CS1029](../compiler-messages/cs1029.md) de um local específico em seu código. Por exemplo:

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> O compilador trata `#error version` de forma especial e relata um erro de compilador, CS8304, com uma mensagem contendo o compilador e as versões de linguagem usadas.

## <a name="remarks"></a>Comentários

Um uso comum de `#error` é em uma diretiva condicional.

Também é possível gerar um aviso definido pelo usuário com [#warning](./preprocessor-warning.md).

## <a name="example"></a>Exemplo

```csharp
// preprocessor_error.cs
// CS1029 expected
#define DEBUG
class MainClass
{
    static void Main()
    {
#if DEBUG
#error DEBUG is defined
#endif
    }
}
```

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Guia de programação C#](../../programming-guide/index.md)
- [Diretivas de pré-processador do C#](./index.md)
