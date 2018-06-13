---
title: Cláusula Take While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 7e0a6bd77ca2594e9d74e669fcd9cddf91ee1cad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600894"
---
# <a name="take-while-clause-visual-basic"></a>Cláusula Take While (Visual Basic)
Inclui elementos em uma coleção desde que uma condição especificada seja `true` e ignora os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`expression`|Necessário. Uma expressão que representa uma condição para testar elementos. A expressão deve retornar um `Boolean` valor ou um equivalente funcional, como um `Integer` a ser avaliada como um `Boolean`.|  
  
## <a name="remarks"></a>Comentários  
 O `Take While` cláusula inclui elementos desde o início de uma consulta até fornecido `expression` retorna `false`. Após o `expression` retorna `false`, a consulta irá ignorar todos os elementos restantes. O `expression` é ignorada para os resultados restantes.  
  
 O `Take While` cláusula difere do `Where` cláusula em que o `Where` cláusula pode ser usada para incluir todos os elementos de uma consulta que atendam a uma condição específica. O `Take While` cláusula inclui elementos apenas até a primeira vez que a condição não for atendida. O `Take While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Take While` cláusula para recuperar os resultados até que o primeiro cliente sem qualquer pedido é encontrado.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
