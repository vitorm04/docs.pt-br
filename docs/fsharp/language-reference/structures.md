---
title: Estruturas (F#)
description: 'Saiba mais sobre a estrutura F #, um tipo de objeto compact geralmente mais eficiente do que uma classe para tipos com uma pequena quantidade de dados e comportamento simple.'
ms.date: 05/16/2016
ms.openlocfilehash: 57c4148aec1d6a19237d74aa99824ef475c3632e
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172458"
---
# <a name="structures"></a>Estruturas

Um *estrutura* é um tipo de objeto compact que pode ser mais eficiente do que uma classe para tipos que têm uma pequena quantidade de dados e comportamento simple.

## <a name="syntax"></a>Sintaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a>Comentários
Estruturas são *os tipos de valor*, o que significa que eles são armazenados diretamente na pilha ou, quando eles são usados como campos ou tipo de elementos da matriz, embutido no pai. Ao contrário de classes e registros, as estruturas têm semântica de passar-por-valor. Isso significa que elas são úteis principalmente para pequenos agregados de dados que são acessados e copiados com frequência.

Na sintaxe anterior, duas formas são mostradas. A primeira não é a sintaxe leve, mas ela é usada com frequência, pois quando você usa as palavras-chave `struct` e `end`, é possível omitir o atributo `StructAttribute`, que aparece na segunda forma. É possível abreviar `StructAttribute` como apenas `Struct`.

O *-definição-elementos-e-membros de tipo* na sintaxe anterior representa definições e declarações de membro. As estruturas podem ter construtores e campos mutáveis e imutáveis e podem declarar membros e implementações de interface. Para obter mais informações, consulte [membros](members/index.md).

As estruturas não podem participar da herança, não podem conter associações `let` ou `do` e não podem conter recursivamente campos de seu próprio tipo (embora possam conter células de referência que fazem referência ao seu próprio tipo).

Como as estruturas não permitem associações `let`, você deve declarar campos em estruturas usando a palavra-chave `val`. A palavra-chave `val` define um campo e seu tipo, mas não permite inicialização. Em vez disso, as declarações `val` são inicializadas como zero ou nulo. Por esse motivo, as estruturas que possuem um construtor implícito (ou seja, parâmetros que são fornecidos imediatamente após o nome da estrutura na declaração) requerem que declarações `val` sejam anotadas com o atributo `DefaultValue`. As estruturas que tenham um construtor definido ainda oferecem suporte à inicialização como zero. Portanto, o atributo `DefaultValue` é uma declaração de que um valor zero é válido para o campo. Construtores implícitos para estruturas não executam nenhuma ação, pois as associações `let` e `do` não são permitidas no tipo, mas os valores de parâmetro construtor implícito passados estão disponíveis como campos particulares.

Construtores explícitos podem envolver inicialização de valores do campo. Quando você tem uma estrutura que possui um construtor explícito, ela ainda suporta inicialização como zero; no entanto, você não usa o atributo `DefaultValue` nas declarações `val`, pois ela entra em conflito com o construtor explícito. Para obter mais informações sobre `val` declarações, consulte [campos explícitos: A `val` palavra-chave](members/explicit-fields-the-val-keyword.md).

Modificadores de atributos e de acessibilidade são permitidos em estruturas e seguem as mesmas regras dos outros tipos. Para obter mais informações, consulte [atributos](attributes.md) e [controle de acesso](access-control.md).

Os exemplos de código a seguir ilustram definições de estrutura.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a>Registros de estrutura e uniões discriminadas

A partir do F # 4.1, você pode representar [registros](records.md) e [uniões discriminada](discriminated-unions.md) como estruturas com o `[<Struct>]` atributo.  Consulte cada artigo para saber mais.
    
## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Classes](classes.md)

[Registros](records.md)

[Membros](members/index.md)
