---
title: "Como unir usando chaves compostas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "chaves compostas [LINQ em C#]"
  - "junções [C#]"
  - "junções [C#], chaves compostas"
  - "consultas [LINQ in C#], junções"
  - "expressões de consulta [LINQ em C#], junções"
ms.assetid: 3e015b3f-9cca-4b0c-aa97-dca0d36ea592
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como unir usando chaves compostas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como executar as operações de associação na qual você deseja usar mais de uma chave para definir uma correspondência.  Isso é realizado usando uma chave composta.  Você cria uma composição nomeada ou chave como um tipo anônimo digitado com os valores que você deseja comparar.  Se a variável de consulta será transmitida através de limites de método, use um tipo nomeado que substitui o <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A> para a chave.  Os nomes das propriedades e a ordem em que eles ocorrem, devem ser idênticos em cada chave.  
  
## Exemplo  
 O exemplo a seguir demonstra como usar uma chave composta para associar dados de três tabelas:  
  
```  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,         d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 Inferência de tipos em chaves compostas depende dos nomes das propriedades em que as chaves e a ordem em que eles ocorrem.  Se as propriedades em seqüências de código\-fonte não tiverem os mesmos nomes, você deve atribuir novos nomes nas chaves.  Por exemplo, se a `Orders` tabela e `OrderDetails` cada tabela usado nomes diferentes para suas colunas, você pode criar as chaves compostas, atribuindo nomes idênticos nos tipos anônimos:  
  
```  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 As chaves compostas também podem ser usadas em um `group` cláusula.  
  
## Compilando o código  
  
-   Para compilar e executar esse código, execute estas etapas:  
  
-   Abrir [Como se conectar ao banco de dados Northwind](../Topic/How%20to:%20Connect%20to%20the%20Northwind%20Database.md) e siga as instruções para configurar o projeto e criar a conexão de banco de dados.  Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../Topic/How%20to:%20Install%20Sample%20Databases.md).  
  
-   No samples.cs, crie um novo método vazio que leva um parâmetro de entrada do Northwind chamado db \(semelhante a outros métodos nesse arquivo\).  Cole o código deste exemplo para o corpo do método.  
  
-   Modificar Program. cs para chamar o novo método de `Main`.  
  
-   Pressione F5 para compilar e executar a consulta.  
  
## Consulte também  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Cláusula join](../../../csharp/language-reference/keywords/join-clause.md)   
 [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md)