---
title: "Opera&#231;&#245;es de consulta b&#225;sica (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "fontes de dados [LINQ no Visual Basic]"
  - "cláusula Join [LINQ no Visual Basic]"
  - "classificando dados [LINQ no Visual Basic]"
  - "projeções [LINQ no Visual Basic]"
  - "LINQ [Visual Basic], operações de consulta"
  - "cláusula Order By [LINQ no Visual Basic]"
  - "unindo dados [LINQ no Visual Basic]"
  - "consultas operações básicas [LINQ no Visual Basic]"
  - "selecionando dados [LINQ no Visual Basic]"
  - "cláusula Group By [LINQ no Visual Basic]"
  - "agrupando dados [LINQ no Visual Basic]"
  - "cláusula Select [LINQ no Visual Basic]"
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
caps.latest.revision: 37
caps.handback.revision: 37
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Opera&#231;&#245;es de consulta b&#225;sica (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico fornece uma breve introdução a [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressões no Visual Basic e alguns dos tipos típicos de operações que podem ser executadas em uma consulta. Para obter mais informações, consulte os seguintes tópicos:  
  
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [Instruções passo a passo: escrevendo consultas em Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## Especificando a fonte de dados \(de\)  
 Em um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta, a primeira etapa é especificar a fonte de dados que você deseja consultar. Portanto, o `From` cláusula em uma consulta sempre vem em primeiro lugar. Operadores de consulta selecionam e formatar o resultado com base no tipo de origem.  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 O `From` cláusula Especifica a fonte de dados, `customers`, e um *variável de intervalo*, `cust`. A variável de intervalo é como uma variável de iteração do loop, exceto que em uma expressão de consulta, nenhuma iteração real ocorre. Quando a consulta é executada, geralmente usando um `For Each` loop, a variável de intervalo serve como uma referência para cada elemento sucessivo `customers`. Porque o compilador pode inferir o tipo de `cust`, você não precisa especificá\-lo explicitamente. Para obter exemplos de consultas escritas com e sem uma digitação explícita, consulte [Relacionamentos de tipo em operações de consulta \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Para obter mais informações sobre como usar o `From` cláusula no Visual Basic, consulte [Cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## Filtragem de dados \(onde\)  
 Provavelmente, a operação de consulta mais comuns é aplicar um filtro na forma de uma expressão booleana. A consulta retorna apenas os elementos para o qual a expressão for verdadeira. Um `Where` cláusula é usada para executar a filtragem. O filtro especifica quais elementos na fonte de dados para incluir na sequência resultante. No exemplo a seguir, estão incluídos somente aqueles clientes que têm um endereço em Londres.  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 Você pode usar operadores lógicos como `And` e `Or` para combinar expressões de filtro em um `Where` cláusula. Por exemplo, para retornar somente os clientes que são de Londres e cujo nome é Juliana PAEs, use o seguinte código:  
  
```vb#  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Para retornar os clientes de Londres ou Paris, use o seguinte código:  
  
```vb#  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Para obter mais informações sobre como usar o `Where` cláusula no Visual Basic, consulte [Cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## Ordenando dados \(Order By\)  
 Muitas vezes é conveniente classificar dados retornados em uma ordem específica. O `Order By` cláusula fará com que os elementos na sequência retornada seja classificada em um campo ou campos especificados. Por exemplo, a consulta a seguir classifica os resultados com base no `Name` propriedade. Porque `Name` é uma cadeia de caracteres, os dados retornados serão classificados em ordem alfabética, de À Z.  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 Para ordenar os resultados na ordem inversa, de Z a, use o `Order By...Descending` cláusula. O padrão é `Ascending` quando nenhuma `Ascending` nem `Descending` for especificado.  
  
 Para obter mais informações sobre como usar o `Order By` cláusula no Visual Basic, consulte [Cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## Selecionando dados \(Selecionar\)  
 O `Select` cláusula Especifica o formato e conteúdo de elementos retornados. Por exemplo, você pode especificar se os resultados consistirá em completa `Customer` objetos, apenas um `Customer` propriedade, um subconjunto de propriedades, uma combinação das propriedades de várias fontes de dados ou algum novo tipo de resultado com base em um cálculo. Quando o `Select` cláusula produz algo diferente de uma cópia do elemento de origem, a operação é chamada um *projeção*.  
  
 Para recuperar uma coleção que consiste em completa `Customer` objetos, selecione a variável de intervalo:  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 Se um `Customer` instância é um objeto grande com muitos campos, e tudo o que você deseja recuperar é o nome, você pode selecionar `cust.Name`, conforme mostrado no exemplo a seguir. Inferência de tipo local reconhece que isso altera o tipo de resultado de uma coleção de `Customer` objetos a uma coleção de cadeias de caracteres.  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 Para selecionar vários campos da fonte de dados, você tem duas opções:  
  
-   No `Select` cláusula, especifique os campos que deseja incluir no resultado. O compilador definirá um tipo anônimo com esses campos como suas propriedades. Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Como os elementos retornados no exemplo a seguir são instâncias de um tipo anônimo, não faz referência a tipo por nome em outro lugar no seu código. O nome do tipo designado pelo compilador contém caracteres que não são válidos no código do Visual Basic normal. No exemplo a seguir, os elementos da coleção que é retornado pela consulta em `londonCusts4` são instâncias de um tipo anônimo  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     \- ou \-  
  
-   Definir um tipo nomeado que contém os campos específicos que você deseja incluir no resultado e criar e inicializar instâncias do tipo de `Select` cláusula. Use esta opção somente se você precisa usar resultados individuais fora da coleção na qual eles são retornados ou se você tiver para passá\-las como parâmetros em chamadas de método. O tipo de `londonCusts5` no exemplo a seguir é IEnumerable \(Of NamePhone\).  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 Para obter mais informações sobre como usar o `Select` cláusula no Visual Basic, consulte [Cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## Ingressando dados \(ingressar e agrupar junções\)  
 Você pode combinar mais de uma fonte de dados de `From` cláusula de várias maneiras. Por exemplo, o código a seguir usa duas fontes de dados e implicitamente combina propriedades de ambos no resultado. A consulta seleciona os alunos cujos sobrenomes começam com um sinal de vogal.  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  Você pode executar esse código com a lista de alunos criado no [Como criar uma lista de itens](../Topic/How%20to:%20Create%20a%20List%20of%20Items.md).  
  
 O `Join` palavra\-chave é equivalente a um `INNER JOIN` no SQL. Ele combina duas coleções baseadas nos valores de chave de correspondência entre os elementos em duas coleções. A consulta retorna todo ou parte dos elementos da coleção que têm valores de chave correspondentes. Por exemplo, o código a seguir duplica a ação da associação implícita anterior.  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join` combina coleções em uma única coleção hierárquica, assim como um `LEFT JOIN` no SQL. Para obter mais informações, consulte [Cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md) e [Cláusula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## Agrupando dados \(agrupar por\)  
 Você pode adicionar uma `Group By` cláusula para agrupar os elementos de acordo com um ou mais campos dos elementos de um resultado de consulta. Por exemplo, o código a seguir agrupa os alunos por ano de classe.  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 Se você executar esse código usando a lista de alunos criado no [Como criar uma lista de itens](../Topic/How%20to:%20Create%20a%20List%20of%20Items.md), a saída do `For Each` instrução é:  
  
 Ano: júnior  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Ano: sênior  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Ano: primeiro ano  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 A variação mostrada no código a seguir ordena os anos de classe e, em seguida, os alunos os pedidos em cada ano por sobrenome.  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 Para obter mais informações sobre `Group By`, consulte [Cláusula Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## Consulte também  
 <xref:System.Collections.Generic.IEnumerable%601>   
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)   
 [Visão geral de operadores de consulta padrão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)