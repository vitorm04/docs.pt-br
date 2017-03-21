---
title: Particionamento de dados (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a746ce3e24812d1df6b6e221cca0364bf2cc7f1c
ms.lasthandoff: 03/13/2017

---
# <a name="partitioning-data-visual-basic"></a>Particionamento de dados (Visual Basic)
Particionamento em LINQ refere-se a operação de dividir uma sequência de entrada em duas seções, sem reorganizar os elementos e, em seguida, retornando uma das seções.  
  
 A ilustração a seguir mostra os resultados de três particionamentos operações diferentes em uma sequência de caracteres. A primeira operação retorna os três primeiros elementos na sequência. A segunda operação ignora os três primeiros elementos e retorna os elementos restantes. A terceira operação ignora os primeiros dois elementos na sequência e retorna os três elementos.  
  
 ![Operações de particionamento de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Os métodos de operador de consulta padrão que sequências de partição são listados na seção a seguir.  
  
## <a name="operators"></a>Operadores  
  
|Nome do operador|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|Ignora elementos até uma posição especificada em uma sequência.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|SkipWhile|Ignora elementos com base em uma função de predicado até que um elemento não atendem à condição.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|Take|Usa elementos até uma posição especificada em uma sequência.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|TakeWhile|Usa elementos com base em uma função de predicado até que um elemento não atendem à condição.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta  
  
### <a name="skip"></a>Skip  
 O seguinte exemplo de código usa o `Skip` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para ignorar as primeiras quatro cadeias de caracteres em uma matriz de cadeias de caracteres antes de retornar as cadeias de caracteres restantes na matriz.  
  
 [!code-vb[CsLINQPartitioning n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 O seguinte exemplo de código usa o `Skip While` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ignorar as cadeias de caracteres em uma matriz durante a primeira letra da cadeia de caracteres é "a". As cadeias de caracteres restantes na matriz são retornadas.  
  
 [!code-vb[CsLINQPartitioning n º&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 O seguinte exemplo de código usa o `Take` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para retornar as primeiras duas cadeias de caracteres em uma matriz de cadeias de caracteres.  
  
 [!code-vb[CsLINQPartitioning n º&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 O seguinte exemplo de código usa o `Take While` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para retornar cadeias de caracteres de uma matriz, enquanto o comprimento da cadeia de caracteres é de cinco ou menos.  
  
 [!code-vb[CsLINQPartitioning n º&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq></xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula Skip](../../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Cláusula Skip While](../../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Cláusula Take](../../../../visual-basic/language-reference/queries/take-clause.md)   
 [Cláusula Take While](../../../../visual-basic/language-reference/queries/take-while-clause.md)
