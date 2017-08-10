---
title: Convertendo Tipos de Dados (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 454fb0ce937d7d20dfce26d92dbf49de24f062f0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="converting-data-types-c"></a>Convertendo Tipos de Dados (C#)
Os métodos de conversão alteram o tipo dos objetos de entrada.  
  
 As operações de conversão em consultas LINQ são úteis em diversas aplicações. A seguir estão alguns exemplos:  
  
-   O método <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> pode ser usado para ocultar a implementação personalizada de um tipo de um operador de consulta padrão.  
  
-   O método <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> pode ser usado para habilitar coleções sem parâmetros para consulta LINQ.  
  
-   Os métodos <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> podem ser usados para forçar a execução de consulta imediata em vez de adiá-la até que a consulta seja enumerada.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos de operador de consulta padrão que realizam conversões de tipo de dados.  
  
 Os métodos de conversão nesta tabela cujos nomes começam com "As" alteram o tipo estático da coleção de origem, mas não a enumeram. Os métodos cujos nomes começam com "To" enumeram a coleção de origem e colocam os itens na coleção de tipo correspondente.  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|AsEnumerable|Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.|Não aplicável.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|AsQueryable|Converte um <xref:System.Collections.IEnumerable> (genérico) em um <xref:System.Linq.IQueryable> (genérico).|Não aplicável.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|Conversão|Converte os elementos de uma coleção em um tipo especificado.|Use uma variável de intervalo de tipo explícito. Por exemplo:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|OfType|Filtra valores, dependendo da capacidade de serem convertidos em um tipo especificado.|Não aplicável.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|ToArray|Converte uma coleção em uma matriz. Esse método força a execução de consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|ToDictionary|Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602> com base em uma função de seletor de chave. Esse método força a execução de consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|ToList|Converte uma coleção em um <xref:System.Collections.Generic.List%601>. Esse método força a execução de consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|ToLookup|Coloca os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave. Esse método força a execução de consulta.|Não aplicável.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>Exemplo de sintaxe de expressão de consulta  
 O exemplo de código a seguir usa uma variável de intervalo de tipo explícito para converter um tipo em um subtipo antes de acessar um membro que está disponível somente no subtipo.  
  
```csharp  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula from](../../../../csharp/language-reference/keywords/from-clause.md)   
 [Expressões de Consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Como consultar um ArrayList com LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)

