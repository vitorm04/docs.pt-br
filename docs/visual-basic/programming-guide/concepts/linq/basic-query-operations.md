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
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266372"
---
# <a name="basic-query-operations-visual-basic"></a>Operações de consulta básica (Visual Basic)
Este tópico fornece uma breve introdução às expressões LINQ (Language-Integrated Query) no Visual Basic e a alguns dos tipos típicos de operações que você executa em uma consulta. Para obter mais informações, consulte estes tópicos:  
  
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Consultas](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Instruções passo a passo: escrevendo consultas em Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Especificando a Fonte de Dados (De)  
 Em uma consulta LINQ, o primeiro passo é especificar a fonte de dados que você deseja consultar. Portanto, a `From` cláusula em uma consulta sempre vem em primeiro lugar. Os operadores de consulta selecionam e moldam o resultado com base no tipo da fonte.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 A `From` cláusula especifica a `customers`fonte de dados `cust`e uma variável *de intervalo.* A variável de intervalo é como uma variável de iteração de loop, exceto que em uma expressão de consulta, não ocorre nenhuma iteração real. Quando a consulta é executada, muitas `For Each` vezes usando um loop, a variável `customers`de intervalo serve como referência a cada elemento sucessivo em . Uma vez que o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente. Para exemplos de consultas escritas com e sem digitação explícita, consulte [Relações de tipo em Operações de Consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Para obter mais informações `From` sobre como usar a cláusula no Visual Basic, consulte [A partir da cláusula](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrando Dados (Onde)  
 Provavelmente a operação de consulta mais comum é a aplicação de um filtro na forma de uma expressão booleana. A consulta então retorna apenas os elementos para os quais a expressão é verdadeira. Uma `Where` cláusula é usada para realizar a filtragem. O filtro especifica quais elementos na fonte de dados serão ressonados na seqüência resultante. No exemplo a seguir, apenas os clientes que têm um endereço em Londres estão incluídos.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Você pode usar operadores `And` `Or` lógicos como e `Where` combinar expressões de filtro em uma cláusula. Por exemplo, para retornar apenas os clientes que são de Londres e cujo nome é Devon, use o seguinte código:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 Para devolver clientes de Londres ou Paris, use o seguinte código:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 Para obter mais informações `Where` sobre como usar a cláusula no Visual Basic, consulte [Onde cláusula](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Ordenando Dados (Ordenar Por)  
 Muitas vezes é conveniente classificar os dados devolvidos em uma ordem específica. A `Order By` cláusula fará com que os elementos da seqüência retornada sejam classificados em um campo ou campos especificados. Por exemplo, a consulta a seguir `Name` classifica os resultados com base na propriedade. Por `Name` ser uma seqüência, os dados retornados serão classificados alfabeticamente, de A a Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Para ordenar os resultados na ordem inversa, de Z para a, use a cláusula `Order By...Descending`. O padrão `Ascending` é `Ascending` `Descending` quando nem nem é especificado.  
  
 Para obter mais informações `Order By` sobre como usar a cláusula no Visual Basic, consulte [Ordem por Cláusula](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Selecionando Dados (Selecionar)  
 A `Select` cláusula especifica o formulário e o conteúdo dos elementos retornados. Por exemplo, você pode especificar se `Customer` seus resultados `Customer` consistirão em objetos completos, apenas uma propriedade, um subconjunto de propriedades, uma combinação de propriedades de várias fontes de dados ou algum novo tipo de resultado com base em um cálculo. Quando a cláusula `Select` produz algo diferente de uma cópia do elemento de origem, a operação é chamada de *projeção*.  
  
 Para recuperar uma coleção que `Customer` consiste em objetos completos, selecione a variável de intervalo em si:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Se `Customer` uma instância for um objeto grande que tem muitos campos, e tudo `cust.Name`o que você deseja recuperar é o nome, você pode selecionar, como mostrado no exemplo a seguir. A inferência do tipo local reconhece que isso `Customer` altera o tipo de resultado de uma coleção de objetos para uma coleção de strings.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Para selecionar vários campos na fonte de dados, você tem duas opções:  
  
- Na `Select` cláusula, especifique os campos que deseja incluir no resultado. O compilador definirá um tipo anônimo que tem esses campos como suas propriedades. Para obter mais informações, consulte [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Como os elementos retornados no exemplo a seguir são instâncias de um tipo anônimo, você não pode se referir ao tipo por nome em outro lugar em seu código. O nome designado pelo compilador para o tipo contém caracteres que não são válidos no código Visual Basic normal. No exemplo a seguir, os elementos da coleção que `londonCusts4` são devolvidos pela consulta em são instâncias de um tipo anônimo  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -ou-  
  
- Defina um tipo nomeado que contenha os campos específicos que você deseja incluir no `Select` resultado e crie e inicialize instâncias do tipo na cláusula. Use esta opção somente se você tiver que usar resultados individuais fora da coleção em que eles são devolvidos, ou se você tiver que passá-los como parâmetros em chamadas de método. O tipo `londonCusts5` de no exemplo a seguir é IEnumerable (Of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Para obter mais informações `Select` sobre como usar a cláusula no Visual Basic, consulte [Selecionar Cláusula](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Ingressando Dados (Ingressar e Agrupar Junções)  
 Você pode combinar mais de `From` uma fonte de dados na cláusula de várias maneiras. Por exemplo, o código a seguir usa duas fontes de dados e combina implicitamente propriedades de ambas no resultado. A consulta seleciona alunos cujos sobrenomes começam com uma vogal.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Você pode executar este código com a lista de alunos criados em [Como: Criar uma Lista de Itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 A `Join` palavra-chave é `INNER JOIN` equivalente a um em SQL. Combina duas coleções com base na correspondência de valores-chave entre os elementos das duas coleções. A consulta retorna todos ou parte dos elementos de coleção que têm valores-chave correspondentes. Por exemplo, o código a seguir duplica a ação da adesão implícita anterior.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`combina coleções em uma única coleção hierárquica, assim como uma `LEFT JOIN` em SQL. Para obter mais informações, consulte [Aderse a Cláusula](../../../../visual-basic/language-reference/queries/join-clause.md) e [Cláusula de Adesão ao Grupo](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Agrupando Dados (Agrupar Por)  
 Você pode `Group By` adicionar uma cláusula para agrupar os elementos em um resultado de consulta de acordo com um ou mais campos dos elementos. Por exemplo, os seguintes grupos de código são estudantes por ano de aula.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Se você executar este código usando a lista de alunos criados em [Como: Criar uma Lista de Itens,](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)a saída da `For Each` declaração é:  
  
 Ano: Júnior  
  
 Tucker  
  
 Garcia  
  
 Garcia  
  
 Tucker  
  
 Ano: Sênior  
  
 Omelchenko  
  
 Osada  
  
 Fakhouri  
  
 Feng  
  
 Adams  
  
 Ano: Calouro  
  
 Mortensen  
  
 Garcia  
  
 A variação mostrada no código a seguir ordena os anos de aula e, em seguida, ordena os alunos dentro de cada ano pelo sobrenome.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Para obter `Group By`mais informações sobre , consulte [Grupo por Cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Collections.Generic.IEnumerable%601>
- [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
- [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Linq](../../../../visual-basic/programming-guide/language-features/linq/index.md)
