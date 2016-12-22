---
title: "Transforma&#231;&#245;es de dados com LINQ (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "LINQ [c#], transformações de dados"
  - "elementos de origem [LINQ em C#]"
  - "unindo várias entradas [LINQ em C#]"
  - "várias saídas para uma sequência de saída [LINQ em C#]"
  - "subconjunto de elementos de origem [LINQ em C#]"
  - "transformações de dados [LINQ em c#], fontes de dados"
  - "transformações de dados [LINQ em C#]"
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Transforma&#231;&#245;es de dados com LINQ (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] não se trata apenas de recuperação de dados. Também é uma ferramenta poderosa para transformar os dados. Usando um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta, você pode usar uma sequência de origem como entrada e modificá\-lo de várias maneiras para criar uma nova seqüência de saída. Você pode modificar a seqüência sem modificar os próprios elementos classificando e agrupando. Mas talvez o recurso mais eficiente de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas é a capacidade de criar novos tipos. Isso é feito no [Selecione](../../../../csharp/language-reference/keywords/select-clause.md) cláusula. Por exemplo, você pode executar as seguintes tarefas:  
  
-   Mescle várias sequências de entrada em uma seqüência de saída única que tem um novo tipo.  
  
-   Crie sequências de saída cujos elementos consistem em apenas uma ou várias propriedades de cada elemento na sequência de origem.  
  
-   Crie sequências de saída cujos elementos consistem os resultados das operações executadas nos dados de origem.  
  
-   Crie sequências de saída em um formato diferente. Por exemplo, você pode transformar dados de linhas SQL ou arquivos de texto em XML.  
  
 Esses são apenas alguns exemplos. Obviamente, essas transformações podem ser combinadas de diversas maneiras na mesma consulta. Além disso, a seqüência de saída de uma consulta pode ser usada como a seqüência de entrada para uma nova consulta.  
  
## Unindo várias entradas em uma saída sequência  
 Você pode usar um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta para criar uma seqüência de saída que contém elementos de mais de uma sequência de entrada. O exemplo a seguir mostra como combinar duas estruturas de dados na memória, mas os mesmos princípios podem ser aplicados para combinar dados de XML ou SQL ou um conjunto de fontes. Considere os seguintes tipos de duas classes:  
  
 [!code-cs[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 O exemplo a seguir mostra a consulta:  
  
 [!code-cs[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 Para obter mais informações, consulte [Cláusula join](../../../../csharp/language-reference/keywords/join-clause.md) e [Cláusula select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## Selecionar um subconjunto de cada elemento de origem  
 Há duas maneiras principais de selecionar um subconjunto de cada elemento na sequência de origem:  
  
1.  Para selecionar apenas um membro do elemento de origem, use a operação de ponto. No exemplo a seguir, suponha que uma `Customer` objeto contém várias propriedades públicas, incluindo uma cadeia de caracteres denominada `City`. Quando executada, essa consulta produzirá uma seqüência de saída de cadeias de caracteres.  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  Para criar elementos que contêm mais de uma propriedade do elemento de origem, você pode usar um inicializador de objeto com um objeto nomeado ou um tipo anônimo. O exemplo a seguir mostra o uso de um tipo anônimo para encapsular duas propriedades de cada `Customer` elemento:  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Para obter mais informações, consulte [Inicializadores de objeto e coleção](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) e [Tipos anônimos](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## Transformando objetos na memória em XML  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas facilitam a transformar dados entre estruturas de dados na memória, bancos de dados SQL [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] Datasets e XML fluxos ou documentos. O exemplo a seguir transforma objetos em uma estrutura de dados na memória em elementos XML.  
  
 [!code-cs[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 O código produz a saída XML a seguir:  
  
```  
< Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 Para obter mais informações, consulte [Criando árvores XML em C\# \(LINQ para XML\)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).  
  
## Executando operações em elementos de origem  
 Uma seqüência de saída não pode conter todos os elementos ou propriedades do elemento da sequência de origem. A saída pode ser uma seqüência de valores que é calculada usando os elementos de origem como argumentos de entrada. A seguinte consulta simples, quando ele é executado, produz uma sequência de cadeias de caracteres cujos valores representam um cálculo com base na sequência de elementos do tipo de origem `double`.  
  
> [!NOTE]
>  Chamar métodos em expressões de consulta não é suportado se a consulta será convertida em algum outro domínio. Por exemplo, você não pode chamar um método comum de c\# em [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] porque o SQL Server não tem contexto para ele. No entanto, você pode mapear os procedimentos armazenados para os métodos e chamar os. Para obter mais informações, consulte [Stored Procedures](../Topic/Stored%20Procedures.md).  
  
 [!code-cs[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## Consulte também  
 [Consulta integrada à linguagem \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/index.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)   
 [LINQ to XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)   
 [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Cláusula select](../../../../csharp/language-reference/keywords/select-clause.md)