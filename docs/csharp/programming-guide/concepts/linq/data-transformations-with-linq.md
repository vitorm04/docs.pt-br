---
title: Transformações de dados com LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: be488b262764480b519e291727a21830d7a18e8f
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201424"
---
# <a name="data-transformations-with-linq-c"></a>Transformações de dados com LINQ (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] não se trata apenas de recuperação de dados. Também é uma ferramenta poderosa para transformação de dados. Ao usar uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você pode usar uma sequência de origem como entrada e modificá-la de várias maneiras para criar uma nova sequência de saída. Você pode modificar a própria sequência sem modificar os respectivos elementos, classificando-os e agrupando-os. Mas talvez o recurso mais poderoso das consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] é a capacidade de criar novos tipos. Isso é feito na cláusula [select](../../../../csharp/language-reference/keywords/select-clause.md). Por exemplo, é possível executar as seguintes tarefas:  
  
-   Mesclar várias sequências de entrada em uma única sequência de saída que tenha um novo tipo.  
  
-   Criar sequências de saída cujos elementos consistem em apenas uma ou várias propriedades de cada elemento da sequência de origem.  
  
-   Criar sequências de saída cujos elementos consistem nos resultados das operações realizadas nos dados de origem.  
  
-   Criar sequências de saída em um formato diferente. Por exemplo, você pode transformar dados de linhas do SQL ou de arquivos de texto em XML.  
  
 Esses são apenas alguns exemplos. É claro que essas transformações podem ser combinadas de diversas maneiras na mesma consulta. Além disso, a sequência de saída de uma consulta pode ser usada como a sequência de entrada de uma nova consulta.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Ingressando Várias Entradas em uma Única Sequência de Saída  
 Você pode usar uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para criar uma sequência de saída que contenha elementos de mais de uma sequência de entrada. O exemplo a seguir mostra como combinar duas estruturas de dados na memória, mas os mesmos princípios podem ser aplicados para combinar dados de origens de XML, SQL ou DataSet. Considere os dois tipos de classe a seguir:  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 O exemplo a seguir mostra a consulta:  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Para obter mais informações, consulte [cláusula join](../../../../csharp/language-reference/keywords/join-clause.md) e [cláusula select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Selecionando um Subconjunto de Cada Elemento de Origem  
 Há duas maneiras principais de selecionar um subconjunto de cada elemento na sequência de origem:  
  
1.  Para selecionar apenas um membro do elemento de origem, use a operação de ponto. No exemplo a seguir, suponha que um objeto `Customer` contém várias propriedades públicas, incluindo uma cadeia de caracteres denominada `City`. Quando executada, essa consulta produzirá uma sequência de saída de cadeias de caracteres.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  Para criar elementos que contenham mais de uma propriedade do elemento de origem, você pode usar um inicializador de objeto com um objeto nomeado ou um tipo anônimo. O exemplo a seguir mostra o uso de um tipo anônimo para encapsular duas propriedades de cada elemento `Customer`:  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Para obter mais informações, consulte [Inicializadores de coleção e de objeto](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) e [Tipos anônimos](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Transformando Objetos na Memória em XML  
 As consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] facilitam a transformação de dados entre estruturas de dados na memória, bancos de dados SQL, conjuntos de dados [!INCLUDE[vstecado](~/includes/vstecado-md.md)] e fluxos ou documentos XML. O exemplo a seguir transforma objetos de uma estrutura de dados na memória em elementos XML.  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 O código produz a seguinte saída XML:  
  
```xml  
<Root>  
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
  
 Para obter mais informações, consulte [Criando árvores XML em C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Realizando Operações em Elementos de Origem  
 Uma sequência de saída pode não conter os elementos ou propriedades de elementos da sequência de origem. Em vez disso, a saída pode ser uma sequência de valores que é calculada usando os elementos de origem como argumentos de entrada. Esta simples consulta a seguir, quando executada, produz uma sequência de cadeias de caracteres cujos valores representam um cálculo com base na sequência de origem de elementos do tipo `double`.  
  
> [!NOTE]
>  Não há suporte para chamar métodos em expressões de consulta se a consulta será movida para outro domínio. Por exemplo, você não pode chamar um método comum de C# no [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] porque o SQL Server não tem contexto para ele. No entanto, você pode mapear procedimentos armazenados para os métodos e chamá-los. Para obter mais informações, consulte [Procedimentos armazenados](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Consulte também

- [LINQ (consulta integrada à linguagem) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
- [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [Cláusula select](../../../../csharp/language-reference/keywords/select-clause.md)
