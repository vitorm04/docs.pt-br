---
title: Classes
description: Saiba como F# as classes são tipos que representam objetos que podem ter propriedades, métodos e eventos.
ms.date: 05/16/2016
ms.openlocfilehash: 5c012d028bc1f89e3e9f5969b3461faab9aad3a0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630448"
---
# <a name="classes"></a>Classes

*Classes* são tipos que representam objetos que podem ter propriedades, métodos e eventos.

## <a name="syntax"></a>Sintaxe

```fsharp
// Class definition:
type [access-modifier] type-name [type-params] [access-modifier] ( parameter-list ) [ as identifier ] =
[ class ]
[ inherit base-type-name(base-constructor-args) ]
[ let-bindings ]
[ do-bindings ]
member-list
...
[ end ]
// Mutually recursive class definitions:
type [access-modifier] type-name1 ...
and [access-modifier] type-name2 ...
...
```

## <a name="remarks"></a>Comentários

Classes representam a descrição fundamental dos tipos de objeto do .NET; a classe é o conceito de tipo principal que oferece suporte à programação orientada a objeto no F#.

Na sintaxe anterior, o `type-name` é qualquer identificador válido. O `type-params` descreve os parâmetros de tipo genérico opcionais. Ele consiste em nomes de parâmetro de tipo e restrições entre colchetes angulares `>`(`<` e). Para obter mais informações, consulte [genéricos](./generics/index.md) e [restrições](./generics/constraints.md). O `parameter-list` descreve os parâmetros do construtor. O primeiro modificador de acesso pertence ao tipo; o segundo pertence ao Construtor principal. Em ambos os casos, o padrão `public`é.

Você especifica a classe base para uma classe usando a `inherit` palavra-chave. Você deve fornecer argumentos, entre parênteses, para o construtor da classe base.

Você declara campos ou valores de função que são locais para a classe usando `let` associações, e você deve seguir as regras gerais para `let` associações. A `do-bindings` seção inclui o código a ser executado na construção do objeto.

O `member-list` consiste em construtores adicionais, declarações de método estático e de instância, declarações de interface, associações abstratas e declarações de eventos e propriedades. Eles são descritos em [Membros](./members/index.md).

O `identifier` que é usado com a palavra `as` -chave Optional fornece um nome para a variável de instância, ou autoidentifier, que pode ser usado na definição de tipo para se referir à instância do tipo. Para obter mais informações, consulte a seção identificadores automáticos mais adiante neste tópico.

As palavras-chave `class` e `end` que marcam o início e o fim da definição são opcionais.

Os tipos recursivos mutuamente, que são tipos que fazem referência uns aos outros, são Unidos `and` junto com a palavra-chave, assim como as funções recursivas mutuamente. Para obter um exemplo, consulte a seção tipos recursivos mutuamente.

## <a name="constructors"></a>Construtores

O construtor é um código que cria uma instância do tipo de classe. Construtores para classes funcionam de maneira um pouco F# diferente em outras linguagens .net. Em uma F# classe, sempre há um construtor principal cujos argumentos são descritos no `parameter-list` que segue o nome do tipo e cujo `let` corpo consiste nas associações (e `let rec`) no início da declaração de classe e no `do` associações a seguir. Os argumentos do construtor primário estão no escopo durante a declaração de classe.

Você pode adicionar construtores adicionais usando a `new` palavra-chave para adicionar um membro, da seguinte maneira:

`new`(`argument-list`) = `constructor-body`

O corpo do novo construtor deve invocar o construtor primário que é especificado na parte superior da declaração de classe.

O exemplo a seguir ilustra esse conceito. No código a seguir, `MyClass` tem dois construtores, um construtor principal que usa dois argumentos e outro construtor que não usa argumentos.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>permitir e fazer associações

As `let` associações `do` e em uma definição de classe formam o corpo do construtor da classe primária e, portanto, são executadas sempre que uma instância de classe é criada. Se uma `let` associação for uma função, ela será compilada em um membro. Se a `let` associação for um valor que não é usado em nenhuma função ou membro, ele será compilado em uma variável que é local para o construtor. Caso contrário, ele é compilado em um campo da classe. As `do` expressões a seguir são compiladas no construtor primário e executam o código de inicialização para cada instância. Como quaisquer construtores adicionais sempre chamam o Construtor principal, as `let` associações e `do` associações sempre são executadas, independentemente de qual Construtor é chamado.

Os campos criados por `let` associações podem ser acessados em todos os métodos e propriedades da classe; no entanto, eles não podem ser acessados de métodos estáticos, mesmo que os métodos estáticos tenham uma variável de instância como um parâmetro. Eles não podem ser acessados usando o autoidentifier, se houver um.

## <a name="self-identifiers"></a>Identificadores automáticos

Um *autoidentifier* é um nome que representa a instância atual. Os autoidentificadores se assemelham à `this` palavra- `Me` chave em C# ou C++ ou em Visual Basic. Você pode definir um autoidentifier de duas maneiras diferentes, dependendo se deseja que o autoidentificador esteja no escopo para a definição de classe inteira ou apenas para um método individual.

Para definir um autoidentifier para a classe inteira, use a `as` palavra-chave após os parênteses de fechamento da lista de parâmetros do construtor e especifique o nome do identificador.

