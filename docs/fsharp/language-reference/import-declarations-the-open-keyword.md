---
title: 'Declarações de importação: a palavra-chave open'
description: Saiba mais sobre as declarações de importação F# e como elas especificam um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021535"
---
# <a name="import-declarations-the-open-keyword"></a>Declarações de Importação: a palavra-chave `open`

> [!NOTE]
> Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Uma *declaração de importação* especifica um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.

## <a name="syntax"></a>Sintaxe

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Comentários

Fazendo referência ao código usando o namespace ou o caminho do módulo totalmente qualificados, cada vez pode criar um código difícil de escrever, ler e manter. Em vez disso, `open` você pode usar a palavra-chave para módulos e namespaces usados com freqüência para que, quando você referenciar um membro desse módulo ou namespace, você pode usar a forma curta do nome em vez do nome totalmente qualificado. Esta palavra-chave é `using` semelhante à palavra-chave em C#, `using namespace` no Visual C++, e `Imports` no Visual Basic.

O módulo ou namespace fornecido deve estar no mesmo projeto ou em um projeto ou montagem referenciado. Se não for, você pode adicionar uma referência `-reference` ao projeto, ou usar a opção `-r`de linha de comando (ou sua abreviação, ). Para obter mais informações, consulte [Opções do compilador](compiler-options.md).

A declaração de importação disponibiliza os nomes no código que segue a declaração, até o final do espaço de nome, módulo ou arquivo de encerramento.

Quando você usa várias declarações de importação, elas devem aparecer em linhas separadas.

O código a seguir `open` mostra o uso da palavra-chave para simplificar o código.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

O compilador F# não emite um erro ou aviso quando as ambiguidades ocorrem quando o mesmo nome ocorre em mais de um módulo aberto ou namespace. Quando ocorrem ambiguidades, F# dá preferência ao módulo ou namespace mais recentemente aberto. Por exemplo, no código `empty` `Seq.empty`a seguir, significa , `empty` embora `Seq` esteja localizado tanto nos módulos quanto nos `List` módulos.

```fsharp
open List
open Seq
printfn "%A" empty
```

Portanto, tenha cuidado ao abrir módulos ou `List` `Seq` namespaces, tais como ou que contenham membros com nomes idênticos; em vez disso, considere usar os nomes qualificados. Você deve evitar qualquer situação em que o código dependa da ordem das declarações de importação.

## <a name="namespaces-that-are-open-by-default"></a>Namespaces que são abertos por padrão

Alguns namespaces são tão freqüentemente usados no código F# que são abertos implicitamente sem a necessidade de uma declaração de importação explícita. A tabela a seguir mostra os namespaces que estão abertos por padrão.

|Namespace|Descrição|
|---------|-----------|
|`Microsoft.FSharp.Core`|Contém definições básicas do tipo F# `int` para `float`tipos incorporados, tais como e .|
|`Microsoft.FSharp.Core.Operators`|Contém operações aritméticas básicas como `+` e `*`.|
|`Microsoft.FSharp.Collections`|Contém classes de coleta imutáveis, tais como `List` e `Array`.|
|`Microsoft.FSharp.Control`|Contém tipos de construções de controle, como avaliação preguiçosa e fluxos de trabalho assíncronos.|
|`Microsoft.FSharp.Text`|Contém funções para IO formatado, como a `printf` função.|

## <a name="autoopen-attribute"></a>Atributo autoaberto

Você pode `AutoOpen` aplicar o atributo a um conjunto se quiser abrir automaticamente um namespace ou módulo quando o conjunto for referenciado. Você também pode `AutoOpen` aplicar o atributo a um módulo para abrir automaticamente esse módulo quando o módulo pai ou namespace for aberto. Para obter mais informações, consulte [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>DeexigiraaaaaaadesAtributo de

Alguns módulos, registros ou tipos `RequireQualifiedAccess` de união podem especificar o atributo. Quando você faz referência a elementos desses módulos, registros ou sindicatos, você deve usar um nome qualificado, independentemente de incluir uma declaração de importação. Se você usar esse atributo estrategicamente em tipos que definem nomes comumente usados, você ajuda a evitar colisões de nomes e, assim, tornar o código mais resistente às alterações nas bibliotecas. Para obter mais informações, consulte [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Confira também

- [Referência de idioma F#](index.md)
- [Namespaces](namespaces.md)
- [Módulos](modules.md)
