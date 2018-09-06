---
title: Como combinar dados a LINQ com junções (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 4db5d288d79379b677bb19b2eba0d094e0d71bc8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748398"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Como combinar dados a LINQ com junções (Visual Basic)
O Visual Basic fornece o `Join` e `Group Join` cláusulas para que você possa combinar o conteúdo de várias coleções com base nos valores comuns entre as coleções de consulta. Esses valores são conhecidos como *chave* valores. Os desenvolvedores familiarizados com conceitos de banco de dados relacional reconhecerá a `Join` cláusula como um INNER JOIN e o `Group Join` cláusula como, efetivamente, uma junção externa esquerda.  
  
 Os exemplos neste tópico demonstram algumas maneiras de combinar dados usando o `Join` e `Group Join` cláusulas de consulta.  
  
## <a name="create-a-project-and-add-sample-data"></a>Criar um projeto e adicionar dados de exemplo  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Para criar um projeto que contém dados de exemplo e tipos  
  
1.  Para executar os exemplos neste tópico, abra o Visual Studio e adicione um novo projeto de aplicativo de Console do Visual Basic. Clique duas vezes no arquivo Module1.vb criado pelo Visual Basic.  
  
2.  Os exemplos neste tópico usam o `Person` e `Pet` tipos e dados do exemplo de código a seguir. Copie esse código para o padrão `Module1` módulo criado pelo Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Realizar uma junção interna usando a cláusula de junção  
 Uma INNER JOIN combina dados de duas coleções. Itens para os quais os valores de chave especificados correspondem são incluídos. Todos os itens de qualquer coleção que não têm um item correspondente na outra coleção são excluídos.  
  
 No Visual Basic LINQ fornece duas opções para executar uma junção interna: um join implícito e um join explícito.  
  
 Um join implícito especifica as coleções a serem agrupadas uma `From` cláusula e identifica os campos de chave correspondentes em um `Where` cláusula. Visual Basic implicitamente une as duas coleções com base em campos de chave especificados.  
  
 Você pode especificar um join explícito usando o `Join` cláusula quando desejar ser específico sobre quais campos-chave para usar na junção. Nesse caso, um `Where` cláusula ainda pode ser usada para filtrar os resultados da consulta.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Para executar uma Inner Join, usando a cláusula de junção  
  
1.  Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de ambos os uma implícita e explícita junção interna.  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Realizar uma junção externa esquerda, usando a cláusula Group Join  
 LEFT OUTER JOIN inclui todos os itens da coleção do lado esquerdo da junção e apenas valores correspondentes da coleção do lado direito da junção. Todos os itens da coleção do lado direito da junção que não têm um item correspondente da coleção do lado esquerdo são excluídos do resultado da consulta.  
  
 O `Group Join` cláusula realiza, na verdade, uma junção externa esquerda. A diferença entre o que é normalmente conhecido como LEFT OUTER JOIN e o que o `Group Join` cláusula retorna é que o `Group Join` resultados de grupos de cláusula da coleção do lado direito da junção para cada item da coleção do lado esquerdo. Em um banco de dados relacional, uma junção externa esquerda retorna um resultado desagrupado no qual cada item na consulta resultar contém itens correspondentes de ambos os conjuntos na junção. Nesse caso, os itens da coleção do lado esquerdo da junção são repetidos para cada item correspondente da coleção do lado direito. Você verá como isso aparece quando você concluir o procedimento a seguir.  
  
 Você pode recuperar os resultados de uma `Group Join` consulta como um resultado desagrupado estendendo sua consulta para retornar um item para cada resultado da consulta agrupada. Para fazer isso, você precisa garantir que você consulte o `DefaultIfEmpty` método da coleção agrupada. Isso garante que os itens da coleção do lado esquerdo da junção ainda são incluídos no resultado da consulta, mesmo se eles tiverem nenhum resultado correspondente da coleção do lado direito. Você pode adicionar código à sua consulta para fornecer um valor de resultado padrão quando não há nenhum valor correspondente da coleção do lado direito da junção.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Para executar uma junção externa esquerda, usando a cláusula Group Join  
  
1.  Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de uma junção externa esquerda de agrupados e uma junção externa esquerda de desagrupados.  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Executar uma junção, usando uma chave composta  
 Você pode usar o `And` palavra-chave em um `Join` ou `Group Join` cláusula para identificar vários campos de chave para usar durante a correspondência de valores das coleções que estão sendo combinadas. O `And` palavra-chave especifica que todos especificados em campos de chave devem corresponder para os itens a serem agrupados.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Para executar uma junção, usando uma chave composta  
  
1.  Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de uma junção que usa uma chave composta.  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a>Execute o código  
  
#### <a name="to-add-code-to-run-the-examples"></a>Para adicionar código para executar os exemplos  
  
1.  Substitua os `Sub Main` no `Module1` módulo em seu projeto com o código a seguir para executar os exemplos neste tópico.  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  Pressione F5 para executar os exemplos.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Cláusula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/index.md)  
 [Transformações de dados com LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
