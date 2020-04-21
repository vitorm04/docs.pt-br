---
title: Registros Anônimos
description: Aprenda a usar o Anonymous Records, um recurso de linguagem que ajuda na manipulação de dados.
ms.date: 06/12/2019
ms.openlocfilehash: 121f0f638dff2ae529b2488d8e3b1ad9c064cf90
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738498"
---
# <a name="anonymous-records"></a><span data-ttu-id="33a91-103">Registros Anônimos</span><span class="sxs-lookup"><span data-stu-id="33a91-103">Anonymous Records</span></span>

<span data-ttu-id="33a91-104">Registros anônimos são agregados simples de valores nomeados que não precisam ser declarados antes do uso.</span><span class="sxs-lookup"><span data-stu-id="33a91-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="33a91-105">Você pode declará-los como estruturas ou tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="33a91-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="33a91-106">São tipos de referência por padrão.</span><span class="sxs-lookup"><span data-stu-id="33a91-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="33a91-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33a91-107">Syntax</span></span>

<span data-ttu-id="33a91-108">Os exemplos a seguir demonstram a sintaxe de registro anônimo.</span><span class="sxs-lookup"><span data-stu-id="33a91-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="33a91-109">Itens delimitados `[item]` como são opcionais.</span><span class="sxs-lookup"><span data-stu-id="33a91-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="33a91-110">Uso básico</span><span class="sxs-lookup"><span data-stu-id="33a91-110">Basic usage</span></span>

<span data-ttu-id="33a91-111">Registros anônimos são melhor pensados como tipos de registro F# que não precisam ser declarados antes da instanciação.</span><span class="sxs-lookup"><span data-stu-id="33a91-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="33a91-112">Por exemplo, aqui como você pode interagir com uma função que produz um registro anônimo:</span><span class="sxs-lookup"><span data-stu-id="33a91-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

<span data-ttu-id="33a91-113">O exemplo a seguir se expande no anterior com uma `printCircleStats` função que toma um registro anônimo como entrada:</span><span class="sxs-lookup"><span data-stu-id="33a91-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let printCircleStats r (stats: {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

<span data-ttu-id="33a91-114">Ligar `printCircleStats` com qualquer tipo de registro anônimo que não tenha a mesma "forma" que o tipo de entrada falhará em compilar:</span><span class="sxs-lookup"><span data-stu-id="33a91-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="33a91-115">Struct registros anônimos</span><span class="sxs-lookup"><span data-stu-id="33a91-115">Struct anonymous records</span></span>

<span data-ttu-id="33a91-116">Registros anônimos também podem ser definidos `struct` como struct com a palavra-chave opcional.</span><span class="sxs-lookup"><span data-stu-id="33a91-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="33a91-117">O exemplo a seguir aumenta o anterior, produzindo e consumindo um registro anônimo de estrutura:</span><span class="sxs-lookup"><span data-stu-id="33a91-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    // Note that the keyword comes before the '{| |}' brace pair
    struct {| Area = a; Circumference = c; Diameter = d |}

// the 'struct' keyword also comes before the '{| |}' brace pair when declaring the parameter type
let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

### <a name="structness-inference"></a><span data-ttu-id="33a91-118">Inferência de estrutura</span><span class="sxs-lookup"><span data-stu-id="33a91-118">Structness inference</span></span>

<span data-ttu-id="33a91-119">Os registros anônimos também permitem "inferência de estrutura" onde você `struct` não precisa especificar a palavra-chave no local de chamada.</span><span class="sxs-lookup"><span data-stu-id="33a91-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="33a91-120">Neste exemplo, você elide a `struct` `printCircleStats`palavra-chave ao chamar:</span><span class="sxs-lookup"><span data-stu-id="33a91-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="33a91-121">O padrão inverso `struct` - especificando quando o tipo de entrada não é um registro anônimo de estruturação - falhará em compilar.</span><span class="sxs-lookup"><span data-stu-id="33a91-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="33a91-122">Incorporando registros anônimos dentro de outros tipos</span><span class="sxs-lookup"><span data-stu-id="33a91-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="33a91-123">É útil declarar [sindicatos discriminados](discriminated-unions.md) cujos casos são registros.</span><span class="sxs-lookup"><span data-stu-id="33a91-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="33a91-124">Mas se os dados nos registros são do mesmo tipo da união discriminada, você deve definir todos os tipos como mutuamente recursivos.</span><span class="sxs-lookup"><span data-stu-id="33a91-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="33a91-125">O uso de registros anônimos evita essa restrição.</span><span class="sxs-lookup"><span data-stu-id="33a91-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="33a91-126">O que se segue é um exemplo de tipo e função que o padrão corresponde sobre ele:</span><span class="sxs-lookup"><span data-stu-id="33a91-126">What follows is an example type and function that pattern matches over it:</span></span>

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named record for Manager and Executive would require mutually recursive definitions.
type Employee =
    | Engineer of FullName
    | Manager of {| Name: FullName; Reports: Employee list |}
    | Executive of {| Name: FullName; Reports: Employee list; Assistant: Employee |}

