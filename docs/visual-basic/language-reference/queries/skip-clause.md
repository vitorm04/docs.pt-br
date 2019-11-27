---
title: Cláusula Skip
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: c582b014bad4fa8fa3165d2b756f4bc955840cfc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349650"
---
# <a name="skip-clause-visual-basic"></a>Cláusula Skip (Visual Basic)
Ignora um número especificado de elementos em uma coleção e, em seguida, retorna os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Partes  
 `count`  
 Necessária. Um valor ou uma expressão que é avaliada como o número de elementos da sequência a serem ignorados.  
  
## <a name="remarks"></a>Comentários  
 A cláusula `Skip` faz com que uma consulta ignore os elementos no início de uma lista de resultados e retorne os elementos restantes. O número de elementos a serem ignorados é identificado pelo parâmetro `count`.  
  
 Você pode usar a cláusula `Skip` com a cláusula `Take` para retornar um intervalo de dados de qualquer segmento de uma consulta. Para fazer isso, passe o índice do primeiro elemento do intervalo para a cláusula `Skip` e o tamanho do intervalo para a cláusula `Take`.  
  
 Quando você usa a cláusula `Skip` em uma consulta, também pode ser necessário garantir que os resultados sejam retornados em uma ordem que permitirá que a cláusula `Skip` ignore os resultados pretendidos. Para obter mais informações sobre como ordenar os resultados da consulta, consulte [cláusula order by](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Você pode usar a cláusula `SkipWhile` para especificar que apenas determinados elementos sejam ignorados, dependendo de uma condição fornecida.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir usa a cláusula `Skip` junto com a cláusula `Take` para retornar dados de uma consulta em páginas. A função `GetCustomers` usa a cláusula `Skip` para ignorar os clientes na lista até o valor de índice inicial fornecido e usa a cláusula `Take` para retornar uma página de clientes que começam com esse valor de índice.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)
