---
title: "Como: combinar dados com LINQ com junções (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: afa21d4fb3a4a6a37703114f7d47163155aafbad
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Como combinar dados a LINQ com junções (Visual Basic)
O Visual Basic fornece o `Join` e `Group Join` cláusulas para que você possa combinar o conteúdo de várias coleções com base em valores comuns entre as coleções de consulta. Esses valores são conhecidos como *chave* valores. Os desenvolvedores familiarizados com os conceitos de banco de dados relacional reconhecerá o `Join` cláusula como um INNER JOIN e o `Group Join` cláusula como efetivamente, um LEFT OUTER JOIN.  
  
 Os exemplos neste tópico demonstram algumas maneiras de combinar dados usando o `Join` e `Group Join` cláusulas de consulta.  
  
## <a name="create-a-project-and-add-sample-data"></a>Criar um projeto e adicione dados de exemplo  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Para criar um projeto que contém dados de exemplo e tipos  
  
1.  Para executar os exemplos neste tópico, abra o Visual Studio e adicione um novo projeto de aplicativo de Console do Visual Basic. Clique duas vezes no arquivo Module1 vb criado pelo Visual Basic.  
  
2.  Os exemplos neste tópico usam o `Person` e `Pet` tipos e dados do exemplo de código a seguir. Copie este código para o padrão `Module1` módulo criado pelo Visual Basic.  
  
     [!code-vb[VbLINQHowTos n º&1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos n º&2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Faça uma Inner Join usando a cláusula Join.  
 Uma INNER JOIN combina dados de duas coleções. Itens para os quais correspondem aos valores de chave especificados estão incluídos. Todos os itens de qualquer coleção que não têm um item correspondente na outra coleção são excluídos.  
  
 No Visual Basic, LINQ fornece duas opções para executar uma INNER JOIN: um join implícito e um join explícito.  
  
 Um join implícito especifica as coleções a serem unidas um `From` cláusula e identifica os campos-chave correspondentes em uma `Where` cláusula. Visual Basic junta implicitamente as duas coleções baseadas nos campos de chave especificados.  
  
 Você pode especificar um join explícito usando o `Join` cláusula quando desejar ser específico sobre quais campos-chave para usar na join. Nesse caso, um `Where` cláusula ainda pode ser usada para filtrar os resultados da consulta.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Para executar uma Inner Join usando a cláusula Join.  
  
1.  Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de ambos os implícita e explícita associação interna.  
  
     [!code-vb[VbLINQHowTos n º&4;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Executar uma junção externa esquerda usando a cláusula Group Join  
 LEFT OUTER JOIN inclui todos os itens da coleção do lado esquerdo do join e apenas valores correspondentes da coleção do lado direito da associação. Todos os itens da coleção do lado direito do join que não têm um item correspondente na coleção do lado esquerdo são excluídos do resultado da consulta.  
  
 O `Group Join` cláusula executa, efetivamente, um LEFT OUTER JOIN. A diferença entre o que é tipicamente conhecido como LEFT OUTER JOIN e o que o `Group Join` cláusula retorna é que o `Group Join` resultados de grupos de cláusula da coleção do lado direito do join para cada item da coleção do lado esquerdo. Em um banco de dados relacional, um LEFT OUTER JOIN retorna um resultado desagrupado no qual cada item na consulta resultar contém itens correspondentes de ambos os conjuntos na junção. Nesse caso, os itens da coleção do lado esquerdo do join são repetidos para cada item correspondente da coleção do lado direito. Você verá sua aparência quando você concluir o procedimento a seguir.  
  
 Você pode recuperar os resultados de uma `Group Join` consulta como um resultado desagrupado estendendo sua consulta para retornar um item para cada resultado de consulta agrupada. Para fazer isso, você precisa garantir que você consulte o `DefaultIfEmpty` método da coleção agrupada. Isso assegura que os itens da coleção do lado esquerdo do join ainda são incluídos no resultado da consulta mesmo se eles não têm resultados correspondentes da coleção do lado direito. Você pode adicionar código à sua consulta para fornecer um valor de resultado padrão quando não há nenhum valor correspondente da coleção do lado direito da associação.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Para executar um Left Outer Join usando a cláusula Group Join  
  
1.  Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de uma junção externa esquerda agrupada e uma junção externa esquerda desagrupada.  
  
     [!code-vb[VbLINQHowTos n º&3;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Executar uma junção usando uma chave composta  
 Você pode usar o `And` palavra-chave em uma `Join` ou `Group Join` cláusula para identificar vários campos de chave para usar ao combinar valores das coleções que estão sendo combinadas. O `And` palavra-chave especifica que todos os especificados campos-chave devem corresponder para os itens a serem unidas.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Para executar uma associação usando uma chave composta  
  
1.  Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de uma associação que usa uma chave composta.  
  
     [!code-vb[VbLINQHowTos n º&5;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a>Executar o código  
  
#### <a name="to-add-code-to-run-the-examples"></a>Para adicionar código para executar os exemplos  
  
1.  Substitua o `Sub Main` no `Module1` módulo em seu projeto com o código a seguir para executar os exemplos neste tópico.  
  
     [!code-vb[VbLINQHowTos n º&6;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  Pressione F5 para executar os exemplos.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Cláusula JOIN](../../../../visual-basic/language-reference/queries/join-clause.md)   
 [Cláusula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Cláusula FROM](../../../../visual-basic/language-reference/queries/from-clause.md)   
 [Onde cláusula](../../../../visual-basic/language-reference/queries/where-clause.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)   
 [Transformações de dados com LINQ (c#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