let getFirstName e =
    match e with
    | Engineer fullName -> fullName.FirstName
    | Manager m -> m.Name.FirstName
    | Executive ex -> ex.Name.FirstName
```

## <a name="copy-and-update-expressions"></a><span data-ttu-id="33a91-127">Copiar e atualizar expressões</span><span class="sxs-lookup"><span data-stu-id="33a91-127">Copy and update expressions</span></span>

<span data-ttu-id="33a91-128">Registros anônimos suportam construção com [expressões de cópia e atualização](copy-and-update-record-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="33a91-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="33a91-129">Por exemplo, aqui está como você pode construir uma nova instância de um registro anônimo que copia os dados de um existente:</span><span class="sxs-lookup"><span data-stu-id="33a91-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="33a91-130">No entanto, ao contrário dos registros nomeados, os registros anônimos permitem que você construa formas completamente diferentes com expressões de cópia e atualização.</span><span class="sxs-lookup"><span data-stu-id="33a91-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="33a91-131">O exemplo a seguir pega o mesmo registro anônimo do exemplo anterior e o expande para um novo registro anônimo:</span><span class="sxs-lookup"><span data-stu-id="33a91-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="33a91-132">Também é possível construir registros anônimos a partir de instâncias de registros nomeados:</span><span class="sxs-lookup"><span data-stu-id="33a91-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="33a91-133">Você também pode copiar dados para e a partir de referências e estruturar registros anônimos:</span><span class="sxs-lookup"><span data-stu-id="33a91-133">You can also copy data to and from reference and struct anonymous records:</span></span>

```fsharp
// Copy data from a reference record into a struct anonymous record
type R1 = { X: int }
let r1 = { X = 1 }

let data1 = struct {| r1 with Y = 1 |}

// Copy data from a struct record into a reference anonymous record
[<Struct>]
type R2 = { X: int }
let r2 = { X = 1 }

let data2 = {| r1 with Y = 1 |}

