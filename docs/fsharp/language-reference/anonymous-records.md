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
# <a name="anonymous-records"></a>Registros Anônimos

Registros anônimos são agregados simples de valores nomeados que não precisam ser declarados antes do uso. Você pode declará-los como estruturas ou tipos de referência. São tipos de referência por padrão.

## <a name="syntax"></a>Sintaxe

Os exemplos a seguir demonstram a sintaxe de registro anônimo. Itens delimitados `[item]` como são opcionais.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Uso básico

Registros anônimos são melhor pensados como tipos de registro F# que não precisam ser declarados antes da instanciação.

Por exemplo, aqui como você pode interagir com uma função que produz um registro anônimo:

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

O exemplo a seguir se expande no anterior com uma `printCircleStats` função que toma um registro anônimo como entrada:

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

Ligar `printCircleStats` com qualquer tipo de registro anônimo que não tenha a mesma "forma" que o tipo de entrada falhará em compilar:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Struct registros anônimos

Registros anônimos também podem ser definidos `struct` como struct com a palavra-chave opcional. O exemplo a seguir aumenta o anterior, produzindo e consumindo um registro anônimo de estrutura:

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

### <a name="structness-inference"></a>Inferência de estrutura

Os registros anônimos também permitem "inferência de estrutura" onde você `struct` não precisa especificar a palavra-chave no local de chamada. Neste exemplo, você elide a `struct` `printCircleStats`palavra-chave ao chamar:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

O padrão inverso `struct` - especificando quando o tipo de entrada não é um registro anônimo de estruturação - falhará em compilar.

## <a name="embedding-anonymous-records-within-other-types"></a>Incorporando registros anônimos dentro de outros tipos

É útil declarar [sindicatos discriminados](discriminated-unions.md) cujos casos são registros. Mas se os dados nos registros são do mesmo tipo da união discriminada, você deve definir todos os tipos como mutuamente recursivos. O uso de registros anônimos evita essa restrição. O que se segue é um exemplo de tipo e função que o padrão corresponde sobre ele:

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

## <a name="copy-and-update-expressions"></a>Copiar e atualizar expressões

Registros anônimos suportam construção com [expressões de cópia e atualização](copy-and-update-record-expressions.md). Por exemplo, aqui está como você pode construir uma nova instância de um registro anônimo que copia os dados de um existente:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

No entanto, ao contrário dos registros nomeados, os registros anônimos permitem que você construa formas completamente diferentes com expressões de cópia e atualização. O exemplo a seguir pega o mesmo registro anônimo do exemplo anterior e o expande para um novo registro anônimo:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Também é possível construir registros anônimos a partir de instâncias de registros nomeados:

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Você também pode copiar dados para e a partir de referências e estruturar registros anônimos:

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

Os registros anônimos têm uma série de características que são essenciais para entender completamente como eles podem ser usados.

### <a name="anonymous-records-are-nominal"></a>Registros anônimos são nominais

Registros anônimos são [tipos nominais.](https://en.wikipedia.org/wiki/Nominal_type_system) Eles são melhor pensados como tipos [de registro](records.md) nomeados (que também são nominais) que não exigem uma declaração antecipada.

Considere o seguinte exemplo com duas declarações de registro anônimo:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

Os `x` `y` e valores têm tipos diferentes e não são compatíveis uns com os outros. Eles não são equatáveis e não são comparáveis. Para ilustrar isso, considere um equivalente de registro nomeado:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Não há nada inerentemente diferente sobre registros anônimos quando comparado com seus equivalentes de registro nomeados quando se trata de equivalência de tipo ou comparação.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Registros anônimos usam igualdade estrutural e comparação

Como tipos de registros, registros anônimos são estruturalmente equatáveis e comparáveis. Isso só é verdade se todos os tipos de constituintes apoiarem a igualdade e a comparação, como com os tipos de registros. Para apoiar a igualdade ou comparação, dois registros anônimos devem ter a mesma "forma".

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Registros anônimos são serializáveis

Você pode serializar registros anônimos assim como você pode com registros nomeados. Aqui está um exemplo usando [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Registros anônimos são úteis para enviar dados leves por uma rede sem a necessidade de definir um domínio para seus tipos serializados/desserializados antecipadamente.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Registros anônimos interoperam com tipos anônimos C#

É possível usar uma API .NET que requer o uso de [tipos anônimos C#](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). C# tipos anônimos são triviais para interoperar usando registros anônimos. O exemplo a seguir mostra como usar registros anônimos para ligar para uma sobrecarga [linq](../../csharp/programming-guide/concepts/linq/index.md) que requer um tipo anônimo:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Há uma infinidade de outras APIs usadas em todo .NET que requerem o uso de passagem em um tipo anônimo. Registros anônimos são sua ferramenta para trabalhar com eles.

## <a name="limitations"></a>Limitações

Registros anônimos têm algumas restrições em seu uso. Alguns são inerentes ao seu design, mas outros são passíveis de mudança.

### <a name="limitations-with-pattern-matching"></a>Limitações com correspondência de padrões

Registros anônimos não suportam correspondência de padrões, ao contrário dos registros nomeados. Há três razões:

1. Um padrão teria que explicar cada campo de um registro anônimo, ao contrário dos tipos de registros nomeados. Isso porque os registros anônimos não suportam subtipagem estrutural – são tipos nominais.
2. Por causa de (1), não há capacidade de ter padrões adicionais em uma expressão de correspondência de padrão, pois cada padrão distinto implicaria um tipo de registro anônimo diferente.
3. Por causa de (3), qualquer padrão de registro anônimo seria mais verboso do que o uso de notação "dot".

Há uma sugestão de linguagem aberta para permitir a [correspondência de padrões em contextos limitados.](https://github.com/fsharp/fslang-suggestions/issues/713)

### <a name="limitations-with-mutability"></a>Limitações com mutabilidade

Atualmente, não é possível definir `mutable` um registro anônimo com dados. Há uma [sugestão de linguagem aberta](https://github.com/fsharp/fslang-suggestions/issues/732) para permitir dados mutáveis.

### <a name="limitations-with-struct-anonymous-records"></a>Limitações com registros anônimos de estrutura

Não é possível declarar registros anônimos `IsByRefLike` `IsReadOnly`de estruturação como ou . Há uma sugestão de `IsByRefLike` idioma `IsReadOnly` [aberto](https://github.com/fsharp/fslang-suggestions/issues/712) para registros anônimos e anônimos.
