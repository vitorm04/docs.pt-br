---
title: Classes (F#)
description: 'Saiba como o F # Classes são tipos que representam os objetos que podem ter propriedades, métodos e eventos.'
ms.date: 05/16/2016
ms.openlocfilehash: 71cd713d192d28565e879b79b2fc9e0530e5f841
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112922"
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

As classes representam a descrição fundamental dos tipos de objeto do .NET; a classe é o conceito de tipo primário que dá suporte à programação orientada a objeto em F #.

Na sintaxe anterior, o `type-name` é qualquer identificador válido. O `type-params` descreve parâmetros de tipo genérico opcional. Ele consiste em nomes de parâmetro de tipo e restrições entre colchetes angulares (`<` e `>`). Para obter mais informações, consulte [genéricos](generics/index.md) e [restrições](generics/constraints.md). O `parameter-list` descreve os parâmetros do construtor. O modificador de acesso de primeira pertence ao tipo; a segunda diz respeito ao construtor primário. Em ambos os casos, o padrão é `public`.

Especificar a classe base para uma classe usando o `inherit` palavra-chave. Você deve fornecer argumentos, entre parênteses, o construtor de classe base.

Declarar campos ou valores que são locais para a classe por meio de função `let` associações e você deve seguir as regras gerais para `let` associações. O `do-bindings` seção inclui o código a ser executado no momento da construção do objeto.

O `member-list` consiste em construtores adicionais, instância e declarações de método estático, declarações de interface, associações abstratas e declarações de propriedade e evento. Elas são descritas em [membros](members/index.md).

O `identifier` que é usado com opcional `as` palavra-chave fornece um nome para a variável de instância, ou identificador self, que pode ser usado na definição de tipo para fazer referência à instância do tipo. Para obter mais informações, consulte a seção Self identificadores neste tópico.

As palavras-chave `class` e `end` que marcam o início e final da definição do são opcionais.

Mutuamente recursivas tipos, que são tipos que fazem referência uns aos outros, são Unidos junto com o `and` exatamente como mutuamente funções recursivas são de palavra-chave. Para obter um exemplo, consulte a seção mutuamente recursivas tipos.

## <a name="constructors"></a>Construtores

O construtor é o código que cria uma instância do tipo de classe. Construtores para classes funcionam de forma um pouco diferente no F # do que em outras linguagens .NET. Em uma classe de F #, sempre há um construtor primário cujos argumentos são descritos na `parameter-list` que segue o nome do tipo e cujo corpo consiste o `let` (e `let rec`) associações no início da declaração de classe e o `do`associações que seguem. Os argumentos do construtor primário estão no escopo em toda a declaração de classe.

Você pode adicionar os construtores adicionais usando o `new` palavra-chave para adicionar um membro, da seguinte maneira:

`new`(`argument-list`) = `constructor-body`

O corpo do novo construtor deve invocar o construtor primário que é especificado no topo da declaração de classe.

O exemplo a seguir ilustra esse conceito. No código a seguir, `MyClass` possui dois construtores, um construtor primário que usa dois argumentos e outro construtor que não usa nenhum argumento.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>Let e associações

O `let` e `do` ligações em uma definição de classe formam o corpo do construtor de classe primária e, portanto, são executados sempre que uma instância da classe é criada. Se um `let` associação é uma função e, em seguida, ele é compilado em um membro. Se o `let` associação é um valor que não é usado em qualquer função ou um membro, em seguida, ele é compilado em uma variável que é local para o construtor. Caso contrário, ele é compilado em um campo da classe. O `do` expressões que seguem são compiladas para o construtor primário e executar o código de inicialização para cada instância. Porque os construtores adicionais sempre chamem o construtor primário, o `let` associações e `do` associações sempre executado, independentemente de qual construtor é chamado.

Campos que são criados por `let` associações podem ser acessadas em todo os métodos e propriedades da classe; no entanto, eles não podem ser acessados de métodos estáticos, mesmo se os métodos estáticos usam uma variável de instância como um parâmetro. Não pode ser acessados usando o identificador de autoatendimento, se houver.

## <a name="self-identifiers"></a>Autoidentificadores

Um *identificador self* é um nome que representa a instância atual. Autoidentificadores se parecer com o `this` palavra-chave em c# ou C++ ou `Me` no Visual Basic. Você pode definir um identificador de autoatendimento de duas maneiras diferentes, dependendo se você deseja que o identificador de autoatendimento do escopo para a definição de classe inteira ou apenas para um método individual.

Para definir um identificador de autoatendimento para a classe inteira, use o `as` palavra-chave depois dos parênteses de fechamento do parâmetro de construtor de lista e especifique o nome do identificador.

Para definir um identificador individual para apenas um método, forneça o identificador de auto na declaração de membro, logo antes do nome do método e um ponto (.) como separador.

O exemplo de código a seguir ilustra as duas maneiras de criar um identificador de self. Na primeira linha, o `as` palavra-chave é usada para definir o identificador de self. Na quinta linha, o identificador `this` é usado para definir um identificador de autoatendimento cujo escopo é restrito para o método `PrintMessage`.

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Ao contrário em outras linguagens .NET, você pode nomear o identificador self desejar; Você não está restrito a nomes, como `self`, `Me`, ou `this`.

O identificador de autoatendimento que é declarado com o `as` palavra-chave não foi inicializado até depois que o `let` associações são executadas. Portanto, ele não pode ser usado no `let` associações. Você pode usar o identificador de autoatendimento no `do` seção de associações.

## <a name="generic-type-parameters"></a>Parâmetros de tipo genérico

Parâmetros de tipo genérico são especificados entre colchetes angulares (`<` e `>`), na forma de uma marca de aspas simples seguida por um identificador. Vários parâmetros de tipo genérico são separados por vírgulas. O parâmetro de tipo genérico está no escopo em toda a declaração. O exemplo de código a seguir mostra como especificar parâmetros de tipo genérico.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Argumentos de tipo são inferidos quando o tipo é usado. No código a seguir, o tipo inferido é uma sequência de tuplas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>Especificação de herança

O `inherit` cláusula identifica a classe base direta, se houver um. No F #, apenas uma classe base direta é permitida. Interfaces que implementa uma classe não são consideradas classes base. Interfaces são discutidos os [Interfaces](Interfaces.md) tópico.

Você pode acessar os métodos e propriedades da classe base da classe derivada usando a palavra-chave de linguagem `base` como um identificador, seguido por um ponto (.) e o nome do membro.

Para obter mais informações, consulte [Herança](inheritance.md).

## <a name="members-section"></a>Seção de membros

Você pode definir estático ou instância métodos, propriedades, implementações de interface, membros abstratos, declarações de evento e construtores adicionais nesta seção. Let e fazem ligações não pode aparecer nesta seção. Porque os membros podem ser adicionados a uma variedade de tipos F #, além de classes, eles serão discutidos em um tópico separado, [membros](members/index.md).

## <a name="mutually-recursive-types"></a>Mutuamente recursivas tipos

Quando você define tipos que fazem referência entre si de uma forma circular, é enfileirar as definições de tipo usando o `and` palavra-chave. O `and` palavra-chave substitui o `type` palavra-chave em todos, exceto a primeira definição, da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

A saída é uma lista de todos os arquivos no diretório atual.

## <a name="when-to-use-classes-unions-records-and-structures"></a>Quando usar Classes e estruturas, registros e uniões

Considerando a variedade de tipos para escolher, você precisa ter uma boa compreensão de como o que cada tipo é projetado para selecionar o tipo apropriado para uma determinada situação. As classes são projetadas para uso em contextos de programação orientada a objeto. Programação orientada a objeto é o paradigma dominante usado em aplicativos que são escritos para o .NET Framework. Se seu código F # tem trabalhem em conjunto com o .NET Framework ou outra biblioteca orientada a objeto e, especialmente se você tiver que estendem a partir de um sistema de tipos orientado a objeto, como uma biblioteca de interface do usuário, as classes são provavelmente apropriadas.

Se você não está interoperando intimamente com o código orientado a objeto, ou se você estiver escrevendo código que é independente e, portanto, protegido contra interações frequentes com o código orientado a objeto, você deve considerar o uso de registros e uniões discriminadas. Uma única e bem pensamento – out união discriminada, junto com correspondência apropriada de código, geralmente pode ser usado como uma alternativa mais simples para uma hierarquia de objetos. Para obter mais informações sobre as uniões discriminadas, consulte [uniões discriminadas](discriminated-unions.md).

Registros têm a vantagem de ser mais simples do que as classes, mas os registros não são apropriados quando as demandas de um tipo excedem o que pode ser feito com a sua simplicidade. Os registros são basicamente simples agregações de valores, sem construtores separados que podem executar ações personalizadas, sem campos ocultos e sem as implementações de herança ou interface. Embora membros como métodos e propriedades podem ser adicionados aos registros para tornar seu comportamento mais complexo, os campos armazenados em um registro ainda são uma agregação simples de valores. Para obter mais informações sobre os registros, consulte [registros](records.md).

Estruturas também são úteis para pequenos agregados de dados, mas elas diferem das classes e registros são tipos de valor do .NET. Registros e classes são tipos de referência do .NET. A semântica de tipos de valor e tipos de referência é diferente tipos de valor são passados por valor. Isso significa que eles são copiados bit por bit quando são passados como um parâmetro ou retornados de uma função. Eles também são armazenados na pilha ou, se eles forem usados como um campo, inserido dentro do objeto pai, em vez de armazenados em seu próprio local separado no heap. Portanto, as estruturas são apropriadas para dados acessados com frequência quando a sobrecarga de acessar o heap é um problema. Para obter mais informações sobre estruturas, consulte [estruturas](structures.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Membros](members/index.md)
- [Herança](inheritance.md)
- [Interfaces](interfaces.md)
