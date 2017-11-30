---
title: Classes (F#)
description: "Saiba como F # Classes são tipos que representam os objetos que podem ter propriedades, métodos e eventos."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d58679d5-7753-4b3b-a12f-6e9f00ed5ba3
ms.openlocfilehash: 2a73baba1f7c1b0d3bd09d22c9d6d9f0524daef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="classes"></a>Classes

*Classes* são tipos que representam os objetos que podem ter propriedades, métodos e eventos.


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
Classes representam a descrição fundamental dos tipos de objeto do .NET; a classe é o conceito de tipo primário que dá suporte à programação orientada a objeto em F #.

Na sintaxe anterior, o `type-name` é qualquer identificador válido. O `type-params` descreve os parâmetros de tipo genérico opcional. Ele consiste em nomes de parâmetro de tipo e restrições entre colchetes angulares (`<` e `>`). Para obter mais informações, consulte [genéricos](generics/index.md) e [restrições](generics/constraints.md). O `parameter-list` descreve os parâmetros do construtor. O modificador de acesso primeiro se refere ao tipo; a segunda se refere ao construtor primário. Em ambos os casos, o padrão é `public`.

Especifique a classe base para uma classe usando o `inherit` palavra-chave. Você deve fornecer argumentos, entre parênteses, o construtor de classe base.

Declarar campos ou valores que são locais para a classe por meio de função `let` associações e você deve seguir as regras gerais para `let` associações. O `do-bindings` seção inclui o código a ser executado após a construção de objeto.

O `member-list` consiste em construtores adicionais, instância e declarações de método estático, declarações de interface, associações abstratas e declarações de evento e propriedade. Elas são descritas nas [membros](members/index.md).

O `identifier` que é usado com opcional `as` palavra-chave fornece um nome para a variável de instância ou identificador de autoatendimento, que pode ser usado na definição de tipo para referir-se à instância do tipo. Para obter mais informações, consulte a seção identificadores de autoatendimento, mais adiante neste tópico.

As palavras-chave `class` e `end` que marca o início e final da definição do são opcionais.

Mutuamente recursivas tipos, que são tipos que referenciam uns aos outros, são Unidos junto com o `and` palavra-chave como são mutuamente de funções recursivas. Para obter um exemplo, consulte a seção mutuamente recursivas tipos.


## <a name="constructors"></a>Construtores
O construtor é o código que cria uma instância do tipo de classe. Construtores para classes funcionam de forma um pouco diferente em F # do que em outras linguagens .NET. Em uma classe de F #, sempre há um construtor primário cujos argumentos são descritos no `parameter-list` que segue o nome do tipo e cujo corpo consiste de `let` (e `let rec`) associações no início da declaração de classe e o `do`associações que seguem. Os argumentos do construtor primário estão no escopo em toda a declaração de classe.

Você pode adicionar construtores adicionais usando o `new` palavra-chave para adicionar um membro, da seguinte maneira:

`new`(`argument-list`) = `constructor-body`

O corpo do novo construtor deve chamar o construtor primário que é especificado no topo da declaração de classe.

O exemplo a seguir ilustra esse conceito. No código a seguir, `MyClass` tem dois construtores, um construtor primário que leva dois argumentos e outro construtor que não usa nenhum argumento.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]
    
## <a name="let-and-do-bindings"></a>Let e associações

O `let` e `do` associações em uma definição de classe formam o corpo de construtor da classe principal e, portanto, são executados sempre que uma instância da classe é criada. Se um `let` associação é uma função e, em seguida, ele é compilado em um membro. Se o `let` associação é um valor que não é usado em qualquer função ou membro, em seguida, ele é compilado em uma variável que é local para o construtor. Caso contrário, ele é compilado em um campo da classe. O `do` expressões que seguem são compiladas em um construtor primário e execute o código de inicialização para cada instância. Porque nenhum construtor adicionais sempre chama o construtor primário, o `let` associações e `do` associações sempre executado, independentemente de qual construtor seja chamado.

Campos que são criados pelo `let` associações podem ser acessadas em todo os métodos e propriedades da classe; no entanto, eles não serão acessados de métodos estáticos, mesmo se os métodos estáticos tenham uma variável de instância como um parâmetro. Não pode ser acessados usando o identificador automático, se houver.


## <a name="self-identifiers"></a>Identificadores de autoatendimento

Um *identificador automático* é um nome que representa a instância atual. Autoidentificadores são semelhantes a `this` palavra-chave em c# ou C++ ou `Me` no Visual Basic. Você pode definir um identificador de autoatendimento de duas maneiras diferentes, dependendo se você deseja que o identificador automático do escopo para a definição de classe inteira ou apenas para um método individual.

Para definir um identificador de autoatendimento para a classe inteira, use o `as` palavra-chave após os parênteses de fechamento do parâmetro de construtor lista e especifique o nome do identificador.

Para definir um identificador de autoatendimento para apenas um método, forneça o identificador self na declaração de membro, antes do nome do método e um ponto (.) como separador.

