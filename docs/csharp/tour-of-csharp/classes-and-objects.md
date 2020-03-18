---
title: Classes e objetos em C# - um tour pela linguagem C#
description: Novato em C#? Leia esta visão geral das classes, objetos e herança
ms.date: 02/27/2020
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: c178e11b5667905f75538555c8a309e2fdb4a9ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159176"
---
# <a name="classes-and-objects"></a>Classes e objetos

*As aulas* são as mais fundamentais dos tipos de C#. Uma classe é uma estrutura de dados que combina ações (métodos e outros membros da função) e estado (campos) em uma única unidade. Uma classe fornece uma definição para *instâncias* da classe criadas dinamicamente, também conhecidas como *objetos*. As classes dão suporte à *herança* e *polimorfismo*, mecanismos nos quais *classes derivadas* podem estender e especializar *classes base*.

Novas classes são criadas usando declarações de classe. Uma declaração de classe inicia com um cabeçalho que especifica os atributos e modificadores de classe, o nome da classe, a classe base (se fornecida) e as interfaces implementadas pela classe. O cabeçalho é seguido pelo corpo da classe, que consiste em uma lista de declarações de membro escrita entre os delimitadores `{` e `}`.

O código a seguir mostra uma `Point`declaração de uma classe simples chamada :

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Instâncias de classes são criadas usando o operador `new`, que aloca memória para uma nova instância, chama um construtor para inicializar a instância e retorna uma referência à instância. As instruções a seguir criam dois objetos Point e armazenam referências a esses objetos em duas variáveis:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

A memória ocupada por um objeto é recuperada automaticamente quando o objeto não está mais acessível. Não é necessário nem possível desalocar explicitamente objetos em C#.

## <a name="members"></a>Membros

Os membros de uma classe são membros estáticos ou membros de instância. Os membros estáticos pertencem às classes e os membros de instância pertencem aos objetos (instâncias de classes).

A lista a seguir fornece uma visão geral dos tipos de membros que uma classe pode conter.

- Constantes
  - Valores constantes associados à classe
- Campos
  - Variáveis de classe
- Métodos
  - Os cálculos e as ações que podem ser executados pela classe
- Propriedades
  - Ações associadas à leitura e à gravação de propriedades nomeadas da classe
- Indexadores
  - Ações associadas a instâncias de indexação da classe como uma matriz
- Eventos
  - Notificações que podem ser geradas pela classe
- Operadores
  - Operadores de conversões e expressão com suporte da classe
- Construtores
  - Ações necessárias para inicializar instâncias da classe ou a própria classe
- Finalizadores
  - Ações a serem executadas antes de as instâncias da classe serem descartadas permanentemente
- Tipos
  - Tipos aninhados declarados pela classe

## <a name="accessibility"></a>Acessibilidade

Cada membro de uma classe tem uma acessibilidade associada, que controla as regiões do texto do programa que podem acessar o membro. Existem seis formas possíveis de acessibilidade. Os modificadores de acesso são resumidos abaixo.

- `public`
  - O acesso não é limitado.
- `protected`
  - O acesso é limitado a esta classe ou classes derivadas desta classe.
- `internal`
  - O acesso é limitado ao conjunto atual (.exe, .dll, e assim por diante.).
- `protected internal`
  - O acesso é limitado à classe de contenção, classes derivadas da classe contendo ou classes dentro do mesmo conjunto.
- `private`
  - O acesso é limitado a esta classe.
- `private protected`
  - O acesso é limitado à classe ou classes que contêm o tipo de contémmento dentro do mesmo conjunto.

## <a name="type-parameters"></a>Parâmetros de tipo

