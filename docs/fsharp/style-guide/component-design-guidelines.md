---
title: F#diretrizes de design do componente
description: Saiba as diretrizes para gravação F# componentes destinadas ao consumo por outros chamadores.
ms.date: 05/14/2018
ms.openlocfilehash: c61e4cd9098388b356c71c325d66c760fa866cf0
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066019"
---
# <a name="f-component-design-guidelines"></a>F#diretrizes de design do componente

Este documento é um conjunto de diretrizes de design do componente para F# de programação, com base no F# diretrizes de Design do componente, v14, Microsoft Research, e [outra versão](https://fsharp.org/specs/component-design-guidelines/) originalmente coletados e mantidos pelo F# Software Foundation.

Este documento pressupõe que você esteja familiarizado com F# de programação. Muitos agradecimentos para os F# comunidade por suas contribuições e comentários úteis em diversas versões deste guia.

## <a name="overview"></a>Visão geral

Este documento aborda alguns dos problemas relacionados ao F# componente design e codificação. Um componente pode significar qualquer um dos seguintes:

* Uma camada em seu F# projeto que tem os consumidores externos dentro desse projeto.
* Uma biblioteca destinada ao consumo por F# código em limites de assembly.
* Uma biblioteca destinada ao consumo por qualquer linguagem .NET em limites de assembly.
* Uma biblioteca destinada para distribuição por meio de um repositório de pacotes, tais como [NuGet](https://nuget.org).

Técnicas descritas neste artigo seguem o [cinco princípios bom F# código](index.md#five-principles-of-good-f-code)e, portanto, utilizar ambos funcional e objeto de programação conforme apropriado.

Independentemente da metodologia, o designer de componente e a biblioteca de faces de inúmeros problemas práticos e prosaicas ao tentar criar uma API que pode ser usada com mais facilidade pelos desenvolvedores. Aplicativo tem consciência do [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/index.md) conduzam para a criação de um conjunto consistente de APIs que são agradáveis consumir.

## <a name="general-guidelines"></a>Diretrizes gerais

Há algumas diretrizes universais que se aplicam a F# bibliotecas, independentemente do público-alvo para a biblioteca.

### <a name="learn-the-net-library-design-guidelines"></a>Saiba as diretrizes de Design de biblioteca do .NET

Independentemente do tipo de F# de codificação que está fazendo, é importante ter um conhecimento prático do [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/index.md). A maioria dos outros F# e os programadores do .NET estar familiarizado com essas diretrizes e esperar que o código .NET em conformidade com a eles.

Diretrizes de Design da biblioteca do .NET fornecem diretrizes gerais sobre nomenclatura, projetando classes e interfaces, design de membro (propriedades, métodos, eventos, etc.) e muito mais e são um útil primeiro ponto de referência para uma variedade de diretrizes de design.

### <a name="add-xml-documentation-comments-to-your-code"></a>Adicionar comentários de documentação XML ao seu código

Documentação XML nas APIs públicas Certifique-se de que os usuários podem obter excelente Intellisense e em Informaçãorápida, ao usar esses tipos e membros e habilitar compilar documentação arquivos para a biblioteca. Consulte a [documentação XML](../language-reference/xml-documentation.md) sobre várias marcas xml que podem ser usadas para marcação adicional dentro de comentários xmldoc.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

Você pode usar os comentários XML de forma abreviada (`/// comment`), ou comentários XML padrão (`///<summary>comment</summary>`).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Considere o uso de arquivos de assinatura explícita (. FSI) para a biblioteca estável e APIs de componente

Usando arquivos de assinaturas explícita em uma F# biblioteca fornece um resumo sucinto do API pública, que ajuda a garantir que você saiba público completo superfície da sua biblioteca fornece uma separação clara entre a documentação do pública e interno detalhes de implementação. Observe que os arquivos de assinatura adicione atrito para alterar a API pública, exigindo que alterações sejam feitas em arquivos de implementação e a assinatura. Como resultado, arquivos de assinatura devem normalmente ser introduzidos somente quando uma API se tornam solidificou e não deve ser alterado significativamente.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Sempre siga práticas recomendadas para usar cadeias de caracteres no .NET

Siga [práticas recomendadas para usar cadeias de caracteres no .NET](../../standard/base-types/best-practices-strings.md) diretrizes. Em particular, sempre especificar claramente *intenção cultura* na conversão e comparação de cadeias de caracteres (quando aplicável).

## <a name="guidelines-for-f-facing-libraries"></a>Diretrizes para F#-voltado para a bibliotecas

Esta seção apresenta recomendações para o desenvolvimento público F#-voltado para a bibliotecas; ou seja, as bibliotecas expondo as APIs públicas que se destinam a serem consumidos por F# os desenvolvedores. Há uma variedade de recomendações de design de bibliotecas aplicáveis especificamente ao F#. Na ausência das recomendações específicas que seguem, as diretrizes de Design de biblioteca do .NET são as diretrizes de fallback.

### <a name="naming-conventions"></a>Convenções de nomenclatura

#### <a name="use-net-naming-and-capitalization-conventions"></a>Usar convenções de nomenclatura e capitalização do .NET

A tabela a seguir segue as convenções de nomenclatura e capitalização do .NET. Há adições pequenas para incluir também as F# constrói.

| Constructo | Caso | Parte | Exemplos | Observações |
|-----------|------|------|----------|-------|
| Tipos concretos | PascalCase | Substantivo / adjetivas | Lista, Double, complexo | Tipos concretos são estruturas, classes, enumerações, delegados, registros e uniões. Embora os nomes de tipo são tradicionalmente minúsculos no OCaml, F# adotou o esquema de nomenclatura do .NET para tipos.
| DLLs           | PascalCase |                 | Fabrikam.Core.dll |  |
| Marcas de união     | PascalCase | Substantivo | Alguns, adicionar, sucesso | Não use um prefixo em APIs públicas. Opcionalmente, use um prefixo ao internos, como `Digite equipes = TAlpha | TBeta | TDelta.` |
| evento          | PascalCase | Verbo | ValueChanged / ValueChanging |  |
| Exceções     | PascalCase |      | WebException | Nome deve terminar com "Exception". |
| Campo          | PascalCase | Substantivo | CurrentName  | |
| Tipos de interface |  PascalCase | Substantivo / adjetivas | IDisposable | Nome deve começar com "I". |
| Método |  PascalCase |  Verbo | ToString | |
| Namespace | PascalCase | | Microsoft.FSharp.Core | Geralmente usam `<Organization>.<Technology>[.<Subnamespace>]`, porém descartar a organização se a tecnologia é independente da organização. |
| Parâmetros | camelCase | Substantivo |  typeName, transform, range | |
| permitir que os valores (internos) | camelCase ou PascalCase | Substantivo / verbo |  getValue, myTable |
| permitir que os valores (externo) | camelCase ou PascalCase | Substantivo/verbo  | List. map, Dates.Today | valores de associação let costumam ser públicos ao seguir padrões de design funcional tradicional. No entanto, geralmente use PascalCase quando o identificador pode ser usado em outras linguagens .NET. |
| Propriedade  | PascalCase  | Substantivo / adjetivas  | IsEndOfFile, BackColor  | Propriedades booleanas geralmente uso é e pode e deve ser afirmativa, como no IsEndOfFile, não IsNotEndOfFile.

#### <a name="avoid-abbreviations"></a>Evite abreviações

As diretrizes do .NET não recomendamos o uso de abreviações de (por exemplo, "usar `OnButtonClick` em vez de `OnBtnClick`"). Abreviações comuns, tais como `Async` "Asynchronous", são tolerados. Essa diretriz, às vezes, é ignorado para programação funcional; Por exemplo, `List.iter` usa uma abreviação de "iterar". Por esse motivo, usando abreviações tende a ser tolerada para um nível mais alto no F#- para -F# de programação, mas ainda geralmente deve ser evitado no design do componente público.

#### <a name="avoid-casing-name-collisions"></a>Evitar colisões de nome de uso de maiusculas

As diretrizes do .NET dizem que a maiusculas e minúsculas sozinho não podem ser usado para resolver a ambiguidade de colisões de nome, já que alguns idiomas de cliente (por exemplo, o Visual Basic) diferenciam maiusculas de minúsculas.

#### <a name="use-acronyms-where-appropriate"></a>Usar acrônimos quando apropriado

Acrônimos como XML não são abreviações e são amplamente usados nas bibliotecas do .NET no formulário uncapitalized (Xml). Somente acrônimos amplamente reconhecidos, bem conhecidos, devem ser usados.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Usar PascalCase para nomes de parâmetro genérico

Usar PascalCase para nomes de parâmetro genérico em APIs públicas, incluindo para F#-voltado para a bibliotecas. Em particular, usar nomes como `T`, `U`, `T1`, `T2` para parâmetros genéricos arbitrários e quando os nomes específicos fazem sentido, em seguida, F#-bibliotecas voltado para usam nomes como `Key`, `Value`, `Arg` (mas não, por exemplo, `TKey`).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Usar PascalCase ou camelCase para funções públicas e valores em F# módulos

camelCase é usado para funções públicas que são projetadas para ser usado não-qualificados (por exemplo, `invalidArg`) e para as "funções de coleção padrão" (por exemplo, List. Map). Em ambos os casos, os nomes de função muito atuam como palavras-chave na linguagem.

### <a name="object-type-and-module-design"></a>Design de objeto, o tipo e o módulo

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Use módulos ou namespaces para conter seus tipos e módulos

Cada F# arquivo em um componente deve começar com uma declaração de namespace ou uma declaração de módulo.

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

As diferenças entre o uso de módulos e namespaces para organizar o código no nível superior são da seguinte maneira:

* Namespaces pode abranger vários arquivos
* Namespaces não podem conter F# , a menos que eles estejam dentro de um módulo interno de funções
* O código de qualquer módulo fornecido deve estar contido em um único arquivo
* Módulos de nível superior podem conter F# funções sem a necessidade de um módulo interno

A escolha entre um namespace de nível superior ou um módulo afeta a forma compilada do código e, portanto, afetam o modo de exibição de outras linguagens .NET deve sua API, eventualmente, ser consumida fora do F# código.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Usar métodos e propriedades para operações intrínsecas para tipos de objeto

Ao trabalhar com objetos, é melhor garantir que a funcionalidade consumível seja implementada como métodos e propriedades no tipo.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

A maior parte da funcionalidade para um determinado membro necessariamente não precisa ser implementada em que o membro, mas a parte consumível parte dessa funcionalidade deve ser.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Use as classes para encapsular o estado mutável

No F#, isso só precisa ser feito onde que estado já não estiver encapsulado por outra construção de linguagem, como um fechamento, uma expressão de sequência ou uma computação assíncrona.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Usar interfaces para agrupar operações relacionadas

Use tipos de interface para representar um conjunto de operações. Isso é preferível para outras opções, como as tuplas de funções ou registros de funções.

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

Preferencialmente a:

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

As interfaces são conceitos de primeira classe no .NET, que pode ser usado para alcançar o que Functors normalmente oferecerá a você. Além disso, eles podem ser usados para codificar tipos existenciais em seu programa, que não é possível de registros de funções.

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>Usar um módulo para o grupo de funções que atuam em coleções

Quando você define um tipo de coleção, recomenda-se de fornecer um conjunto padrão de operações, como `CollectionType.map` e `CollectionType.iter`) para novos tipos de coleção.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Se você incluir um módulo desse tipo, siga as convenções de nomenclatura padrão para funções encontradas no FSharp. Core.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Usar um módulo para funções do grupo para funções comuns, canonical, especialmente em matemática e bibliotecas DSL

Por exemplo, `Microsoft.FSharp.Core.Operators` é uma coleção automaticamente aberta de funções de nível superior (como `abs` e `sin`) fornecida pelo FSharp.

Da mesma forma, uma biblioteca de estatísticas pode incluir um módulo com funções `erf` e `erfc`, em que esse módulo é projetado para ser aberto de forma explícita ou automaticamente.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>Considere o uso de RequireQualifiedAccess e aplicar cuidadosamente os atributos de AutoOpen

Adicionando o `[<RequireQualifiedAccess>]` atributo a um módulo indica que o módulo não pode ser aberto e que as referências aos elementos do módulo exigem explícita qualificados acesso. Por exemplo, o `Microsoft.FSharp.Collections.List` módulo tem esse atributo.

Isso é útil quando funções e valores no módulo têm nomes que têm probabilidade de entrar em conflito com nomes em outros módulos. Exigir acesso qualificado pode aumentar muito a manutenção de longo prazo e a capacidade de evolução de uma biblioteca.

Adicionando o `[<AutoOpen>]` atributo a um módulo significa que o módulo será aberto quando o namespace que a contém é aberto. O `[<AutoOpen>]` atributo também pode ser aplicado a um assembly para indicar um módulo que é aberto automaticamente quando o assembly for referenciado.

Por exemplo, uma biblioteca de estatísticas **MathsHeaven.Statistics** pode conter um `module MathsHeaven.Statistics.Operators` que contêm funções `erf` e `erfc`. É razoável marcar este módulo como `[<AutoOpen>]`. Isso significa `open MathsHeaven.Statistics` também abrirá esse módulo e colocar os nomes `erf` e `erfc` dentro do escopo. Outro bom uso de `[<AutoOpen>]` é para módulos que contêm métodos de extensão.

Uso excessivo de `[<AutoOpen>]` leva a poluído namespaces e o atributo deve ser usada com cuidado. Para bibliotecas específicas em domínios específicos, uso criterioso de `[<AutoOpen>]` pode levar a melhor usabilidade.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>Considere definir membros de operador em classes em que é apropriado usar operadores conhecidos

Às vezes, as classes são usadas para construções de matemáticas como vetores de modelo. Quando o domínio que está sendo modelado tem operadores conhecidos, defini-los como membros intrínsecos para a classe é útil.

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Essa orientação corresponde a diretrizes gerais do .NET para esses tipos. No entanto, ele pode ser adicionalmente importante em F# de codificação, pois isso permite que esses tipos a ser usado em conjunto com F# funções e métodos com restrições de membro, como List. sumby.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Considere o uso de CompiledName para fornecer um. Nome amigável para o NET para outros consumidores de linguagem do .NET

Às vezes, talvez você queira atribuir um nome em um estilo para o F# consumidores (como um membro estático em minúsculas de modo que ele apareça como se fosse uma função associada de módulo), mas tem um estilo diferente para o nome quando ele é compilado em um assembly. Você pode usar o `[<CompiledName>]` atributo para fornecer um estilo diferente para não F# código que consome o assembly.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Usando `[<CompiledName>]`, você pode usar as convenções de nomenclatura do .NET para não F# consumidores do assembly.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Use a sobrecarga de método para funções de membro, se isso proporciona uma API mais simples

Sobrecarga de método é uma ferramenta poderosa para simplificar uma API que talvez seja necessário executar uma funcionalidade semelhante, mas com argumentos ou opções diferentes.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

No F#, é mais comum de sobrecarga em número de argumentos em vez de tipos de argumentos.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Ocultar as representações de registro e os tipos de união, se o design desses tipos é provavelmente a evoluir

Evite revelar concretas representações de objetos. Por exemplo, a representação concreta do <xref:System.DateTime> valores não serão revelados pela API externa, público do design da biblioteca do .NET. Em tempo de execução, o Common Language Runtime sabe a implementação de confirmado que será usada em toda a execução. No entanto, código compilado não próprio acompanhar dependências na representação concreta.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Evite o uso de herança de implementação para extensibilidade

No F#, herança de implementação é raramente usada. Além disso, hierarquias de herança costumam ser complexos e difíceis de alterar a chegada de novos requisitos. Implementação da herança ainda existe no F# para compatibilidade e raros casos em que é a melhor solução para um problema, mas devem ser procuradas técnicas alternativas no seu F# ao projetar para polimorfismo, como a interface de programas implementação.

### <a name="function-and-member-signatures"></a>Assinaturas de função e membro

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Usar tuplas para valores de retorno ao retornar um número pequeno de vários valores não relacionados

Eis um bom exemplo de como usar uma tupla em um tipo de retorno:

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

Para retornar os tipos que contém vários componentes ou onde os componentes estão relacionados a uma única entidade identificável, considere o uso de um tipo nomeado, em vez de uma tupla.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Use `Async<T>` para assíncrono de programação em F# limites de API

Se há uma operação síncrona correspondente denominada `Operation` que retorna um `T`, em seguida, a operação assíncrona deve ser nomeada `AsyncOperation` se ele retornar `Async<T>` ou `OperationAsync` se ele retornar `Task<T>`. Para tipos .NET comumente usados que expõem métodos Begin/End, considere o uso `Async.FromBeginEnd` escrever métodos de extensão como uma fachada para fornecer a F# modelo de programação assíncrona para as APIs do .NET.

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>Exceções

Ver [gerenciamento de erro](conventions.md#error-management) para saber mais sobre o uso apropriado de exceções, resultados e opções.

### <a name="extension-members"></a>Membros de extensão

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Aplicar cuidadosamente F# membros de extensão em F#- para -F# componentes

F#membros de extensão, geralmente, só devem ser usados para operações que estão no fechamento de operações intrínseco associado ao tipo na maioria dos seus modos de uso. Um uso comum é fornecer APIs que são mais expressões idiomáticas para F# para vários tipos de .NET:

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

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Use as uniões discriminadas em vez de hierarquias de classe para dados estruturados em árvore

Estruturas de árvore são definida de forma recursiva. Isso é estranho com herança, mas elegante com uniões discriminadas.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Que representa dados de árvore com uniões discriminadas também permite que você se beneficie dos exhaustiveness na correspondência de padrão.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Use `[<RequireQualifiedAccess>]` em tipos de união cujos nomes com maiusculas não são suficientemente exclusivos

Você pode encontrar em um domínio em que o mesmo nome é o nome melhor para coisas diferentes, como casos de união discriminada. Você pode usar `[<RequireQualifiedAccess>]` para resolver a ambiguidade de nomes com maiusculas para evitar disparar erros confusos devido ao sombreamento dependentes a ordenação de `open` instruções

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Ocultar as representações de uniões discriminadas binário APIs compatíveis, se o design desses tipos é provavelmente a evoluir

Tipos de uniões dependem da F# formulários de correspondência para um modelo de programação sucinto. Conforme mencionado anteriormente, você deve evitar revelar representações de dados concretos se o design desses tipos é provavelmente a evoluir.

Por exemplo, a representação de uma união discriminada pode ficar oculto usando uma declaração privada ou interna, ou usando um arquivo de assinatura.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Se você revelar as uniões discriminadas indiscriminadamente, talvez seja difícil versão sua biblioteca sem quebrar o código do usuário. Em vez disso, considere a possibilidade de revelar um ou mais padrões de Active Directory para permitir que a correspondência de valores do seu tipo.

Padrões de Active Directory fornecem uma maneira alternativa para fornecer F# consumidores com correspondência de padrões, evitando a exposição de F# diretamente os tipos de união.

### <a name="inline-functions-and-member-constraints"></a>Funções embutidas e restrições de membro

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Definir os algoritmos genéricos numéricos, usando as funções embutidas com restrições de membro implícito e tipos genéricos estaticamente resolvidos

Restrições de aritmética de membro e F# restrições de comparação são um padrão para F# de programação. Por exemplo, considere o seguinte código:

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

O tipo dessa função é da seguinte maneira:

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

Essa é uma função adequada para uma API pública em uma biblioteca de matemática.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Evite usar restrições de membro para simular classes de tipo e a digitação pato

É possível simular "tipagem pato" usando F# restrições de membro. No entanto, os membros que fazem usam dessa não está em geral deve ser usado em F#- para -F# projetos de biblioteca. Isso ocorre porque os designs de biblioteca com base nas restrições implícitas desconhecidas ou não-padrão tendem a fazer com que o código de usuário para se tornar inflexíveis e são associados ao padrão de uma determinada estrutura.

Além disso, há uma boa chance de que o uso intenso de restrições de membro dessa maneira pode resultar em tempos de compilação muito longos.

### <a name="operator-definitions"></a>Definições de operador

#### <a name="avoid-defining-custom-symbolic-operators"></a>Evite definir operadores simbólicos personalizados

Operadores personalizados são essenciais em algumas situações e são altamente úteis dispositivos da notação dentro de uma grande quantidade de código de implementação. Para novos usuários de uma biblioteca, geralmente são mais fáceis de usar funções nomeadas. Além disso, operadores simbólicos personalizados podem ser difíceis de documento e usuários acham mais difícil pesquisar a Ajuda em operadores, devido a limitações existentes no IDE, mecanismos de pesquisa.

Como resultado, é melhor publicar sua funcionalidade como funções nomeadas e membros e Além disso, expor operadores para essa funcionalidade somente se os benefícios da notação superam a documentação e cognitivo custo de tê-los.

### <a name="units-of-measure"></a>Unidades de medida

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Cuidadosamente, usar unidades de medida para a segurança de tipo adicionado no F# código

Informações adicionais de digitação para unidades de medida são apagadas quando visualizado por outras linguagens .NET. Lembre-se de que a reflexão, ferramentas e componentes do .NET verá tipos sans unidades. Por exemplo, verá os consumidores de c# `float` em vez de `float<kg>`.

### <a name="type-abbreviations"></a>Abreviações de tipo

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Usar cuidadosamente as abreviações de tipo para simplificar o F# código

Reflexão, ferramentas e componentes do .NET não verá os nomes abreviados para tipos. Uso significativo de abreviações de tipo também pode fazer um domínio aparecem mais complicado do que realmente é, que poderia confundir os consumidores.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Evite abreviações de tipo para tipos públicos cujos membros e propriedades devem ser intrinsecamente diferentes daqueles disponíveis no tipo que está sendo abreviado

Nesse caso, o tipo que está sendo abreviado revela muito sobre a representação do tipo real que está sendo definido. Em vez disso, considere o encapsulamento a abreviação em um tipo de classe ou uma união discriminada de caso único (ou, quando o desempenho é essencial, considere o uso de um tipo de struct para encapsular a abreviação).

Por exemplo, é tentador para definir um mapa com vários como um caso especial de um F# mapear, por exemplo:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

No entanto, as operações lógicas de notação de ponto nesse tipo não são o mesmo que as operações em um mapa – por exemplo, é razoável de que o operador de pesquisa de mapa. uma lista vazia se a chave não estiver no dicionário, em vez de gerar uma exceção de retorno [chave].

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Diretrizes para as bibliotecas de uso de outras linguagens .NET

Durante a criação de bibliotecas para uso de outras linguagens .NET, é importante aderir à [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/index.md). Neste documento, essas bibliotecas são rotuladas como baunilha bibliotecas do .NET, em vez de F#-voltado para a bibliotecas que usam F# constrói sem restrição. Criar bibliotecas .NET de baunilha significa fornecendo familiar e expressões idiomáticas APIs consistentes com o restante do .NET Framework, minimizando o uso de F#-construções específicas na API pública. As regras são explicadas nas seções a seguir.

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>Namespace e tipo de design (para as bibliotecas de uso de outras linguagens .NET)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Aplicar as convenções de nomenclatura do .NET para a API pública de seus componentes

Preste atenção especial para o uso de nomes abreviados e as diretrizes de maiusculas e minúsculas do .NET.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Usar namespaces, tipos e membros como a estrutura organizacional primária para os componentes

Todos os arquivos que contém a funcionalidade pública devem começar com um `namespace` declaração e as únicas entidades voltados ao público em namespaces devem ser tipos. Não use F# módulos.

Use módulos de não-públicos para manter o código de implementação, utilitário tipos e funções de utilitário.

Tipos estáticos devem ser preferenciais em vez de módulos, já que permitem futura evolução da API para usar a sobrecarga e outros conceitos de design .NET API que não podem ser usados dentro do F# módulos.

Por exemplo, em vez da API pública do seguinte:

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

Considere em vez disso:

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Use F# tipos de registro no baunilha APIs .NET se o design dos tipos não evoluir

F#tipos de registro seja compilado para uma classe simples do .NET. Eles são adequados para alguns tipos simples e estáveis em APIs. Você deve considerar usar o `[<NoEquality>]` e `[<NoComparison>]` atributos para suprimir a geração automática de interfaces. Além disso, evite usar campos de registro mutável em baunilha APIs .NET como esses expõe um campo público. Sempre considere se uma classe forneceria uma opção mais flexível para futura evolução da API.

Por exemplo, a seguinte F# código expõe a API pública para um C# consumidor:

F#:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
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

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Ocultar a representação de F# tipos de união em baunilha APIs do .NET

F#tipos de união não são comumente usados nos limites do componente, mesmo para F#- para -F# de codificação. Eles são um dispositivo de implementação excelente quando usado internamente em componentes e bibliotecas.

Ao criar uma API .NET de baunilha, considere ocultando a representação de um tipo de união, usando uma declaração particular ou um arquivo de assinatura.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Você também poderá aumentar os tipos que usam uma representação de união internamente com membros para fornecer um desejado. NET voltado para a API.

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

Há muitas estruturas diferentes dentro do .NET, como WinForms, WPF e ASP.NET. Convenções de nomenclatura e design para cada um devem ser usadas se você estiver criando componentes para uso em dessas estruturas. Por exemplo, para o WPF em programação, adote padrões de design do WPF para as classes que você está criando. Para modelos na programação de interface do usuário, use os padrões de design, como eventos e baseada em notificação coleções como aquelas encontradas no <xref:System.Collections.ObjectModel>.

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Design de objetos e membros (para as bibliotecas de uso de outras linguagens .NET)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>Usar o atributo CLIEvent para expor eventos .NET

Construir uma `DelegateEvent` com um .NET específica o tipo que usa um objeto de delegado e `EventArgs` (em vez de uma `Event`, que usa apenas o `FSharpHandler` tipo por padrão) para que os eventos são publicados da forma familiar para outras linguagens .NET.

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>Expor operações assíncronas como métodos que retornam tarefas do .NET

As tarefas são usadas em .NET para representar as computações assíncronas Active Directory. Tarefas são em geral composicional menor que F# `Async<T>` objetos, uma vez que eles representam tarefas "já em execução" e não podem ser compostos juntas de maneiras que realizar a composição paralela ou que oculte a propagação de sinais de cancelamento e outros parâmetros contextuais.

No entanto, apesar disso, os métodos que retornam tarefas são a representação padrão de programação assíncrona no .NET.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Com frequência, você irá também deseja aceitar um token de cancelamento explícita:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>Usar tipos de delegados do .NET em vez de F# tipos de função

Veja "F# tipos de função" significa que os tipos de "seta" como `int -> int`.

Em vez disto:

```fsharp
member this.Transform(f: int->int) =
    ...
```

Faça o seguinte:

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

O F# tipo de função é exibido como `class FSharpFunc<T,U>` para outras linguagens .NET e é menos adequada para recursos de linguagem e ferramentas que entender os tipos de delegado. Ao criar um método de ordem superior direcionados ao .NET Framework 3.5 ou posterior, o `System.Func` e `System.Action` os delegados são as APIs certas para publicar para permitir que os desenvolvedores de .NET consumir essas APIs de uma maneira de baixo atrito. (Ao direcionar o .NET Framework 2.0, os tipos de delegado definido pelo sistema são mais limitados; considere o uso de tipos de delegado predefinidos, como `System.Converter<T,U>` ou definindo um tipo de delegado específico.)

Por outro lado, os delegados do .NET não são naturais para F#-voltados para bibliotecas (consulte a próxima seção sobre F#-voltados para bibliotecas). Como resultado, uma estratégia de implementação comum ao desenvolver métodos de ordem superior para bibliotecas .NET de baunilha é criar todos os implementação usando F# tipos de função e, em seguida, crie a API pública usando delegados como uma fachada fina sobre o real F#implementação.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>Usar o padrão de TryGetValue em vez de retornar F# valores de opção e preferir a sobrecarga de método para tirar F# valores como argumentos de opção

Padrões comuns de uso para o F# tipo de opção em APIs são melhores implementado em baunilha APIs do .NET usando o .NET standard técnicas de design. Em vez de retornar um F# valor de opção, considere usar o tipo de retorno booleano além de um parâmetro de saída como o padrão de "TryGetValue". E, em vez de usar F# valores como parâmetros de opção, considere o uso de argumentos opcionais ou sobrecarga de método.

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>Usar a interface de coleção do .NET tipos IEnumerable\<T\> e IDictionary\<da chave, valor\> para parâmetros e valores de retorno

Evite o uso de tipos de coleção concretos, como as matrizes do .NET `T[]`, F# tipos `list<T>`, `Map<Key,Value>` e `Set<T>`, e tipos de coleção concreta do .NET, como `Dictionary<Key,Value>`. Diretrizes de Design da biblioteca do .NET ter bons conselhos sobre quando usar vários tipos de coleção, como `IEnumerable<T>`. Algum uso de matrizes (`T[]`) é aceitável em algumas circunstâncias, em razão de desempenho. Observe especialmente `seq<T>` é apenas o F# alias do `IEnumerable<T>`, e, portanto, seq costuma ser um tipo apropriado para uma API .NET de baunilha.

Em vez de F# lista:

```fsharp
member this.PrintNames(names: string list) =
    ...
```

Use F# sequências:

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Usar o tipo de unidade como o único tipo de entrada de um método para definir um método de argumento de zero ou como o único tipo de retorno para definir um método de retorno void

Evite a outros usos do tipo de unidade. Essas são boas:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

Isso é ruim:

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Verificar valores nulos em baunilha limites de API do .NET

F#código de implementação tende a ter menos valores nulos, devido a padrões de design imutável e restrições no uso de literais nulas para F# tipos. Outras linguagens .NET geralmente usam nulo como um valor muito mais frequência. Por isso, F# código que expõe uma API .NET de baunilha deve verificar parâmetros de null no limite da API e impedir que esses valores fluindo profunda o F# código de implementação. O `isNull` função ou correspondência de padrão no `null` padrão pode ser usado.

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

Em vez disso, prefira retornando um tipo nomeado que contém os dados de agregação, ou usando os parâmetros de saída para retornar vários valores. Embora existam, tuplas e tuplas de struct, no .NET (incluindo suporte à linguagem c# tuplas de struct), eles geralmente não fornecerá a API ideal e esperada para desenvolvedores do .NET.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Evite o uso de currying de parâmetros

Em vez disso, use o .NET de convenções de chamada `Method(arg1,arg2,…,argN)`.

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

Dica: Se você estiver criando bibliotecas para uso em qualquer linguagem .NET, não há nenhum substituto para realmente fazer algumas experimental C# e para garantir que suas bibliotecas "sensação à direita" dessas linguagens de programação Visual Basic. Você também pode usar ferramentas como o .NET Reflector e o Pesquisador de objetos do Visual Studio para garantir que as bibliotecas e sua documentação aparecem conforme o esperado para os desenvolvedores.

## <a name="appendix"></a>Anexo

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Exemplo de ponta a ponta da criação F# código para uso por outras linguagens .NET

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

Inferido F# tipo dessa classe é o seguinte:

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

Vamos dar uma olhada em como isso F# tipo será exibido para um programador usando outra linguagem .NET. Por exemplo, o aproximado c# "assinatura" é da seguinte maneira:

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

Há alguns pontos importantes a observar sobre como F# representa constrói aqui. Por exemplo:

* Metadados, como nomes de argumentos foi preservado.

* F#métodos que usam dois argumentos que se tornam C# métodos que usam dois argumentos.

* Funções e listas se tornam as referências a tipos correspondentes no F# biblioteca.

O código a seguir mostra como ajustar este código para levar tudo isso em conta.

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

Inferido F# tipo de código é da seguinte maneira:

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

A assinatura c# agora é da seguinte maneira:

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

As correções feitas para preparar esse tipo para uso como parte de uma biblioteca .NET baunilha são da seguinte maneira:

* Ajustado diversos nomes: `Point1`, `n`, `l`, e `f` se tornou `RadialPoint`, `count`, `factor`, e `transform`, respectivamente.

* Usado um tipo de retorno `seq<RadialPoint>` em vez de `RadialPoint list` alterando uma construção de lista usando `[ ... ]` para uma construção de sequência usando `IEnumerable<RadialPoint>`.

* Usado o tipo de delegado do .NET `System.Func` em vez de um F# tipo de função.

Isso torna muito mais agradável consumir em código c#.
