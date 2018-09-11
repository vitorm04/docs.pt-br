---
title: Associações do (F#)
description: "Saiba como F # 'do' associação é usado para executar o código sem definir uma função ou um valor."
ms.date: 05/16/2016
ms.openlocfilehash: 78dbf8da0fe40b5af566ad98693df1109eede7e4
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353090"
---
# <a name="do-bindings"></a>Associações do

Um `do` associação é usada para executar o código sem definir uma função ou um valor. Além disso, as associações fazem pode ser usado em classes, consulte [ `do` associações em Classes](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Sintaxe

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Comentários

Use um `do` quando você deseja executar o código, independentemente de uma definição de função ou o valor de associação. A expressão em uma `do` associação deve retornar `unit`. Código em um nível superior `do` associação é executada quando o módulo é inicializado. A palavra-chave `do` é opcional.

Atributos podem ser aplicados a um nível superior `do` associação. Por exemplo, se seu programa usa interoperabilidade COM, você talvez queira aplicar o `STAThread` de atributo para o seu programa. Você pode fazer isso usando um atributo em um `do` de associação, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](../index.md)
- [Funções](index.md)
