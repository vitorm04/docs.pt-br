---
title: "Convertendo tipos de dados (c#) | Microsoft Docs"
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
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Convertendo tipos de dados (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Métodos de conversão alterar o tipo de objetos de entrada.  
  
 Operações de conversão em consultas LINQ são úteis em uma variedade de aplicativos. Estes são alguns exemplos:  
  
-   O <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> método pode ser usado para ocultar a implementação personalizada do tipo de um operador de consulta padrão.  
  
-   O <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> método pode ser usado para habilitar a coleções sem parâmetros de consulta LINQ.  
  
-   O <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> métodos podem ser usados para forçar a execução imediata da consulta em vez de adiamento de até que a consulta é enumerada.  
  
## Métodos  
 A tabela a seguir lista os métodos de operador de consulta padrão que executam conversões de tipo de dados.  
  
 Os métodos de conversão nesta tabela cujos nomes começam com "Como" alterar o tipo estático da coleção de origem, mas não enumerar. Digite os métodos cujos nomes começam com "Para enumerar a coleção de origem e colocar os itens na coleção correspondente".  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta c\#|Mais Informações|  
|--------------------|---------------|------------------------------------------|----------------------|  
|AsEnumerable|Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.|Não aplicável.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|AsQueryable|Converte um \(genérico\) <xref:System.Collections.IEnumerable> para \(genérico\) <xref:System.Linq.IQueryable>.|Não aplicável.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|Conversão|Converte os elementos de uma coleção para um tipo especificado.|Use uma variável de intervalo explicitamente digitado. Por exemplo:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|OfType|Filtros de valores, dependendo de sua capacidade de ser convertido em um tipo especificado.|Não aplicável.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|ToArray|Converte uma coleção para uma matriz. Esse método força a execução da consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|ToDictionary|Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602> com base em uma função de seletor de chave. Esse método força a execução da consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|ToList|Converte uma coleção para um <xref:System.Collections.Generic.List%601>. Esse método força a execução da consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|ToLookup|Coloca os elementos em um <xref:System.Linq.Lookup%602> \(um dicionário de um\-para\-muitos\) com base em uma função de seletor de chave. Esse método força a execução da consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## Exemplo de sintaxe de expressão de consulta  
 O exemplo de código a seguir usa uma variável de intervalo digitado explicitamente converter um tipo em um subtipo antes de acessar um membro que está disponível somente no subtipo.  
  
```c#  
class Plant  
{  
    public string Name { get; set; }  
}  
  
class CarnivorousPlant : Plant  
{  
    public string TrapType { get; set; }  
}  
  
static void Cast()  
{  
    Plant[] plants = new Plant[] {  
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },  
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },  
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },  
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }  
    };  
  
    var query = from CarnivorousPlant cPlant in plants  
                where cPlant.TrapType == "Snap Trap"  
                select cPlant;  
  
    foreach (Plant plant in query)  
        Console.WriteLine(plant.Name);  
  
    /* This code produces the following output:  
  
        Venus Fly Trap  
        Waterwheel Plant  
    */  
}  
```  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula from](../../../../visual-basic/language-reference/queries/from-clause.md)   
 [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Como: consultar um ArrayList com LINQ \(c\#\)](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ%20\(C%23\).md)