Uma definição de classe pode especificar um conjunto de parâmetros de tipo seguindo o nome da classe com colchetes angulares com uma lista de nomes de parâmetro de tipo. Em seguida, os parâmetros de tipo podem ser usados no corpo das declarações de classe para definir os membros da classe. No exemplo a seguir, os parâmetros de tipo de `Pair` são `TFirst` e `TSecond`:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Um tipo de classe que é declarado para pegar parâmetros de tipo é chamado de *tipo de classe genérica*. Os tipos de estrutura, interface e delegação também podem ser genéricos.
Quando a classe genérica é usada, os argumentos de tipo devem ser fornecidos para cada um dos parâmetros de tipo:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Um tipo genérico com argumentos de tipo fornecidos, como `Pair<int,string>` acima, é chamado de *tipo construído*.

## <a name="base-classes"></a>Classes base

Uma declaração de classe pode especificar uma classe base, seguindo os parâmetros de nome da classe e tipo com dois-pontos e o nome da classe base. Omitir uma especificação de classe base é o mesmo que derivar do `object` de tipo. No exemplo a seguir, a classe base de `Point3D` é `Point` e a classe base de `Point` é `object`:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Uma classe herda os membros de sua classe base. A herança significa que uma classe contém implicitamente todos os membros de sua classe base, exceto para a instância e os construtores estáticos, além dos finalizadores da classe base. Uma classe derivada pode adicionar novos membros aos membros que herda, mas não pode remover a definição de um membro herdado. No exemplo anterior, `Point3D` herda os campos `x` e `y` de `Point` e cada instância `Point3D` contém três campos: `x`, `y` e `z`.

Existe uma conversão implícita de um tipo de classe para qualquer um de seus tipos de classe base. Uma variável de um tipo de classe pode referenciar uma instância dessa classe ou uma instância de qualquer classe derivada. Por exemplo, dadas as declarações de classe anteriores, uma variável do tipo `Point` podem referenciar um `Point` ou um `Point3D`:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Campos

Um *campo* é uma variável que está associada a uma classe ou a uma instância de uma classe.

Um campo declarado com o modificador estático define um campo estático. Um campo estático identifica exatamente um local de armazenamento. Não importa quantas instâncias de uma classe sejam criadas, só há uma cópia de um campo estático.

Um campo declarado sem o modificador estático define um campo de instância. Cada instância de uma classe contém uma cópia separada de todos os campos de instância dessa classe.

No exemplo a seguir, `Color` cada instância da classe `r` `g`tem `b` uma cópia separada dos campos , `Black`e `White` `Red`instância, mas há apenas uma cópia dos campos, e `Green` `Blue` estática:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Conforme mostrado no exemplo anterior, os *campos somente leitura* podem ser declarados com um modificador `readonly`. A atribuição a um campo `readonly` só pode ocorrer como parte da declaração do campo ou em um construtor na mesma classe.

## <a name="methods"></a>Métodos

Um *método* é um membro que implementa um cálculo ou uma ação que pode ser executada por um objeto ou classe. Os *métodos estáticos* são acessados pela classe. Os *métodos de instância* são acessados pelas instâncias da classe.

Os métodos podem ter uma lista de *parâmetros* que representam valores ou referências de variável passadas para o método, e um *tipo de retorno*, que especifica o tipo do valor calculado e retornado pelo método. O tipo de retorno `void` de um método é se ele não retornar um valor.

Como os tipos, os métodos também podem ter um conjunto de parâmetros de tipo, para que os quais os argumentos de tipo devem ser especificados quando o método é chamado. Ao contrário dos tipos, os argumentos de tipo geralmente podem ser inferidos de argumentos de uma chamada de método e não precisam ser fornecidos explicitamente.

A *assinatura* de um método deve ser exclusiva na classe na qual o método é declarado. A assinatura de um método consiste no nome do método, número de parâmetros de tipo e número, modificadores e tipos de seus parâmetros. A assinatura de um método não inclui o tipo de retorno.

### <a name="parameters"></a>parâmetros

Os parâmetros são usados para passar valores ou referências de variável aos métodos. Os parâmetros de um método obtêm seus valores reais de *argumentos* que são especificados quando o método é invocado. Há quatro tipos de parâmetros: parâmetros de valor, parâmetros de referência, parâmetros de saída e matrizes de parâmetros.

