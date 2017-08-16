---
title: "Ignorar cláusula While (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkipWhile
dev_langs:
- VB
helpviewer_keywords:
- Skip While statement
- Skip While clause
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: ca59068b66f55126afdf3f0718ce42c1ee95e5bd
ms.lasthandoff: 03/13/2017

---
# <a name="skip-while-clause-visual-basic"></a>Ignorar cláusula While (Visual Basic)
Ignora elementos em uma coleção desde que uma condição especificada for `true` e, em seguida, retorna os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`expression`|Necessário. Uma expressão que representa uma condição para testar elementos. A expressão deve retornar um `Boolean` valor ou um funcional equivalente, como um `Integer` seja avaliada como um `Boolean`.|  
  
## <a name="remarks"></a>Comentários  
 O `Skip While` cláusula ignora elementos do começo do resultado de uma consulta até fornecido `expression` retorna `false`. Depois de `expression` retorna `false`, a consulta retorna todos os elementos restantes. O `expression` é ignorada para os resultados restantes.  
  
 O `Skip While` cláusula difere do `Where` cláusula em que o `Where` cláusula pode ser usada para excluir todos os elementos de uma consulta que não atendem a uma condição específica. O `Skip While` cláusula excluir elementos apenas até a primeira vez que a condição não for atendida. O `Skip While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.  
  
 Você pode ignorar um número específico de resultados desde o início de uma consulta usando o `Skip` cláusula.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Skip While` cláusula para ignorar resultados até que o primeiro cliente dos Estados Unidos é encontrado.  
  
 [!code-vb[VbSimpleQuerySamples n º&3;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
