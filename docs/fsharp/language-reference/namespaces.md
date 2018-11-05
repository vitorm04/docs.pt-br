---
title: Namespaces (F#)
description: 'Saiba como um namespace do F # permite que você organize o código em áreas de funcionalidade relacionada, permitindo que você anexe um nome para um agrupamento de elementos do programa.'
ms.date: 04/24/2017
ms.openlocfilehash: 769a1241f76ac32d3a6a80bd637078493119bb3c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44178234"
---
# <a name="namespaces"></a>Namespaces

Um namespace permite organizar o código em áreas de funcionalidade relacionada ao permitir que você anexe um nome a um agrupamento de elementos de programação.

## <a name="syntax"></a>Sintaxe

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a>Comentários

Se você quiser colocar código em um namespace, a primeira declaração no arquivo deve declarar o namespace. O conteúdo do arquivo inteiro se tornam parte do namespace.

Namespaces diretamente não pode conter valores e funções. Em vez disso, valores e funções devem ser incluídas em módulos e os módulos são incluídos em namespaces. Namespaces pode conter tipos de módulos.

Namespaces podem ser declarados explicitamente com a palavra-chave de namespace, ou implicitamente ao declarar um módulo. Para declarar um namespace explicitamente, use a palavra-chave namespace seguida pelo nome do namespace. O exemplo a seguir mostra um arquivo de código que declara um namespace de Widgets com um tipo e um módulo incluído nesse namespace.

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

F # 4.1 introduz a noção de namespaces que permitem para todo o código contido ser mutuamente recursivas.  Isso é feito por meio de `namespace rec`.  Uso de `namespace rec` podem aliviar alguns problemas ao não ser capaz de escrever código mutuamente referencial entre módulos e tipos.  Este é um exemplo disso:

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

Observe que a exceção `DontSqueezeTheBananaException` e a classe `Banana` fazem referência entre si.  Além disso, o módulo `BananaHelpers` e a classe `Banana` também fazer referência uns aos outros.  Isso não seria possível expressar em F #, se você tiver removido o `rec` palavra-chave do `MutualReferences` namespace.

Esse recurso também está disponível para o nível superior [módulos](modules.md) em F # 4.1 ou superior.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Módulos](modules.md)
- [FS-1009 do F # RFC - permitir mutuamente referenciais tipos e módulos em escopos maiores dentro de arquivos](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
