---
title: Expressões de objeto (F#)
description: Saiba como usar expressões de objeto do F# quando você quer evitar o código extra e sobrecarga necessária para criar um novo tipo nomeado.
ms.date: 05/16/2016
ms.openlocfilehash: 1a971044d680d3bf5a6fff38affdaf001d5403b4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865456"
---
# <a name="object-expressions"></a>Expressões de objeto

Uma *do objeto expressão* é uma expressão que cria uma nova instância de um tipo de objeto criado dinamicamente e anônimo que é baseada em um tipo base existente, interface ou conjunto de interfaces.

## <a name="syntax"></a>Sintaxe

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, o *typename* representa um tipo de interface ou tipo de classe existente. *parâmetros de tipo* descreve os parâmetros de tipo genérico opcional. O *argumentos* são usados apenas para tipos de classe, que exigem parâmetros do construtor. O *definições de membro* são substituições dos métodos da classe base ou implementações de método abstrato de uma classe base ou uma interface.

O exemplo a seguir ilustra vários tipos diferentes de expressões de objeto.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>Usando expressões de objeto

Você usar expressões de objeto quando você quer evitar o código extra e uma sobrecarga que é necessária para criar um novo tipo nomeado. Se você usar expressões de objeto para minimizar o número de tipos criados em um programa, você pode reduzir o número de linhas de código e evitar a proliferação desnecessária de tipos. Em vez de criar muitos tipos apenas para lidar com situações específicas, você pode usar uma expressão de objeto que personaliza a um tipo existente ou fornece uma implementação apropriada de uma interface para o caso específico em questão.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
