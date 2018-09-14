---
title: Propriedades (F#)
description: 'Saiba mais sobre propriedades F #, que são membros que representam os valores associados a um objeto.'
ms.date: 05/16/2016
ms.openlocfilehash: 75d21415b44ccc1c26ef5f478d5f5de20c3412e8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45619144"
---
# <a name="properties"></a>Propriedades

*Propriedades* são membros que representam os valores associados a um objeto.

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

Propriedades representam o "tem um" relação na programação orientada a objeto, que representa os dados que está associados com instâncias de objeto ou, para propriedades estáticas, com o tipo.

Você pode declarar propriedades de duas maneiras, dependendo se você deseja especificar explicitamente o valor subjacente (também chamado de repositório de backup) para a propriedade, ou se você deseja permitir que o compilador gerar automaticamente o repositório de backup para você. Em geral, você deve usar a maneira mais explícita, se a propriedade tem uma implementação não triviais e forma automática quando a propriedade é apenas um wrapper simples para um valor ou uma variável. Para declarar uma propriedade explicitamente, use o `member` palavra-chave. Essa sintaxe declarativa é seguido pela sintaxe que especifica o `get` e `set` métodos, também denominados *acessadores*. As várias formas da sintaxe explícita mostrado na seção de sintaxe são usadas para propriedades de leitura/gravação, somente leitura e somente gravação. Para propriedades somente leitura, você define apenas um `get` método; para propriedades somente gravação, defina apenas um `set` método. Observe que, quando uma propriedade tiver tanto `get` e `set` acessadores, a sintaxe alternativa permite que você especifique atributos e modificadores de acessibilidade que são diferentes para cada acessador, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Para propriedades de leitura/gravação, que têm ambas uma `get` e `set` método, a ordem dos `get` e `set` pode ser revertida. Como alternativa, você pode fornecer a sintaxe mostrada para `get` apenas e a sintaxe mostrada para `set` somente, em vez de usar a sintaxe combinada. Isso torna mais fácil para comentar o indivíduo `get` ou `set` método, se isso é algo que talvez você precise fazer. Essa alternativa usando a sintaxe combinada é mostrada no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Privada valores que espera que os dados para as propriedades são chamados *repositório de backup*. Para fazer com que o compilador criar automaticamente o repositório de backup, use as palavras-chave `member val`, omitir o identificador de Self e, em seguida, forneça uma expressão para inicializar a propriedade. Se a propriedade deve ser mutáveis, incluir `with get, set`. Por exemplo, o seguinte tipo de classe inclui duas propriedades implementadas automaticamente. `Property1` é somente leitura e é inicializada para o argumento fornecido para o construtor primário, e `Property2` é uma propriedade configurável, inicializada como uma cadeia de caracteres vazia:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Propriedades implementadas automaticamente fazem parte da inicialização de um tipo, portanto, eles devem ser incluídos antes das outras definições de membro, assim como `let` associações e `do` ligações em uma definição de tipo. Observe que a expressão que inicializa uma propriedade implementada automaticamente é avaliada apenas na inicialização e não sempre que a propriedade é acessada. Esse comportamento é diferente do comportamento de uma propriedade implementada explicitamente. Isso efetivamente significa que o código para inicializar essas propriedades é adicionado ao construtor de uma classe. Considere o seguinte código que mostra essa diferença:

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

A saída do código anterior mostra que o valor de AutoProperty é inalterado quando chamado várias vezes, enquanto o ExplicitProperty muda sempre que ele é chamado. Isso demonstra que a expressão para uma propriedade implementada automaticamente não é avaliada a cada vez, pois é o método de getter da propriedade explícita.

>[!WARNING]
Há algumas bibliotecas, como o Entity Framework (`System.Data.Entity`) que executam operações personalizadas em construtores de classe base que não funcionam bem com a inicialização de propriedades implementadas automaticamente. Nesses casos, tente usar propriedades explícitas.

Propriedades podem ser membros de classes, estruturas, uniões discriminadas, registros, interfaces e extensões de tipo e também podem ser definidas em expressões de objeto.

Atributos podem ser aplicados às propriedades. Para aplicar um atributo a uma propriedade, gravar o atributo em uma linha separada antes da propriedade. Para obter mais informações, consulte [Atributos](../attributes.md).

Por padrão, as propriedades são públicas. Modificadores de acessibilidade também podem ser aplicados a propriedades. Para aplicar um modificador de acessibilidade, adicioná-lo imediatamente antes do nome da propriedade caso ele deva ser aplicado a ambas as `get` e `set` métodos; adicioná-lo antes do `get` e `set` palavras-chave se for de acessibilidade diferente necessário para cada acessador. O *modificador de acessibilidade* pode ser uma das seguintes opções: `public`, `private`, `internal`. Para saber mais, veja [Controle de acesso](../access-control.md).

Implementações de propriedade são executadas sempre que uma propriedade é acessada.

## <a name="static-and-instance-properties"></a>Estáticos e propriedades da instância

As propriedades podem ser estáticos ou propriedades da instância. Propriedades podem ser chamadas sem uma instância e estáticos são usadas para valores associados com o tipo, não com objetos individuais. Para propriedades estáticas, omita o identificador de Self. O identificador de Self é necessário para as propriedades de instância.

A seguinte definição de propriedade estática é baseada em um cenário em que você tenha um campo estático `myStaticValue` que é o repositório de backup para a propriedade.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

As propriedades também podem ser de tipo de matriz, nesse caso, eles são chamados *propriedades indexadas*. Para obter mais informações, consulte [as propriedades indexadas](indexed-properties.md).

## <a name="type-annotation-for-properties"></a>Anotação de tipo para propriedades

Em muitos casos, o compilador tem informações suficientes para inferir o tipo de uma propriedade do tipo de repositório de backup, mas você pode definir o tipo explicitamente adicionando uma anotação de tipo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Usando a propriedade definir acessadores

Você pode definir propriedades que fornecem `set` acessadores usando o `<-` operador.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

A saída é **20**.

## <a name="abstract-properties"></a>Propriedades abstratas

As propriedades podem ser abstratas. Assim como acontece com métodos, `abstract` apenas significa que há uma expedição virtual associada à propriedade. Propriedades abstratas podem ser realmente abstratas, ou seja, sem uma definição na mesma classe. Portanto, a classe que contém essa propriedade é uma classe abstrata. Como alternativa, abstrata apenas pode significar que uma propriedade é virtual e, nesse caso, uma definição deve estar presente na mesma classe. Observe que propriedades abstratas não devem ser particulares e, se um acessador é abstrato, o outro também deverá ser abstrato. Para obter mais informações sobre classes abstratas, consulte [Classes abstratas](../abstract-classes.md).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Consulte também

- [Membros](index.md)
- [Métodos](methods.md)
