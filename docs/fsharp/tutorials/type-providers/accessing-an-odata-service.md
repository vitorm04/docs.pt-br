---
title: "Instruções passo a passo: acessando um serviço OData por meio de provedores de tipos (F#)"
description: "Saiba como usar o provedor de tipos ODataService F # em F # 3.0 para gerar tipos de cliente para um serviço OData e feeds de dados que o serviço de consulta fornece."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0adae84c-b0fa-455f-994b-274ecdc6df30
ms.openlocfilehash: 750407c36a989cece30c0c0654ff905c8eee3b33
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-an-odata-service-by-using-type-providers"></a>Instruções passo a passo: acessando um serviço OData por meio de provedores de tipos

> [!NOTE]
Este guia foi escrito para F # 3.0 e será atualizado.  Consulte [FSharp.Data](https://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.

> [!NOTE]
Os links de referência de API levará você para o MSDN.  A referência da API docs.microsoft.com não está completa.

OData, que significa que o Open Data Protocol, é um protocolo de transferência de dados pela Internet. Muitos provedores de dados expõem o acesso aos dados publicando um serviço web OData. Você pode acessar dados de qualquer fonte OData em F # 3.0 usando tipos de dados que são gerados automaticamente pelo `ODataService` provedor de tipo. Para obter mais informações sobre o OData, consulte https://msdn.microsoft.com/library/da3380cc-f6da-4c6c-bdb2-bb86afa59d62.

Este passo a passo mostra como usar o provedor de tipos ODataService F # para gerar tipos de cliente para um serviço OData e feeds de dados que o serviço de consulta fornece.

Esse guia passo a passo ilustra as seguintes tarefas que você deve executar nesta ordem para que as instruções sejam bem-sucedidas:


- Configurando um projeto de cliente para um serviço OData
<br />

- Acessar tipos de OData
<br />

- Consultando um serviço OData
<br />

- Verificando as solicitações de OData
<br />


## <a name="configuring-a-client-project-for-an-odata-service"></a>Configurando um projeto de cliente para um serviço OData
Nesta etapa, você configura um projeto para usar um provedor de tipo OData.


#### <a name="to-configure-a-client-project-for-an-odata-service"></a>Para configurar um projeto de cliente para um serviço OData

- Abra um projeto de aplicativo de Console do F # e, em seguida, adicione uma referência para o `System.Data.Services.Client` assembly do Framework.
<br />

- Em `Extensions`, adicione uma referência para o `FSharp.Data.TypeProviders` assembly.
<br />

## <a name="accessing-odata-types"></a>Acessar tipos de OData
Nesta etapa, você deve criar um provedor de tipo que fornece acesso para os tipos e os dados para um serviço OData.


#### <a name="to-access-odata-types"></a>Para acessar os tipos de OData

- No Editor de códigos, abra um arquivo de origem F # e insira o código a seguir.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type Northwind = ODataService<"https://services.odata.org/Northwind/Northwind.svc/">

let db = Northwind.GetDataContext()
let fullContext = Northwind.ServiceTypes.NorthwindEntities()
```

Neste exemplo, você tem invocado o provedor de tipos F # e instruções para criar um conjunto de tipos que se baseiam o URI do OData que você especificou. Dois objetos estão disponíveis que contêm informações sobre os dados. um é um contexto de dados simplificado, `db` no exemplo. Este objeto contém apenas os tipos de dados que estão associados com o banco de dados, que incluem os tipos de tabelas ou feeds. O objeto, `fullContext` neste exemplo, é uma instância de `System.Data.Linq.DataContext` e contém muitas propriedades adicionais, métodos e eventos.
<br />


## <a name="querying-an-odata-service"></a>Consultando um serviço OData
Nesta etapa, você pode usar expressões de consulta do F # para consultar o serviço OData.


#### <a name="to-query-an-odata-service"></a>Para consultar um serviço OData

1. Agora que você configurou o provedor de tipos, você pode consultar um serviço OData.
<br />  OData oferece suporte a apenas um subconjunto das operações de consulta disponível. Há suporte para as seguintes operações e palavras-chave correspondentes:
<br />
  - projeção (`select`)
<br />

  - filtragem (`where`, usando a cadeia de caracteres e operações de data)
<br />

  - paginação (`skip`, `take`)
<br />

  - ordenação (`orderBy`, `thenBy`)
<br />

  - `AddQueryOption` e `Expand`, que são operações específicas do OData
<br />

  Para obter mais informações, consulte [considerações sobre o LINQ &#40; WCF Data Services &#41; ](https://msdn.microsoft.com/library/ee622463.aspx).
<br />  Se desejar que todas as entradas em um feed ou uma tabela, use a forma mais simples da expressão de consulta, como no código a seguir:
<br />

```fsharp
query {
  for customer in db.Customers do
  select customer
} |> Seq.iter (fun customer ->
                  printfn "ID: %s\nCompany: %s" customer.CustomerID customer.CompanyName
                  printfn "Contact: %s\nAddress: %s" customer.ContactName customer.Address
                  printfn "         %s, %s %s" customer.City customer.Region customer.PostalCode
                  printfn "%s\n" customer.Phone)