// Copy the reference anonymous record data into a struct anonymous record
let data3 = struct {| data2 with Z = r2.X |}
```

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="33a91-134">Propriedades de registros anônimos</span><span class="sxs-lookup"><span data-stu-id="33a91-134">Properties of anonymous records</span></span>

<span data-ttu-id="33a91-135">Os registros anônimos têm uma série de características que são essenciais para entender completamente como eles podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="33a91-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="33a91-136">Registros anônimos são nominais</span><span class="sxs-lookup"><span data-stu-id="33a91-136">Anonymous records are nominal</span></span>

<span data-ttu-id="33a91-137">Registros anônimos são [tipos nominais.](https://en.wikipedia.org/wiki/Nominal_type_system)</span><span class="sxs-lookup"><span data-stu-id="33a91-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="33a91-138">Eles são melhor pensados como tipos [de registro](records.md) nomeados (que também são nominais) que não exigem uma declaração antecipada.</span><span class="sxs-lookup"><span data-stu-id="33a91-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="33a91-139">Considere o seguinte exemplo com duas declarações de registro anônimo:</span><span class="sxs-lookup"><span data-stu-id="33a91-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="33a91-140">Os `x` `y` e valores têm tipos diferentes e não são compatíveis uns com os outros.</span><span class="sxs-lookup"><span data-stu-id="33a91-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="33a91-141">Eles não são equatáveis e não são comparáveis.</span><span class="sxs-lookup"><span data-stu-id="33a91-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="33a91-142">Para ilustrar isso, considere um equivalente de registro nomeado:</span><span class="sxs-lookup"><span data-stu-id="33a91-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="33a91-143">Não há nada inerentemente diferente sobre registros anônimos quando comparado com seus equivalentes de registro nomeados quando se trata de equivalência de tipo ou comparação.</span><span class="sxs-lookup"><span data-stu-id="33a91-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="33a91-144">Registros anônimos usam igualdade estrutural e comparação</span><span class="sxs-lookup"><span data-stu-id="33a91-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="33a91-145">Como tipos de registros, registros anônimos são estruturalmente equatáveis e comparáveis.</span><span class="sxs-lookup"><span data-stu-id="33a91-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="33a91-146">Isso só é verdade se todos os tipos de constituintes apoiarem a igualdade e a comparação, como com os tipos de registros.</span><span class="sxs-lookup"><span data-stu-id="33a91-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="33a91-147">Para apoiar a igualdade ou comparação, dois registros anônimos devem ter a mesma "forma".</span><span class="sxs-lookup"><span data-stu-id="33a91-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="33a91-148">Registros anônimos são serializáveis</span><span class="sxs-lookup"><span data-stu-id="33a91-148">Anonymous records are serializable</span></span>

<span data-ttu-id="33a91-149">Você pode serializar registros anônimos assim como você pode com registros nomeados.</span><span class="sxs-lookup"><span data-stu-id="33a91-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="33a91-150">Aqui está um exemplo usando [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="33a91-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="33a91-151">Registros anônimos são úteis para enviar dados leves por uma rede sem a necessidade de definir um domínio para seus tipos serializados/desserializados antecipadamente.</span><span class="sxs-lookup"><span data-stu-id="33a91-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="33a91-152">Registros anônimos interoperam com tipos anônimos C#</span><span class="sxs-lookup"><span data-stu-id="33a91-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="33a91-153">É possível usar uma API .NET que requer o uso de [tipos anônimos C#](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="33a91-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="33a91-154">C# tipos anônimos são triviais para interoperar usando registros anônimos.</span><span class="sxs-lookup"><span data-stu-id="33a91-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="33a91-155">O exemplo a seguir mostra como usar registros anônimos para ligar para uma sobrecarga [linq](../../csharp/programming-guide/concepts/linq/index.md) que requer um tipo anônimo:</span><span class="sxs-lookup"><span data-stu-id="33a91-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="33a91-156">Há uma infinidade de outras APIs usadas em todo .NET que requerem o uso de passagem em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="33a91-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="33a91-157">Registros anônimos são sua ferramenta para trabalhar com eles.</span><span class="sxs-lookup"><span data-stu-id="33a91-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="33a91-158">Limitações</span><span class="sxs-lookup"><span data-stu-id="33a91-158">Limitations</span></span>

<span data-ttu-id="33a91-159">Registros anônimos têm algumas restrições em seu uso.</span><span class="sxs-lookup"><span data-stu-id="33a91-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="33a91-160">Alguns são inerentes ao seu design, mas outros são passíveis de mudança.</span><span class="sxs-lookup"><span data-stu-id="33a91-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="33a91-161">Limitações com correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="33a91-161">Limitations with pattern matching</span></span>

<span data-ttu-id="33a91-162">Registros anônimos não suportam correspondência de padrões, ao contrário dos registros nomeados.</span><span class="sxs-lookup"><span data-stu-id="33a91-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="33a91-163">Há três razões:</span><span class="sxs-lookup"><span data-stu-id="33a91-163">There are three reasons:</span></span>

1. <span data-ttu-id="33a91-164">Um padrão teria que explicar cada campo de um registro anônimo, ao contrário dos tipos de registros nomeados.</span><span class="sxs-lookup"><span data-stu-id="33a91-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="33a91-165">Isso porque os registros anônimos não suportam subtipagem estrutural – são tipos nominais.</span><span class="sxs-lookup"><span data-stu-id="33a91-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="33a91-166">Por causa de (1), não há capacidade de ter padrões adicionais em uma expressão de correspondência de padrão, pois cada padrão distinto implicaria um tipo de registro anônimo diferente.</span><span class="sxs-lookup"><span data-stu-id="33a91-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="33a91-167">Por causa de (3), qualquer padrão de registro anônimo seria mais verboso do que o uso de notação "dot".</span><span class="sxs-lookup"><span data-stu-id="33a91-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="33a91-168">Há uma sugestão de linguagem aberta para permitir a [correspondência de padrões em contextos limitados.](https://github.com/fsharp/fslang-suggestions/issues/713)</span><span class="sxs-lookup"><span data-stu-id="33a91-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="33a91-169">Limitações com mutabilidade</span><span class="sxs-lookup"><span data-stu-id="33a91-169">Limitations with mutability</span></span>

<span data-ttu-id="33a91-170">Atualmente, não é possível definir `mutable` um registro anônimo com dados.</span><span class="sxs-lookup"><span data-stu-id="33a91-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="33a91-171">Há uma [sugestão de linguagem aberta](https://github.com/fsharp/fslang-suggestions/issues/732) para permitir dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="33a91-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="33a91-172">Limitações com registros anônimos de estrutura</span><span class="sxs-lookup"><span data-stu-id="33a91-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="33a91-173">Não é possível declarar registros anônimos `IsByRefLike` `IsReadOnly`de estruturação como ou .</span><span class="sxs-lookup"><span data-stu-id="33a91-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="33a91-174">Há uma sugestão de `IsByRefLike` idioma `IsReadOnly` [aberto](https://github.com/fsharp/fslang-suggestions/issues/712) para registros anônimos e anônimos.</span><span class="sxs-lookup"><span data-stu-id="33a91-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
