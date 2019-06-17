---
title: Registros anônimos
description: Saiba como usar a construção e usar registros anônimos, um recurso de linguagem que ajuda com a manipulação de dados.
ms.date: 06/12/2019
ms.openlocfilehash: e576210d4fb76ccfd09f8feb157ef4542aa94ccf
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041800"
---
# <a name="anonymous-records"></a><span data-ttu-id="df061-103">Registros anônimos</span><span class="sxs-lookup"><span data-stu-id="df061-103">Anonymous Records</span></span>

<span data-ttu-id="df061-104">Registros anônimos são agregações simples de valores nomeados que não precisam ser declarados antes do uso.</span><span class="sxs-lookup"><span data-stu-id="df061-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="df061-105">Você pode declará-los como tipos de structs ou referência.</span><span class="sxs-lookup"><span data-stu-id="df061-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="df061-106">Eles são tipos de referência por padrão.</span><span class="sxs-lookup"><span data-stu-id="df061-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="df061-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df061-107">Syntax</span></span>

<span data-ttu-id="df061-108">Os exemplos a seguir demonstram a sintaxe de registro anônimo.</span><span class="sxs-lookup"><span data-stu-id="df061-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="df061-109">Itens delimitada como `[item]` são opcionais.</span><span class="sxs-lookup"><span data-stu-id="df061-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="df061-110">Uso básico</span><span class="sxs-lookup"><span data-stu-id="df061-110">Basic usage</span></span>

<span data-ttu-id="df061-111">Registros anônimos são mais bem pensados como F# tipos que não precisam ser declarada antes da instanciação de registro.</span><span class="sxs-lookup"><span data-stu-id="df061-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="df061-112">Por exemplo, aqui como você pode interagir com uma função que gera um registro anônimo:</span><span class="sxs-lookup"><span data-stu-id="df061-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="df061-113">O exemplo a seguir expande no anterior com um `printCircleStats` função que usa um registro anônimo como entrada:</span><span class="sxs-lookup"><span data-stu-id="df061-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="df061-114">Chamar `printCircleStats` com qualquer tipo de registro anônimo que não tem a mesma "forma" como o tipo de entrada não será compilado:</span><span class="sxs-lookup"><span data-stu-id="df061-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="df061-115">Registros de struct anônimos</span><span class="sxs-lookup"><span data-stu-id="df061-115">Struct anonymous records</span></span>

<span data-ttu-id="df061-116">Registros anônimos também podem ser definidos como struct com opcional `struct` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="df061-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="df061-117">O exemplo a seguir aumenta aquele anterior, produzindo e consumindo um registro de struct anônimo:</span><span class="sxs-lookup"><span data-stu-id="df061-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="df061-118">Inferência de tipos Structness</span><span class="sxs-lookup"><span data-stu-id="df061-118">Structness inference</span></span>

<span data-ttu-id="df061-119">Registros de struct anônimos também permitem a "structness inferência" em que você não precisará especificar o `struct` palavra-chave no site de chamada.</span><span class="sxs-lookup"><span data-stu-id="df061-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="df061-120">Neste exemplo, você elide a `struct` palavra-chave ao chamar `printCircleStats`:</span><span class="sxs-lookup"><span data-stu-id="df061-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="df061-121">O inverso de padrão - especificando `struct` quando o tipo de entrada não é um registro de struct anônimo - não será compilado.</span><span class="sxs-lookup"><span data-stu-id="df061-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="df061-122">Inserindo registros anônimos dentro de outros tipos</span><span class="sxs-lookup"><span data-stu-id="df061-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="df061-123">É útil declarar [uniões discriminadas](discriminated-unions.md) cujas maiusculas e minúsculas são registros.</span><span class="sxs-lookup"><span data-stu-id="df061-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="df061-124">Mas, se os dados em registros forem do mesmo tipo que a união discriminada, você deve definir todos os tipos como mutuamente recursivas.</span><span class="sxs-lookup"><span data-stu-id="df061-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="df061-125">O uso de registros anônimos evita essa restrição.</span><span class="sxs-lookup"><span data-stu-id="df061-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="df061-126">A seguir está um exemplo de tipo e a função corresponde a esse padrão sobre ele:</span><span class="sxs-lookup"><span data-stu-id="df061-126">What follows is an example type and function that pattern matches over it:</span></span>

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named for Manager and Executive would require mutually recursive definitions.
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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="df061-127">Copiar e atualizar expressões</span><span class="sxs-lookup"><span data-stu-id="df061-127">Copy and update expressions</span></span>

