---
title: 'Declarações de importação: a palavra-chave open (F#)'
description: 'Saiba mais sobre declarações de importação do F # e como elas especificam um módulo ou namespace cujos elementos que você pode fazer referência sem usar um nome totalmente qualificado.'
ms.date: 05/16/2016
ms.openlocfilehash: 29f09297993b347464f1572ac9ca24902c786f4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="import-declarations-the-open-keyword"></a>Declarações de importação: O `open` palavra-chave

> [!NOTE]
Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Um *declaração da importação* Especifica um módulo ou namespace cujos elementos que você pode fazer referência sem usar um nome totalmente qualificado.


## <a name="syntax"></a>Sintaxe

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Comentários
Referência de código usando o caminho totalmente qualificado de namespace ou módulo sempre pode criar o código que é difícil de gravar, ler e manter. Em vez disso, você pode usar o `open` palavra-chave usados em módulos e namespaces para que quando você faz referência a um membro desse módulo ou namespace, você pode usar a forma abreviada do nome em vez do nome totalmente qualificado. Esta palavra-chave é semelhante do `using` palavra-chave em c#, `using namespace` no Visual C++, e `Imports` no Visual Basic.

O módulo ou namespace fornecido deve ser no mesmo projeto ou em um projeto referenciado ou assembly. Se não estiver, você pode adicionar uma referência ao projeto ou usar o `-reference` comando`-`opção de linha (ou abreviatura, `-r`). Para obter mais informações, consulte [Opções do compilador](compiler-options.md).

A declaração de importação disponibiliza os nomes no código que segue a declaração, até o fim do delimitador namespace, módulo ou arquivo.

Quando você usa várias declarações de importação, devem ser exibidos em linhas separadas.

O código a seguir mostra o uso do `open` palavra-chave para simplificar o código.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

O compilador F # não emite um erro ou aviso quando ambiguidades ocorrem quando ocorre o mesmo nome em mais de um namespace ou módulo aberto. Quando ambiguidades ocorrem, F # dá preferência para o namespace ou módulo abertas mais recentemente. Por exemplo, no código a seguir, `empty` significa `Seq.empty`, mesmo que `empty` está localizado em ambos os `List` e `Seq` módulos.

```fsharp
open List
open Seq
printfn "%A" empty
```

Portanto, tenha cuidado ao abrir módulos ou namespaces, como `List` ou `Seq` que contêm membros que tenham nomes idênticos; em vez disso, considere usar os nomes qualificados. Você deve evitar qualquer situação em que o código é dependente de ordem das declarações de importação.


## <a name="namespaces-that-are-open-by-default"></a>Namespaces que estão abertos por padrão
Alguns namespaces são então usados no código F # que são abertas implicitamente sem a necessidade de uma declaração de importação explícita. A tabela a seguir mostra os namespaces que estão abertos por padrão.

|Namespace|Descrição|
|---------|-----------|
|`Microsoft.FSharp.Core`|Contém básicas definições de tipo F # para tipos internos, como `int` e `float`.|
|`Microsoft.FSharp.Core.Operators`|Contém operações aritméticas básicas como `+` e `*`.|
|`Microsoft.FSharp.Collections`|Contém classes de coleção imutável como `List` e `Array`.|
|`Microsoft.FSharp.Control`|Contém tipos para construções de controle, como avaliação lenta e fluxos de trabalho assíncronos.|
|`Microsoft.FSharp.Text`|Contém funções de e/s formatado, tais como o `printf` função.|

## <a name="autoopen-attribute"></a>Atributo AutoOpen
Você pode aplicar o `AutoOpen` atributo a um assembly, se você quiser abrir automaticamente um namespace ou módulo quando o assembly é referenciado. Você também pode aplicar o `AutoOpen` de atributo para um módulo para abrir o módulo automaticamente quando o módulo principal ou o namespace é aberto. Para obter mais informações, consulte [classe autoopenattribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).


## <a name="requirequalifiedaccess-attribute"></a>Atributo RequireQualifiedAccess
Alguns módulos, registros ou tipos de união podem especificar o `RequireQualifiedAccess` atributo. Ao fazer referência a elementos desses módulos, registros ou uniões, você deve usar um nome qualificado, independentemente de se você incluir uma declaração de importação. Se você usar esse atributo estrategicamente em nomes de tipos que definem comumente usados, ajudar a evitar conflitos de nome e, portanto, tornar o código mais resiliente a alterações em bibliotecas. Para obter mais informações, consulte [classe requirequalifiedaccessattribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).


## <a name="see-also"></a>Consulte também
[# Referência de linguagem](index.md)

[Namespaces](namespaces.md)

[Módulos](modules.md)

