---
title: 'Diretrizes de design do componente F #'
description: 'Aprenda as diretrizes para escrever componentes F # destinados ao consumo por outros chamadores.'
ms.date: 05/14/2018
ms.openlocfilehash: 7859baac76be01b2cfbdc8602b6cc417cfe5106f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
---
# <a name="f-component-design-guidelines"></a>Diretrizes de design do componente F #

Este documento é um conjunto de diretrizes de design do componente para F # de programação, com base no F # componente diretrizes de Design, v14, Microsoft Research, e [outra versão](https://fsharp.org/specs/component-design-guidelines/) curadoria e mantido pela F # Software Foundation originalmente.

Este documento pressupõe que você esteja familiarizado com a programação F #. Muito obrigado a comunidade do F # para suas contribuições e comentários úteis em diversas versões deste guia.

## <a name="overview"></a>Visão geral

Este documento examina alguns dos problemas relacionados ao design de componente do F # e a codificação. Um componente pode significar qualquer um dos seguintes:

* Uma camada em seu projeto F # com consumidores externos no projeto.
* Uma biblioteca destinada ao consumo por código F # em limites de assembly.
* Uma biblioteca destinada ao consumo por qualquer linguagem .NET em limites de assembly.
* Uma biblioteca se destina para distribuição por meio de um repositório de pacotes, tais como [NuGet](https://nuget.org).

Execute as técnicas descritas neste artigo o [cinco princípios de BOM código F #](index.md#five-principles-of-good-f-code)e, portanto, utilizar funcionais e objetos de programação conforme apropriado.

Independentemente da metodologia, o designer do componente e a biblioteca enfrentará uma série de práticas e prosaico problemas ao tentar criar uma API que pode ser facilmente usada por desenvolvedores. Aplicativo consciência do [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/index.md) voltar para a criação de um conjunto consistente de APIs que são agradável consumir.

## <a name="general-guidelines"></a>Diretrizes gerais

Há algumas diretrizes universais que se aplicam a F # bibliotecas, independentemente do público-alvo para a biblioteca.

### <a name="learn-the-net-library-design-guidelines"></a>Aprenda as diretrizes de Design de biblioteca do .NET

Independentemente do tipo de F # estão fazendo de codificação, é importante ter um conhecimento prático do [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/index.md). A maioria das outras F # e programadores do .NET serão estar familiarizado com estas diretrizes e esperar que o código .NET de acordo com a eles.

As diretrizes de Design de biblioteca .NET fornecem diretrizes gerais sobre nomenclatura, projetando classes e interfaces, design de membros (propriedades, métodos, eventos, etc.) e muito mais e são úteis primeiro ponto de referência para uma variedade de diretrizes de design.

### <a name="add-xml-documentation-comments-to-your-code"></a>Adicionar comentários de documentação XML ao seu código

Documentação XML em APIs públicas Certifique-se de que os usuários podem obter ótimo Intellisense e Inforapida ao usar esses tipos e membros e documentação de construção habilitar arquivos para a biblioteca. Consulte o [documentação XML](../language-reference/xml-documentation.md) sobre várias marcas xml que podem ser usadas para marcação adicional em xmldoc comentários.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

Você pode usar os comentários XML de forma abreviada (`/// comment`), ou os comentários XML padrão (`///<summary>comment</summary>`).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Considere o uso de arquivos de assinatura explícita (. FSI) para a biblioteca estável e APIs de componente

Usando arquivos de assinaturas explícita em uma biblioteca F # fornece um resumo sucinto do API pública, que ajuda a garantir que você sabe a superfície pública completa da biblioteca, bem como fornece uma separação clara entre documentação pública e internos detalhes de implementação. Observe que os arquivos de assinatura adicionar fricção para alterar a API pública, exigindo que as alterações sejam feitas em arquivos de assinatura e implementação. Como resultado, os arquivos de assinatura devem normalmente ser introduzidos somente quando uma API se tornam consolidou e não deve alterar significativamente.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Sempre siga as práticas recomendadas para o uso de cadeias de caracteres no .NET

Execute [práticas recomendadas para usar cadeias de caracteres no .NET](../../standard/base-types/best-practices-strings.md) orientação. Em particular, sempre claramente *intenção cultura* na conversão e comparação de cadeias de caracteres (quando aplicável).

## <a name="guidelines-for-f-facing-libraries"></a>Diretrizes para F #-voltada para bibliotecas

Esta seção apresenta recomendações para o desenvolvimento de F # pública-voltada para bibliotecas; ou seja, as bibliotecas expor APIs públicas que são destinados a serem consumidos por desenvolvedores de F #. Há uma variedade de recomendações de design de biblioteca aplicável especificamente para F #. Na ausência das recomendações específicas que execute, as diretrizes de Design de biblioteca do .NET estão as diretrizes de fallback.

### <a name="naming-conventions"></a>Convenções de nomenclatura

#### <a name="use-net-naming-and-capitalization-conventions"></a>Use convenções de nomenclatura e capitalização do .NET

A tabela a seguir segue convenções de nomenclatura e capitalização do .NET. Há pequenas adições para incluir também as construções de linguagem F #.

| Constructo | Caso | Parte | Exemplos | Observações |
|-----------|------|------|----------|-------|
| Tipos concretos | PascalCase | Substantivo / adjetivo | Lista, duplo, complexo | Tipos concretos são estruturas, classes, enumerações, delegados, registros e uniões. Embora os nomes de tipo são tradicionalmente minúsculos em OCaml, F # adotou o esquema de nomenclatura do .NET para tipos.
| DLLs           | PascalCase |                 | Fabrikam.Core.dll |  |
| Marcas de união     | PascalCase | substantivo | Alguns, adicionar, sucesso | Não use um prefixo em APIs públicas. Opcionalmente, use um prefixo ao interna, como ' ' Digite equipes = TAlpha | TBeta | TDelta. ' ' |
| evento          | PascalCase | Verbo | ValueChanged / ValueChanging |  |
| Exceções     | PascalCase |      | WebException | Nome deve terminar com "Exception". |
| Campo          | PascalCase | substantivo | CurrentName  | |
| Tipos de interface |  PascalCase | Substantivo / adjetivo | IDisposable | Nome deve começar com "I". |
| Método |  PascalCase |  Verbo | ToString | |
| Namespace | PascalCase | | FSharp | Geralmente usa `<Organization>.<Technology>[.<Subnamespace>]`, embora drop da organização se a tecnologia é independente da organização. |
| Parâmetros | camelCase | substantivo |  typeName, transform, intervalo | |
| permitir que os valores (internos) | camelCase ou PascalCase | Substantivo / verbo |  getValue, myTable |
| permitir que os valores (externo) | camelCase ou PascalCase | Substantivo/verbo  | List.map, Dates.Today | os valores associados a Let geralmente são públicos ao seguir os padrões de design funcional tradicional. No entanto, geralmente usa PascalCase quando o identificador pode ser usado em outras linguagens .NET. |
| Propriedade  | PascalCase  | Substantivo / adjetivo  | IsEndOfFile, BackColor  | Propriedades Boolianas geralmente uso é e pode e deve ser afirmativa, como IsEndOfFile, não IsNotEndOfFile.

#### <a name="avoid-abbreviations"></a>Evite abreviações

As diretrizes do .NET evitar o uso de abreviações (por exemplo, "usar `OnButtonClick` em vez de `OnBtnClick`"). Abreviações comuns, como `Async` para "Assíncrona" tolerado. Esta diretriz às vezes é ignorada para programação funcional; Por exemplo, `List.iter` usa uma abreviação para "Repetir". Por esse motivo, usar abreviações tende a ser tolerada para um nível mais alto em F #-para-programação F #, mas ainda geralmente devem ser evitadas no design do componente público.

#### <a name="avoid-casing-name-collisions"></a>Evitar conflitos de nome de maiusculas e minúsculas

As diretrizes do .NET que se maiusculas e minúsculas sozinho não podem ser usado para resolver a ambiguidade conflitos de nome, pois alguns idiomas de cliente (por exemplo, o Visual Basic) diferenciam maiusculas de minúsculas.

#### <a name="use-acronyms-where-appropriate"></a>Use acrônimos quando apropriado

Acrônimos como XML não são abreviações e são amplamente usados em bibliotecas do .NET no formulário uncapitalized (Xml). Somente acrônimos bem conhecidos e amplamente reconhecidos devem ser usados.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Use PascalCase para nomes de parâmetro genérico

Use PascalCase para nomes de parâmetro genérico em APIs públicas, inclusive para F #-voltada para bibliotecas. Em particular, usar nomes como `T`, `U`, `T1`, `T2` para parâmetros genéricos arbitrários, e quando nomes específicos fazem sentido, em seguida, para F #-bibliotecas voltado para usam nomes como `Key`, `Value`, `Arg`(mas não por exemplo, `TKey`).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Use PascalCase ou camelCase para valores em F # módulos e funções públicas

camelCase é usado para funções públicas que são projetadas para serem usados não qualificado (por exemplo, `invalidArg`) e para as "funções de coleção padrão" (por exemplo, List.map). Ambos nesses casos, os nomes de função muito atuam como palavras-chave no idioma.

### <a name="object-type-and-module-design"></a>Design de objeto, o tipo e o módulo

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Use módulos ou namespaces para conter seus tipos e módulos

Cada arquivo de F # em um componente deve começar com uma declaração de namespace ou uma declaração de módulo.

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

ou

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

As diferenças entre usar módulos e namespaces para organizar o código no nível superior são da seguinte maneira:

* Namespaces pode abranger vários arquivos
* Namespaces não podem conter funções F #, a menos que eles estão dentro de um módulo interno
* O código de qualquer módulo especificado deve estar contido em um único arquivo
* Módulos de nível superior podem conter funções de F # sem a necessidade de um módulo interno

A escolha entre um namespace de nível superior ou o módulo afeta a forma compilada do código e, portanto, afetam o modo de exibição de outras linguagens .NET deve sua API, eventualmente, ser consumida fora do código F #.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Use os métodos e propriedades para operações intrínsecas para tipos de objeto

Ao trabalhar com objetos, é melhor certificar-se de que a funcionalidade consumível é implementada como métodos e propriedades no tipo.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

A maior parte da funcionalidade para um determinado membro não precisa necessariamente implementada em que o membro, mas o consumo essa funcionalidade deve estar.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Usar classes para encapsular estado mutável

Em F #, isso só precisa ser feito onde que estado já não é encapsulado por outra construção de linguagem, como um fechamento, expressão de sequência ou computação assíncrona.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Usar interfaces para agrupar operações relacionadas

Use tipos de interface para representar um conjunto de operações. Isso é preferível para outras opções, como registros de funções ou tuplas de funções.

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

Preferencialmente a:

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

Interfaces são conceitos de primeira classe do .NET, que você pode usar para obter o que Functors normalmente seria. Além disso, eles podem ser usados para codificar tipos existential em seu programa, que não é possível de registros de funções.

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>Usar um módulo para funções do grupo que atuam em coleções

Quando você define um tipo de coleção, considere fornecer um conjunto padrão de operações, como `CollectionType.map` e `CollectionType.iter`) para novos tipos de coleção.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Se você incluir esse um módulo, siga as convenções de nomenclatura padrão para funções encontradas em FSharp. Core.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Usar um módulo para funções de grupo para as funções comuns, canônicas, especialmente em matemática e bibliotecas DSL

Por exemplo, `Microsoft.FSharp.Core.Operators` é uma coleção automaticamente aberta de funções de nível superior (como `abs` e `sin`) fornecidas pelo FSharp.Core.dll.

Da mesma forma, uma biblioteca de estatísticas pode incluir um módulo com funções `erf` e `erfc`, em que esse módulo é projetado para ser explicitamente ou automaticamente aberto.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>Considere o uso de RequireQualifiedAccess e aplicar cuidadosamente AutoOpen atributos

Adicionando o `[<RequireQualifiedAccess>]` atributo para um módulo indica que o módulo não pode ser aberto e que as referências aos elementos do módulo exigem explícita qualificado acesso. Por exemplo, o `Microsoft.FSharp.Collections.List` módulo tem esse atributo.

Isso é útil quando funções e os valores no módulo têm nomes que possam entrar em conflito com nomes em outros módulos. Exigir acesso qualificado pode aumentar significativamente a facilidade de manutenção de longo prazo e evolvability de uma biblioteca.

Adicionando o `[<AutoOpen>]` atributo para um módulo significa que o módulo seja aberto quando o namespace que contém é aberto. O `[<AutoOpen>]` atributo também pode ser aplicado a um assembly para indicar um módulo que é aberto automaticamente quando o assembly é referenciado.

Por exemplo, uma biblioteca de estatísticas **MathsHeaven.Statistics** pode conter um `module MathsHeaven.Statistics.Operators` que contêm funções `erf` e `erfc`. É aconselhável marcar este módulo como `[<AutoOpen>]`. Isso significa `open MathsHeaven.Statistics` também abrir este módulo e colocar os nomes `erf` e `erfc` no escopo. Usa outro bom `[<AutoOpen>]` para módulos que contêm métodos de extensão.

Uso excessivo de `[<AutoOpen>]` leva a namespaces poluído e o atributo deve ser usada com cuidado. Para bibliotecas específicas em domínios específicos, uso criterioso de `[<AutoOpen>]` pode levar à melhor utilização.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>Considere definir membros de operador em classes em que é apropriado usar operadores conhecidos

Às vezes, as classes são usadas para construções de matemáticas como vetores de modelo. Quando o domínio que está sendo modelado tem operadores conhecidos, defini-los como membros intrínsecos para a classe é útil.

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Este guia corresponde a diretrizes gerais do .NET para esses tipos. No entanto, ele pode ser importante adicionalmente em F # de codificação, pois isso permite que esses tipos a serem usados em conjunto com as funções de F # e métodos com restrições de membro, como sumby.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Considere o uso de CompiledName para fornecer uma. Nome amigável do NET para outros consumidores de linguagem do .NET

Às vezes, talvez você queira atribuir um nome em um estilo para consumidores de F # (como um membro estático em letras minúsculas para que ele apareça como se fosse uma função associada de módulo), mas tem um estilo diferente para o nome quando ele é compilado em um assembly. Você pode usar o `[<CompiledName>]` atributo para fornecer um estilo diferente para F # não consumindo o assembly de código.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Usando `[<CompiledName>]`, você pode usar as convenções de nomenclatura do .NET para F # não consumidores do assembly.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Use a sobrecarga de método para funções de membro, se isso proporciona uma API simples

Sobrecarga de método é uma ferramenta poderosa para simplificar uma API que pode precisar executar uma funcionalidade semelhante, mas com diferentes opções ou argumentos.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

Em F #, é mais comum de sobrecarga no número de argumentos, em vez dos tipos de argumentos.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Ocultar as representações de registro e tipos de união, se o design desses tipos é mais provável de envolver

Evite revelar concretas representações de objetos. Por exemplo, a representação concreta de <xref:System.DateTime> valores não é revelado pela API externa, público do design da biblioteca do .NET. Em tempo de execução, o Common Language Runtime sabe a implementação de confirmado que será utilizada durante a execução. No entanto, código compilado não próprio acompanhar dependências na representação concreta.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Evite o uso de herança de implementação para extensibilidade

Herança de implementação raramente é usada em F #. Além disso, hierarquias de herança são geralmente complexos e difíceis de alterar quando chegarem novos requisitos. Implementação de herança ainda existe em F # para compatibilidade e raros casos em que é a melhor solução para um problema, mas técnicas alternativas a ser procuradas em seus programas F # ao criar para polimorfismo, como a implementação de interface.

### <a name="function-and-member-signatures"></a>Assinaturas de função e membro

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Use tuplas para valores de retorno ao retornar um número pequeno de vários valores relacionados

Aqui está um bom exemplo do uso de uma coleção de itens em um tipo de retorno:

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

Para retornar tipos que contém vários componentes, ou onde os componentes estiverem relacionados a uma única entidade de identificação, considere o uso de um tipo nomeado em vez de uma tupla.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Use `Async<T>` para programação assíncrona em limites de API do F #

Se houver uma operação síncrona correspondente chamada `Operation` que retorna um `T`, em seguida, a operação assíncrona deve ser nomeada `AsyncOperation` se ele retorna `Async<T>` ou `OperationAsync` se ele retorna `Task<T>`. Para tipos de .NET comumente usados que expõem métodos Begin/End, considere o uso `Async.FromBeginEnd` para gravar os métodos de extensão como uma fachada para fornecer o F # modelo de programação assíncrona para essas APIs .NET.

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>Exceções

As exceções são excepcionais no .NET; ou seja, eles não devem ocorrer com frequência em tempo de execução. Quando isso acontece, as informações que eles contêm serão valiosas. As exceções são um conceito de primeira classe do .NET; de núcleo IT, portanto, de maneira que apropriado aplicativo das exceções deve ser usadas como parte do design de interface de um componente.

#### <a name="follow-the-net-guidelines-for-exceptions"></a>Siga as diretrizes do .NET para exceções

O [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/exceptions.md) dar ótimo conselho sobre o uso de exceções no contexto de programação do .NET todos os. Algumas dessas diretrizes são as seguintes:

* Não use exceções para o fluxo normal de controle. Embora essa técnica é geralmente usada em idiomas como OCaml, ele é propensa a erros e pode ser ineficiente no .NET. Em vez disso, considere a possibilidade de retornar um `None` valor para indicar uma falha que é uma ocorrência comum ou esperada de opção.

* Documente as exceções lançadas por componentes do seu quando uma função é usada incorretamente.

* Sempre que possível, usar exceções existentes dos namespaces System. Evite <xref:System.ApplicationException>, embora.

* Não emitem <xref:System.Exception> quando ele um caractere de escape ao código do usuário. Isso inclui a evitar o uso de `failwith`, `failwithf`, que são funções úteis para uso em scripts e código em desenvolvimento, mas devem ser removido de código da biblioteca F # em favor lançando um tipo de exceção mais específico.

* Use `nullArg`, `invalidArg`, e `invalidOp` como o mecanismo para lançar <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, e <xref:System.InvalidOperationException> quando apropriado.

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a>Considere o uso de valores de opção para tipos de retorno quando a falha não é um cenário excepcional

A abordagem de .NET para exceções é que eles devem ser "excepcionais"; ou seja, eles devem ocorrer relativamente com pouca frequência. No entanto, algumas operações (por exemplo, uma tabela) podem falhar com frequência. Os valores de opção F # são uma maneira excelente para representar os tipos de retorno dessas operações. Essas operações convencionalmente começam com o prefixo de nome "try":

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a>Membros de extensão

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Aplicar cuidadosamente os membros de extensão F # em F #-a-F # componentes

Membros de extensão do F #, geralmente, só devem ser usados para operações que estão no fechamento das operações intrínsecos associadas a um tipo na maioria dos modos de uso. Um uso comum é fornecer APIs que são mais idiomática para F # para vários tipos de .NET:

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a>Tipos de união

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Use uniões discriminadas em vez de hierarquias de classe para dados estruturados em árvore

Estruturas de árvore são definidos recursivamente. Isso é complicado com herança, mas elegante com uniões discriminada.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Que representa dados de árvore com uniões discriminada também permite que você se beneficiar de exhaustiveness na correspondência de padrões.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Use `[<RequireQualifiedAccess>]` em tipos de união cujos nomes casos não forem suficientemente exclusivos

Você pode perceber que está em um domínio onde o mesmo nome é o melhor nome para coisas diferentes, como casos união discriminada. Você pode usar `[<RequireQualifiedAccess>]` para resolver a ambiguidade de nomes com maiusculas para evitar disparar erros confusos devido ao sombreamento dependentes a ordenação de `open` instruções

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Ocultar as representações de uniões discriminadas binário APIs compatível se o design desses tipos é mais provável de envolver

Tipos de uniões dependem de F # correspondência formulários para um modelo de programação sucinto. Conforme mencionado anteriormente, você deve evitar revelar representações de dados concretos se mais provável de envolver o design desses tipos.

Por exemplo, a representação de uma união discriminada pode ser ocultada usando uma declaração privada ou interna, ou usando um arquivo de assinatura.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Se você revelar uniões discriminadas modo indiscriminado, talvez seja difícil versão sua biblioteca sem quebrar o código do usuário. Em vez disso, considere a possibilidade de revelar um ou mais padrões ativos para permitir correspondência sobre os valores do seu tipo de padrão.

Padrões ativos fornecem uma maneira alternativa para oferecer aos consumidores de F # padrão de correspondência, evitando a exposição de tipos de união F # diretamente.

### <a name="inline-functions-and-member-constraints"></a>Funções embutidas e restrições de membro

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Definir genéricos algoritmos numéricos usando funções embutidas com restrições de membro implícito e tipos genéricos resolvidos estaticamente

Membro aritmético restrições e F # comparação são um padrão de programação F #. Por exemplo, considere o seguinte código:

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

O tipo dessa função é como segue:

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

Essa é uma função adequada para uma API pública em uma biblioteca de matemática.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Evite usar restrições de membro para simular classes de tipo e digitação pato

É possível simular "Jantar digitando" usando as restrições de membro F #. No entanto, os membros que usam esse geral não deve ser usada em F #-para-designs de biblioteca F #. Isso ocorre porque os designs de biblioteca com base em restrições implícita desconhecidas ou não-padrão tendem a fazer com que o código do usuário se tornar inflexíveis e associado ao padrão de uma estrutura específica.

Além disso, há uma boa chance de uso intenso de restrições de membro dessa maneira pode resultar em tempo de compilação muito longo.

### <a name="operator-definitions"></a>Definições de operador

#### <a name="avoid-defining-custom-symbolic-operators"></a>Evite definir operadores simbólicos personalizados

Operadores personalizados são essenciais em algumas situações e altamente útil dispositivos notação dentro de um corpo grande do código de implementação. Para novos usuários de uma biblioteca, denominado funções geralmente são mais fáceis de usar. Além disso, operadores simbólicos personalizados podem ser difíceis de documento e os usuários encontram mais difícil procurar ajuda sobre operadores, devido a limitações existentes nos mecanismos IDE e pesquisa.

Como resultado, é melhor publicar sua funcionalidade como funções nomeadas e membros e Além disso expor operadores para essa funcionalidade somente se os benefícios de notação superam a documentação e o custo cognitivo de tê-los.

### <a name="units-of-measure"></a>Unidades de medida

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Cuidadosamente usar unidades de medida de segurança de tipo adicionados no código F #

Informações adicionais de digitação para as unidades de medida são apagadas quando vistos por outras linguagens .NET. Lembre-se de reflexão, ferramentas e componentes do .NET Consulte tipos sans unidades. Por exemplo, verá c# consumidores `float` em vez de `float<kg>`.

### <a name="type-abbreviations"></a>Abreviações de tipo

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Use com cuidado abreviações de tipo para simplificar o código F #

Reflexão, ferramentas e componentes do .NET não verá nomes abreviados de tipos. Uso significativo de abreviações de tipo também pode fazer um domínio aparecem mais complicado do que na verdade é, que pode confundir os consumidores.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Evite abreviações de tipo para os tipos públicos cujos membros e propriedades devem ser intrinsecamente diferentes daqueles disponível no tipo sendo abreviado

Nesse caso, o tipo sendo abreviado revela muito sobre a representação do tipo real que está sendo definido. Em vez disso, considere a abreviação em um tipo de classe ou uma união discriminada único caso de encapsulamento (ou, quando o desempenho é essencial, considere o uso de um tipo struct para encapsular a abreviação).

Por exemplo, é tentador para definir um multi-mapa de como um caso especial de um mapa de F #, por exemplo:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

No entanto, as operações lógicas de notação de ponto neste tipo não são as mesmas operações em um mapa — por exemplo, é razoável de que o operador de pesquisa do mapa. [chave] retornar uma lista vazia se a chave não estiver no dicionário, em vez de gerar uma exceção.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Diretrizes para bibliotecas para uso em outras linguagens .NET

Durante a criação de bibliotecas para uso em outras linguagens .NET, é importante seguir o [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/index.md). Neste documento, essas bibliotecas são rotuladas como baunilha bibliotecas .NET, em vez de F #-voltada para bibliotecas que usam F # constrói sem restrição. Criar bibliotecas do .NET baunilha significa fornecendo familiar e idiomática APIs consistentes com o restante do .NET Framework, reduzindo o uso da linguagem F #-construções específicas na API pública. As regras são explicadas nas seções a seguir.

### <a name="namespace-and-type-sesign-for-libraries-for-use-from-other-net-languages"></a>Namespace e tipo sesign (para bibliotecas para uso em outras linguagens .NET)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Aplicar as convenções de nomenclatura do .NET para a API pública de seus componentes

Preste atenção especial para o uso de nomes abreviados e as diretrizes de capitalização do .NET.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Usar namespaces, tipos e membros como a estrutura organizacional primária para os componentes

Todos os arquivos que contém a funcionalidade de pública devem começar com um `namespace` declaração e as entidades públicos somente namespaces devem ser tipos. Não use os módulos de F #.

Use os módulos de não-públicos para manter o código de implementação, utilitário tipos e funções de utilitário.

Tipos estáticos devem ser preferidos nos módulos, já que permitem futura evolução da API para usar a sobrecarga e outros conceitos de design API .NET que não podem ser usados dentro de módulos do F #.

Por exemplo, em vez da API pública do seguinte:

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

Em vez disso, considere:

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Use os tipos de registro F # baunilha APIs .NET se o design dos tipos não evoluir

Tipos de registro F # compilados para uma classe simples do .NET. Eles são adequados para alguns tipos simples e estáveis nas APIs. Você deve considerar o uso de `[<NoEquality>]` e `[<NoComparison>]` atributos para suprimir a geração automática de interfaces. Além disso, evite usar campos de registro mutável em baunilha APIs .NET como esses expõe um campo público. Sempre considere se uma classe seria fornecem uma opção mais flexível para futuras evolução da API.

Por exemplo, o seguinte código F # expõe a API pública de um consumidor do c#:

F #:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

C#:

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Ocultar a representação de tipos de união F # em baunilha APIs do .NET

Tipos de união F # não são normalmente usados nos limites do componente, mesmo para F #-a-F # codificação. Eles são um dispositivo de implementação excelente quando usado internamente no bibliotecas e componentes.

Durante a criação de uma API .NET baunilha, considere a possibilidade de ocultar a representação de um tipo de união, usando uma declaração privada ou um arquivo de assinatura.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Você também poderá aumentar tipos que usam uma representação de união internamente com membros para fornecer um desejado. API de voltado para a rede.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Design de interface gráfica do usuário e outros componentes usando os padrões de design do framework

Há muitas estruturas diferentes no .NET, como WinForms, WPF e ASP.NET. Convenções de nomenclatura e design para cada um devem ser usadas se você estiver criando componentes para uso nessas estruturas. Por exemplo, para WPF de programação, adote padrões de design do WPF para as classes que você está criando. Para modelos de programação de interface do usuário, use padrões de design, como eventos e baseada em notificação coleções, como aqueles encontrados em <xref:System.Collections.ObjectModel>.

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Design de objeto e o membro (para bibliotecas para uso em outras linguagens .NET)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>Use o atributo CLIEvent para expor os eventos do .NET

Construir um `DelegateEvent` com .NET específica de tipo que utiliza um objeto delegado e `EventArgs` (em vez de um `Event`, que usa apenas o `FSharpHandler` tipo por padrão) para que os eventos são publicados na maneira familiar de outras linguagens .NET.

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>Expor operações assíncronas como métodos que retornam tarefas do .NET

Tarefas são usadas em .NET para representar active computações assíncronas. Tarefas são em geral composicional menor que F # `Async<T>` objetos, uma vez que representam tarefas "já em execução" e não podem ser compostos juntas de maneiras que realizar a composição de paralela, ou que ocultar a propagação de sinais de cancelamento e outros parâmetros de contextuais.

No entanto, apesar de isso, os métodos que retornam tarefas são a representação padrão de programação assíncrona em .NET.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Você vai frequentemente também deseja aceitar um token de cancelamento explícita:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>Usar tipos de delegado do .NET em vez de tipos de função do F #

Aqui "tipos de função F #" significam "direção" tipos como `int -> int`.

Em vez de isso:

```fsharp
member this.Transform(f:int->int) =
    ...
```

Faça o seguinte:

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

O tipo de função do F # aparece como `class FSharpFunc<T,U>` a outras linguagens .NET e é menos adequada para recursos de linguagem e ferramentas que entender os tipos de delegado. Ao criar um método de ordem superior direcionamento do .NET Framework 3.5 ou superior, o `System.Func` e `System.Action` delegados são as APIs do direito para publicar para permitir que os desenvolvedores de .NET consumir essas APIs de uma maneira de baixa fricção. (Durante o direcionamento do .NET Framework 2.0, os tipos de delegado definido pelo sistema são mais limitados; considere o uso de tipos de delegado predefinidos, como `System.Converter<T,U>` ou definição de um tipo específico de delegado.)

Por outro lado, os delegados do .NET não são naturais para F #-voltada para bibliotecas (consulte a próxima seção em F #-voltada para bibliotecas). Como resultado, uma estratégia de implementação comum ao desenvolver métodos de ordem superior para bibliotecas do .NET baunilha é criar todas a implementação usando tipos de função do F # e, em seguida, crie a API pública usando delegados como uma fachada thin sobre F # real implementação.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>Use o padrão de TryGetValue em vez de retornar valores de opção de F # e prefere a sobrecarga de método para colocar valores de opção F # como argumentos

Padrões comuns de uso para o tipo de opção F # em APIs são melhores implementado em baunilha APIs do .NET usando .NET padrão técnicas de design. Em vez de retornar um valor de opção F #, considere usar o tipo de retorno booleano mais de um parâmetro de saída como o padrão "TryGetValue". E, em vez de usar valores de opção F # como parâmetros, considere usar a sobrecarga de método ou argumentos opcionais.

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>Use a interface de coleção do .NET tipos IEnumerable\<T\> e IDictionary\<chave, valor\> para parâmetros e valores de retorno

Evite o uso de tipos de coleção concretos, como matrizes de .NET `T[]`, tipos F # `list<T>`, `Map<Key,Value>` e `Set<T>`, e tipos de coleção concreta do .NET, como `Dictionary<Key,Value>`. As diretrizes de Design de biblioteca .NET ter conselhos sobre quando usar vários tipos de coleção como `IEnumerable<T>`. Uso de matrizes (`T[]`) é aceitável em algumas circunstâncias, em para terrenos de desempenho. Observe especialmente que `seq<T>` é apenas o F # alias para `IEnumerable<T>`, e, portanto, seq geralmente é um tipo apropriado para uma API .NET baunilha.

Em vez de F # listas:

```fsharp
member this.PrintNames(names : string list) =
    ...
```

Use sequências de F #:

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Use o tipo de unidade como o único tipo de entrada de um método para definir um método de argumento de zero ou como o único tipo para definir um método de retorno de void de retorno

Evite a outros usos do tipo de unidade. Essas são boas:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

Isso é inválido:

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Verificar valores nulos em limites de API .NET baunilha

Código de implementação do F # tende a ter menos valores nulos, devido a restrições no uso de literais nulas para tipos F # e padrões de design imutável. Outras linguagens .NET geralmente usam nulo como um valor muito mais frequentemente. Por isso, código F #, que é expor uma API .NET baunilha deve verificar parâmetros de null no limite da API e impedir que esses valores que fluem mais profundo para o código de implementação do F #. O `isNull` função ou padrões coincidentes no `null` padrão pode ser usado.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Evite usar tuplas como valores de retorno

Em vez disso, preferir retornando um tipo nomeado, mantendo os dados de agregação, ou usando os parâmetros de saída para retornar vários valores. Embora tuplas e struct tuplas existam no .NET (incluindo suporte a linguagem c# para tuplas de struct), eles geralmente não fornecerá a API ideal e esperada para desenvolvedores do .NET.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Evite o uso de currying de parâmetros

Em vez disso, use o .NET convenções de chamada ``Method(arg1,arg2,…,argN)``.

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

Dica: Se você estiver criando bibliotecas para uso em qualquer linguagem .NET, em seguida, há nenhum substituto para realmente fazer algumas experimental c# e Visual Basic de programação para garantir que suas bibliotecas "funcionalidade à direita" desses idiomas. Você também pode usar ferramentas como o .NET Reflector e o Pesquisador de objeto do Visual Studio para garantir que os documentos e bibliotecas aparecem conforme o esperado para os desenvolvedores.

## <a name="appendix"></a>Anexo

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Exemplo de ponta a ponta da criação de código F # para uso por outras linguagens .NET

Considere a seguinte classe:

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

O tipo F # deduzido dessa classe é o seguinte:

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

Vamos dar uma olhada em como esse tipo de F # é exibido para um programador usando outra linguagem .NET. Por exemplo, aproximado c# "assinatura" é o seguinte:

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

Há alguns pontos importantes a serem observados sobre como F # representa construções aqui. Por exemplo:

* Metadados, como nomes de argumento foi preservado.

* F # métodos que usam dois argumentos se tornar c# métodos que usam dois argumentos.

* Funções e listas se tornam as referências aos tipos correspondentes na biblioteca F #.

O código a seguir mostra como ajustar esse código para fazer essas coisas em conta.

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

O tipo F # inferido do código é o seguinte:

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

A assinatura c# agora é o seguinte:

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

As correções feitas preparar esse tipo para uso como parte de uma biblioteca .NET baunilha são da seguinte maneira:

* Ajustado vários nomes: `Point1`, `n`, `l`, e `f` tornou-se `RadialPoint`, `count`, `factor`, e `transform`, respectivamente.

* Usado um tipo de retorno `seq<RadialPoint>` em vez de `RadialPoint list` alterando uma construção de lista usando `[ ... ]` para uma construção de sequência usando `IEnumerable<RadialPoint>`.

* Usar o tipo de delegado .NET `System.Func` em vez de um tipo de função do F #.

Isso facilita muito melhor consumir o código c#.
