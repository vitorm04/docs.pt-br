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
# <a name="anonymous-records"></a>Registros anônimos

Registros anônimos são agregações simples de valores nomeados que não precisam ser declarados antes do uso. Você pode declará-los como tipos de structs ou referência. Eles são tipos de referência por padrão.

## <a name="syntax"></a>Sintaxe

Os exemplos a seguir demonstram a sintaxe de registro anônimo. Itens delimitada como `[item]` são opcionais.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Uso básico

Registros anônimos são mais bem pensados como F# tipos que não precisam ser declarada antes da instanciação de registro.

Por exemplo, aqui como você pode interagir com uma função que gera um registro anônimo:

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

O exemplo a seguir expande no anterior com um `printCircleStats` função que usa um registro anônimo como entrada:

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

Chamar `printCircleStats` com qualquer tipo de registro anônimo que não tem a mesma "forma" como o tipo de entrada não será compilado:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Registros de struct anônimos

Registros anônimos também podem ser definidos como struct com opcional `struct` palavra-chave. O exemplo a seguir aumenta aquele anterior, produzindo e consumindo um registro de struct anônimo:

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

### <a name="structness-inference"></a>Inferência de tipos Structness

Registros de struct anônimos também permitem a "structness inferência" em que você não precisará especificar o `struct` palavra-chave no site de chamada. Neste exemplo, você elide a `struct` palavra-chave ao chamar `printCircleStats`:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

O inverso de padrão - especificando `struct` quando o tipo de entrada não é um registro de struct anônimo - não será compilado.

## <a name="embedding-anonymous-records-within-other-types"></a>Inserindo registros anônimos dentro de outros tipos

É útil declarar [uniões discriminadas](discriminated-unions.md) cujas maiusculas e minúsculas são registros. Mas, se os dados em registros forem do mesmo tipo que a união discriminada, você deve definir todos os tipos como mutuamente recursivas. O uso de registros anônimos evita essa restrição. A seguir está um exemplo de tipo e a função corresponde a esse padrão sobre ele:

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

## <a name="copy-and-update-expressions"></a>Copiar e atualizar expressões

Construção com suportam a registros anônimos [copiar e atualizar expressões](copy-and-update-record-expressions.md). Por exemplo, aqui está como você pode construir uma nova instância de um registro anônimo que copia um existente de dados:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

No entanto, diferentemente nomeados registros, registros anônimos permitem construir formulários totalmente diferentes com cópia e atualizar expressões. O exemplo a seguir usa o mesmo registro anônimo do exemplo anterior e expandi-la em um novo registro anônimo:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Também é possível construir registros anônimos de instâncias de registros nomeados:

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Você também pode copiar dados para e de referência e struct registros anônimos:

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

## <a name="properties-of-anonymous-records"></a>Propriedades de registros anônimos

Registros anônimos têm uma série de características que são essenciais para compreender totalmente como eles podem ser usados.

### <a name="anonymous-records-are-nominal"></a>Registros anônimos são nominais

Registros anônimos são [tipos de substantivo](https://en.wikipedia.org/wiki/Nominal_type_system). Eles são mais bem considerados como denominada [registro](records.md) tipos (que também são nominais) que não exigem uma declaração inicial.

Considere o exemplo a seguir com duas declarações de registro anônimo:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

O `x` e `y` valores têm tipos diferentes e não são compatíveis entre si. Eles não são equacionável, e não são comparáveis. Para ilustrar isso, considere um registro nomeado equivalente:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Não há nada inerentemente diferente sobre registros anônimos em comparação com seus equivalentes de registro nomeado quando relativas a equivalência de tipo ou comparação.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Registros anônimos, use comparação e igualdade estrutural

Como os tipos de registros, registros anônimos são estruturalmente equacionável e pode ser comparado. Isso só é true se todos os tipos constituintes suportam igualdade e comparação, como com tipos de registro. Para dar suporte à igualdade ou comparação, os dois registros anônimos devem ter a mesma "forma".

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Registros anônimos são serializáveis

Você pode serializar registros anônimos, exatamente como é possível com registros nomeados. Aqui está um exemplo usando [newtonsoft. JSON](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Registros anônimos são úteis para envio de dados leves em uma rede sem a necessidade de definir um domínio para seus tipos serializados/desserializados com antecedência.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Registros anônimos interoperam com C# tipos anônimos

É possível usar uma API .NET que requer o uso de [ C# tipos anônimos](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). C#tipos anônimos são simples de interoperar com usando registros anônimos. O exemplo a seguir mostra como usar registros anônimos para chamar um [LINQ](../../csharp/programming-guide/concepts/linq/index.md) sobrecarga que requer um tipo anônimo:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Há uma variedade de outras APIs usadas em todo o .NET que exigem o uso de passagem em um tipo anônimo. Registros anônimos são a sua ferramenta para trabalhar com eles.

## <a name="limitations"></a>Limitações

Registros anônimos têm algumas restrições em seu uso. Algumas são inerentes ao seu design, mas outros são receptivos a alterar.

### <a name="limitations-with-pattern-matching"></a>Limitações com correspondência de padrões

Registros anônimos não têm suporte para a correspondência de padrão, ao contrário de registros nomeados. Há três motivos:

1. Um padrão de teria para levar em conta todos os campos de registro anônimo, diferentemente dos tipos de registro nomeado. Isso ocorre porque os registros anônimos não têm suporte para o subtipo estrutural: eles são tipos de substantivo.
2. Por causa de (1), não é possível ter padrões adicionais em uma expressão de correspondência de padrão, como cada padrão distinto implicariam um tipo de registro diferente de anônimo.
3. Por causa de (3), qualquer padrão de registro anônimo seria mais detalhado do que o uso da notação "dot".

Há uma sugestão de linguagem aberta para [permitir correspondência de padrões em limitado contextos](https://github.com/fsharp/fslang-suggestions/issues/713).

### <a name="limitations-with-mutability"></a>Limitações com Mutabilidade

Não é possível no momento definir um registro anônimo com `mutable` dados. Há um [abrir sugestão de linguagem](https://github.com/fsharp/fslang-suggestions/issues/732) para permitir que dados mutáveis.

### <a name="limitations-with-struct-anonymous-records"></a>Limitações com registros de struct anônimo

Não é possível declarar struct anônimos registros conforme `IsByRefLike` ou `IsReadOnly`. Há um [abrir sugestão de linguagem](https://github.com/fsharp/fslang-suggestions/issues/712) para `IsByRefLike` e `IsReadOnly` registros anônimos.