```

2. Especifique os campos ou colunas que desejar usar uma tupla após a palavra-chave select.
<br />

```fsharp
  query { 
    for cat in db.Categories do
    select (cat.CategoryID, cat.CategoryName, cat.Description)
  } |> Seq.iter (fun (id, name, description) ->
                    printfn "ID: %d\nCategory: %s\nDescription: %s\n" id name description)
```

3. Especificar condições usando um `where` cláusula.
<br />

```fsharp
query {
  for employee in db.Employees do
  where (employee.EmployeeID = 9)
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

4. Especificar uma condição de subcadeia de caracteres para a consulta usando o `System.String.Contains(System.String)` método. A consulta a seguir retorna todos os produtos que têm "Chefe" em seus nomes. Observe também o uso de `System.Nullable<'T>.GetValueOrDefault()`. O `UnitPrice` é um valor nulo, portanto, você deve obter ou o valor usando o `Value` propriedade, ou você deve chamar `System.Nullable<'T>.GetValueOrDefault()`.
<br />

```fsharp
query { 
  for product in db.Products do
  where (product.ProductName.Contains("Chef"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

5. Use o `System.String.EndsWith(System.String)` método para especificar que uma cadeia de caracteres termina com uma determinada subcadeia de caracteres.
<br />

```fsharp
query {
  for product in db.Products do
  where (product.ProductName.EndsWith("u"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

6. Combinar condições em um onde cláusula usando o `&&` operador.
<br />

```fsharp
// Open this module to use the nullable operators ?> and ?<.
open Microsoft.FSharp.Linq.NullableOperators

let salesIn1997 = query { 
  for sales in db.Category_Sales_for_1997 do
  where (sales.CategorySales ?> 50000.00M && sales.CategorySales ?< 60000.0M)
  select sales }

salesIn1997
|> Seq.iter (fun sales ->
                printfn "Category: %s Sales: %M" sales.CategoryName (sales.CategorySales.GetValueOrDefault()))
```

Os operadores `?>` e `?<` são operadores anuláveis. Você pode usar um conjunto completo de operadores de comparação e de igualdade permite valor nulos. Para obter mais informações, consulte [módulo LINQ. nullableoperators](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).
<br />

7. Use o `sortBy` operador para especificar a ordenação de consulta e use `thenBy` para especificar outro nível de ordenação. Observe também o uso de uma tupla na parte select da consulta. Portanto, a consulta tem uma coleção de itens como um tipo de elemento.
<br />

```fsharp
printfn "Freight for some orders: "

query { 
  for order in db.Orders do
  sortBy (order.OrderDate.Value)
  thenBy (order.OrderID)
  select (order.OrderDate, order.OrderID, order.Customer.CompanyName)
} |> Seq.iter (fun (orderDate, orderID, company) ->
                  printfn "OrderDate: %s" (orderDate.GetValueOrDefault().ToString())
                  printfn "OrderID: %d Company: %s\n" orderID company)
```

8. Ignorar um número especificado de registros usando o operador skip e usar o operador take para especificar um número de registros a serem retornados. Dessa forma, você pode implementar a paginação em feeds de dados.
<br />

```fsharp
printfn "Get the first page of 2 employees."

query { 
  for employee in db.Employees do
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID)) 

printfn "Get the next 2 employees."

query { 
  for employee in db.Employees do
  skip 2
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

## <a name="verifying-the-odata-request"></a>Verificando a solicitação do OData
Cada consulta OData é convertida em um URI de solicitação OData específico. Você pode verificar que URI, talvez para depuração fins, adicionando um manipulador de eventos para o `SendingRequest` evento no objeto de contexto de dados completo.


#### <a name="to-verify-the-odata-request"></a>Para verificar se a solicitação do OData

- Para verificar se o URI de solicitação OData, use o seguinte código:
<br />

```fsharp
// The DataContext property returns the full data context.
db.DataContext.SendingRequest.Add (fun eventArgs -> printfn "Requesting %A" eventArgs.Request.RequestUri)
```

A saída do código anterior é:
<br />`requesting https://services.odata.org/Northwind/Northwind.svc/Orders()?$orderby=ShippedDate&amp;$select=OrderID,ShippedDate`


## <a name="see-also"></a>Consulte também
[Expressões de Consulta](../../language-reference/query-expressions.md)

[Considerações sobre o LINQ (WCF Data Services)](https://msdn.microsoft.com/library/ee622463.aspx)

[Provedor de tipos ODataService (F #)](https://msdn.microsoft.com/visualfsharpdocs/conceptual/odataservice-type-provider-%5bfsharp%5d)
