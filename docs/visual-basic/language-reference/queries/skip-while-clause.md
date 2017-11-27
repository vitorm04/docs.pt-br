---
title: "Ignorar cláusula While (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a>Ignorar cláusula While (Visual Basic)
Ignora elementos em uma coleção desde que uma condição especificada seja `true` e, em seguida, retorna os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`expression`|Necessário. Uma expressão que representa uma condição para testar elementos. A expressão deve retornar um `Boolean` valor ou um equivalente funcional, como um `Integer` a ser avaliada como um `Boolean`.|  
  
## <a name="remarks"></a>Comentários  
 O `Skip While` cláusula ignora elementos desde o início de uma consulta até fornecido `expression` retorna `false`. Depois de `expression` retorna `false`, a consulta retorna todos os elementos restantes. O `expression` é ignorada para os resultados restantes.  
  
 O `Skip While` cláusula difere do `Where` cláusula em que o `Where` cláusula pode ser usada para excluir todos os elementos de uma consulta que não atendem a uma determinada condição. O `Skip While` cláusula excluir elementos apenas até a primeira vez que a condição não for atendida. O `Skip While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.  
  
 Você pode ignorar um número específico de resultados desde o início de uma consulta usando o `Skip` cláusula.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Skip While` cláusula para ignorar resultados até que o primeiro cliente dos Estados Unidos é encontrado.  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
