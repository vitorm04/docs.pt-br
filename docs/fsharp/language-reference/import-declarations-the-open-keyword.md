---
title: 'Declarações de importação: A palavra-chave open'
description: Saiba mais F# sobre as declarações de importação e como elas especificam um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630579"
---
# <a name="import-declarations-the-open-keyword"></a>Declarações de importação: A palavra-chave `open`

> [!NOTE]
> Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Uma *declaração de importação* especifica um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.

## <a name="syntax"></a>Sintaxe

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Comentários

Fazer referência ao código usando o namespace totalmente qualificado ou o caminho do módulo toda vez pode criar código que seja difícil de gravar, ler e manter. Em vez disso, você pode `open` usar a palavra-chave para módulos e namespaces usados com frequência para que, ao fazer referência a um membro desse módulo ou namespace, você possa usar a forma abreviada do nome em vez do nome totalmente qualificado. Essa palavra-chave é semelhante `using` à palavra C#- `using namespace` chave no C++, no `Imports` visual e no Visual Basic.

O módulo ou namespace fornecido deve estar no mesmo projeto ou em um projeto ou assembly referenciado. Se não for, você poderá adicionar uma referência ao projeto ou usar a opção de linha `-reference` de`-`comando (ou sua abreviação, `-r`). Para obter mais informações, consulte [Opções do compilador](compiler-options.md).

A declaração de importação torna os nomes disponíveis no código que segue a declaração, até o final do namespace, módulo ou arquivo de circunscrição.

Quando você usa várias declarações de importação, elas devem aparecer em linhas separadas.

O código a seguir mostra o uso da `open` palavra-chave para simplificar o código.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

O F# compilador não emite um erro ou aviso quando as ambiguidades ocorrem quando o mesmo nome ocorre em mais de um módulo ou namespace aberto. Quando ocorrerem ambiguidades F# , o fornecerá preferência para o módulo ou namespace aberto mais recentemente. Por exemplo, no código a seguir, `empty` significa `Seq.empty`, embora `empty` esteja localizado nos `List` módulos e `Seq` .

```fsharp
open List
open Seq
printfn "%A" empty
```

Portanto, tenha cuidado ao abrir módulos ou namespaces, `List` como ou `Seq` que contenham Membros com nomes idênticos; em vez disso, considere usar os nomes qualificados. Você deve evitar qualquer situação na qual o código seja dependente da ordem das declarações de importação.

## <a name="namespaces-that-are-open-by-default"></a>Namespaces que estão abertos por padrão

Alguns namespaces são tão frequentemente usados no F# código que são abertos implicitamente sem a necessidade de uma declaração de importação explícita. A tabela a seguir mostra os namespaces que estão abertos por padrão.

|Namespace|Descrição|
|---------|-----------|
|`Microsoft.FSharp.Core`|Contém definições F# de tipo básicas para tipos internos, `int` como e. `float`|
|`Microsoft.FSharp.Core.Operators`|Contém operações aritméticas básicas, `+` como `*`e.|
|`Microsoft.FSharp.Collections`|Contém classes de coleção imutáveis, como `List` e `Array`.|
|`Microsoft.FSharp.Control`|Contém tipos de construções de controle, como avaliação lenta e fluxos de trabalho assíncronos.|
|`Microsoft.FSharp.Text`|Contém funções para e/s formatada, como `printf` a função.|

## <a name="autoopen-attribute"></a>Atributo AutoOpen

Você pode aplicar o `AutoOpen` atributo a um assembly se desejar abrir automaticamente um namespace ou módulo quando o assembly for referenciado. Você também pode aplicar o `AutoOpen` atributo a um módulo para abrir esse módulo automaticamente quando o namespace ou o módulo pai for aberto. Para obter mais informações, consulte [classe Core.](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)AutoOpenAttribute.

## <a name="requirequalifiedaccess-attribute"></a>Atributo RequireQualifiedAccess

Alguns módulos, registros ou tipos de União podem especificar o `RequireQualifiedAccess` atributo. Ao referenciar elementos desses módulos, registros ou uniões, você deve usar um nome qualificado, independentemente de você incluir uma declaração de importação. Se você usar esse atributo estrategicamente em tipos que definem nomes comumente usados, você ajudará a evitar colisões de nomes e, portanto, tornará o código mais resiliente às alterações nas bibliotecas. Para obter mais informações, consulte [classe Core. RequireQualifiedAccessAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Namespaces](namespaces.md)
- [Módulos](modules.md)
