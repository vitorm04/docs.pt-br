---
title: Particionamento de dados (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ea305a67765e1b11ceebbf65c48a685024a41f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-visual-basic"></a>Particionamento de dados (Visual Basic)
Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.  
  
 A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres. A primeira operação retorna os três primeiros elementos na sequência. A segunda operação ignora os três primeiros elementos e retorna os elementos restantes. A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.  
  
 ![Operações de particionamento de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.  
  
## <a name="operators"></a>Operadores  
  
|Nome do operador|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|Ignora elementos até uma posição especificada na sequência.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Aceita elementos até uma posição especificada na sequência.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta  
  
### <a name="skip"></a>Skip  
 O seguinte exemplo de código usa o `Skip` cláusula [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] para ignorar as primeiras quatro cadeias de caracteres em uma matriz de cadeias de caracteres antes de retornar as cadeias de caracteres restantes na matriz.  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 O seguinte exemplo de código usa o `Skip While` cláusula [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ignorar as cadeias de caracteres em uma matriz durante a primeira letra da cadeia de caracteres é "a". As cadeias de caracteres restantes na matriz são retornadas.  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 O seguinte exemplo de código usa o `Take` cláusula [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] para retornar as primeiras duas cadeias de caracteres em uma matriz de cadeias de caracteres.  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 O seguinte exemplo de código usa o `Take While` cláusula [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] para retornar cadeias de caracteres de uma matriz, enquanto o comprimento da cadeia de caracteres for cinco ou menos.  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>  
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Cláusula Skip](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Cláusula Skip While](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Cláusula Take](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [Cláusula Take While](../../../../visual-basic/language-reference/queries/take-while-clause.md)
