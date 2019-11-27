---
title: 'Como: combinar dados com LINQ usando junções'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 7279908c5d262b65f4c4da9cd9b6c1b4117bc402
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344997"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Como combinar dados a LINQ com junções (Visual Basic)
Visual Basic fornece as cláusulas de consulta `Join` e `Group Join` para permitir que você combine o conteúdo de várias coleções com base em valores comuns entre as coleções. Esses valores são conhecidos como valores de *chave* . Os desenvolvedores familiarizados com conceitos de banco de dados relacional reconhecerão a cláusula `Join` como uma junção interna e a cláusula `Group Join` como, efetivamente, uma junção externa esquerda.  
  
 Os exemplos neste tópico demonstram algumas maneiras de combinar dados usando as cláusulas de consulta `Join` e `Group Join`.  
  
## <a name="create-a-project-and-add-sample-data"></a>Criar um projeto e adicionar dados de exemplo  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Para criar um projeto que contém dados de exemplo e tipos  
  
1. Para executar os exemplos neste tópico, abra o Visual Studio e adicione um novo projeto de aplicativo de console Visual Basic. Clique duas vezes no arquivo Module1. vb criado por Visual Basic.  
  
2. Os exemplos neste tópico usam os tipos `Person` e `Pet` e dados do exemplo de código a seguir. Copie esse código para o módulo de `Module1` padrão criado por Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Executar uma junção interna usando a cláusula JOIN  
 Uma junção interna combina dados de duas coleções. Os itens para os quais os valores de chave especificados correspondem são incluídos. Todos os itens de uma das coleções que não têm um item correspondente na outra coleção são excluídos.  
  
 No Visual Basic, o LINQ fornece duas opções para executar uma junção interna: uma junção implícita e uma junção explícita.  
  
 Uma junção implícita especifica as coleções a serem unidas em uma cláusula `From` e identifica os campos de chave correspondentes em uma cláusula `Where`. Visual Basic une implicitamente as duas coleções com base nos campos de chave especificados.  
  
 Você pode especificar uma junção explícita usando a cláusula `Join` quando quiser ser específico sobre quais campos de chave usar na junção. Nesse caso, uma cláusula `Where` ainda pode ser usada para filtrar os resultados da consulta.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Para executar uma junção interna usando a cláusula JOIN  
  
1. Adicione o código a seguir ao módulo `Module1` em seu projeto para ver exemplos de uma junção interna implícita e explícita.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Executar uma junção externa esquerda usando a cláusula Group Join  
 Uma junção externa esquerda inclui todos os itens da coleção do lado esquerdo da junção e apenas valores correspondentes da coleção do lado direito da junção. Todos os itens da coleção do lado direito da junção que não têm um item correspondente na coleção do lado esquerdo são excluídos do resultado da consulta.  
  
 A cláusula `Group Join` executa, na verdade, uma junção externa esquerda. A diferença entre o que normalmente é conhecido como uma junção externa esquerda e o que a cláusula `Group Join` retorna é que a cláusula `Group Join` agrupa os resultados da coleção do lado direito da junção para cada item na coleção do lado esquerdo. Em um banco de dados relacional, uma junção externa esquerda retorna um resultado não agrupado no qual cada item no resultado da consulta contém itens correspondentes de ambas as coleções na junção. Nesse caso, os itens da coleção do lado esquerdo da junção são repetidos para cada item correspondente da coleção do lado direito. Você verá como isso se parece quando você conclui o próximo procedimento.  
  
 Você pode recuperar os resultados de uma consulta `Group Join` como um resultado não agrupado estendendo sua consulta para retornar um item para cada resultado de consulta agrupado. Para fazer isso, você precisa garantir que você consulte o método `DefaultIfEmpty` da coleção agrupada. Isso garante que os itens da coleção do lado esquerdo da junção ainda estejam incluídos no resultado da consulta, mesmo que não tenham resultados correspondentes da coleção do lado direito. Você pode adicionar código à sua consulta para fornecer um valor de resultado padrão quando não houver nenhum valor correspondente da coleção do lado direito da junção.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Para executar uma junção externa esquerda usando a cláusula Group Join  
  
1. Adicione o seguinte código ao módulo `Module1` em seu projeto para ver exemplos de uma junção externa agrupada à esquerda e uma junção externa esquerda desagrupada.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Executar uma junção usando uma chave composta  
 Você pode usar a palavra-chave `And` em uma cláusula `Join` ou `Group Join` para identificar vários campos de chave a serem usados ao corresponder valores das coleções que estão sendo Unidas. A palavra-chave `And` especifica que todos os campos de chave especificados devem corresponder aos itens a serem ingressados.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Para executar uma junção usando uma chave composta  
  
1. Adicione o código a seguir ao módulo `Module1` em seu projeto para ver exemplos de uma junção que usa uma chave composta.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Executar o código  
  
#### <a name="to-add-code-to-run-the-examples"></a>Para adicionar código para executar os exemplos  
  
1. Substitua o `Sub Main` no módulo `Module1` em seu projeto pelo código a seguir para executar os exemplos neste tópico.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. Pressione F5 para executar os exemplos.  
  
## <a name="see-also"></a>Consulte também

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Cláusula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
- [Transformações de dados com LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
