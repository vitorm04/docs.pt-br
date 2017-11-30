---
title: "Módulos (F#)"
description: "Saiba como um módulo F # é um agrupamento de código F #, como valores, tipos e valores de função em um programa em F #."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 46de2d18-da51-40fa-a262-92edecada79d
ms.openlocfilehash: 89401c1f889be6c5585a302e3a7ac62478573b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="modules"></a>Módulos

No contexto da linguagem F #, um *módulo* é um agrupamento de código F #, como valores, tipos e valores de função em um programa em F #. O agrupamento de código em módulos ajuda a manter junto o código relacionado e ajuda a evitar conflitos de nome em seu programa.

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
Um módulo F # é um agrupamento de construções de código F #, como tipos, valores, valores de função e código em `do` associações. Ele é implementado como uma classe common language runtime (CLR) que tenha apenas membros estáticos. Há dois tipos de declarações de módulo, dependendo se o arquivo inteiro é incluído no módulo: uma declaração de módulo de nível superior e uma declaração de módulo local. Uma declaração de módulo de nível superior inclui todo o arquivo do módulo. Uma declaração de módulo de nível superior pode aparecer somente como a primeira declaração em um arquivo.

Na sintaxe de declaração de módulo de nível superior, opcional *namespace qualificado* é a sequência de nomes de namespace aninhada que contém o módulo. O namespace qualificado não precisa ser declarado anteriormente.

Não é necessário que recuar as declarações em um módulo de nível superior. Você tem que recuar todas as declarações em módulos locais. Em uma declaração de módulo local, somente as declarações que são recuadas sob essa declaração de módulo são parte do módulo.

Se um arquivo de código não começar com uma declaração de módulo de nível superior ou uma declaração de namespace, todo o conteúdo do arquivo, incluindo todos os módulos locais, torna-se parte de um módulo de nível superior criado implicitamente que tem o mesmo nome do arquivo, sem a extensão com a primeira letra convertidos em maiusculas. Por exemplo, considere o seguinte arquivo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

Esse arquivo deve ser compilado como se tivesse sido escrito desta forma:

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

Se você tiver vários módulos em um arquivo, você deve usar uma declaração de módulo local para cada módulo. Se um namespace delimitador for declarado, esses módulos são parte do namespace de delimitador. Se não está declarado como um namespace delimitador, os módulos se tornam parte do módulo de nível superior criado implicitamente. O exemplo de código a seguir mostra um arquivo de código que contém vários módulos. O compilador cria um módulo de nível superior chamado implicitamente `Multiplemodules`, e `MyModule1` e `MyModule2` são aninhadas no nível mais alto que o módulo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

Se você tiver vários arquivos em um projeto ou em uma única compilação, ou se você estiver criando uma biblioteca, você deve incluir uma declaração de namespace ou declaração de módulo na parte superior do arquivo. O compilador F # determina apenas um nome de módulo em implicitamente quando há apenas um arquivo em uma linha de comando de compilação ou de projeto, e você estiver criando um aplicativo.

O *modificador de acessibilidade* pode ser um dos seguintes: `public`, `private`, `internal`. Para saber mais, veja [Controle de acesso](access-control.md). O padrão é público.


## <a name="referencing-code-in-modules"></a>Referência de código em módulos
Quando você faz referência a funções, tipos e valores de outro módulo, você deve usar um nome qualificado ou abrir o módulo. Se você usar um nome qualificado, você deve especificar os namespaces, o módulo e o identificador para o elemento do programa que você deseja. Separe cada parte do caminho qualificado com um ponto (.), da seguinte maneira.

`Namespace1.Namespace2.ModuleName.Identifier`

Você pode abrir o módulo ou um ou mais dos namespaces para simplificar o código. Para obter mais informações sobre namespaces de abertura e módulos, consulte [declarações de importação: O `open` palavra-chave](import-declarations-the-open-keyword.md).

O exemplo de código a seguir mostra um módulo de nível superior que contém todo o código até o fim do arquivo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

Para usar esse código de outro arquivo no mesmo projeto, você usa nomes qualificados ou abrir o módulo antes de usar as funções, conforme mostrado nos exemplos a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Módulos aninhados
Os módulos podem ser aninhados. Módulos internos devem ser recuados do ponto de vista declarações do módulo externo para indicar que eles são módulos internos, não novos módulos. Por exemplo, compare os dois exemplos a seguir. Módulo `Z` é um módulo interno no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

Mas o módulo `Z` for um irmão de módulo `Y` no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
Módulo `Z` também é um módulo de irmão no código a seguir, porque ele não é recuado do ponto de vista outras declarações no módulo `Y`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
Finalmente, se o módulo externo não tem nenhum declarações e é seguido imediatamente por outra declaração de módulo, a nova declaração de módulo é considerada como um módulo interno, mas o compilador avisará se a segunda definição de módulo não ficará recuada para mais longe que o primeiro.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
Para eliminar o aviso, recue o módulo interno.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
Se você deseja que todo o código em um arquivo em um único módulo externo e você desejar módulos internos, o módulo externo não exige o sinal de igual e as declarações, incluindo qualquer declaração de módulo interno, que vai entrar no módulo externo não precisam ser recuado. Declarações em declarações de módulo interna precisa ser recuado. O código a seguir mostra este caso.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="module-rec-allowing-mutual-recursive-code-at-the-module-level"></a>Módulo `rec`: possibilitar que um código comum recursiva no nível de módulo

4.1 F # introduz a noção de módulos que permitem que todo o código independente ser mutuamente recursivas.  Isso é feito por meio de `module rec`.  O uso de `module rec` pode aliviar alguns problemas de não conseguir gravar código mutuamente referencial entre módulos e tipos.  Este é um exemplo disso:

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

    module private BananaHelpers =
        let peel (b : Banana) =
            let flip banana =
                match banana.Orientation with
                | Up -> 
                    banana.Orientation <- Down
                    banana
                | Down -> banana

            let peelSides banana =
                for side in banana.Sides do
                    if side = Unpeeled then
                        side <- Peeled

            match b.Orientation with
            | Up ->   b |> flip |> peelSides
            | Down -> b |> peelSides
```

Observe que a exceção `DontSqueezeTheBananaException` e a classe `Banana` ambos referem-se entre si.  Além disso, o módulo `BananaHelpers` e a classe `Banana` também fazer referência uns aos outros.  Isso não seria possível expressar em F #, se você tiver removido o `rec` palavra-chave do `RecursiveModule` módulo.

Esse recurso também é possível no [Namespaces](namespaces.md) com F # 4.1.

## <a name="see-also"></a>Consulte também

[Referência da linguagem F #](index.md)
[Namespaces](namespaces.md)
[F # RFC FS-1009 - permitir tipos mutuamente referenciais e módulos em escopos maiores em arquivos](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
