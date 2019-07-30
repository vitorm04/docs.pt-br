---
title: Módulos
description: Saiba como um F# módulo é um agrupamento de F# código, como valores, tipos e valores de função, em um F# programa.
ms.date: 04/24/2017
ms.openlocfilehash: 685ab638e7e1b6c8d47d1a316483abcc18e40199
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627429"
---
# <a name="modules"></a>Módulos

No contexto do F# idioma, um *módulo* é um agrupamento de F# código, como valores, tipos e valores de função, em um F# programa. O agrupamento de código em módulos ajuda a manter junto o código relacionado e ajuda a evitar conflitos de nome em seu programa.

## <a name="syntax"></a>Sintaxe

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a>Comentários

Um F# módulo é um agrupamento de F# construções de código, como tipos, valores, valores de função e código em `do` associações. Ele é implementado como uma classe Common Language Runtime (CLR) que tem apenas membros estáticos. Há dois tipos de declarações de módulo, dependendo se o arquivo inteiro está incluído no módulo: uma declaração de módulo de nível superior e uma declaração de módulo local. Uma declaração de módulo de nível superior inclui o arquivo inteiro no módulo. Uma declaração de módulo de nível superior pode aparecer somente como a primeira declaração em um arquivo.

Na sintaxe para a declaração de módulo de nível superior, o *namespace qualificado* opcional é a sequência de nomes de namespace aninhados que contém o módulo. O namespace qualificado não precisa ser declarado anteriormente.

Você não precisa recuar declarações em um módulo de nível superior. Você precisa recuar todas as declarações em módulos locais. Em uma declaração de módulo local, somente as declarações que são recuadas sob essa declaração de módulo fazem parte do módulo.

Se um arquivo de código não começar com uma declaração de módulo de nível superior ou uma declaração de namespace, todo o conteúdo do arquivo, incluindo quaisquer módulos locais, se tornará parte de um módulo de nível superior criado implicitamente que tem o mesmo nome que o arquivo, sem a extensão, com a primeira letra convertida em maiúsculas. Por exemplo, considere o arquivo a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

Esse arquivo seria compilado como se tivesse sido escrito desta maneira:

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

Se você tiver vários módulos em um arquivo, deverá usar uma declaração de módulo local para cada módulo. Se um namespace delimitador for declarado, esses módulos serão parte do namespace delimitador. Se um namespace delimitador não for declarado, os módulos se tornarão parte do módulo de nível superior criado implicitamente. O exemplo de código a seguir mostra um arquivo de código que contém vários módulos. O compilador cria implicitamente um módulo de nível superior denominado `Multiplemodules` `MyModule1` e e `MyModule2` é aninhado nesse módulo de nível superior.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

Se você tiver vários arquivos em um projeto do ou em uma única compilação, ou se estiver criando uma biblioteca, deverá incluir uma declaração de namespace ou declaração de módulo na parte superior do arquivo. O F# compilador determina apenas um nome de módulo implicitamente quando há apenas um arquivo em um projeto ou linha de comando de compilação, e você está criando um aplicativo.

O *modificador de acessibilidade* pode ser um dos seguintes: `public`, `private`, `internal`. Para saber mais, veja [Controle de acesso](access-control.md). O padrão é público.

## <a name="referencing-code-in-modules"></a>Referenciando código em módulos

Ao fazer referência a funções, tipos e valores de outro módulo, você deve usar um nome qualificado ou abrir o módulo. Se você usar um nome qualificado, deverá especificar os namespaces, o módulo e o identificador para o elemento de programa desejado. Você separa cada parte do caminho qualificado com um ponto (.), da seguinte maneira.

`Namespace1.Namespace2.ModuleName.Identifier`

Você pode abrir o módulo ou um ou mais dos namespaces para simplificar o código. Para obter mais informações sobre como abrir módulos e namespaces [, consulte importar declarações: A `open` palavra](import-declarations-the-open-keyword.md)-chave.

O exemplo de código a seguir mostra um módulo de nível superior que contém todo o código até o final do arquivo.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

Para usar esse código de outro arquivo no mesmo projeto, você pode usar nomes qualificados ou abrir o módulo antes de usar as funções, conforme mostrado nos exemplos a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Módulos aninhados

Os módulos podem ser aninhados. Os módulos internos devem ser recuados até o momento como declarações de módulo externas para indicar que são módulos internos, não novos módulos. Por exemplo, compare os dois exemplos a seguir. `Z` É um módulo interno no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

Mas o `Z` módulo é um irmão para `Y` o módulo no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
O `Z` módulo também é um módulo irmão no código a seguir, porque ele não é recuado até outras declarações no módulo `Y`.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
Finalmente, se o módulo externo não tiver declarações e for seguido imediatamente por outra declaração de módulo, a nova declaração de módulo será considerada um módulo interno, mas o compilador avisará se a segunda definição de módulo não for recuada além da primeiro.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
Para eliminar o aviso, recue o módulo interno.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
Se você quiser que todo o código em um arquivo esteja em um único módulo externo e queira módulos internos, o módulo externo não exigirá o sinal de igual, e as declarações, incluindo quaisquer declarações de módulo internas, que vão no módulo externo, não precisarão ser recuadas. As declarações dentro das declarações de módulo internas precisam ser recuadas. O código a seguir mostra esse caso.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Módulos recursivos

F#4,1 apresenta a noção de módulos que permitem que todo o código independente seja recursivo mutuamente.  Isso é feito por `module rec`meio de.  O uso `module rec` de pode aliviar alguns problemas em não ser capaz de escrever código referencial mutuamente entre tipos e módulos.  Veja a seguir um exemplo disso:

```fsharp
module rec RecursiveModule =
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

Observe que a exceção `DontSqueezeTheBananaException` e a classe `Banana` fazem referência umas às outras.  Além disso, o `BananaHelpers` módulo e a `Banana` classe também se referem uns aos outros.  Isso não seria possível expressar em F# se você removesse a `rec` palavra-chave do `RecursiveModule` módulo.

Esse recurso também é possível em [namespaces](namespaces.md) com F# 4,1.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Namespaces](namespaces.md)
- [F#RFC FS-1009-permitir tipos e módulos de referência mútua em escopos maiores nos arquivos](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