Um *parâmetro de valor* é usado para passar argumentos de entrada. Um parâmetro de valor corresponde a uma variável local que obtém seu valor inicial do argumento passado para o parâmetro. Modificações em um parâmetro de valor não afetam o argumento que foi aprovado para o parâmetro.

Os parâmetros de valor podem ser opcionais, especificando um valor padrão para que os argumentos correspondentes possam ser omitidos.

Um *parâmetro de referência* é usado para passar argumentos por referência. O argumento passado para um parâmetro de referência deve ser uma variável com um valor definido e, durante a execução do método, o parâmetro de referência representa o mesmo local de armazenamento como a variável de argumento. Um parâmetro de referência é declarado com o modificador `ref`. O exemplo a seguir mostra o uso de parâmetros `ref`.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

Um *parâmetro de saída* é usado para passar argumentos por referência. Ele é semelhante a um parâmetro de referência, exceto que ele não requer que você atribua explicitamente um valor ao argumento fornecido pelo chamador. Um parâmetro de saída é declarado com o modificador `out`. O exemplo a seguir mostra o uso de parâmetros `out` usando a sintaxe introduzida no C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

Uma *matriz de parâmetros* permite que um número variável de argumentos sejam passados para um método. Uma matriz de parâmetro é declarada com o modificador `params`. Somente o último parâmetro de um método pode ser uma matriz de parâmetros e o tipo de uma matriz de parâmetros deve ser um tipo de matriz unidimensional. Os métodos Write e WriteLine da classe <xref:System.Console?displayProperty=nameWithType> são bons exemplos de uso da matriz de parâmetros. Eles são declarados da seguinte forma.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

Dentro de um método que usa uma matriz de parâmetros, a matriz de parâmetros se comporta exatamente como um parâmetro regular de um tipo de matriz. No entanto, em uma invocação de um método com uma matriz de parâmetros, é possível passar um único argumento do tipo de matriz de parâmetros ou qualquer número de argumentos do tipo de elemento da matriz de parâmetros. No último caso, uma instância de matriz é automaticamente criada e inicializada com os argumentos determinados. Esse exemplo

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

é equivalente ao escrito a seguir.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Corpo do método e variáveis locais

Um corpo do método especifica as instruções para execução quando o método é invocado.

Um corpo de método pode declarar variáveis que são específicas para a invocação do método. Essas variáveis são chamadas de *variáveis locais*. Uma declaração de variável local especifica um nome de tipo, um nome de variável e, possivelmente, um valor inicial. O exemplo a seguir declara uma variável local `i` com um valor inicial de zero e uma variável local `j` sem valor inicial.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

O C# requer que uma variável local seja *atribuída definitivamente* antes de seu valor poder ser obtido. Por exemplo, se a `i` declaração do anterior não incluísse um valor inicial, o `i` compilador relataria um erro para os usos subsequentes de porque `i` não seria definitivamente atribuído nesses pontos do programa.

Um método pode usar instruções `return` para retornar o controle é pelo chamador. Em um método `void` `return` de retorno, as instruções não podem especificar uma expressão. Em um método que retorna não nulo, as instruções `return` devem incluir uma expressão que calcula o valor retornado.

### <a name="static-and-instance-methods"></a>Métodos estáticos e de instância

Um método declarado com um modificador estático é um *método estático*. Um método estático não opera em uma instância específica e só pode acessar diretamente membros estáticos.

Um método declarado sem um modificador estático é um *método de instância*. Um método de instância opera em uma instância específica e pode acessar membros estáticos e de instância. A instância em que um método de instância foi invocado pode ser explicitamente acessada como `this`. É um erro a `this` que se refere em um método estático.

A seguinte classe `Entity` tem membros estáticos e de instância.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Cada `Entity` instância contém um número de série (e, presumivelmente, alguma outra informação que não é mostrada aqui). O construtor `Entity` (que é como um método de instância) inicializa a nova instância com o próximo número de série disponível. Como o construtor é um membro de instância, é `serialNo` permitido acessar `nextSerialNo` tanto o campo de instância quanto o campo estático.

