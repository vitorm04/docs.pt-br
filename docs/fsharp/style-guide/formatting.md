---
title: Diretrizes de formatação de código do F#
description: Aprenda as diretrizes para formatar o código F# .
ms.date: 11/04/2019
ms.openlocfilehash: dd48380a90ee92b2c1edaaabc116fa1cd8010390
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102483"
---
# <a name="f-code-formatting-guidelines"></a>Diretrizes de formatação de código do F#

Este artigo oferece diretrizes de como formatar seu código para que seu código F# seja:

* Mais legível
* De acordo com as convenções aplicadas por ferramentas de formatação no Visual Studio e outros editores
* Semelhante a outro código online

Essas diretrizes são baseadas em [um guia abrangente de Convenções de Formatação F#](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) por [Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Regras gerais para recuo

F# usa espaço branco significativo por padrão. As seguintes diretrizes destinam-se a orientar sobre como lidar com alguns desafios que isso pode impor.

### <a name="using-spaces"></a>Usando espaços

Quando o recuo é necessário, você deve usar espaços, não guias. Pelo menos um espaço é necessário. Sua organização pode criar padrões de codificação para especificar o número de espaços a serem usados para recuo; dois, três ou quatro espaços de recuo em cada nível onde ocorre o recuo é típico.

**Recomendamos quatro espaços por recuo.**

Dito isto, o recuo dos programas é uma questão subjetiva. As variações são ok, mas a primeira regra que você deve seguir é *a consistência do recuo*. Escolha um estilo geralmente aceito de recuo e use-o sistematicamente em toda a sua base de código.

## <a name="formatting-white-space"></a>Formatação do espaço em branco

F# é sensível ao espaço branco. Embora a maioria das semânticas do espaço branco sejam cobertas por um recuo adequado, há algumas outras coisas a considerar.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Operadores de formatação em expressões aritméticas

Use sempre o espaço branco em torno de expressões aritméticas binárias:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Os `-` operadores unary devem ser sempre imediatamente seguidos pelo valor que estão negando:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

Adicionar um caractere de `-` espaço branco depois que o operador pode levar a confusão para outros.

Em resumo, é importante sempre:

* Operadores binários surround com espaço branco
* Nunca tenha seguido espaço branco depois de um operador unary

A diretriz do operador aritmético binário é especialmente importante. Não cercar um `-` operador binário, quando combinado com certas escolhas de formatação, pode levar a interpretá-lo como um unary `-`.

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Cerque uma definição de operador personalizado com espaço em branco

Use sempre o espaço em branco para cercar uma definição do operador:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Para qualquer operador personalizado `*` que comece com e que tenha mais de um caractere, você precisa adicionar um espaço em branco ao início da definição para evitar uma ambiguidade compilador. Por causa disso, recomendamos que você simplesmente cerque as definições de todos os operadores com um único caractere de espaço branco.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Setas de parâmetro de função surround com espaço branco

Ao definir a assinatura de uma função, use o espaço em branco ao redor do `->` símbolo:

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Argumentos de função surround com espaço branco

Ao definir uma função, use o espaço em branco em torno de cada argumento.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a>Coloque parâmetros em uma nova linha para definições de membros longos

Se você tiver uma definição de membro muito longa, coloque os parâmetros em novas linhas e recue-os em um escopo.

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

Isso também se aplica aos construtores:

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a>Anotações de tipo

#### <a name="right-pad-function-argument-type-annotations"></a>Anotações do tipo de argumento de função do bloco direito

Ao definir argumentos com anotações de tipo, use o espaço em branco após o `:` símbolo:

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Anotações do tipo de retorno surround com espaço branco

Em uma função let-bound ou anotação de tipo de valor (tipo de `:` retorno no caso de uma função), use o espaço em branco antes e depois do símbolo:

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>Formatação de linhas em branco

* Separe as definições de função e classe de nível superior com duas linhas em branco.
* As definições de método dentro de uma classe são separadas por uma única linha em branco.
* Linhas em branco extras podem ser usadas (com moderação) para grupos separados de funções relacionadas. Linhas em branco podem ser omitidas entre um grupo de linhas uniline (por exemplo, um conjunto de implementações manequim).
* Use linhas em branco em funções, com moderação, para indicar seções lógicas.

## <a name="formatting-comments"></a>Formatação de comentários

Geralmente preferem vários comentários de corte duplo em vez de comentários de bloco no estilo ML.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Comentários inline devem capitalizar a primeira letra.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Convenções de nomenclatura

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Use camelCase para valores e funções vinculados à classe, vinculados à expressão e padrão

É comum e aceito estilo F# para usar camelCase para todos os nomes vinculados como variáveis locais ou em correspondências de padrão e definições de função.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Funções vinculadas localmente nas classes também devem usar camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Use camelCase para funções públicas vinculadas ao módulo

Quando uma função vinculada ao módulo faz parte de uma API pública, ela deve usar camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Use camelCase para valores e funções internas e privadas vinculados a módulos

Use camelCase para valores privados vinculados a módulos, incluindo o seguinte:

* Funções ad hoc em scripts

* Valores que compõem a implementação interna de um módulo ou tipo

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Use cameloCase para parâmetros

Todos os parâmetros devem usar camelCase de acordo com as convenções de nomeação .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Use PascalCase para módulos

Todos os módulos (de nível superior, interno, privado, aninhados) devem usar PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Use PascalCase para declarações de tipo, membros e rótulos

Classes, interfaces, estruturas, enumerações, delegados, registros e sindicatos discriminados devem ser nomeados com PascalCase. Os membros dentro de tipos e rótulos para registros e sindicatos discriminados também devem usar o PascalCase.

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Use PascalCase para construções intrínsecas a .NET

Namespaces, exceções, eventos e`.dll` projetos/nomes também devem usar PascalCase. Isso não só faz com que o consumo de outras línguas .NET pareça mais natural para os consumidores, como também é consistente com as convenções de nomeação .NET que você provavelmente encontrará.

### <a name="avoid-underscores-in-names"></a>Evite sublinhados em nomes

Historicamente, algumas bibliotecas F# têm usado sublinhados em nomes. No entanto, isso não é mais amplamente aceito, em parte porque se choca com as convenções de nomeação .NET. Dito isto, alguns programadores F# usam sublinhações pesadamente, em parte por razões históricas, e tolerância e respeito é importante. No entanto, esteja ciente de que o estilo muitas vezes é detestado por outros que têm uma escolha sobre se usá-lo.

Uma exceção inclui interoperar com componentes nativos, onde sublinhados são comuns.

### <a name="use-standard-f-operators"></a>Use operadores F# padrão

Os seguintes operadores são definidos na biblioteca padrão F# e devem ser usados em vez de definir equivalentes. O uso desses operadores é recomendado, pois tende a tornar o código mais legível e idiomático. Desenvolvedores com experiência em OCaml ou outra linguagem de programação funcional podem estar acostumados a diferentes expressões. A lista a seguir resume os operadores F# recomendados.

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Use a sintaxe`Foo<T>`prefixada para genéricos (`T Foo`) em preferência à sintaxe pós-fixação ( )

F# herda tanto o estilo ML pós-fixação `int list`de nomear tipos genéricos (por `list<int>`exemplo, ) quanto o prefixo .NET estilo (por exemplo, ). Prefira o estilo .NET, exceto por cinco tipos específicos:

1. Para listas F#, use o `int list` formulário `list<int>`postfix: em vez de .
2. Para opções F#, use `int option` o `option<int>`formulário postfix: em vez de .
3. Para f# opções de valor, `int voption` use `voption<int>`o formulário postfix: em vez de .
4. Para matrizes F#, use o `int[]` nome `int array` `array<int>`sintático em vez de ou .
5. Para células de `int ref` referência, use em vez de `ref<int>` ou `Ref<int>`.

Para todos os outros tipos, use a forma de prefixo.

## <a name="formatting-tuples"></a>Formatação de tuplas

Uma instanciação tupla deve ser parêntena, e as comúdes delimitadoras dentro dela devem ser seguidas por um único espaço, por exemplo: `(1, 2)`. `(x, y, z)`

É comumente aceito para omitir parênteses na correspondência de padrões de tuplas:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Também é comumente aceito para omitir parênteses se o tuplo é o valor de retorno de uma função:

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

Em resumo, prefira instanciais tuplas parênteses, mas ao usar tuplas para correspondência de padrões ou um valor de retorno, é considerado bom para evitar parênteses.

## <a name="formatting-discriminated-union-declarations"></a>Formatação de declarações sindicais discriminadas

Recuo `|` na definição do tipo por quatro espaços:

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a>Formatação de sindicatos discriminados

Sindicatos discriminados instanciados que se dividem em várias linhas devem dar aos dados contidos um novo escopo com recuo:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Os parênteses de fechamento também podem estar em uma nova linha:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Formatação de declarações de registro

Recue `{` na definição de tipo por quatro espaços e inicie a lista de campo na mesma linha:

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

Colocar o token de abertura em uma nova linha e o token de fechamento em uma nova linha é preferível se você estiver declarando implementações de interface ou membros no registro:

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>Formatação de registros

Registros curtos podem ser escritos em uma linha:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Os registros que são mais longos devem usar novas linhas para rótulos:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Colocando o token de abertura em uma nova linha, o conteúdo tabulado em um escopo e o token de fechamento em uma nova linha é preferível se você for:

* Movendo registros em código com diferentes escopos de recuo
* Encanando-os em uma função

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

As mesmas regras se aplicam a elementos de lista e matriz.

## <a name="formatting-copy-and-update-record-expressions"></a>Formatação de expressões de registro de cópia e atualização

Uma expressão de registro de cópia e atualização ainda é um registro, então diretrizes semelhantes se aplicam.

Expressões curtas podem caber em uma linha:

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

Expressões mais longas devem usar novas linhas:

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

E como com a orientação de registro, você pode querer dedicar linhas separadas para o aparelho e recue um escopo para a direita com a expressão. Em alguns casos especiais, como embrulhar um valor com um opcional sem parênteses, você pode precisar manter uma cinta em uma linha:

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a>Listas de formatação e matrizes

Escreva `x :: l` com espaços `::` ao`::` redor do operador ( é um operador de infixo, portanto cercado por espaços).

Lista e matrizes declaradas em uma única linha devem ter um espaço após o suporte de abertura e antes do suporte de fechamento:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Use sempre pelo menos um espaço entre dois operadores distintos. Por exemplo, deixe um `[` espaço `{`entre a e a .

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

A mesma diretriz se aplica a listas ou matrizes de tuplas.

Listas e matrizes divididas em várias linhas seguem uma regra semelhante à dos registros:

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

E como acontece com os registros, declarar os suportes de abertura e fechamento em sua própria linha facilitará a movimentação de códigos e tubulações em funções.

Ao gerar matrizes e listas programáticas, prefira `->` quando `do ... yield` um valor é sempre gerado:

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

Versões mais antigas do `yield` idioma F# são necessárias especificando em situações em que os dados podem ser gerados condicionalmente, ou podem haver expressões consecutivas a serem avaliadas. Prefira `yield` omitir essas palavras-chave, a menos que você deve compilar com uma versão mais antiga do idioma F#:

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

Em alguns `do...yield` casos, pode auxiliar na legibilidade. Esses casos, embora subjetivos, devem ser levados em consideração.

## <a name="formatting-if-expressions"></a>Formatação se expressões

O recuo das condicionalidades depende dos tamanhos das expressões que as compõem. Se `cond` `e1` , `e2` e for curto, basta escrevê-los em uma linha:

```fsharp
if cond then e1 else e2
```

Se `cond`for `e1` `e2` em tempo maior, mas não em várias linhas:

```fsharp
if cond
then e1
else e2
```

Se alguma das expressões for multi-linha:

```fsharp
if cond then
    e1
else
    e2
```

Múltiplas condicionales `elif` com `else` e são recuadas no `if`mesmo escopo que:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Construções de correspondência de padrões

Use `|` a para cada cláusula de uma partida sem recuo. Se a expressão for curta, você pode considerar o uso de uma única linha se cada subexpressão também for simples.

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

Se a expressão à direita da seta de correspondência de padrão for muito grande, `match` / `|`mova-a para a linha seguinte, recuada a um passo da .

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

A correspondência de padrões `function`de funções anônimas, a partir de , geralmente não deve se identificar muito longe. Por exemplo, recuar um escopo da seguinte forma é bom:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

A correspondência de padrões `let rec` em funções definidas ou `let` `let` deve `function` ser recuada quatro espaços após o início de , mesmo que a palavra-chave seja usada:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Não recomendamos alinhar setas.

## <a name="formatting-trywith-expressions"></a>Formatação try/com expressões

A correspondência de padrões no tipo de exceção deve ser recuada no mesmo nível que `with`.

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a>Aplicativo de parâmetro de função de formatação

Em geral, a maior parte da aplicação do parâmetro de função é feita na mesma linha.

Se você deseja aplicar parâmetros a uma função em uma nova linha, recue-os por um escopo.

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

As mesmas diretrizes se aplicam às expressões lambda como argumentos de função. Se o corpo de uma expressão lambda, o corpo pode ter outra linha, recuada por um escopo

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

No entanto, se o corpo de uma expressão lambda é mais do que uma linha, considere fatorá-lo em uma função separada em vez de ter uma construção multi-linha aplicada como um único argumento para uma função.

### <a name="formatting-infix-operators"></a>Formatação de operadores de infixo

Operadores separados por espaços. Exceções óbvias a `!` esta `.` regra são os operadores.

As expressões infix são OK para lineup na mesma coluna:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Operadores de gasodutos de formatação

Os `|>` operadores de gasodutos devem ir por baixo das expressões em que operam.

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a>Módulos de formatação

O código em um módulo local deve ser recuado em relação ao módulo, mas o código em um módulo de nível superior não deve ser recuado. Os elementos de namespace não devem ser recuados.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Formatação de expressões e interfaces de objeto

Expressões e interfaces de objeto devem ser `member` alinhadas da mesma forma com o recuo após quatro espaços.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Formatação do espaço em branco em expressões

Evite espaço branco estranho nas expressões F#.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Os argumentos nomeados também `=`não devem ter espaço em torno do:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Atributos de formatação

[Os atributos](../language-reference/attributes.md) são colocados acima de um construto:

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a>Formatação de atributos em parâmetros

Atributos também podem ser colocados em parâmetros. Neste caso, coloque na mesma linha do parâmetro e antes do nome:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Formatação de vários atributos

Quando vários atributos são aplicados a um construto que não é um parâmetro, eles devem ser colocados de tal forma que haja um atributo por linha:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Quando aplicados a um parâmetro, devem estar na mesma `;` linha e separados por um separador.

## <a name="formatting-literals"></a>Formatação de literais

[Os literais f#](../language-reference/literals.md) que usam o atributo `Literal` devem colocar o atributo em sua própria linha e usar a nomenclatura PascalCase:

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Evite colocar o atributo na mesma linha que o valor.
