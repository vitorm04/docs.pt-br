---
title: Associações do
description: Saiba como uma F# Associação ' do ' é usada para executar o código sem definir uma função ou um valor.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630531"
---
# <a name="do-bindings"></a>Associações do

Uma `do` associação é usada para executar código sem definir uma função ou um valor. Além disso, as associações podem ser usadas em classes, consulte [ `do` associações em classes](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Sintaxe

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Comentários

Use uma `do` associação quando desejar executar código independentemente de uma definição de função ou valor. A expressão em uma `do` associação deve retornar `unit`. O código em uma associação de `do` nível superior é executado quando o módulo é inicializado. A palavra `do` -chave é opcional.

Os atributos podem ser aplicados a uma associação de `do` nível superior. Por exemplo, se o seu programa usar a interoperabilidade com, talvez você `STAThread` queira aplicar o atributo ao seu programa. Você pode fazer isso usando um atributo em uma `do` associação, conforme mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](../index.md)
- [Funções](index.md)
