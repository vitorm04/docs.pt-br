---
title: "Cláusula JOIN (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement
- Join clause
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 0a017032e3e0bb06986a5c52f03725f714d9bd95
ms.lasthandoff: 03/13/2017

---
# <a name="join-clause-visual-basic"></a>Cláusula Join (Visual Basic)
Combina duas coleções em uma única coleção. A operação de junção é baseada em chaves correspondentes e usa o `Equals` operador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>Partes  
 `element`  
 Necessário. A variável de controle para a coleção sendo associada.  
  
 `collection`  
 Necessário. A coleção a combinar com a coleção identificada no lado esquerdo do `Join` operador. A `Join` cláusula pode ser aninhada em outro `Join` cláusula, ou em um `Group Join` cláusula.  
  
 `joinClause`  
 Opcional. Um ou mais adicionais `Join` outras cláusulas refinar a consulta.  
  
 `groupJoinClause`  
 Opcional. Um ou mais adicionais `Group Join` outras cláusulas refinar a consulta.  
  
 `key1` `Equals` `key2`  
 Necessário. Identifica chaves para as coleções que estão sendo combinadas. Você deve usar o `Equals` operador para comparar chaves das coleções que estão sendo combinadas. Você pode combinar condições de associação usando o `And` operador para identificar várias chaves. `key1`deve ser da coleção no lado esquerdo do `Join` operador. `key2`deve ser da coleção no lado direito do `Join` operador.  
  
 As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção. No entanto, cada expressão chave pode conter somente itens da sua respectiva coleção.  
  
## <a name="remarks"></a>Comentários  
 O `Join` cláusula combina duas coleções baseadas nos valores de chave das coleções que estão sendo combinadas correspondentes. A coleção resultante pode conter qualquer combinação de valores da coleção no lado esquerdo do `Join` operador e na coleção identificada no `Join` cláusula. A consulta retornará apenas os resultados para os quais a condição especificada, o `Equals` operador for atendido. Isso é equivalente a um `INNER JOIN` no SQL.  
  
 Você pode usar várias `Join` cláusulas em uma consulta para unir dois ou mais coleções em uma única coleção.  
  
 Você pode executar uma junção implícita para combinar coleções sem a `Join` cláusula. Para fazer isso, incluir vários `In` cláusulas em seu `From` cláusula e especifique um `Where` cláusula que identifica as chaves que você deseja usar para a junção.  
  
 Você pode usar o `Group Join` cláusula para combinar coleções em uma única coleção hierárquica. Isso é como um `LEFT OUTER JOIN` no SQL.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir executa uma junção implícita para combinar uma lista de clientes com seus pedidos.  
  
 [!code-vb[VbSimpleQuerySamples&13;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir une duas coleções usando a `Join` cláusula.  
  
 [!code-vb[VbSimpleQuerySamples&#12;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 Este exemplo produzirá a saída semelhante à seguinte:  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir une duas coleções usando a `Join` cláusula com duas colunas de chave.  
  
 [!code-vb[17 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 Este exemplo produzirá a saída semelhante à seguinte:  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
