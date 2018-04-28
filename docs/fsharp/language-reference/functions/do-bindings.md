---
title: Associações do (F#)
description: "Saiba como F # 'do' associação é usado para executar código sem definir uma função ou um valor."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4c63da0c5e2f4130d59f9efa6bc54a55e5fe9fd8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
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