Para definir um autoidentifier para apenas um método, forneça o autoidentifier na declaração de membro, logo antes do nome do método e de um ponto (.) como um separador.

O exemplo de código a seguir ilustra as duas maneiras de criar um autoidentifier. Na primeira linha, a `as` palavra-chave é usada para definir o próprio identificador. Na quinta linha, o identificador `this` é usado para definir um identificador próprio cujo escopo é restrito ao método. `PrintMessage`

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Ao contrário de outras linguagens .NET, você pode nomear o autoidentificador como desejar; Você não está restrito a nomes como `self`, `Me`ou `this`.

O autoidentifier declarado com a `as` palavra-chave não é inicializado até que as `let` associações sejam executadas. Portanto, ele não pode ser usado nas `let` associações. Você pode usar o autoidentifier na `do` seção associações.

## <a name="generic-type-parameters"></a>Parâmetros de tipo genérico

Parâmetros de tipo genérico são especificados entre colchetes angulares `>`(`<` e), na forma de uma aspa simples seguida por um identificador. Vários parâmetros de tipo genérico são separados por vírgulas. O parâmetro de tipo genérico está no escopo durante a declaração. O exemplo de código a seguir mostra como especificar parâmetros de tipo genérico.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Os argumentos de tipo são inferidos quando o tipo é usado. No código a seguir, o tipo inferido é uma sequência de tuplas.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>Especificando a herança

A `inherit` cláusula identifica a classe base direta, se houver uma. No F#, apenas uma classe base direta é permitida. As interfaces que uma classe implementa não são consideradas classes base. As interfaces são discutidas no tópico [interfaces](Interfaces.md) .

Você pode acessar os métodos e as propriedades da classe base da classe derivada usando a palavra-chave `base` Language como um identificador, seguido por um ponto final (.) e o nome do membro.

Para obter mais informações, consulte [Herança](inheritance.md).

## <a name="members-section"></a>Seção Membros

Você pode definir métodos estáticos ou de instância, propriedades, implementações de interface, membros abstratos, declarações de eventos e construtores adicionais nesta seção. As associações Let e não podem aparecer nesta seção. Como os membros podem ser adicionados a uma variedade F# de tipos além de classes, eles são discutidos em um tópico separado, [Membros](./members/index.md).

## <a name="mutually-recursive-types"></a>Tipos recursivos mutuamente

Quando você define tipos que fazem referência uns aos outros de forma circular, você cadeia de caracteres de acordo com as `and` definições de tipo usando a palavra-chave. A `and` palavra-chave `type` substitui a palavra-chave em todos, exceto a primeira definição, da seguinte maneira.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

A saída é uma lista de todos os arquivos no diretório atual.

## <a name="when-to-use-classes-unions-records-and-structures"></a>Quando usar classes, uniões, registros e estruturas

Considerando a variedade de tipos dos quais escolher, você precisa ter uma boa compreensão do que cada tipo foi projetado para selecionar o tipo apropriado para uma situação específica. As classes são projetadas para uso em contextos de programação orientada a objeto. A programação orientada a objeto é o paradigma dominante usado em aplicativos que são escritos para o .NET Framework. Se o F# seu código tiver que trabalhar junto com o .NET Framework ou outra biblioteca orientada a objeto e, especialmente, se você precisar se estender de um sistema de tipos orientado a objeto, como uma biblioteca de interface do usuário, as classes provavelmente serão apropriadas.

Se você não estiver Interoperando com código orientado a objeto, ou se estiver escrevendo código que seja autônomo e, portanto, protegido contra uma interação frequente com o código orientado a objeto, considere usar registros e uniões discriminadas. Uma única união discriminada e bem pensada, junto com o código de correspondência de padrões apropriado, geralmente pode ser usada como uma alternativa mais simples para uma hierarquia de objetos. Para obter mais informações sobre uniões discriminadas, consulte [uniões discriminadas](discriminated-unions.md).

Os registros têm a vantagem de ser mais simples do que as classes, mas os registros não são apropriados quando as demandas de um tipo excedem o que pode ser feito com sua simplicidade. Os registros são basicamente agregações simples de valores, sem construtores separados que podem executar ações personalizadas, sem campos ocultos, e sem implementações de herança ou de interface. Embora Membros como propriedades e métodos possam ser adicionados aos registros para tornar seu comportamento mais complexo, os campos armazenados em um registro ainda são uma agregação simples de valores. Para obter mais informações sobre registros, consulte [registros](records.md).

As estruturas também são úteis para pequenas agregações de dados, mas diferem de classes e registros em que são tipos de valor .NET. Classes e registros são tipos de referência do .NET. A semântica dos tipos de valor e dos tipos de referência são diferentes nos tipos de valor que são passados por valor. Isso significa que eles são bits copiados para bit quando são passados como um parâmetro ou retornados de uma função. Eles também são armazenados na pilha ou, se forem usados como um campo, inserido dentro do objeto pai, em vez de armazenados em seu próprio local separado no heap. Portanto, as estruturas são apropriadas para dados acessados com frequência quando a sobrecarga de acessar o heap é um problema. Para obter mais informações sobre estruturas, consulte [estruturas](structures.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Membros](./members/index.md)
- [Herança](inheritance.md)
- [Interfaces](interfaces.md)
