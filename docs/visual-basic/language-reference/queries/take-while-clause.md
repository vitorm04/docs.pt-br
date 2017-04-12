---
title: "Cláusula Take While (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTakeWhile
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause
- Take While statement
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 14
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
ms.openlocfilehash: 859fb96c2639f4a2bb78377ac243b7f95baf2c71
ms.lasthandoff: 03/13/2017

---
# <a name="take-while-clause-visual-basic"></a>Cláusula Take While (Visual Basic)
Inclui elementos em uma coleção desde que uma condição especificada for `true` e ignora os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`expression`|Necessário. Uma expressão que representa uma condição para testar elementos. A expressão deve retornar um `Boolean` valor ou um funcional equivalente, como um `Integer` seja avaliada como um `Boolean`.|  
  
## <a name="remarks"></a>Comentários  
 O `Take While` cláusula inclui elementos desde o início de um resultado de consulta até fornecido `expression` retorna `false`. Após o `expression` retorna `false`, a consulta irá ignorar todos os elementos restantes. O `expression` é ignorada para os resultados restantes.  
  
 O `Take While` cláusula difere do `Where` cláusula em que o `Where` cláusula pode ser usada para incluir todos os elementos de uma consulta que atendam a uma condição específica. O `Take While` cláusula inclui elementos apenas até a primeira vez que a condição não for atendida. O `Take While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Take While` cláusula para recuperar os resultados até que o primeiro cliente sem qualquer pedido é encontrado.  
  
 [!code-vb[VbSimpleQuerySamples n º&2;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)   
 [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