Os métodos estáticos `GetNextSerialNo` e `SetNextSerialNo` podem acessar o campo estático `nextSerialNo`, mas seria um erro para eles acessar diretamente o campo de instância `serialNo`.

O exemplo a seguir mostra o uso da classe Entity.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Os `SetNextSerialNo` `GetNextSerialNo` métodos e estática são invocados `GetSerialNo` na classe, enquanto o método de instância é invocado em instâncias da classe.

### <a name="virtual-override-and-abstract-methods"></a>Métodos abstratos, virtuais e de substituição

Quando uma declaração de método de instância inclui um modificador `virtual`, o método deve ser um *método virtual*. Quando nenhum modificador virtual estiver presente, o método será um *método não virtual*.

Quando um método virtual é invocado, o *tipo de tempo de execução* da instância para o qual essa invocação ocorre determina a implementação real do método para invocar. Em uma invocação de método não virtual, o *tipo de tempo de compilação* da instância é o fator determinante.

Um método virtual pode ser *substituído* em uma classe derivada. Quando uma declaração de método de instância inclui um modificador de substituição, o método substitui um método virtual herdado com a mesma assinatura. Enquanto uma declaração de método virtual apresenta um novo método, uma declaração de método de substituição restringe um método virtual herdado existente fornecendo uma nova implementação do método.

Um *método abstrato* é um método virtual sem implementação. Um método abstrato é declarado com o modificador abstrato e é permitido somente em uma classe que também é declarada como abstrata. Um método abstrato deve ser substituído em cada classe derivada não abstrata.

O exemplo a seguir declara uma classe abstrata, `Expression`, que representa um nó de árvore de expressão e três classes derivadas, `Constant`, `VariableReference` e `Operation`, que implementam nós de árvore de expressão para operações aritméticas, referências de variável e constantes. (Este exemplo é semelhante, mas não deve ser confundido com os tipos de árvore de expressão).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

As quatro classes anteriores podem ser usadas para modelar expressões aritméticas. Por exemplo, usando instâncias dessas classes, a expressão `x + 3` pode ser representada da seguinte maneira.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

O método `Evaluate` de uma instância `Expression` é chamado para avaliar a expressão especificada e produzir um valor `double`. O método recebe um argumento `Dictionary` que contém nomes de variáveis (como chaves das entradas) e valores (como valores das entradas). Como `Evaluate` é um método abstrato, classes não abstratas derivadas de `Expression` devem substituir `Evaluate`.

Uma implementação de `Evaluate` do `Constant` retorna apenas a constante armazenada. Uma implementação de `VariableReference` consulta o nome de variável no dicionário e retorna o valor resultante. Uma implementação de `Operation` primeiro avalia os operandos esquerdo e direito (chamando recursivamente seus métodos `Evaluate`) e, em seguida, executa a operação aritmética determinada.

O seguinte programa usa as classes `Expression` para avaliar a expressão `x * (y + 2)` para valores diferentes de `x` e `y`.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Sobrecarga de método

A *sobrecarga* de método permite que vários métodos na mesma classe tenham o mesmo nome, contanto que tenham assinaturas exclusivas. Ao compilar uma invocação de um método sobrecarregado, o compilador usa a *resolução de sobrecarga* para determinar o método específico para invocar. A resolução de sobrecarga localizará o método que melhor corresponde aos argumentos ou relatará um erro se nenhuma correspondência for encontrada. O exemplo a seguir mostra a resolução de sobrecarga em vigor. O comentário de cada `UsageExample` invocação no método mostra qual método é invocado.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Conforme mostrado no exemplo, um determinado método sempre pode ser selecionado ao converter explicitamente os argumentos para os tipos de parâmetro exatos e/ou fornecendo explicitamente os argumentos de tipo.

## <a name="other-function-members"></a>Outros membros da função

