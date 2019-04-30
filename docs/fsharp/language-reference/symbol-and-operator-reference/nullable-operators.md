---
title: Operadores anuláveis
description: Saiba mais sobre os operadores que permitem valor nulos que estão disponíveis no F# linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: b17c0de2d81a1ef88b31d833a49ff9e3f9d34e8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960453"
---
# <a name="nullable-operators"></a>Operadores anuláveis

Operadores anuláveis são operadores binários de comparação ou aritmética que funcionam com tipos aritméticos que permitem valor nulos em um ou ambos os lados. Tipos anuláveis surgem com frequência quando você trabalha com dados de fontes, como bancos de dados que permitem valores nulos no lugar de valores reais. Operadores anuláveis costumam ser usadas em expressões de consulta. Além dos operadores que permitem valor nulos para comparação e aritméticos, operadores de conversão podem ser usados para converter entre tipos anuláveis. Também há versões anuláveis de determinados operadores de consulta.

## <a name="table-of-nullable-operators"></a>Tabela de operadores que permitem valor nulos

A tabela a seguir lista os operadores que permitem valor nulos tem suportadas no F# idioma.

|Permite valor nulo à esquerda|Permite valor nulo à direita|Ambos os lados que permitem valor nulos|
|---|---|---|
|[?>=](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[>=?](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[?>=?](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[?>](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[>?](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[?>?](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[?<=](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[<=?](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[?<=?](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[?<](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<?](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[?<?](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[?<>](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[<>?](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[?<>?](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>Comentários

Os operadores que permitem valor nulos são incluídos na [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) módulo no namespace [FSharp](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d). O tipo de dados que permitem valor nulos é `System.Nullable<'T>`.

Em expressões de consulta, tipos anuláveis, podem surgir ao selecionar os dados de uma fonte de dados que permite valores nulos em vez de valores. Em um banco de dados do SQL Server, cada coluna de dados em uma tabela tem um atributo que indica se valores nulos são permitidos. Se valores nulos são permitidos, os dados retornados do banco de dados podem conter valores nulos que não podem ser representados por um tipo de dados primitivos como `int`, `float`e assim por diante. Portanto, os dados são retornados como uma `System.Nullable<int>` em vez de `int`, e `System.Nullable<float>` em vez de `float`. O valor real pode ser obtido de um `System.Nullable<'T>` objeto usando o `Value` propriedade e você pode determinar se um `System.Nullable<'T>` objeto tem um valor chamando o `HasValue` método. Outro método útil é o `System.Nullable<'T>.GetValueOrDefault` método, que permite que você obtenha o valor ou um valor padrão do tipo apropriado. O valor padrão é de alguma forma de valor de "zero", como 0, 0,0, ou `false`.

Tipos anuláveis podem ser convertidos para tipos primitivos não anuláveis, usando os operadores de conversão usuais, como `int` ou `float`. Também é possível converter de um tipo que permite valor nulo em outro tipo anulável, usando os operadores de conversão para tipos anuláveis. Os operadores de conversão apropriada têm o mesmo nome como padrão, mas eles estão em um módulo separado, o [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) módulo na [FSharp](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) namespace. Normalmente, você abrir esse espaço para nome ao trabalhar com expressões de consulta. Nesse caso, você pode usar os operadores de conversão que permitem valor nulo, adicionando o prefixo `Nullable.` para o operador de conversão apropriada, conforme mostrado no código a seguir.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

A saída é `10.000000`.

Consulta operadores nos campos de dados que permite valor nulo, tais como `sumByNullable`, também existem para uso em expressões de consulta. Os operadores de consulta para tipos não anuláveis não são tipo compatível com tipos anuláveis, então você deve usar a versão que permite valor nula do operador de consulta apropriado quando você estiver trabalhando com valores de dados que permite valor nulo. Para obter mais informações, consulte [expressões de consulta](../query-expressions.md).

O exemplo a seguir mostra o uso de operadores que permitem valor nulos em um F# expressão de consulta. A primeira consulta mostra como você escreveria uma consulta sem um operador que permite valor nulo; a segunda consulta mostra uma consulta equivalente que usa um operador que permite valor nulo. Para o contexto completo, incluindo como configurar o banco de dados para usar esse código de exemplo, consulte [passo a passo: Acessando um banco de dados SQL por meio de provedores de tipos](../../tutorials/type-providers/accessing-a-sql-database.md).

```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq

[<Generate>]
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">

let db = dbSchema.GetDataContext()

query {
    for row in db.Table2 do
    where (row.TestData1.HasValue && row.TestData1.Value > 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
    for row in db.Table2 do
    // Use a nullable operator ?>
    where (row.TestData1 ?> 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="see-also"></a>Consulte também

- [Provedores de Tipos](../../tutorials/type-providers/index.md)
- [Expressões de Consulta](../query-expressions.md)