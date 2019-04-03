---
title: Cláusula Skip (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: db2d79596895505ddaa7778e831082a94c7ad44e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821095"
---
# <a name="skip-clause-visual-basic"></a>Cláusula Skip (Visual Basic)
Ignora um número especificado de elementos em uma coleção e, em seguida, retorna os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Partes  
 `count`  
 Necessário. Um valor ou uma expressão que é avaliada como o número de elementos da sequência a ignorar.  
  
## <a name="remarks"></a>Comentários  
 O `Skip` cláusula faz com que uma consulta ignorar a elementos no início de uma lista de resultados e retornar os elementos restantes. O número de elementos a serem ignorados é identificado pelo `count` parâmetro.  
  
 Você pode usar o `Skip` cláusula com o `Take` cláusula para retornar um intervalo de dados de qualquer segmento de uma consulta. Para fazer isso, passe o índice do primeiro elemento do intervalo para o `Skip` cláusula e o tamanho do intervalo para o `Take` cláusula.  
  
 Quando você usa o `Skip` cláusula em uma consulta, você também precisará garantir que os resultados são retornados em uma ordem que permitirá que o `Skip` cláusula para ignorar os resultados pretendidos. Para obter mais informações sobre a ordenação de resultados da consulta, consulte [cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Você pode usar o `SkipWhile` cláusula para especificar que somente determinados elementos são ignorados, dependendo de uma condição fornecida.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Skip` cláusula junto com o `Take` cláusula para retornar dados de uma consulta em páginas. O `GetCustomers` função usa o `Skip` cláusula para ignorar os clientes na lista até que o de índice inicial fornecido valor e usa o `Take` cláusula para retornar uma página de clientes a partir desse valor de índice.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)
