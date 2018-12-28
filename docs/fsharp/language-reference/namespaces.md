---
title: Namespaces
description: Saiba como um F# namespace permite organizar o código em áreas de funcionalidade relacionada, permitindo que você anexe um nome para um agrupamento de elementos do programa.
ms.date: 12/08/2018
ms.openlocfilehash: 526d7a07e4804751811c15fa91b0c74c1954d591
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613434"
---
# <a name="namespaces"></a>Namespaces

Um namespace permite organizar o código em áreas de funcionalidade relacionada, permitindo que você anexe um nome para um agrupamento de F# elementos do programa. Namespaces são elementos de nível superior geralmente no F# arquivos.

## <a name="syntax"></a>Sintaxe

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a>Comentários

Se você quiser colocar código em um namespace, a primeira declaração no arquivo deve declarar o namespace. O conteúdo do arquivo inteiro, em seguida, se tornam parte do namespace, desde que nenhuma outra declaração de namespaces existe mais no arquivo. Se esse for o caso, todo o código até a próxima declaração de namespace é considerado para estar dentro do namespace primeiro.

Namespaces diretamente não pode conter valores e funções. Em vez disso, valores e funções devem ser incluídas em módulos e os módulos são incluídos em namespaces. Namespaces pode conter tipos de módulos.

Comentário da documentação XML pode ser declarado acima de um namespace, mas eles são ignorados. Diretivas de compilador também podem ser declaradas acima de um namespace.

Namespaces podem ser declarados explicitamente com a palavra-chave de namespace, ou implicitamente ao declarar um módulo. Para declarar um namespace explicitamente, use a palavra-chave namespace seguida pelo nome do namespace. O exemplo a seguir mostra um arquivo de código que declara um namespace `Widgets` com um tipo e um módulo incluído nesse namespace.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Se todo o conteúdo do arquivo estiver em um módulo, você também pode declarar namespaces implicitamente, usando o `module` palavra-chave e fornecendo o novo nome de namespace no nome do módulo totalmente qualificado. O exemplo a seguir mostra um arquivo de código que declara um namespace `Widgets` e um módulo `WidgetsModule`, que contém uma função.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

O código a seguir é equivalente ao código anterior, mas o módulo é uma declaração de módulo local. Nesse caso, o namespace deve aparecer em sua própria linha.

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

Se mais de um módulo é necessária no mesmo arquivo em um ou mais namespaces, você deve usar declarações de módulo local. Quando você usa as declarações de módulo local, você não pode usar o namespace qualificado nas declarações de módulo. O código a seguir mostra um arquivo que tem uma declaração de namespace e duas declarações de módulo local. Nesse caso, os módulos estão contidos diretamente no namespace; Não há nenhum módulo criado implicitamente que tem o mesmo nome do arquivo. Qualquer outro código no arquivo, como um `do` associação, está no namespace, mas não nos módulos internos, portanto, você precisa qualificar o membro de módulo `widgetFunction` usando o nome do módulo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

A saída deste exemplo é da seguinte maneira.

```fsharp
Module1 10 20
Module2 5 6
```

Para obter mais informações, consulte [módulos](modules.md).

## <a name="nested-namespaces"></a>Namespaces aninhados

Quando você cria um namespace aninhado, você deve qualificá-la totalmente. Caso contrário, você pode criar um novo namespace de nível superior. Recuo é ignorado em declarações de namespace.

O exemplo a seguir mostra como declarar um namespace aninhado.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Namespaces em arquivos e Assemblies

Namespaces podem abranger vários arquivos em um único projeto ou compilação. O termo *fragmento de namespace* descreve a parte de um namespace que está incluído em um arquivo. Namespaces também podem abranger vários assemblies. Por exemplo, o `System` namespace inclui o .NET Framework inteiro, que abrange muitos assemblies e contém muitos namespaces aninhados.

## <a name="global-namespace"></a>Namespace global

Você usa o namespace predefinido `global` para colocar os nomes no namespace de nível superior de .NET.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Você também pode usar global para referenciar o namespace .NET de nível superior, por exemplo, para resolver conflitos de nomes com outros namespaces.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Namespaces recursiva

Namespaces também podem ser declarados como recursivo para permitir todo o código contido para ser mutuamente recursivas.  Isso é feito por meio de `namespace rec`. Uso de `namespace rec` podem aliviar alguns problemas ao não ser capaz de escrever código mutuamente referencial entre módulos e tipos. Este é um exemplo disso:

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

Observe que a exceção `DontSqueezeTheBananaException` e a classe `Banana` fazem referência entre si.  Além disso, o módulo `BananaHelpers` e a classe `Banana` também fazer referência uns aos outros. Isso não seria possível expressar em F# se você tiver removido o `rec` palavra-chave do `MutualReferences` namespace.

Esse recurso também está disponível para o nível superior [módulos](modules.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Módulos](modules.md)
- [F#RFC FS-1009 - permitir mutuamente referenciais tipos e módulos em escopos maiores dentro de arquivos](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)