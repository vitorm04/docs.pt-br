---
title: Escrevendo a primeira consulta LINQ (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: 56
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 48f1c5e15654580b6e4d060860a0d7001af5e2ef
ms.lasthandoff: 03/13/2017

---
# <a name="writing-your-first-linq-query-visual-basic"></a>Escrevendo a primeira consulta LINQ (Visual Basic)
A *consulta* é uma expressão que recupera dados de uma fonte de dados. Consultas são expressas em uma linguagem de consulta dedicado. Ao longo do tempo, diferentes idiomas foram desenvolvidos para diferentes tipos de fontes de dados, por exemplo, SQL para bancos de dados relacionais e o XQuery para XML. Isso torna necessária para o desenvolvedor de aplicativos aprender uma nova linguagem de consulta para cada tipo de fonte de dados ou formato de dados que tem suporte.  
  
 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]simplifica a situação, oferecendo um modelo consistente para trabalhar com dados em vários tipos de fontes de dados e formatos. Em um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta, está sempre trabalhando com objetos. Use os mesmos padrões de codificação básicos para consultar e transformar dados em documentos XML, bancos de dados SQL, datasets ADO.NET e entidades, coleções do .NET Framework e outra fonte ou formato para o qual um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedor está disponível. Este documento descreve as três fases da criação e uso do basic [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas.  
  
## <a name="three-stages-of-a-query-operation"></a>Três Estágios de uma Operação de Consulta  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]operações de consulta consiste em três ações:  
  
1.  Obter a fonte de dados ou fontes.  
  
2.  Crie a consulta.  
  
3.  Execute a consulta.  
  
 Em [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], a execução de uma consulta é diferente da criação da consulta. Você não recuperar os dados apenas criando uma consulta. Esse ponto é abordado em mais detalhes posteriormente neste tópico.  
  
 O exemplo a seguir ilustra as três partes de uma operação de consulta. O exemplo usa uma matriz de inteiros como uma fonte de dados conveniente para fins de demonstração. No entanto, os mesmos conceitos também se aplicam a outras fontes de dados.  
  
> [!NOTE]
>  Sobre o [página de compilação, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic), certifique-se de que **Option infer** é definido como **em**.  
  
 [!code-vb[VbLINQFirstQuery n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Saída:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>A Fonte de Dados  
 Como a fonte de dados no exemplo anterior é uma matriz, implicitamente suporta genérica <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601> É esse fato que permite que você use uma matriz como uma fonte de dados para um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta. Tipos que oferecem suporte a <xref:System.Collections.Generic.IEnumerable%601>ou uma interface derivada como genérica <xref:System.Linq.IQueryable%601>são chamados *tipos consultáveis*.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 Como um tipo que podem ser consultado implicitamente, a matriz não requer modificação ou tratamento especial para servir como um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fonte de dados. O mesmo é verdadeiro para qualquer tipo de coleção que oferece suporte a <xref:System.Collections.Generic.IEnumerable%601>, incluindo genérica <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>e outras classes na biblioteca de classes do .NET Framework.</xref:System.Collections.Generic.Dictionary%602> </xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 Se os dados de origem já não implementam <xref:System.Collections.Generic.IEnumerable%601>, um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedor é necessário para implementar a funcionalidade do *operadores de consulta padrão* nessa fonte de dados.</xref:System.Collections.Generic.IEnumerable%601> Por exemplo, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] manipula o trabalho de carregamento de um documento XML em um que podem ser consultados <xref:System.Xml.Linq.XElement>tipo, conforme mostrado no exemplo a seguir.</xref:System.Xml.Linq.XElement> Para obter mais informações sobre operadores de consulta padrão, consulte [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery n º&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 Com [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], primeiro você deve criar um mapeamento relacional de objeto em tempo de design, manualmente ou usando o [LINQ to SQL Tools no Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) no Visual Studio. Você escrever suas consultas em relação os objetos e em tempo de execução [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] gerencia a comunicação com o banco de dados. No exemplo a seguir, `customers` representa uma tabela específica no banco de dados e <xref:System.Data.Linq.Table%601>oferece suporte a genéricos <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Data.Linq.Table%601>  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Para obter mais informações sobre como criar tipos específicos de fontes de dados, consulte a documentação para os diversos [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedores. (Para obter uma lista desses provedores, consulte [LINQ (consulta integrada à linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).) A regra básica é simple: um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fonte de dados é qualquer objeto que ofereça suporte a genéricos <xref:System.Collections.Generic.IEnumerable%601>interface, ou uma interface que herda do proprietário.</xref:System.Collections.Generic.IEnumerable%601>  
  
> [!NOTE]
>  Tipos, como <xref:System.Collections.ArrayList>que oferecem suporte a não genérica <xref:System.Collections.IEnumerable>interface também pode ser usada como [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fontes de dados.</xref:System.Collections.IEnumerable> </xref:System.Collections.ArrayList> Para obter um exemplo que usa um <xref:System.Collections.ArrayList>, consulte [como: consultar um ArrayList com LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).</xref:System.Collections.ArrayList>  
  
## <a name="the-query"></a>A Consulta  
 Na consulta, você deve especificar quais informações você deseja recuperar da fonte de dados ou fontes. Você também tem a opção de especificar como essas informações devem ser classificadas, agrupadas ou estruturadas antes de serem retornado. Para habilitar a criação da consulta, Visual Basic incorporou a nova sintaxe de consulta de linguagem.  
  
 Quando ele é executado, a consulta no exemplo a seguir retorna todos os números pares de uma matriz de inteiros, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 A expressão de consulta contém três cláusulas: `From`, `Where`, e `Select`. A função específica e a finalidade de cada cláusula de expressão de consulta é discutida em [operações básicas de consulta (Visual Basic)](basic-query-operations.md). Para obter mais informações, consulte [consultas](../../../../visual-basic/language-reference/queries/queries.md). Observe que, em [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], uma definição de consulta geralmente é armazenada em uma variável e executada posteriormente. A consulta a variável, como `evensQuery` no exemplo anterior, deve ser um tipo que pode ser consultado. O tipo de `evensQuery` é `IEnumerable(Of Integer)`, atribuído pelo compilador usando inferência de tipo local.  
  
 É importante lembrar que a variável de consulta não faz nada e não retorna nenhum dado. Ela apenas armazena a definição de consulta. No exemplo anterior, ele é o `For Each` loop que executa a consulta.  
  
## <a name="query-execution"></a>Execução da Consulta  
 A execução da consulta é separada da criação da consulta. Criação de consulta define a consulta, mas a execução é disparada por um mecanismo diferente. Uma consulta pode ser executada assim que ela é definida (*execução imediata*), ou a definição pode ser armazenada e a consulta pode ser executada posteriormente (*execução diferida*).  
  
### <a name="deferred-execution"></a>Execução Adiada  
 Um típico [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta semelhante no exemplo anterior, em que `evensQuery` é definido. Ele cria a consulta, mas não executá-lo imediatamente. Em vez disso, a definição de consulta é armazenada na variável de consulta `evensQuery`. Executar a consulta posteriormente, normalmente usando um `For Each` loop, que retorna uma sequência de valores, ou aplicando um operador de consulta padrão, como `Count` ou `Max`. Esse processo é conhecido como *execução diferida*.  
  
 [!code-vb[VbLINQFirstQuery&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Uma sequência de valores, você deve acessar os dados recuperados usando a variável de iteração no `For Each` loop (`number` no exemplo anterior). Porque a variável de consulta, `evensQuery`, contém a definição de consulta, em vez dos resultados da consulta, você pode executar uma consulta sempre que desejar usando a variável de consulta mais de uma vez. Por exemplo, você pode ter um banco de dados em seu aplicativo que está sendo atualizado continuamente por um aplicativo separado. Depois de criar uma consulta que recupera dados do banco de dados, você pode usar um `For Each` loop para executar a consulta repetidamente, recuperar os dados mais recentes toda vez.  
  
 O exemplo a seguir demonstra como execução adiada funciona. Depois de `evensQuery2` é definido e executado com uma `For Each` loop, como nos exemplos anteriores, alguns elementos da fonte de dados `numbers` são alteradas. Em seguida, um segundo `For Each` executa um loop `evensQuery2` novamente. Os resultados são diferentes na segunda vez, porque o `For Each` loop executa a consulta novamente, usando os novos valores no `numbers`.  
  
 [!code-vb[VbLINQFirstQuery n º&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Saída:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Execução Imediata  
 Na execução adiada de consultas, a definição de consulta é armazenada em uma variável de consulta para execução posterior. Execução imediata, a consulta é executada no momento de sua definição. Execução é disparada quando você aplica um método que exige acesso aos elementos individuais do resultado da consulta. Execução imediata geralmente é forçada usando um dos operadores de consulta padrão que retornam valores únicos. Examples are `Count`, `Max`, `Average`, and `First`. Esses operadores de consulta padrão execute a consulta assim que elas são aplicadas para calcular e retornar um resultado singleton. Para obter mais informações sobre operadores de consulta padrão que retornam valores únicos, consulte [operações de agregação](aggregation-operations.md), [operações de elemento](element-operations.md), e [operações de quantificador](quantifier-operations.md).  
  
 A consulta a seguir retorna uma contagem de números pares em uma matriz de inteiros. A definição de consulta não é salvo, e `numEvens` é um simples `Integer`.  
  
 [!code-vb[VbLINQFirstQuery n º&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Você pode obter o mesmo resultado usando o `Aggregate` método.  
  
 [!code-vb[VbLINQFirstQuery n º&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Você também pode forçar a execução de uma consulta chamando o `ToList` ou `ToArray` método em uma consulta (imediata) ou a variável de consulta (diferido), conforme mostrado no código a seguir.  
  
 [!code-vb[VbLINQFirstQuery n º&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 Nos exemplos anteriores, `evensQuery3` é uma consulta de variável, mas `evensList` é uma lista e `evensArray` é uma matriz.  
  
 Usando `ToList` ou `ToArray` para forçar imediata execução é especialmente útil em cenários nos quais você deseja executar a consulta imediatamente e armazenar em cache os resultados em um único objeto de coleção. Para obter mais informações sobre esses métodos, consulte [converter tipos de dados](converting-data-types.md).  
  
 Você também pode causar uma consulta a ser executada usando um `IEnumerable` método como o <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>método.</xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](getting-started-with-linq.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Visão geral de operadores de consulta padrão (Visual Basic)](standard-query-operators-overview.md)   
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)
