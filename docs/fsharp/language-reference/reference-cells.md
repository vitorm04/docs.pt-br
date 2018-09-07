---
title: Células de referência (F#)
description: 'Saiba como células de referência em F # são locais de armazenamento que permitem criar valores mutáveis com semântica de referência.'
ms.date: 05/16/2016
ms.openlocfilehash: e2e1a91c62fd76e4992bc5ae11bb672766850718
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079290"
---
# <a name="reference-cells"></a>Células de referência

*Células de referência* são locais de armazenamento que permitem criar valores mutáveis com semântica de referência.

## <a name="syntax"></a>Sintaxe

```fsharp
ref expression
```

## <a name="remarks"></a>Comentários

Você usa o operador `ref` antes de um valor para criar uma nova célula de referência que encapsule o valor. Em seguida, é possível alterar o valor subjacente porque ele é mutável.

Uma célula de referência mantém um valor real. Não é apenas um endereço. Ao criar uma célula de referência usando o operador `ref`, você cria uma cópia do valor subjacente como um valor mutável encapsulado.

Você pode desreferenciar uma célula de referência usando o operador `!` (bang).

O exemplo de código a seguir ilustra a declaração e o uso das células de referência.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

A saída é `50`.

As células de referência são instâncias do tipo de registro genérico `Ref`, declarado da maneira a seguir.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

O tipo `'a ref` é um sinônimo de `Ref<'a>`. O compilador e o IntelliSense no IDE exibem o primeiro para esse tipo, mas a definição subjacente é do último.

O operador `ref` cria uma nova célula de referência. O código a seguir é a declaração do operador `ref`.

```fsharp
let ref x = { contents = x }
```

A tabela a seguir mostra os recursos disponíveis na célula de referência.

|Operador, membro ou campo|Descrição|Tipo|Definição|
|--------------------------|-----------|----|----------|
|`!` (operador de desreferência)|Retorna o valor subjacente.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (operador de atribuição)|Altera o valor subjacente.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (operador)|Encapsula um valor em uma nova célula de referência.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (propriedade)|Obtém ou define o valor subjacente.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (campo de registro)|Obtém ou define o valor subjacente.|`'a`|`let ref x = { contents = x }`|
Existem várias maneiras de acessar o valor subjacente. O valor retornado pelo operador de desreferência (`!`) não é um valor atribuível. Portanto, se estiver modificando o valor subjacente, você deverá usar o operador de atribuição (`:=`) em vez disso.

A propriedade `Value` e o campo `contents` são valores atribuíveis. Portanto, é possível usá-los para acessar ou alterar o valor subjacente, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

A saída é a seguinte.

```
10
10
11
12
```

O campo `contents` é fornecido para compatibilidade com outras versões do ML e produzirá um aviso durante a compilação. Para desabilitar o aviso, use a opção do compilador `--mlcompatibility`. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).

Programadores de c# devem saber que `ref` em c# não é a mesma coisa que `ref` em F #. As construções equivalentes em F # são [byrefs](byrefs.md), que são um conceito diferente das células de referência.

Valores marcados como `mutable`pode ser elevada automaticamente a `'a ref` se capturados por um fechamento; veja [valores](values/index.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Parâmetros e Argumentos](parameters-and-arguments.md)
- [Referência de Símbolos e Operadores](symbol-and-operator-reference/index.md)
- [Valores](values/index.md)