Os membros que contêm código executável são conhecidos coletivamente como *membros de função* de uma classe. A seção anterior descreve métodos, que são os principais tipos de membros da função. Esta seção descreve os outros tipos de membros da função com suporte do C#: construtores, propriedades, indexadores, eventos, operadores e finalizadores.

O exemplo a seguir `MyList<T>`mostra uma classe genérica chamada , que implementa uma lista de objetos growable. A classe contém vários exemplos dos tipos mais comuns de membros da função.

> [!NOTE]
> Este exemplo cria uma classe `MyList`, que não é igual ao .NET padrão <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Ele ilustra os conceitos necessários para esse tour, mas não serve como substituto para essa classe.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Construtores

O C# dá suporte aos construtores estáticos e de instância. Um *construtor de instância* é um membro que implementa as ações necessárias para inicializar uma instância de uma classe. Um *construtor estático* é um membro que implementa as ações necessárias para inicializar uma classe em si quando ela é carregada pela primeira vez.

Um construtor é declarado como um método sem nenhum tipo de retorno e o mesmo nome que a classe continente. Se uma declaração de construtor inclui um modificador estático, ela declara um construtor estático. Caso contrário, ela declara um construtor de instância.

Construtores de instância podem ser sobrecarregados e ter parâmetros opcionais. Por exemplo, a classe `MyList<T>` declara um construtor de instância com um único parâmetro `int` opcional. Os construtores de instância são invocados usando o operador `new`. As seguintes instruções alocam duas instâncias `MyList<string>` usando o construtor da classe `MyList` com e sem o argumento opcional.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Ao contrário de outros membros, os construtores de instâncias não são herdados, e uma classe não tem nenhum exemplo de construtores além daqueles construtores realmente declarados na classe. Se nenhum construtor de instância for fornecido para uma classe, então um construtor vazio sem parâmetros será fornecido automaticamente.

### <a name="properties"></a>Propriedades

As *propriedades* são uma extensão natural dos campos. Elas são denominadas membros com tipos associados, e a sintaxe para acessar os campos e as propriedades é a mesma. No entanto, ao contrário dos campos, as propriedades não denotam os locais de armazenamento. Em vez disso, as propriedades têm *acessadores* que especificam as instruções a serem executadas quando os valores forem lidos ou gravados.

Uma propriedade é declarada como um campo, exceto quando a declaração termina com um acessador get e/ou um acessador set gravado entre os delimitadores `{` e `}` em vez de terminar com um ponto-e-vírgula. Uma propriedade que tem um acessador get e um acessador set é uma *propriedade de leitura-gravação*. Uma propriedade que tem apenas um acessador get é uma *propriedade somente leitura*, e uma propriedade que tem apenas um acessador set é uma *propriedade somente gravação*.

Um acessador get corresponde a um método sem parâmetros com um valor retornado do tipo de propriedade. Exceto como o destino de uma atribuição, quando uma propriedade é referenciada em uma expressão, o acessador get da propriedade é invocado para calcular o valor da propriedade.

Um acessador set corresponde a um método com um parâmetro único chamado valor e nenhum tipo de retorno. Quando uma propriedade é referenciada como o destino de uma atribuição ou como o operando do + + ou --, o acessador set é invocado com um argumento que fornece o novo valor.

A classe `MyList<T>` declara duas propriedades, `Count` e `Capacity`, que são somente leitura e leitura/gravação, respectivamente. O código a seguir é um exemplo de uso dessas propriedades:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Como nos campos e métodos, o C# dá suporte a propriedades de instância e a propriedades estáticas. As propriedades estáticas são declaradas com o modificador estático e as propriedades de instância são declaradas sem ele.

Os acessadores de uma propriedade podem ser virtuais. Quando uma declaração de propriedade inclui um modificador `virtual`, `abstract` ou `override`, ela se aplica aos acessadores da propriedade.

### <a name="indexers"></a>Indexadores

