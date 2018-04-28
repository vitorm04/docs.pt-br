---
title: Propriedades (F#)
description: 'Saiba mais sobre F # propriedades, que são membros que representam os valores associados a um objeto.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 6cad5d0e32958374e080f9b8046f7eb73b6bf615
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="properties"></a>Propriedades

*Propriedades* membros que representam os valores associados a um objeto.


## <a name="syntax"></a>Sintaxe

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>Comentários
Representa propriedades de "tem um" relação em programação orientada a objeto, que representa os dados associados com instâncias de objeto ou, para propriedades estáticas, com o tipo.

Você pode declarar propriedades de duas maneiras, dependendo se você deseja especificar explicitamente o valor subjacente (também chamado de armazenamento de backup) para a propriedade, ou se você deseja permitir que o compilador gerar automaticamente o repositório de backup para você. Em geral, você deve usar a forma mais explícita se a propriedade tem uma implementação não trivial e o modo automático quando a propriedade é apenas um wrapper simple para um valor ou uma variável. Para declarar explicitamente uma propriedade, use o `member` palavra-chave. Essa sintaxe declarativa é seguido pela sintaxe que especifica o `get` e `set` métodos, também denominados *acessadores*. As várias formas da sintaxe explícita mostrado na seção de sintaxe são usadas para propriedades somente leitura e gravação de leitura/gravação. Propriedades somente leitura, você define apenas um `get` método; propriedades somente gravação, defina apenas um `set` método. Observe que, quando uma propriedade com ambos `get` e `set` acessadores, a sintaxe alternativa permite que você especifique atributos e os modificadores de acessibilidade que são diferentes para cada acessador, conforme é mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Para propriedades de leitura/gravação, que têm ambos um `get` e `set` método, a ordem de `get` e `set` podem ser revertidas. Como alternativa, você pode fornecer a sintaxe mostrada para `get` apenas e a sintaxe mostrada para `set` somente, em vez de usar a sintaxe combinada. Isso torna mais fácil para comentar o indivíduo `get` ou `set` método, se isso é algo que você pode precisar fazer. Essa alternativa usando a sintaxe combinada é mostrada no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Privada que espera que os dados para as propriedades são chamados de valores *armazenamentos de backup*. Para fazer com que o compilador cria automaticamente o repositório de backup, use as palavras-chave `member val`, omita o identificador interno e forneça uma expressão para inicializar a propriedade. Se a propriedade é ser mutável, incluir `with get, set`. Por exemplo, o seguinte tipo de classe inclui duas propriedades implementadas automaticamente. `Property1` é somente leitura e é inicializado para o argumento fornecido para o construtor primário, e `Property2` é uma propriedade definível inicializada para uma cadeia de caracteres vazia:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Propriedades implementadas automaticamente fazem parte da inicialização de um tipo, elas devem ser incluídas antes de quaisquer outras definições de membro, como `let` associações e `do` associações em uma definição de tipo. Observe que a expressão que inicializa uma propriedade implementada automaticamente é avaliada apenas na inicialização e não toda vez que a propriedade for acessada. Esse comportamento é diferente do comportamento de uma propriedade implementada explicitamente. O que isso significa é que o código para inicializar a essas propriedades é adicionado ao construtor de uma classe. Considere o seguinte código que mostra essa diferença:

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

**Saída**

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

A saída do código anterior mostra que o valor de AutoProperty é alterado quando chamado repetidamente, enquanto o ExplicitProperty mudará sempre que ele é chamado. Isso demonstra que a expressão para uma propriedade implementada automaticamente não é avaliada toda vez que é o método de getter da propriedade explícita.


>[!WARNING]
Há algumas bibliotecas, como o Entity Framework (`System.Data.Entity`) que executam operações personalizadas em construtores de classe base que não funcionam bem com a inicialização de propriedades implementadas automaticamente. Nesses casos, tente usar propriedades explícitas.

Propriedades podem ser membros de classes, estruturas, uniões discriminadas, registros, interfaces e extensões de tipo e também podem ser definidas em expressões de objeto.

Atributos podem ser aplicados às propriedades. Para aplicar um atributo a uma propriedade, grave o atributo em uma linha separada antes da propriedade. Para obter mais informações, consulte [Atributos](../attributes.md).

Por padrão, as propriedades são públicas. Modificadores de acessibilidade também podem ser aplicadas às propriedades. Para aplicar um modificador de acessibilidade, adicione-o imediatamente antes do nome da propriedade se ele deve se aplicam a ambos os `get` e `set` métodos; adicioná-lo antes do `get` e `set` palavras-chave se acessibilidade diferente é necessário para cada acessador. O *modificador de acessibilidade* pode ser um dos seguintes: `public`, `private`, `internal`. Para saber mais, veja [Controle de acesso](../access-control.md).

Implementações de propriedade são executadas sempre que uma propriedade é acessada.


## <a name="static-and-instance-properties"></a>Estático e propriedades da instância
Propriedades podem ser estáticos ou propriedades da instância. Propriedades estáticas podem ser chamadas sem uma instância e são usadas para valores associados com o tipo, não com objetos individuais. Para propriedades estáticas, omita o identificador interno. O identificador interno é necessário para as propriedades de instância.

A seguinte definição de propriedade estática baseia-se em um cenário em que você tenha um campo estático `myStaticValue` que é o repositório de backup para a propriedade.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Propriedades também podem ser tipo de matriz, caso em que eles são chamados *propriedades indexadas*. Para obter mais informações, consulte [propriedades indexadas](indexed-properties.md).


## <a name="type-annotation-for-properties"></a>Anotação de tipo para propriedades
Em muitos casos, o compilador não tem informações suficientes para inferir o tipo de uma propriedade do tipo de armazenamento de backup, mas você pode definir o tipo explicitamente adicionando uma anotação de tipo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Usando a propriedade acessadores definidos
Você pode definir propriedades que fornecem `set` acessadores usando o `<-` operador.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

A saída é **20**.


## <a name="abstract-properties"></a>Propriedades abstratas
Propriedades podem ser abstratas. Como com métodos, `abstract` apenas significa que há um despacho virtual associado à propriedade. Propriedades abstratas podem ser realmente abstratas, ou seja, sem uma definição na mesma classe. A classe que contém essa propriedade, portanto, é uma classe abstrata. Como alternativa, abstrato apenas pode significar que uma propriedade é virtual e, nesse caso, uma definição deve estar presente na mesma classe. Observe que propriedades abstratas não devem ser privadas, e se um acessador é abstrato, o outro também deverá ser abstrato. Para obter mais informações sobre classes abstratas, consulte [Classes abstratas](../abstract-classes.md).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Consulte também
[Membros](index.md)

[Métodos](methods.md)