O exemplo de código a seguir ilustra os dois modos de criar um identificador de autoatendimento. Na primeira linha, o `as` palavra-chave é usada para definir o identificador de autoatendimento. Na quinta linha, o identificador `this` é usado para definir um identificador de autoatendimento cujo escopo é restrito ao método `PrintMessage`.

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Ao contrário em outras linguagens .NET, você pode nomear o identificador automático mas desejado. Você não está restrito a nomes como `self`, `Me`, ou `this`.

O identificador de autoatendimento que é declarado com o `as` palavra-chave não é inicializado até depois que o `let` associações são executadas. Portanto, ele não pode ser usado o `let` associações. Você pode usar o identificador de autoatendimento no `do` seção associações.


## <a name="generic-type-parameters"></a>Parâmetros de tipo genérico

Parâmetros de tipo genéricos são especificados entre colchetes angulares (`<` e `>`), na forma de uma aspa simples seguida por um identificador. Vários parâmetros de tipo genérico são separados por vírgulas. O parâmetro de tipo genérico é em escopo da declaração. O exemplo de código a seguir mostra como especificar parâmetros de tipo genérico.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Argumentos de tipo são inferidos quando o tipo é usado. No código a seguir, o tipo inferido é uma sequência de tuplas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]
    
## <a name="specifying-inheritance"></a>Especificação de herança

O `inherit` cláusula identifica a classe base direta, se houver um. Em F #, apenas uma classe base direta é permitida. Interfaces que implementa uma classe não são considerados classes base. Interfaces são discutidas a [Interfaces](Interfaces.md) tópico.

Você pode acessar os métodos e propriedades da classe base da classe derivada usando a palavra-chave do idioma `base` como um identificador, seguido por um ponto (.) e o nome do membro.

Para obter mais informações, consulte [Herança](inheritance.md).


## <a name="members-section"></a>Seção de membros
Você pode definir estático ou métodos de instância, propriedades, implementações de interface, membros abstratos, declarações de evento e construtores adicionais nesta seção. Permitem e associações não aparecem nesta seção. Como os membros podem ser adicionados a uma variedade de tipos F # além das classes, eles serão discutidos em um tópico separado, [membros](members/index.md).


## <a name="mutually-recursive-types"></a>Mutuamente recursivas tipos
Quando você define os tipos de referenciam entre si de maneira circular, é enfileirar as definições de tipo usando o `and` palavra-chave. O `and` palavra-chave substitui o `type` palavra-chave em todas, exceto a primeira definição, da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

A saída é uma lista de todos os arquivos no diretório atual.


## <a name="when-to-use-classes-unions-records-and-structures"></a>Quando usar Classes e estruturas, registros e uniões
Dada a variedade de tipos para escolher, você precisa ter uma boa compreensão de como o que cada tipo foi projetado para selecionar o tipo apropriado para uma situação específica. Classes são projetadas para uso em contextos de programação orientada a objeto. Programação orientada a objeto é o paradigma dominante usado em aplicativos que são escritos para o .NET Framework. Se seu código F # tem que trabalham em conjunto com o .NET Framework ou outra biblioteca orientada a objeto e, especialmente se você precisa estender a partir de um sistema de tipo orientada a objeto, como uma biblioteca de interface do usuário, as classes são provavelmente apropriados.

Se você não está interoperando junto com o código e orientada a objeto, ou se você estiver escrevendo código que é independente e, portanto, protegidos contra frequente interação com o código e orientada a objeto, você deve considerar o uso de registros e discriminada uniões. Um único bem pensamento – out união discriminada, junto com o padrão apropriado, correspondência de código, geralmente pode ser usado como uma alternativa mais simples para uma hierarquia de objetos. Para obter mais informações sobre uniões discriminadas, consulte [uniões discriminada](discriminated-unions.md).

Registros têm a vantagem de ser mais simples do que classes, mas os registros não são apropriados quando as demandas de um tipo excedem o que pode ser realizado com sua simplicidade. Os registros são basicamente simples agregações de valores, sem construtores separados que podem executar ações personalizadas, sem campos ocultos e sem implementações de interface ou de herança. Embora membros, como propriedades e métodos podem ser adicionados a registros para tornar seu comportamento mais complexo, os campos armazenados em um registro ainda são uma agregação simples de valores. Para obter mais informações sobre os registros, consulte [registros](records.md).

Estruturas também são úteis para agregações pequenas de dados, mas eles são diferentes de classes e registros são tipos de valor de .NET. Classes e registros são tipos de referência do .NET. A semântica de tipos de valor e tipos de referência é diferente tipos de valor são transmitidos por valor. Isso significa que eles são copiados bit por bit quando são passados como um parâmetro ou retornados de uma função. Eles também são armazenados na pilha ou, se eles são usados como um campo, inserido no objeto pai, em vez de armazenados em seu próprio local separado no heap. Portanto, estruturas são apropriadas para dados acessados com frequência quando a sobrecarga de acessar o heap é um problema. Para obter mais informações sobre estruturas, consulte [estruturas](structures.md).


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Membros](members/index.md)

[Herança](inheritance.md)

[Interfaces](interfaces.md)

