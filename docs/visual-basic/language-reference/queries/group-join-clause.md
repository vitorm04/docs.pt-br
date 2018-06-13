---
title: Cláusula Join Group (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 094281b0afb34451ae8539e4eb967043b21d379c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604751"
---
# <a name="group-join-clause-visual-basic"></a>Cláusula Join Group (Visual Basic)
Combina duas coleções em uma única coleção hierárquica. A operação de junção é baseada em chaves correspondentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`element`|Necessário. A variável de controle para a coleção sendo unida.|  
|`type`|Opcional. O tipo de `element`. Se nenhum `type` for especificado, o tipo de `element` é inferido do `collection`.|  
|`collection`|Necessário. A coleção a combinar com a coleção que está no lado esquerdo do `Group Join` operador. Um `Group Join` cláusula pode ser aninhada em uma `Join` cláusula ou em outro `Group Join` cláusula.|  
|`key1``Equals``key2`|Necessário. Identifica chaves para as coleções que estão sendo combinadas. Você deve usar o `Equals` operador para comparar chaves das coleções que estão sendo combinadas. Você pode combinar condições de junção usando o `And` operador para identificar várias chaves. O `key1` parâmetro deve ser da coleção no lado esquerdo do `Join` operador. O `key2` parâmetro deve ser da coleção no lado direito do `Join` operador.<br /><br /> As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção. No entanto, cada expressão de chave pode conter apenas os itens da sua respectiva coleção.|  
|`expressionList`|Necessário. Uma ou mais expressões que identificam como os grupos de elementos da coleção são agregados. Para identificar um nome de membro para os resultados agrupados, use o `Group` palavra-chave (`<alias> = Group`). Você também pode incluir funções agregadas para aplicar ao grupo.|  
  
## <a name="remarks"></a>Comentários  
 O `Group Join` cláusula combina duas coleções com base na correspondência de valores de chave das coleções que estão sendo combinadas. A coleção resultante pode conter um membro que referencia uma coleção de elementos da segunda coleção que corresponde ao valor de chave da coleção primeiro. Você também pode especificar funções de agregação para aplicar aos elementos agrupados da segunda coleção. Para obter informações sobre funções de agregação, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Considere, por exemplo, uma coleção de gerentes e uma coleção de funcionários. Elementos de ambas as coleções têm uma propriedade ManagerID que identifica os funcionários subordinados a um gerente específico. Os resultados de uma operação de junção conterá um resultado para cada gerente e funcionário com um valor de ManagerID correspondente. Os resultados de uma `Group Join` operação contém a lista completa dos gerentes. Cada gerente no resultado teria um membro a lista de funcionários que foram uma correspondência para o gerente específico.  
  
 O conjunto resultante de uma `Group Join` operação pode conter qualquer combinação de valores de coleção identificados no `From` cláusula e as expressões identificadas no `Into` cláusula do `Group Join` cláusula. Para obter mais informações sobre expressões válidas para o `Into` cláusula, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Um `Group Join` operação retornará todos os resultados da coleção identificada no lado esquerdo do `Group Join` operador. Isso é verdadeiro mesmo se não houver nenhuma correspondência na coleção sendo associado. Isso é como uma `LEFT OUTER JOIN` em SQL.  
  
 Você pode usar o `Join` cláusula para combinar coleções em uma única coleção. Isso é equivalente a um `INNER JOIN` em SQL.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir une duas coleções usando o `Group Join` cláusula.  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Join](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
