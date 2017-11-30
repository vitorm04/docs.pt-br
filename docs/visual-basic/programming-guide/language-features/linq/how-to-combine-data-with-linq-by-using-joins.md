---
title: "Como combinar dados a LINQ com junções (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 432be646ce4353fd4627a34f363e7562f6181e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Como combinar dados a LINQ com junções (Visual Basic)
Visual Basic fornece o `Join` e `Group Join` cláusulas para que você possa combinar o conteúdo de várias coleções com base em valores comuns entre as coleções de consulta. Esses valores são conhecidos como *chave* valores. Os desenvolvedores familiarizados com conceitos de banco de dados relacional reconhecerá o `Join` cláusula como um INNER JOIN e o `Group Join` cláusula as, efetivamente, uma junção externa esquerda.  
  
 Os exemplos neste tópico demonstram algumas maneiras de combinar dados usando o `Join` e `Group Join` cláusulas de consulta.  
  
## <a name="create-a-project-and-add-sample-data"></a>Criar um projeto e adicione dados de exemplo  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Para criar um projeto que contém os tipos e dados de exemplo  
  
1.  Para executar os exemplos neste tópico, abra o Visual Studio e adicionar um novo projeto de aplicativo de Console do Visual Basic. Clique duas vezes o arquivo Module1. vb criado pelo Visual Basic.  
  
2.  Os exemplos neste tópico usam o `Person` e `Pet` tipos e dados do exemplo de código a seguir. Copie este código para o padrão `Module1` módulo criado pelo Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Executar uma junção interna usando a cláusula Join.  
 Uma INNER JOIN combina dados de duas coleções. Itens para os quais os valores de chave especificados correspondem aos são incluídos. Todos os itens de qualquer coleção que não têm um item correspondente na outra coleção são excluídos.  
  
 No Visual Basic, LINQ fornece duas opções para executar uma INNER JOIN: um join implícito e um join explícito.  
  
 Um join implícito especifica as coleções a serem agrupadas uma `From` cláusula e identifica os campos de chave correspondentes em um `Where` cláusula. Visual Basic junta implicitamente as duas coleções com base em campos de chave especificados.  
  
 Você pode especificar uma associação explícita usando o `Join` cláusula quando você deseja ser específico sobre quais campos-chave para usar na junção. Nesse caso, um `Where` cláusula ainda pode ser usada para filtrar os resultados da consulta.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Para executar uma Inner Join usando a cláusula Join.  
  
1.  Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de ambos os uma implícita e explícita inner join.  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Executar uma junção externa esquerda usando a cláusula Group Join  
 LEFT OUTER JOIN inclui todos os itens da coleção do lado esquerdo da junção e apenas valores correspondentes da coleção do lado direito da junção. Quaisquer itens da coleção do lado direito da junção que não têm um item correspondente na coleção do lado esquerdo são excluídos do resultado da consulta.  
  
 O `Group Join` cláusula executa, na verdade, uma junção externa esquerda. A diferença entre o que é normalmente conhecido como LEFT OUTER JOIN e o que o `Group Join` cláusula retorna é que o `Group Join` resultados de grupos de cláusula da coleção do lado direito da junção para cada item da coleção do lado esquerdo. Em um banco de dados relacional, uma junção externa esquerda retorna um resultado desagrupado no qual cada item na consulta resultar contém itens correspondentes de ambos os conjuntos na junção. Nesse caso, os itens da coleção do lado esquerdo da junção são repetidos para cada item correspondente da coleção do lado direito. Você verá a aparência quando você concluir o procedimento a seguir.  
  
 Você pode recuperar os resultados de uma `Group Join` consulta como um resultado desagrupado estendendo sua consulta para retornar um item para cada resultado da consulta agrupada. Para fazer isso, você precisa garantir que você consulte o `DefaultIfEmpty` método da coleção agrupada. Isso garante que os itens da coleção do lado esquerdo da junção ainda estão incluídos no resultado da consulta mesmo se eles não têm resultados correspondentes da coleção do lado direito. Você pode adicionar código à sua consulta para fornecer um valor de resultado padrão quando não há nenhum valor correspondente da coleção do lado direito da junção.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Para executar uma junção externa esquerda, usando a cláusula Group Join  
  
1.  Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de uma junção externa esquerda agrupada e uma desagrupados junção externa esquerda.  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Executar uma junção, usando uma chave composta  
 Você pode usar o `And` palavra-chave em um `Join` ou `Group Join` cláusula para identificar vários campos de chave a ser usado durante a correspondência de valores das coleções que estão sendo combinadas. O `And` palavra-chave especifica que todos os especificado campos-chave devem corresponder para os itens a serem agrupados.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Para executar uma junção, usando uma chave composta  
  
1.  Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de uma junção que usa uma chave composta.  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a>Execute o código  
  
#### <a name="to-add-code-to-run-the-examples"></a>Para adicionar código para executar os exemplos  
  
1.  Substitua o `Sub Main` no `Module1` módulo em seu projeto com o código a seguir para executar os exemplos neste tópico.  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  Pressione F5 para executar os exemplos.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Cláusula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)  
 [Transformações de dados com LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
