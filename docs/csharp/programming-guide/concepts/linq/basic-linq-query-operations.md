---
title: Operações de consulta LINQ básica (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 2825b79c9638fff050522da43184a8d95a3fe02f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333034"
---
# <a name="basic-linq-query-operations-c"></a>Operações de consulta LINQ básica (C#)
Este tópico fornece uma breve introdução às expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] e a alguns dos tipos típicos de operações que podem ser executadas em uma consulta. Informações mais detalhadas estão nos tópicos a seguir:  
  
 [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [Passo a passo: escrevendo consultas em C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  Se já estiver familiarizado com uma linguagem de consulta como SQL ou XQuery, você poderá ignorar a maior parte deste tópico. Leia sobre a "cláusula `from`" na próxima seção para saber mais sobre a ordem das cláusulas em expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
## <a name="obtaining-a-data-source"></a>Obtendo uma Fonte de Dados  
 Em um consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a primeira etapa é especificar a fonte de dados. No C#, como na maioria das linguagens de programação, uma variável deve ser declarada antes que possa ser usada. Em um consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a cláusula `from` vem primeiro para introduzir a fonte de dados (`customers`) e a *variável de intervalo* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 A variável de intervalo é como a variável de iteração em um loop `foreach`, mas nenhuma iteração real ocorre em uma expressão de consulta. Quando a consulta é executada, a variável de intervalo servirá como uma referência para cada elemento sucessivo em `customers`. Uma vez que o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente. Variáveis de intervalo adicionais podem ser introduzidas por uma cláusula `let`. Para obter mais informações, consulte [Cláusula let](../../../../csharp/language-reference/keywords/let-clause.md).  
  
> [!NOTE]
>  Para fontes de dados não genéricas, como <xref:System.Collections.ArrayList>, a variável de intervalo deve ser tipada explicitamente. Para obter mais informações, consulte [Como consultar um ArrayList com LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) e [Cláusula from](../../../../csharp/language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtragem  
 Provavelmente, a operação de consulta mais comum é aplicar um filtro no formulário de uma expressão booliana. O filtro faz com que a consulta retorne apenas os elementos para os quais a expressão é verdadeira. O resultado é produzido usando a cláusula `where`. O filtro em vigor especifica os elementos a serem excluídos da sequência de origem. No exemplo a seguir, somente os `customers` que têm um endereço em Londres são retornados.  
  
 [!code-csharp[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 Você pode usar os operadores lógicos `AND` e `OR` de C# para aplicar quantas expressões de filtro forem necessárias na cláusula `where`. Por exemplo, para retornar somente clientes de "Londres" `AND` cujo nome seja "Devon", você escreveria o seguinte código:  
  
 [!code-csharp[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 Para retornar clientes de Londres ou Paris, você escreveria o seguinte código:  
  
 [!code-csharp[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 Para obter mais informações, consulte [Cláusula where](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Ordenando  
 Muitas vezes é conveniente classificar os dados retornados. A cláusula `orderby` fará com que os elementos na sequência retornada sejam classificados de acordo com o comparador padrão para o tipo que está sendo classificado. Por exemplo, a consulta a seguir pode ser estendida para classificar os resultados com base na propriedade `Name`. Como `Name` é uma cadeia de caracteres, o comparador padrão executa uma classificação em ordem alfabética de A a Z.  
  
 [!code-csharp[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 Para ordenar os resultados na ordem inversa, de Z para a, use a cláusula `orderby…descending`.  
  
 Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Agrupamento  
 A cláusula `group` permite agrupar seus resultados com base em uma chave que você especificar. Por exemplo, você pode especificar que os resultados sejam agrupados segundo o `City`, de modo que todos os clientes de Londres ou Paris fiquem em grupos individuais. Nesse caso, `cust.City` é a chave.  
  
 [!code-csharp[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 Quando você terminar uma consulta com um cláusula `group`, seus resultados assumirão a forma de uma lista de listas. Cada elemento na lista é um objeto que tem um membro `Key` e uma lista dos elementos que estão agrupados sob essa chave. Quando itera em uma consulta que produz uma sequência de grupos, você deve usar um loop `foreach` aninhado. O loop externo itera em cada grupo e o loop interno itera nos membros de cada grupo.  
  
 Se precisar consultar os resultados de uma operação de grupo, você poderá usar a palavra-chave `into` para criar um identificador que pode ser consultado ainda mais. A consulta a seguir retorna apenas os grupos que contêm mais de dois clientes:  
  
 [!code-csharp[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 Para obter mais informações, consulte [Cláusula group](../../../../csharp/language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Ingressando  
 Operações de junção criam associações entre sequências que não são modeladas explicitamente nas fontes de dados. Por exemplo, você pode executar uma junção para localizar todos os clientes e distribuidores que têm o mesmo local. Em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a cláusula `join` sempre funciona com coleções de objetos em vez de tabelas de banco de dados diretamente.  
  
 [!code-csharp[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 Em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você não precisa usar `join` com a mesma frequência que o faz no SQL, porque as chaves estrangeiras em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] são representados no modelo do objeto como propriedades que mantêm uma coleção de itens. Por exemplo, um objeto `Customer` que contém uma coleção de objetos `Order`. Em vez de executar uma junção, você pode acessar os pedidos usando notação de ponto:  
  
```  
from order in Customer.Orders...  
```  
  
 Para obter mais informações, consulte [Cláusula join](../../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Selecionando (Projeções)  
 A cláusula `select` produz os resultados da consulta e especifica a "forma" ou o tipo de cada elemento retornado. Por exemplo, você pode especificar se os resultados consistirão em objetos `Customer` completos, apenas um membro, um subconjunto de membros ou algum tipo de resultado completamente diferente com base em um cálculo ou na criação de um novo objeto. Quando a cláusula `select` produz algo diferente de uma cópia do elemento de origem, a operação é chamada de *projeção*. O uso de projeções para transformar dados é uma funcionalidade poderosa das expressões de consulta de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Para obter mais informações, consulte [Transformações de dados com LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) e [Cláusula select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução a LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Passo a passo: escrevendo consultas em C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [Palavras-chave de Consulta (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)  
 [Tipos Anônimos](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
