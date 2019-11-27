---
title: Operações de consulta básica
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: e9a646d60bb22507f4c6bcbcdf9222fd0ed18f02
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345756"
---
# <a name="basic-query-operations-visual-basic"></a>Operações de consulta básica (Visual Basic)
Este tópico fornece uma breve introdução à [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] de expressões no Visual Basic e a alguns dos tipos típicos de operações que você executa em uma consulta. Para mais informações, consulte os seguintes tópicos:  
  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Consultas](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Walkthrough: gravando consultas no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Especificando a Fonte de Dados (De)  
 Em uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a primeira etapa é especificar a fonte de dados que você deseja consultar. Portanto, a cláusula `From` em uma consulta sempre é exibida primeiro. Operadores de consulta Selecione e formate o resultado com base no tipo de origem.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 A cláusula `From` especifica a fonte de dados, `customers`e uma *variável de intervalo*, `cust`. A variável de intervalo é como uma variável de iteração de loop, exceto que em uma expressão de consulta, nenhuma iteração real ocorre. Quando a consulta é executada, muitas vezes usando um loop `For Each`, a variável Range serve como uma referência a cada elemento sucessivo em `customers`. Uma vez que o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente. Para obter exemplos de consultas escritas com e sem digitação explícita, consulte [relações de tipo em operações de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Para obter mais informações sobre como usar a cláusula `From` em Visual Basic, consulte a [cláusula from](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrando Dados (Onde)  
 Provavelmente, a operação de consulta mais comum é aplicar um filtro na forma de uma expressão booliana. Em seguida, a consulta retorna somente os elementos para os quais a expressão é verdadeira. Uma cláusula `Where` é usada para executar a filtragem. O filtro especifica quais elementos na fonte de dados incluir na sequência resultante. No exemplo a seguir, somente os clientes que têm um endereço em Londres estão incluídos.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Você pode usar operadores lógicos, como `And` e `Or` para combinar expressões de filtro em uma cláusula `Where`. Por exemplo, para retornar somente os clientes que são de Londres e cujo nome é Devon, use o seguinte código:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Para retornar os clientes de Londres ou Paris, use o seguinte código:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Para obter mais informações sobre como usar a cláusula `Where` em Visual Basic, consulte [cláusula WHERE](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Ordenando Dados (Ordenar Por)  
 Geralmente, é conveniente classificar os dados retornados em uma ordem específica. A cláusula `Order By` fará com que os elementos na sequência retornada sejam classificados em um campo ou campos especificados. Por exemplo, a consulta a seguir classifica os resultados com base na propriedade `Name`. Como `Name` é uma cadeia de caracteres, os dados retornados serão classificados alfabeticamente, de A a Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Para ordenar os resultados na ordem inversa, de Z para a, use a cláusula `Order By...Descending`. O padrão é `Ascending` quando nem `Ascending` nem `Descending` é especificado.  
  
 Para obter mais informações sobre como usar a cláusula `Order By` em Visual Basic, consulte [cláusula order by](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Selecionando Dados (Selecionar)  
 A cláusula `Select` especifica o formulário e o conteúdo dos elementos retornados. Por exemplo, você pode especificar se os resultados consistirão em objetos de `Customer` completos, apenas uma propriedade `Customer`, um subconjunto de propriedades, uma combinação de propriedades de várias fontes de dados ou um novo tipo de resultado com base em uma computação. Quando a cláusula `Select` produz algo diferente de uma cópia do elemento de origem, a operação é chamada de *projeção*.  
  
 Para recuperar uma coleção que consiste em objetos de `Customer` completos, selecione a variável de intervalo em si:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Se uma instância de `Customer` for um objeto grande que tem muitos campos e tudo o que você deseja recuperar for o nome, você poderá selecionar `cust.Name`, conforme mostrado no exemplo a seguir. A inferência de tipo local reconhece que isso altera o tipo de resultado de uma coleção de objetos `Customer` para uma coleção de cadeias de caracteres.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Para selecionar vários campos da fonte de dados, você tem duas opções:  
  
- Na cláusula `Select`, especifique os campos que você deseja incluir no resultado. O compilador irá definir um tipo anônimo que tenha esses campos como suas propriedades. Para obter mais informações, consulte [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Como os elementos retornados no exemplo a seguir são instâncias de um tipo anônimo, você não pode fazer referência ao tipo por nome em outro lugar no seu código. O nome designado pelo compilador para o tipo contém caracteres que não são válidos no código de Visual Basic normal. No exemplo a seguir, os elementos na coleção que são retornados pela consulta em `londonCusts4` são instâncias de um tipo anônimo  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     - ou -  
  
- Defina um tipo nomeado que contenha os campos específicos que você deseja incluir no resultado e crie e inicialize instâncias do tipo na cláusula `Select`. Use esta opção somente se você precisar usar resultados individuais fora da coleção na qual eles são retornados ou se você tiver que passá-los como parâmetros nas chamadas de método. O tipo de `londonCusts5` no exemplo a seguir é IEnumerable (Of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Para obter mais informações sobre como usar a cláusula `Select` em Visual Basic, consulte [cláusula SELECT](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Ingressando Dados (Ingressar e Agrupar Junções)  
 Você pode combinar mais de uma fonte de dados na cláusula `From` de várias maneiras. Por exemplo, o código a seguir usa duas fontes de dados e combina implicitamente as propriedades de ambas elas no resultado. A consulta seleciona os alunos cujos últimos nomes começam com uma vogal.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Você pode executar esse código com a lista de alunos criados em [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 A palavra-chave `Join` é equivalente a uma `INNER JOIN` no SQL. Ele combina duas coleções com base em valores de chave correspondentes entre elementos nas duas coleções. A consulta retorna todos ou parte dos elementos da coleção que têm valores de chave correspondentes. Por exemplo, o código a seguir duplica a ação da junção implícita anterior.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` combina coleções em uma única coleção hierárquica, assim como uma `LEFT JOIN` no SQL. Para obter mais informações, consulte cláusula [Join](../../../../visual-basic/language-reference/queries/join-clause.md) e [cláusula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Agrupando Dados (Agrupar Por)  
 Você pode adicionar uma cláusula `Group By` para agrupar os elementos em um resultado de consulta de acordo com um ou mais campos dos elementos. Por exemplo, o código a seguir agrupa alunos por ano de aula.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Se você executar esse código usando a lista de alunos criados em [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), a saída da instrução `For Each` será:  
  
 Ano: Júnior  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Débora  
  
 Tucker, lance  
  
 Ano: sênior  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Ano: atualizador  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 A variação mostrada no código a seguir ordena a classe Years e, em seguida, ordena os alunos em cada ano pelo sobrenome.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Para obter mais informações sobre `Group By`, consulte [cláusula Group by](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic.IEnumerable%601>
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
- [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
