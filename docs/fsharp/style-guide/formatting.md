---
title: 'F # diretrizes de formatação de código'
description: 'Saiba mais diretrizes de formatação de código F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 6c8e4059fd4bf1e7450118a6df02609217c4f4db
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231496"
---
# <a name="f-code-formatting-guidelines"></a>F # diretrizes de formatação de código

Este artigo oferece diretrizes sobre como formatar seu código para que seu código F #:

* Geralmente considerado mais legível
* Está de acordo com as convenções aplicadas por ferramentas do Visual Studio e outros editores de formatação
* Semelhante a outro código online

Essas diretrizes se baseiam no [um guia abrangente para convenções de formatação do F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) por [Anh Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Regras gerais para recuo

F # usa o espaço em branco significativo por padrão. As diretrizes a seguir são destinadas a fornecer orientação sobre como manipular alguns desafios que isso pode impor.

### <a name="using-spaces"></a>Usando espaços

Quando o recuo for necessário, você deve usar espaços, tabulações não. É necessário pelo menos um espaço. Sua organização pode criar padrões de codificação para especificar o número de espaços a serem usados para recuo; duas, três ou quatro espaços de recuo em cada nível onde ocorre o recuo é comum.

**Recomendamos 4 espaços por recuo.**

Dito isso, recuo de programas é uma questão subjetiva. Variações são Okey, mas é a primeira regra, você deve seguir *consistência de recuo*. Escolha um estilo geralmente aceito de recuo e usá-lo sistematicamente em toda a sua base de código.

## <a name="formatting-blank-lines"></a>Formatação de linhas em branco

* Separado nível superior função classe definições e com duas linhas em branco.
* Definições de método dentro de uma classe são separadas por uma única linha em branco.
* Linhas em branco adicional podem ser usadas (moderadamente) para separar grupos de funções relacionadas. Linhas em branco podem ser omitidas entre um conjunto de linhas relacionadas (por exemplo, um conjunto de implementações fictícios).
* Use linhas em branco em funções, moderação, para indicar seções lógicas.

## <a name="formatting-comments"></a>Comentários de formatação

Geralmente prefira vários comentários barra dupla comentários do bloco de estilo ML.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Comentários in-line devem colocar em maiuscula a primeira letra.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Convenções de nomenclatura

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Use camelCase para funções e os valores associados de classe, associadas a expressão e limite padrão

É comum e aceita F # estilo a ser usado em camelCase todos os nomes associados como variáveis locais ou em correspondências de padrão e as definições de função.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Funções associadas a localmente em classes também devem usar camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Use camelCase para funções públicas associadas ao módulo

Quando uma função associada de módulo fizer parte de uma API pública, ele deve usar camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Use camelCase para funções e os valores de limite de módulo internos e privados

Use camelCase para valores de limite de módulo privados, incluindo o seguinte:

* Funções ad hoc em scripts

* Valores que compõem a implementação interna de um módulo ou tipo

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Use camelCase para parâmetros

Todos os parâmetros devem usar camelCase de acordo com as convenções de nomenclatura do .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Use PascalCase para módulos

Todos os módulos (nível superior, internos, privados, aninhados) devem usar PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Use PascalCase para declarações de tipo, membros e rótulos

Classes, interfaces, estruturas, enumerações, delegados, registros e uniões discriminadas devem ser chamados com PascalCase. Membros de tipos e rótulos para registros e uniões discriminadas também devem usar PascalCase.

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Use PascalCase para construções intrínsecas para .NET

Namespaces, exceções, eventos e projeto /`.dll` nomes também devem usar PascalCase. Não apenas isso faz o consumo de outras linguagens .NET bem mais fácil para os consumidores, também é consistente com as convenções de nomenclatura de .NET probabilidade de encontrar.

### <a name="avoid-underscores-in-names"></a>Evite sublinhados em nomes

Historicamente, algumas bibliotecas F # usou sublinhados em nomes. No entanto, isso não é mais amplamente é aceito, em parte porque entrar em conflito com as convenções de nomenclatura do .NET. Dito isso, alguns programadores F # usam sublinhados intensamente, parcialmente por razões históricas e tolerância e respeito é importante. No entanto, lembre-se de que o estilo é geralmente disliked por outras pessoas que têm a opção de usá-lo.

Algumas exceções inclui interagir com componentes nativos, onde sublinhados são muito comuns.

### <a name="use-standard-f-operators"></a>Use operadores padrão F #

Os operadores a seguir são definidos na biblioteca padrão do F # e devem ser usados em vez de definir equivalentes. Usar esses operadores é recomendado conforme ele tende a tornar o código mais legível e idiomática. Os desenvolvedores com um plano de fundo em OCaml ou outra linguagem de programação funcional podem estar acostumados a idiomas diferentes. A lista a seguir resume os operadores de F # recomendados.

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Use a sintaxe de prefixo para genéricos (`Foo<T>`) em vez da sintaxe de sufixo (`T Foo`)

F # herda ambos o estilo de ML sufixo de nomeação de tipos genéricos (por exemplo, `int list`), bem como o prefixo de estilo do .NET (por exemplo, `list<int>`). Preferir o estilo do .NET, exceto os quatro tipos específicos:

1. Para F # lista, use o formulário de sufixo: `int list` em vez de `list<int>`.
2. Para opções de F #, use o formulário de sufixo: `int option` em vez de `option<int>`.
3. Para matrizes de F #, use o nome sintático `int[]` em vez de `int array` ou `array<int>`.
4. Para fazer referência a células, use `int ref` em vez de `ref<int>` ou `Ref<int>`.

Para todos os outros tipos, use o formulário de prefixo.

## <a name="formatting-discriminated-union-declarations"></a>Formatação discriminada declarações de união

Recuar `|` na definição de tipo por 4 espaços:

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

Uniões instanciado discriminada divididos em várias linhas devem fornecer os dados contidos um novo escopo com recuo:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

O parêntese de fechamento também pode estar em uma nova linha:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a>Formatação tuplas

Uma instanciação de tupla deve estar entre parênteses e vírgulas dentro de delimitadores devem ser seguidas por um único espaço, por exemplo: `(1, 2)`, `(x, y, z)`.

Uma exceção geralmente aceita é omitir parênteses na correspondência de padrões de tuplas:

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a>Formatação de registros

Registros curtos podem ser escritos em uma linha:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Registros mais devem usar novas linhas para rótulos:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Também é bom colocando o token de abertura na mesma linha e o token de fechamento em uma nova linha:

```fsharp
let rainbow = {
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
```

Aplicam as mesmas regras para elementos de matriz e de lista.

## <a name="formatting-lists-and-arrays"></a>Formatação de listas e matrizes

Gravar `x :: l` com espaços em torno de `::` operador (`::` é um operador infixo, portanto, cercado por espaços) e `[1; 2; 3]` (`;` é um delimitador, portanto, seguido por um espaço).

Sempre use pelo menos um espaço entre os dois operadores de tipo de chave distintos. Por exemplo, deixar um espaço entre um `[` e um `{`.

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

Listas e matrizes que são divididos em várias linhas seguem uma regra semelhante como registros:

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a>Formatação se expressões

Recuo de condicionais depende dos tamanhos das expressões que compõem-los. Se `cond`, `e1` e `e2` são pequenas, simplesmente gravá-los em uma única linha:

```fsharp
if cond then e1 else e2
```

Se `e1` e `cond` são pequenas, mas `e2` é grande:

```fsharp
if cond then e1
else
    e2
```

Se `e1` e `cond` são grandes e `e2` é pequeno:

```fsharp
if cond then
    e1
else e2
```

Se todas as expressões forem grandes:

```fsharp
if cond then
    e1
else
    e2
```

Várias condições com `elif` e `else` são recuadas no mesmo escopo de `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Construções de correspondência de padrão

Use um `|` para cada cláusula de correspondência com nenhum recuo. Se a expressão for pequena, você pode considerar usando uma única linha, se cada subexpressão também é simple.

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

Se a expressão à direita do padrão de correspondência de seta é muito grande, mova-o para a seguinte linha, recuo de uma etapa do `match` / `|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Padrão de correspondência de funções anônimas, começando pelo `function`, não geralmente deve Recuar muito distante. Por exemplo, é bom recuar um escopo da seguinte maneira:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Correspondência de padrão de funções definidas pelo `let` ou `let rec` devem ser recuados 4 espaços após a inicialização do `let`, mesmo se `function` palavra-chave é usada:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Não é recomendável alinhando setas.

## <a name="formatting-trywith-expressions"></a>Tente formatação / com expressões

Padrão de correspondência no tipo de exceção deve ser recuado no mesmo nível como `with`.

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

## <a name="formatting-function-parameter-application"></a>Formatação de aplicativo de parâmetro de função

Em geral, a maioria dos aplicativos de parâmetro de função é feito na mesma linha.

Se você quiser aplicar parâmetros para uma função em uma nova linha, recuo-los por um escopo.

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

As mesmas diretrizes se aplicam para expressões lambda como argumentos de função. Se o corpo de uma expressão lambda, o corpo pode ter outra linha recuada de acordo com um escopo

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

No entanto, se o corpo de uma expressão lambda é mais de uma linha, considere fatorar-o em uma função separada em vez de uma construção de várias linha aplicada como um único argumento para uma função.

### <a name="formatting-infix-operators"></a>Formatação operadores fixos

Operadores separados por espaços. Óbvias exceções a essa regra são o `!` e `.` operadores.

Expressões de infixo são Okey linha na mesma coluna:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formatação de operadores de pipeline

Pipeline `|>` operadores devem ir sob eles operam em expressões.

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

Em um módulo local deverá ser recuado em relação ao módulo, mas não deve ser recuado código em um módulo de nível superior. Elementos de Namespace não precisam ser recuado.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Formatação de expressões de objeto e interfaces

Expressões de objeto e interfaces devem ser alinhados da mesma maneira com `member` sendo recuado após 4 espaços.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a>Formatação de espaço em branco em expressões

Evite estranhos espaço em branco em expressões de F #.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Argumentos nomeados também não devem ter espaço em torno de `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