<span data-ttu-id="df061-128">Construção com suportam a registros anônimos [copiar e atualizar expressões](copy-and-update-record-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="df061-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="df061-129">Por exemplo, aqui está como você pode construir uma nova instância de um registro anônimo que copia um existente de dados:</span><span class="sxs-lookup"><span data-stu-id="df061-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="df061-130">No entanto, diferentemente nomeados registros, registros anônimos permitem construir formulários totalmente diferentes com cópia e atualizar expressões.</span><span class="sxs-lookup"><span data-stu-id="df061-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="df061-131">O exemplo a seguir usa o mesmo registro anônimo do exemplo anterior e expandi-la em um novo registro anônimo:</span><span class="sxs-lookup"><span data-stu-id="df061-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="df061-132">Também é possível construir registros anônimos de instâncias de registros nomeados:</span><span class="sxs-lookup"><span data-stu-id="df061-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="df061-133">Você também pode copiar dados para e de referência e struct registros anônimos:</span><span class="sxs-lookup"><span data-stu-id="df061-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="df061-134">Propriedades de registros anônimos</span><span class="sxs-lookup"><span data-stu-id="df061-134">Properties of anonymous records</span></span>

<span data-ttu-id="df061-135">Registros anônimos têm uma série de características que são essenciais para compreender totalmente como eles podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="df061-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="df061-136">Registros anônimos são nominais</span><span class="sxs-lookup"><span data-stu-id="df061-136">Anonymous records are nominal</span></span>

<span data-ttu-id="df061-137">Registros anônimos são [tipos de substantivo](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="df061-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="df061-138">Eles são mais bem considerados como denominada [registro](records.md) tipos (que também são nominais) que não exigem uma declaração inicial.</span><span class="sxs-lookup"><span data-stu-id="df061-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="df061-139">Considere o exemplo a seguir com duas declarações de registro anônimo:</span><span class="sxs-lookup"><span data-stu-id="df061-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="df061-140">O `x` e `y` valores têm tipos diferentes e não são compatíveis entre si.</span><span class="sxs-lookup"><span data-stu-id="df061-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="df061-141">Eles não são equacionável, e não são comparáveis.</span><span class="sxs-lookup"><span data-stu-id="df061-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="df061-142">Para ilustrar isso, considere um registro nomeado equivalente:</span><span class="sxs-lookup"><span data-stu-id="df061-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="df061-143">Não há nada inerentemente diferente sobre registros anônimos em comparação com seus equivalentes de registro nomeado quando relativas a equivalência de tipo ou comparação.</span><span class="sxs-lookup"><span data-stu-id="df061-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="df061-144">Registros anônimos, use comparação e igualdade estrutural</span><span class="sxs-lookup"><span data-stu-id="df061-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="df061-145">Como os tipos de registros, registros anônimos são estruturalmente equacionável e pode ser comparado.</span><span class="sxs-lookup"><span data-stu-id="df061-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="df061-146">Isso só é true se todos os tipos constituintes suportam igualdade e comparação, como com tipos de registro.</span><span class="sxs-lookup"><span data-stu-id="df061-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="df061-147">Para dar suporte à igualdade ou comparação, os dois registros anônimos devem ter a mesma "forma".</span><span class="sxs-lookup"><span data-stu-id="df061-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="df061-148">Registros anônimos são serializáveis</span><span class="sxs-lookup"><span data-stu-id="df061-148">Anonymous records are serializable</span></span>

<span data-ttu-id="df061-149">Você pode serializar registros anônimos, exatamente como é possível com registros nomeados.</span><span class="sxs-lookup"><span data-stu-id="df061-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="df061-150">Aqui está um exemplo usando [newtonsoft. JSON](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="df061-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="df061-151">Registros anônimos são úteis para envio de dados leves em uma rede sem a necessidade de definir um domínio para seus tipos serializados/desserializados com antecedência.</span><span class="sxs-lookup"><span data-stu-id="df061-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="df061-152">Registros anônimos interoperam com C# tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="df061-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="df061-153">É possível usar uma API .NET que requer o uso de [ C# tipos anônimos](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="df061-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="df061-154">C#tipos anônimos são simples de interoperar com usando registros anônimos.</span><span class="sxs-lookup"><span data-stu-id="df061-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="df061-155">O exemplo a seguir mostra como usar registros anônimos para chamar um [LINQ](../../csharp/programming-guide/concepts/linq/index.md) sobrecarga que requer um tipo anônimo:</span><span class="sxs-lookup"><span data-stu-id="df061-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="df061-156">Há uma variedade de outras APIs usadas em todo o .NET que exigem o uso de passagem em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="df061-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="df061-157">Registros anônimos são a sua ferramenta para trabalhar com eles.</span><span class="sxs-lookup"><span data-stu-id="df061-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="df061-158">Limitações</span><span class="sxs-lookup"><span data-stu-id="df061-158">Limitations</span></span>

<span data-ttu-id="df061-159">Registros anônimos têm algumas restrições em seu uso.</span><span class="sxs-lookup"><span data-stu-id="df061-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="df061-160">Algumas são inerentes ao seu design, mas outros são receptivos a alterar.</span><span class="sxs-lookup"><span data-stu-id="df061-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="df061-161">Limitações com correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="df061-161">Limitations with pattern matching</span></span>

<span data-ttu-id="df061-162">Registros anônimos não têm suporte para a correspondência de padrão, ao contrário de registros nomeados.</span><span class="sxs-lookup"><span data-stu-id="df061-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="df061-163">Há três motivos:</span><span class="sxs-lookup"><span data-stu-id="df061-163">There are three reasons:</span></span>

1. <span data-ttu-id="df061-164">Um padrão de teria para levar em conta todos os campos de registro anônimo, diferentemente dos tipos de registro nomeado.</span><span class="sxs-lookup"><span data-stu-id="df061-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="df061-165">Isso ocorre porque os registros anônimos não têm suporte para o subtipo estrutural: eles são tipos de substantivo.</span><span class="sxs-lookup"><span data-stu-id="df061-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="df061-166">Por causa de (1), não é possível ter padrões adicionais em uma expressão de correspondência de padrão, como cada padrão distinto implicariam um tipo de registro diferente de anônimo.</span><span class="sxs-lookup"><span data-stu-id="df061-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="df061-167">Por causa de (3), qualquer padrão de registro anônimo seria mais detalhado do que o uso da notação "dot".</span><span class="sxs-lookup"><span data-stu-id="df061-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="df061-168">Há uma sugestão de linguagem aberta para [permitir correspondência de padrões em limitado contextos](https://github.com/fsharp/fslang-suggestions/issues/713).</span><span class="sxs-lookup"><span data-stu-id="df061-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="df061-169">Limitações com Mutabilidade</span><span class="sxs-lookup"><span data-stu-id="df061-169">Limitations with mutability</span></span>

<span data-ttu-id="df061-170">Não é possível no momento definir um registro anônimo com `mutable` dados.</span><span class="sxs-lookup"><span data-stu-id="df061-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="df061-171">Há um [abrir sugestão de linguagem](https://github.com/fsharp/fslang-suggestions/issues/732) para permitir que dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="df061-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="df061-172">Limitações com registros de struct anônimo</span><span class="sxs-lookup"><span data-stu-id="df061-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="df061-173">Não é possível declarar struct anônimos registros conforme `IsByRefLike` ou `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="df061-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="df061-174">Há um [abrir sugestão de linguagem](https://github.com/fsharp/fslang-suggestions/issues/712) para `IsByRefLike` e `IsReadOnly` registros anônimos.</span><span class="sxs-lookup"><span data-stu-id="df061-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