Um *indexador* é um membro que permite que objetos sejam indexados da mesma forma que uma matriz. Um indexador é declarado como uma propriedade, exceto se o nome do membro for `this` seguido por uma lista de parâmetros escrita entre os delimitadores `[` e `]`. Os parâmetros estão disponíveis nos acessadores do indexador. Semelhante às propriedades, os indexadores podem ser de leitura-gravação, somente leitura e somente gravação, e os acessadores de um indexador pode ser virtuais.

A classe `MyList<T>` declara um indexador único de leitura-gravação que usa um parâmetro `int`. O indexador possibilita indexar instâncias `MyList<T>` com valores `int`. Por exemplo: 

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Os indexadores podem ser sobrecarregados, o que significa que uma classe pode declarar vários indexadores, desde que o número ou os tipos de seus parâmetros sejam diferentes.

### <a name="events"></a>Eventos

Um *evento* é um membro que permite que uma classe ou objeto forneça notificações. Um evento é declarado como um campo exceto se a declaração incluir uma palavra-chave do evento e o tipo deverá ser um tipo delegado.

Dentro de uma classe que declara um membro do evento, o evento se comporta como um campo de um tipo de delegado (desde que o evento não seja abstrato e não declare acessórios). O campo armazena uma referência a um delegado que representa os manipuladores de eventos que foram adicionados ao evento. Se nenhum manipulador de evento estiver presente, o campo será `null`.

A classe `MyList<T>` declara um membro único de evento chamado `Changed`, que indica que um novo item foi adicionado à lista. O evento Alterado é gerado pelo método virtual `OnChanged`, que primeiro verifica se o evento é `null` (o que significa que nenhum manipulador está presente). A noção de gerar um evento é precisamente equivalente a invocar o delegado representado pelo evento — assim, não há constructos de linguagem especial para gerar eventos.

Os clientes reagem a eventos por meio de *manipuladores de eventos*. Os manipuladores de eventos são conectados usando o operador `+=` e removidos usando o operador `-=`. O exemplo a seguir anexa um manipulador de eventos para o evento `Changed` de um `MyList<string>`.

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Para cenários avançados onde o controle do armazenamento subjacente de um `add` evento `remove` é desejado, uma `set` declaração de evento pode fornecer explicitamente e acessórios, que são semelhantes ao acessório de uma propriedade.

### <a name="operators"></a>Operadores

Um *operador* é um membro que define o significado da aplicação de um operador de expressão específico para instâncias de uma classe. Três tipos de operadores podem ser definidos: operadores unários, operadores binários e operadores de conversão. Todos os operadores devem ser declarados como `public` e `static`.

A classe `MyList<T>` declara dois operadores, `operator ==` e `operator !=` e, portanto, dá um novo significado para as expressões que aplicam esses operadores a instâncias `MyList`. Especificamente, os operadores definem a igualdade de duas instâncias `MyList<T>` ao comparar cada um dos objetos contidos usando os métodos Equals. O exemplo a seguir usa o operador `==` para comparar duas instâncias `MyList<int>`.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

O primeiro `Console.WriteLine` gera `True` porque as duas listas contêm o mesmo número de objetos com os mesmos valores na mesma ordem. Como `MyList<T>` não definiu `operator ==`, o primeiro `Console.WriteLine` geraria `False` porque `a` e `b` referenciam diferentes instâncias `MyList<int>`.

### <a name="finalizers"></a>Finalizadores

Um *finalizador* é um membro que implementa as ações necessárias para finalizar uma instância de uma classe. Os finalizadores não podem ter parâmetros, não podem ter modificadores de acessibilidade, e não podem ser invocados explicitamente. O finalizador de uma instância é invocado automaticamente durante a coleta de lixo.

O coletor de lixo tem latitude ampla ao decidir quando coletar objetos e executar os finalizadores. Especificamente, o tempo das invocações de finalizadores não é determinístico, e os finalizadores podem ser executados em qualquer segmento. Para esses e outros motivos, as classes devem implementar os finalizadores apenas quando não houver outras soluções viáveis.

A instrução `using` fornece uma abordagem melhor para a destruição de objetos.

> [!div class="step-by-step"]
> [Próximo](statements.md)
> [anterior](arrays.md)
