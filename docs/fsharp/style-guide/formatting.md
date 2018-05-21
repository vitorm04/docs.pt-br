---
title: 'F # diretrizes de formatação de código'
description: 'Saiba mais diretrizes de formatação de código F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 1433b6891a6a0ddcdc082c141365ae54fa40c27b
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="3a876-103">F # diretrizes de formatação de código</span><span class="sxs-lookup"><span data-stu-id="3a876-103">F# code formatting guidelines</span></span>

<span data-ttu-id="3a876-104">Este artigo oferece diretrizes sobre como formatar seu código para que seu código F #:</span><span class="sxs-lookup"><span data-stu-id="3a876-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="3a876-105">Geralmente considerado mais legível</span><span class="sxs-lookup"><span data-stu-id="3a876-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="3a876-106">Está de acordo com as convenções aplicadas por ferramentas do Visual Studio e outros editores de formatação</span><span class="sxs-lookup"><span data-stu-id="3a876-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="3a876-107">Semelhante a outro código online</span><span class="sxs-lookup"><span data-stu-id="3a876-107">Similar to other code online</span></span>

<span data-ttu-id="3a876-108">Essas diretrizes se baseiam no [um guia abrangente para convenções de formatação do F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) por [Anh Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="3a876-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="3a876-109">Regras gerais para recuo</span><span class="sxs-lookup"><span data-stu-id="3a876-109">General rules for indentation</span></span>

<span data-ttu-id="3a876-110">F # usa o espaço em branco significativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="3a876-110">F# uses significant whitespace by default.</span></span> <span data-ttu-id="3a876-111">As diretrizes a seguir são destinadas a fornecer orientação sobre como manipular alguns desafios que isso pode impor.</span><span class="sxs-lookup"><span data-stu-id="3a876-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="3a876-112">Usando espaços</span><span class="sxs-lookup"><span data-stu-id="3a876-112">Using spaces</span></span>

<span data-ttu-id="3a876-113">Quando o recuo for necessário, você deve usar espaços, tabulações não.</span><span class="sxs-lookup"><span data-stu-id="3a876-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="3a876-114">É necessário pelo menos um espaço.</span><span class="sxs-lookup"><span data-stu-id="3a876-114">At least one space is required.</span></span> <span data-ttu-id="3a876-115">Sua organização pode criar padrões de codificação para especificar o número de espaços a serem usados para recuo; duas, três ou quatro espaços de recuo em cada nível onde ocorre o recuo é comum.</span><span class="sxs-lookup"><span data-stu-id="3a876-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="3a876-116">**Recomendamos 4 espaços por recuo.**</span><span class="sxs-lookup"><span data-stu-id="3a876-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="3a876-117">Dito isso, recuo de programas é uma questão subjetiva.</span><span class="sxs-lookup"><span data-stu-id="3a876-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="3a876-118">Variações são Okey, mas é a primeira regra, você deve seguir *consistência de recuo*.</span><span class="sxs-lookup"><span data-stu-id="3a876-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="3a876-119">Escolha um estilo geralmente aceito de recuo e usá-lo sistematicamente em toda a sua base de código.</span><span class="sxs-lookup"><span data-stu-id="3a876-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="3a876-120">Formatação discriminada declarações de união</span><span class="sxs-lookup"><span data-stu-id="3a876-120">Formatting discriminated union declarations</span></span>

<span data-ttu-id="3a876-121">Recuar `|` na definição de tipo por 4 espaços:</span><span class="sxs-lookup"><span data-stu-id="3a876-121">Indent `|` in type definition by 4 spaces:</span></span>

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

<span data-ttu-id="3a876-122">Uniões instanciado discriminada divididos em várias linhas devem fornecer os dados contidos um novo escopo com recuo:</span><span class="sxs-lookup"><span data-stu-id="3a876-122">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="3a876-123">O parêntese de fechamento também pode estar em uma nova linha:</span><span class="sxs-lookup"><span data-stu-id="3a876-123">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a><span data-ttu-id="3a876-124">Formatação tuplas</span><span class="sxs-lookup"><span data-stu-id="3a876-124">Formatting tuples</span></span>

<span data-ttu-id="3a876-125">Uma instanciação de tupla deve estar entre parênteses e vírgulas dentro de delimitadores devem ser seguidas por um único espaço, por exemplo: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="3a876-125">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="3a876-126">Uma exceção geralmente aceita é omitir parênteses na correspondência de padrões de tuplas:</span><span class="sxs-lookup"><span data-stu-id="3a876-126">A commonly accepted exception is to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a><span data-ttu-id="3a876-127">Formatação de registros</span><span class="sxs-lookup"><span data-stu-id="3a876-127">Formatting records</span></span>

<span data-ttu-id="3a876-128">Registros curtos podem ser escritos em uma linha:</span><span class="sxs-lookup"><span data-stu-id="3a876-128">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="3a876-129">Registros mais devem usar novas linhas para rótulos:</span><span class="sxs-lookup"><span data-stu-id="3a876-129">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="3a876-130">Também é bom colocando o token de abertura na mesma linha e o token de fechamento em uma nova linha:</span><span class="sxs-lookup"><span data-stu-id="3a876-130">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

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

<span data-ttu-id="3a876-131">Aplicam as mesmas regras para elementos de matriz e de lista.</span><span class="sxs-lookup"><span data-stu-id="3a876-131">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="3a876-132">Formatação de listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="3a876-132">Formatting lists and arrays</span></span>

<span data-ttu-id="3a876-133">Gravar `x :: l` com espaços em torno de `::` operador (`::` é um operador infixo, portanto, cercado por espaços) e `[1; 2; 3]` (`;` é um delimitador, portanto, seguido por um espaço).</span><span class="sxs-lookup"><span data-stu-id="3a876-133">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="3a876-134">Sempre use pelo menos um espaço entre os dois operadores de tipo de chave distintos.</span><span class="sxs-lookup"><span data-stu-id="3a876-134">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="3a876-135">Por exemplo, deixar um espaço entre um `[` e um `{`.</span><span class="sxs-lookup"><span data-stu-id="3a876-135">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="3a876-136">Listas e matrizes que são divididos em várias linhas seguem uma regra semelhante como registros:</span><span class="sxs-lookup"><span data-stu-id="3a876-136">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

## <a name="formatting-if-expressions"></a><span data-ttu-id="3a876-137">Formatação se expressões</span><span class="sxs-lookup"><span data-stu-id="3a876-137">Formatting if expressions</span></span>

<span data-ttu-id="3a876-138">Recuo de condicionais depende dos tamanhos das expressões que compõem-los.</span><span class="sxs-lookup"><span data-stu-id="3a876-138">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="3a876-139">Se `cond`, `e1` e `e2` são pequenas, simplesmente gravá-los em uma única linha:</span><span class="sxs-lookup"><span data-stu-id="3a876-139">If `cond`, `e1` and `e2` are small, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="3a876-140">Se `e1` e `cond` são pequenas, mas `e2` é grande:</span><span class="sxs-lookup"><span data-stu-id="3a876-140">If `e1` and `cond` are small, but `e2` is large:</span></span>

```fsharp
if cond then e1
else
    e2
```

<span data-ttu-id="3a876-141">Se `e1` e `cond` são grandes e `e2` é pequeno:</span><span class="sxs-lookup"><span data-stu-id="3a876-141">If `e1` and `cond` are large and `e2` is small:</span></span>

```fsharp
if cond then
    e1
else e2
```

<span data-ttu-id="3a876-142">Se todas as expressões forem grandes:</span><span class="sxs-lookup"><span data-stu-id="3a876-142">If all the expressions are large:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="3a876-143">Várias condições com `elif` e `else` são recuadas no mesmo escopo de `if`:</span><span class="sxs-lookup"><span data-stu-id="3a876-143">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="3a876-144">Construções de correspondência de padrão</span><span class="sxs-lookup"><span data-stu-id="3a876-144">Pattern matching constructs</span></span>

<span data-ttu-id="3a876-145">Use um `|` para cada cláusula de correspondência com nenhum recuo.</span><span class="sxs-lookup"><span data-stu-id="3a876-145">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="3a876-146">Se a expressão for pequena, você pode usar uma única linha.</span><span class="sxs-lookup"><span data-stu-id="3a876-146">If the expression is short, you can use a single line.</span></span>

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

// OK
match l with [] -> false | _ :: _ -> true
```

<span data-ttu-id="3a876-147">Se a expressão à direita do padrão de correspondência de seta é muito grande, mova-o para a seguinte linha, recuo de uma etapa do `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="3a876-147">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="3a876-148">Padrão de correspondência de funções anônimas, começando pelo `function`, não geralmente deve Recuar muito distante.</span><span class="sxs-lookup"><span data-stu-id="3a876-148">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="3a876-149">Por exemplo, é bom recuar um escopo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3a876-149">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="3a876-150">Correspondência de padrão de funções definidas pelo `let` ou `let rec` devem ser recuados 4 espaços após a inicialização do `let`, mesmo se `function` palavra-chave é usada:</span><span class="sxs-lookup"><span data-stu-id="3a876-150">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="3a876-151">Não é recomendável alinhando setas.</span><span class="sxs-lookup"><span data-stu-id="3a876-151">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="3a876-152">Tente formatação / com expressões</span><span class="sxs-lookup"><span data-stu-id="3a876-152">Formatting try/with expressions</span></span>

<span data-ttu-id="3a876-153">Padrão de correspondência no tipo de exceção deve ser recuado no mesmo nível como `with`.</span><span class="sxs-lookup"><span data-stu-id="3a876-153">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="3a876-154">Formatação de aplicativo de parâmetro de função</span><span class="sxs-lookup"><span data-stu-id="3a876-154">Formatting function parameter application</span></span>

<span data-ttu-id="3a876-155">Em geral, a maioria dos aplicativos de parâmetro de função é feito na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="3a876-155">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="3a876-156">Se você quiser aplicar parâmetros para uma função em uma nova linha, recuo-los por um escopo.</span><span class="sxs-lookup"><span data-stu-id="3a876-156">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="3a876-157">Argumentos de função anônima podem ser na próxima linha ou com um pendente `fun` na linha de argumento:</span><span class="sxs-lookup"><span data-stu-id="3a876-157">Anonymous function arguments can be either on next line or with a dangling `fun` on the argument line:</span></span>

```fsharp
// OK
let printListWithOffset a list1 =
    List.iter (fun elem ->
        printfn "%d" (a + elem)) list1

// OK, but prefer previous
let printListWithOffset a list1 =
    List.iter (
        fun elem ->
            printfn "%d" (a + elem)) list1
```

### <a name="formatting-infix-operators"></a><span data-ttu-id="3a876-158">Formatação operadores fixos</span><span class="sxs-lookup"><span data-stu-id="3a876-158">Formatting infix operators</span></span>

<span data-ttu-id="3a876-159">Operadores separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="3a876-159">Separate operators by spaces.</span></span> <span data-ttu-id="3a876-160">Óbvias exceções a essa regra são o `!` e `.` operadores.</span><span class="sxs-lookup"><span data-stu-id="3a876-160">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="3a876-161">Expressões de infixo são Okey linha na mesma coluna:</span><span class="sxs-lookup"><span data-stu-id="3a876-161">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="3a876-162">Formatação de operadores de pipeline</span><span class="sxs-lookup"><span data-stu-id="3a876-162">Formatting pipeline operators</span></span>

<span data-ttu-id="3a876-163">Pipeline `|>` operadores devem ir sob eles operam em expressões.</span><span class="sxs-lookup"><span data-stu-id="3a876-163">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="3a876-164">Módulos de formatação</span><span class="sxs-lookup"><span data-stu-id="3a876-164">Formatting modules</span></span>

<span data-ttu-id="3a876-165">Em um módulo local deverá ser recuado em relação ao módulo, mas não deve ser recuado código em um módulo de nível superior.</span><span class="sxs-lookup"><span data-stu-id="3a876-165">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="3a876-166">Elementos de Namespace não precisam ser recuado.</span><span class="sxs-lookup"><span data-stu-id="3a876-166">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="3a876-167">Formatação de expressões de objeto e interfaces</span><span class="sxs-lookup"><span data-stu-id="3a876-167">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="3a876-168">Expressões de objeto e interfaces devem ser alinhados da mesma maneira com `member` sendo recuado após 4 espaços.</span><span class="sxs-lookup"><span data-stu-id="3a876-168">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a><span data-ttu-id="3a876-169">Formatação de espaço em branco em expressões</span><span class="sxs-lookup"><span data-stu-id="3a876-169">Formatting whitespace in expressions</span></span>

<span data-ttu-id="3a876-170">Evite estranhos espaço em branco em expressões de F #.</span><span class="sxs-lookup"><span data-stu-id="3a876-170">Avoid extraneous whitespace in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="3a876-171">Argumentos nomeados também não devem ter espaço em torno de `=`:</span><span class="sxs-lookup"><span data-stu-id="3a876-171">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="3a876-172">Formatação de linhas em branco</span><span class="sxs-lookup"><span data-stu-id="3a876-172">Formatting blank lines</span></span>

* <span data-ttu-id="3a876-173">Separado nível superior função classe definições e com duas linhas em branco.</span><span class="sxs-lookup"><span data-stu-id="3a876-173">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="3a876-174">Definições de método dentro de uma classe são separadas por uma única linha em branco.</span><span class="sxs-lookup"><span data-stu-id="3a876-174">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="3a876-175">Linhas em branco adicional podem ser usadas (moderadamente) para separar grupos de funções relacionadas.</span><span class="sxs-lookup"><span data-stu-id="3a876-175">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="3a876-176">Linhas em branco podem ser omitidas entre um conjunto de linhas relacionadas (por exemplo, um conjunto de implementações fictícios).</span><span class="sxs-lookup"><span data-stu-id="3a876-176">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="3a876-177">Use linhas em branco em funções, moderação, para indicar seções lógicas.</span><span class="sxs-lookup"><span data-stu-id="3a876-177">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="3a876-178">Comentários de formatação</span><span class="sxs-lookup"><span data-stu-id="3a876-178">Formatting comments</span></span>

<span data-ttu-id="3a876-179">Geralmente prefira vários comentários barra dupla comentários do bloco de estilo ML.</span><span class="sxs-lookup"><span data-stu-id="3a876-179">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    Generally avoid these kinds of comments.
*)
```

<span data-ttu-id="3a876-180">Comentários in-line devem colocar em maiuscula a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="3a876-180">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="3a876-181">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="3a876-181">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="3a876-182">Use camelCase para funções e os valores associados de classe, associadas a expressão e limite padrão</span><span class="sxs-lookup"><span data-stu-id="3a876-182">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="3a876-183">É comum e aceita F # estilo a ser usado em camelCase todos os nomes associados como variáveis locais ou em correspondências de padrão e as definições de função.</span><span class="sxs-lookup"><span data-stu-id="3a876-183">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="3a876-184">Funções associadas a localmente em classes também devem usar camelCase.</span><span class="sxs-lookup"><span data-stu-id="3a876-184">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="3a876-185">Use camelCase para funções e os valores de limite de módulo internos e privados</span><span class="sxs-lookup"><span data-stu-id="3a876-185">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="3a876-186">Use camelCase para valores de limite de módulo privados, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3a876-186">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="3a876-187">Funções ad hoc em scripts</span><span class="sxs-lookup"><span data-stu-id="3a876-187">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="3a876-188">Valores que compõem a implementação interna de um módulo ou tipo</span><span class="sxs-lookup"><span data-stu-id="3a876-188">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="3a876-189">Use camelCase para parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a876-189">Use camelCase for parameters</span></span>

<span data-ttu-id="3a876-190">Todos os parâmetros devem usar camelCase de acordo com as convenções de nomenclatura do .NET.</span><span class="sxs-lookup"><span data-stu-id="3a876-190">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="3a876-191">Use PascalCase para módulos</span><span class="sxs-lookup"><span data-stu-id="3a876-191">Use PascalCase for modules</span></span>

<span data-ttu-id="3a876-192">Todos os módulos (nível superior, internos, privados, aninhados) devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="3a876-192">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="3a876-193">Use PascalCase para declarações de tipo, membros e rótulos</span><span class="sxs-lookup"><span data-stu-id="3a876-193">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="3a876-194">Classes, interfaces, estruturas, enumerações, delegados, registros e uniões discriminadas devem ser chamados com PascalCase.</span><span class="sxs-lookup"><span data-stu-id="3a876-194">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="3a876-195">Membros de tipos e rótulos para registros e uniões discriminadas também devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="3a876-195">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="3a876-196">Use PascalCase para construções intrínsecas para .NET</span><span class="sxs-lookup"><span data-stu-id="3a876-196">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="3a876-197">Namespaces, exceções, eventos e projeto /`.dll` nomes também devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="3a876-197">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="3a876-198">Não apenas isso faz o consumo de outras linguagens .NET bem mais fácil para os consumidores, também é consistente com as convenções de nomenclatura de .NET probabilidade de encontrar.</span><span class="sxs-lookup"><span data-stu-id="3a876-198">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="3a876-199">Evite sublinhados em nomes</span><span class="sxs-lookup"><span data-stu-id="3a876-199">Avoid underscores in names</span></span>

<span data-ttu-id="3a876-200">Historicamente, algumas bibliotecas F # usou sublinhados em nomes.</span><span class="sxs-lookup"><span data-stu-id="3a876-200">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="3a876-201">No entanto, isso não é mais amplamente é aceito, em parte porque entrar em conflito com as convenções de nomenclatura do .NET.</span><span class="sxs-lookup"><span data-stu-id="3a876-201">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="3a876-202">Dito isso, alguns programadores F # usam sublinhados intensamente, parcialmente por razões históricas e tolerância e respeito é importante.</span><span class="sxs-lookup"><span data-stu-id="3a876-202">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="3a876-203">No entanto, lembre-se de que o estilo é geralmente disliked por outras pessoas que têm a opção de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="3a876-203">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="3a876-204">Algumas exceções inclui interagir com componentes nativos, onde sublinhados são muito comuns.</span><span class="sxs-lookup"><span data-stu-id="3a876-204">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="3a876-205">Use operadores padrão F #</span><span class="sxs-lookup"><span data-stu-id="3a876-205">Use standard F# operators</span></span>

<span data-ttu-id="3a876-206">Os operadores a seguir são definidos na biblioteca padrão do F # e devem ser usados em vez de definir equivalentes.</span><span class="sxs-lookup"><span data-stu-id="3a876-206">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="3a876-207">Usar esses operadores é recomendado conforme ele tende a tornar o código mais legível e idiomática.</span><span class="sxs-lookup"><span data-stu-id="3a876-207">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="3a876-208">Os desenvolvedores com um plano de fundo em OCaml ou outra linguagem de programação funcional podem estar acostumados a idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="3a876-208">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="3a876-209">A lista a seguir resume os operadores de F # recomendados.</span><span class="sxs-lookup"><span data-stu-id="3a876-209">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Throwing away a value
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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="3a876-210">Use a sintaxe de prefixo para genéricos (`Foo<T>`) em vez da sintaxe de sufixo (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="3a876-210">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="3a876-211">F # herda ambos o estilo de ML sufixo de nomeação de tipos genéricos (por exemplo, `int list`), bem como o prefixo de estilo do .NET (por exemplo, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="3a876-211">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="3a876-212">Preferir o estilo do .NET, exceto os quatro tipos específicos:</span><span class="sxs-lookup"><span data-stu-id="3a876-212">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="3a876-213">Para F # lista, use o formulário de sufixo: `int list` em vez de `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="3a876-213">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="3a876-214">Para opções de F #, use o formulário de sufixo: `int option` em vez de `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="3a876-214">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="3a876-215">Para matrizes de F #, use o nome sintático `int[]` em vez de `int array` ou `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="3a876-215">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="3a876-216">Para fazer referência a células, use `int ref` em vez de `ref<int>` ou `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="3a876-216">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="3a876-217">Para todos os outros tipos, use o formulário de prefixo.</span><span class="sxs-lookup"><span data-stu-id="3a876-217">For all other types, use the prefix form.</span></span>
