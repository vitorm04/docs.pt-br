---
title: Ignorar cláusula While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 3d6caeb1938e8e53e8ec2575f740cd5e49496f62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054413"
---
# <a name="skip-while-clause-visual-basic"></a>Ignorar cláusula While (Visual Basic)
Ignora elementos em uma coleção, desde que uma condição especificada seja `true` e, em seguida, retorna os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`expression`|Necessário. Uma expressão que representa uma condição para testar elementos. A expressão deve retornar um `Boolean` valor ou um equivalente funcional, como um `Integer` a ser avaliada como um `Boolean`.|  
  
## <a name="remarks"></a>Comentários  
 O `Skip While` cláusula ignora elementos desde o início de um resultado de consulta até que o fornecido `expression` retorna `false`. Após `expression` retorna `false`, a consulta retorna todos os elementos restantes. O `expression` é ignorado para os resultados restantes.  
  
 O `Skip While` cláusula difere de `Where` cláusula em que o `Where` cláusula pode ser usada para excluir todos os elementos de uma consulta que não atendem a uma determinada condição. O `Skip While` cláusula excluir elementos apenas até a primeira vez em que a condição não for atendida. O `Skip While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.  
  
 Você pode ignorar um número específico de resultados desde o início de uma consulta usando o `Skip` cláusula.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Skip While` cláusula para ignorar resultados até que o primeiro cliente dos Estados Unidos é encontrado.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
