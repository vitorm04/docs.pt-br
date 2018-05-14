---
title: Células de referência (F#)
description: 'Saiba como células de referência do F # são locais de armazenamento permitem criar valores mutáveis com semântica de referência.'
ms.date: 05/16/2016
ms.openlocfilehash: 3a632425356a250f07e5babd2751b9923eec6552
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2018
---
# <a name="reference-cells"></a>Células de referência

*Fazer referência a células* são locais de armazenamento permitem criar valores mutáveis com semântica de referência.

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

O código a seguir ilustra o uso das células de referência na passagem de parâmetro. O tipo de Incrementor tem um método de incremento que aceita um parâmetro que inclui o tipo de parâmetro byref. O tipo de parâmetro byref indica que os chamadores deverá passar uma célula de referência ou o endereço de uma variável típico do tipo especificado, esse int. caso O código restante ilustra como chamar incremento com ambos os tipos de argumentos e mostra o uso do operador ref em uma variável para criar uma célula de referência (ref myDelta1). Em seguida, ele mostra o uso do operador address-of (&amp;) para gerar um argumento apropriado. Por fim, o método de incremento é chamado novamente por meio de uma célula de referência que é declarada usando uma associação let. A linha final do código demonstra o uso de! operador para cancelar a célula de referência para impressão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

Para obter mais informações sobre como passar por referência, consulte [parâmetros e argumentos](parameters-and-arguments.md).

>[!NOTE]
Os programadores c# devem saber que ref funciona de forma diferente em F # do que no c#. Por exemplo, o uso de ref quando você passar um argumento não tem o mesmo efeito em F # como faz em c#.

>[!NOTE]
`mutable` variáveis podem ser promovidas automaticamente a `'a ref` se capturados por um fechamento; consulte [valores](values/index.md).

## <a name="consuming-c-ref-returns"></a>Consumindo c# `ref` retorna

A partir do F # 4.1, você pode consumir `ref` retorna gerado em c#.  O resultado de tal chamada é um `byref<_>` ponteiro.

O seguinte método em c#:

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

Pode ser transparente chamado por F # com nenhuma sintaxe especial:

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

Também é possível declarar funções que poderiam levar um `ref` retornar como entrada, por exemplo:

```fsharp
let f (x: byref<int>) = &x
```

Atualmente, não há nenhuma maneira de gerar um `ref` retorno em F #, que pode ser consumido em c#.

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Parâmetros e Argumentos](parameters-and-arguments.md)

[Referência de Símbolos e Operadores](symbol-and-operator-reference/index.md)

[Valores](values/index.md)
