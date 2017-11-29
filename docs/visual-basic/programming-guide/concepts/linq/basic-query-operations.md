---
title: "Operações de consulta básica (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 794d77a18b50cc1667fddbad17c46735ae91be26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="basic-query-operations-visual-basic"></a>Operações de consulta básica (Visual Basic)
Este tópico fornece uma breve introdução ao [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressões no Visual Basic e alguns dos tipos típicos de operações executadas em uma consulta. Para mais informações, consulte os seguintes tópicos:  
  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [Passo a passo: Escrevendo consultas em Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Especificando a Fonte de Dados (De)  
 Em um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta, a primeira etapa é especificar a fonte de dados que você deseja consultar. Portanto, o `From` cláusula em uma consulta sempre ocorrer primeira. Operadores de consulta selecionam e formatar o resultado com base no tipo de origem.  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 O `From` cláusula Especifica a fonte de dados, `customers`e um *variável de intervalo*, `cust`. A variável de intervalo é como uma variável de iteração do loop, exceto que em uma expressão de consulta, não ocorre nenhuma iteração real. Quando a consulta é executada, geralmente usando um `For Each` loop, a variável de intervalo serve como uma referência para cada elemento sucessivo `customers`. Uma vez que o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente. Para obter exemplos de consultas escritas com e sem digitar explícitas, consulte [relacionamentos de tipo em operações de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Para obter mais informações sobre como usar o `From` cláusula no Visual Basic, consulte [cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrando Dados (Onde)  
 Provavelmente, a operação de consulta mais comuns é aplicar um filtro na forma de uma expressão booleana. A consulta retorna apenas os elementos para o qual a expressão for verdadeira. Um `Where` cláusula é usada para executar a filtragem. O filtro especifica quais elementos na fonte de dados para incluir na sequência resultante. No exemplo a seguir, estão incluídos somente aqueles clientes que têm um endereço em Londres.  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 Você pode usar os operadores lógicos, como `And` e `Or` para combinar expressões de filtro em um `Where` cláusula. Por exemplo, para retornar somente os clientes que são de Londres e cujo nome é Juliana PAEs, use o código a seguir:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Para retornar os clientes de Londres ou Paris, use o seguinte código:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Para obter mais informações sobre como usar o `Where` cláusula no Visual Basic, consulte [cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Ordenando Dados (Ordenar Por)  
 Geralmente, é conveniente classificar os dados retornados em uma ordem específica. O `Order By` cláusula fará com que os elementos na sequência a ser classificada em um campo especificado ou campos retornada. Por exemplo, a consulta a seguir classifica os resultados com base no `Name` propriedade. Porque `Name` é uma cadeia de caracteres, os dados retornados serão classificados em ordem alfabética, de À Z.  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 Para ordenar os resultados na ordem inversa, de Z para a, use a cláusula `Order By...Descending`. O padrão é `Ascending` quando nenhuma `Ascending` nem `Descending` for especificado.  
  
 Para obter mais informações sobre como usar o `Order By` cláusula no Visual Basic, consulte [cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Selecionando Dados (Selecionar)  
 O `Select` cláusula Especifica o formato e conteúdo de elementos retornados. Por exemplo, você pode especificar se os resultados consistirá completa `Customer` objetos, apenas um `Customer` propriedade, um subconjunto de propriedades, uma combinação de propriedades de várias fontes de dados ou algum tipo de resultado novo com base em um cálculo. Quando a cláusula `Select` produz algo diferente de uma cópia do elemento de origem, a operação é chamada de *projeção*.  
  
 Para recuperar uma coleção que consiste em completa `Customer` objetos, selecione a variável de intervalo:  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 Se um `Customer` instância é um objeto grande com muitos campos, e tudo o que você deseja recuperar é o nome, você pode selecionar `cust.Name`, conforme mostrado no exemplo a seguir. Inferência de tipo local reconhece que isso altera o tipo de resultado de uma coleção de `Customer` objetos a uma coleção de cadeias de caracteres.  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 Para selecionar vários campos da fonte de dados, você tem duas opções:  
  
-   No `Select` cláusula, especifique os campos que você deseja incluir no resultado. O compilador definirá um tipo anônimo com esses campos como suas propriedades. Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Como os elementos retornados no exemplo a seguir são instâncias de um tipo anônimo, você não pode se referir ao tipo por nome em outro lugar no seu código. O nome designado pelo compilador para o tipo contém caracteres que não são válidos no código do Visual Basic normal. No exemplo a seguir, os elementos da coleção que é retornado pela consulta em `londonCusts4` são instâncias de um tipo anônimo  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     -ou-  
  
-   Definir um tipo nomeado que contém os campos específicos que você deseja incluir no resultado e criar e inicializar as instâncias do tipo de `Select` cláusula. Use esta opção somente se você precisa usar os resultados individuais fora da coleção na qual eles são retornados, ou se você tem para passá-las como parâmetros em chamadas de método. O tipo de `londonCusts5` no exemplo a seguir é IEnumerable (Of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 Para obter mais informações sobre como usar o `Select` cláusula no Visual Basic, consulte [cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Ingressando Dados (Ingressar e Agrupar Junções)  
 Você pode combinar mais de uma fonte de dados no `From` cláusula de várias maneiras. Por exemplo, o código a seguir usa duas fontes de dados e combina implicitamente propriedades de ambos os parâmetros no resultado. A consulta seleciona os alunos cujos sobrenomes começam com uma vogal.  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  Você pode executar esse código com a lista de alunos criado no [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 O `Join` palavra-chave é equivalente a um `INNER JOIN` em SQL. Ele combina duas coleções baseadas nos valores de chave de correspondência entre os elementos na coleção. A consulta retorna todo ou parte dos elementos da coleção que têm valores de chave correspondentes. Por exemplo, o código a seguir duplica a ação da junção implícita anterior.  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join`combina coleções em uma única coleção hierárquica, como um `LEFT JOIN` no SQL. Para obter mais informações, consulte [cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md) e [cláusula Join do grupo](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Agrupando Dados (Agrupar Por)  
 Você pode adicionar um `Group By` cláusula para agrupar os elementos de acordo com os campos de um ou mais dos elementos de um resultado de consulta. Por exemplo, o código a seguir agrupa os alunos por ano de classe.  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 Se você executar esse código usando a lista de alunos criado no [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), a saída do `For Each` instrução é:  
  
 Ano: júnior  
  
 Terra, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Terra, Lance  
  
 Ano: sênior  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Diogo  
  
 Ano: primeiro ano  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 A variação mostrada no código a seguir classifica os anos de classe e ordena os alunos dentro de cada ano por sobrenome.  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 Para obter mais informações sobre `Group By`, consulte [grupo pela cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)  
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
