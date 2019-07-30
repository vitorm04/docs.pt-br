---
title: Namespaces
description: Saiba como um F# namespace permite que você organize o código em áreas de funcionalidades relacionadas, permitindo que você anexe um nome a um agrupamento de elementos de programa.
ms.date: 12/08/2018
ms.openlocfilehash: d295f25cae81bc28b4fcb522bdcacde862f9517a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627383"
---
# <a name="namespaces"></a>Namespaces

Um namespace permite que você organize o código em áreas de funcionalidades relacionadas, permitindo que você anexe um nome a um F# agrupamento de elementos do programa. Os namespaces normalmente são elementos de nível superior F# em arquivos.

## <a name="syntax"></a>Sintaxe

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a>Comentários

Se você quiser colocar o código em um namespace, a primeira declaração no arquivo deverá declarar o namespace. O conteúdo de todo o arquivo torna-se parte do namespace, desde que não exista mais nenhuma declaração de namespace no arquivo. Se esse for o caso, então, todos os códigos até a próxima declaração de namespace serão considerados no primeiro namespace.

Os namespaces não podem conter diretamente valores e funções. Em vez disso, os valores e funções devem ser incluídos em módulos, e os módulos são incluídos em namespaces. Namespaces podem conter tipos, módulos.

Comentários de documentos XML podem ser declarados acima de um namespace, mas são ignorados. As diretivas do compilador também podem ser declaradas acima de um namespace.

Os namespaces podem ser declarados explicitamente com a palavra-chave namespace ou implicitamente ao declarar um módulo. Para declarar explicitamente um namespace, use a palavra-chave namespace seguida pelo nome do namespace. O exemplo a seguir mostra um arquivo de código que declara um `Widgets` namespace com um tipo e um módulo incluídos nesse namespace.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Se todo o conteúdo do arquivo estiver em um módulo, você também poderá declarar Namespaces implicitamente usando a `module` palavra-chave e fornecendo o novo nome de namespace no nome do módulo totalmente qualificado. O exemplo a seguir mostra um arquivo de código que declara um `Widgets` namespace e um `WidgetsModule`módulo, que contém uma função.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

O código a seguir é equivalente ao código anterior, mas o módulo é uma declaração de módulo local. Nesse caso, o namespace deve aparecer em sua própria linha.

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

Se mais de um módulo for necessário no mesmo arquivo em um ou mais namespaces, você deverá usar declarações de módulo local. Quando você usa declarações de módulo local, não pode usar o namespace qualificado nas declarações de módulo. O código a seguir mostra um arquivo que tem uma declaração de namespace e duas declarações de módulo local. Nesse caso, os módulos estão contidos diretamente no namespace; Não há um módulo criado implicitamente que tenha o mesmo nome que o arquivo. Qualquer outro código no arquivo, como uma `do` associação, está no namespace, mas não nos módulos internos, portanto, você precisa qualificar o membro `widgetFunction` do módulo usando o nome do módulo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

A saída deste exemplo é a seguinte:

```fsharp
Module1 10 20
Module2 5 6
```

Para obter mais informações, consulte [módulos](modules.md).

## <a name="nested-namespaces"></a>Namespaces aninhados

Ao criar um namespace aninhado, você deve qualificá-lo totalmente. Caso contrário, você cria um novo namespace de nível superior. O recuo é ignorado nas declarações de namespace.

O exemplo a seguir mostra como declarar um namespace aninhado.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Namespaces em arquivos e assemblies

Os namespaces podem abranger vários arquivos em um único projeto ou compilação. O *fragmento do namespace* de termo descreve a parte de um namespace que está incluído em um arquivo. Os namespaces também podem abranger vários assemblies. Por exemplo, o `System` namespace inclui a .NET Framework inteira, que abrange muitos assemblies e contém muitos namespaces aninhados.

## <a name="global-namespace"></a>Namespace global

Você usa o namespace `global` predefinido para colocar nomes no namespace de nível superior do .net.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Você também pode usar global para fazer referência ao namespace .NET de nível superior, por exemplo, para resolver conflitos de nome com outros namespaces.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Namespaces recursivos

Os namespaces também podem ser declarados como recursivos para permitir que todo o código independente seja recursivo mutuamente.  Isso é feito por `namespace rec`meio de. O uso `namespace rec` de pode aliviar alguns problemas em não ser capaz de escrever código referencial mutuamente entre tipos e módulos. Veja a seguir um exemplo disso:

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

Observe que a exceção `DontSqueezeTheBananaException` e a classe `Banana` fazem referência umas às outras.  Além disso, o `BananaHelpers` módulo e a `Banana` classe também se referem uns aos outros. Isso não seria possível expressar em F# se você removesse a `rec` palavra-chave do `MutualReferences` namespace.

Esse recurso também está disponível para [módulos](modules.md)de nível superior.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Módulos](modules.md)
- [F#RFC FS-1009-permitir tipos e módulos de referência mútua em escopos maiores nos arquivos](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
