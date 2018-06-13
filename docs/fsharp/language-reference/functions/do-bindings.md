---
title: Associações do (F#)
description: "Saiba como F # 'do' associação é usado para executar código sem definir uma função ou um valor."
ms.date: 05/16/2016
ms.openlocfilehash: 6fd084090a204beab0da1c2deb5b5ae2a86281c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562330"
---
# <a name="do-bindings"></a>Associações do

Um `do` associação é usada para executar o código sem definir uma função ou um valor. Além disso, associações pode ser usado em classes, consulte [ `do` associações em Classes](../members/do-bindings-in-classes.md).


## <a name="syntax"></a>Sintaxe

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Comentários
Use um `do` quando você quer executar código independentemente de uma definição de função ou o valor de associação. A expressão em uma `do` associação deve retornar `unit`. Código em um nível superior `do` associação é executada quando o módulo é inicializado. A palavra-chave `do` é opcional.

Atributos podem ser aplicados a um nível superior `do` associação. Por exemplo, se o programa usa a interoperabilidade COM, convém aplicar o `STAThread` de atributo para o seu programa. Você pode fazer isso usando um atributo em uma `do` de associação, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](../index.md)

[Funções](index.md)

