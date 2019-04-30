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
ms.openlocfilehash: 3da4ca2db299a65b2c0f1fa259bbaabe4f53aa33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945308"
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
|`collection`|Necessário. A coleção a combinar com a coleção que está no lado esquerdo do `Group Join` operador. Um `Group Join` cláusula pode ser aninhada em um `Join` cláusula ou em outro `Group Join` cláusula.|  
|`key1` `Equals` `key2`|Necessário. Identifica as chaves para as coleções que estão sendo unidas. Você deve usar o `Equals` operador para comparar as chaves das coleções que estão sendo combinadas. Você pode combinar condições de junção, usando o `And` operador para identificar várias chaves. O `key1` parâmetro deve ser da coleção no lado esquerdo do `Join` operador. O `key2` parâmetro deve ser da coleção no lado direito do `Join` operador.<br /><br /> As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção. No entanto, cada expressão de chave pode conter apenas os itens de sua respectiva coleção.|  
|`expressionList`|Necessário. Uma ou mais expressões que identificam como os grupos de elementos da coleção são agregados. Para identificar um nome de membro para os resultados agrupados, use o `Group` palavra-chave (`<alias> = Group`). Você também pode incluir funções agregadas para aplicar ao grupo.|  
  
## <a name="remarks"></a>Comentários  
 O `Group Join` cláusula combina duas coleções com base na correspondência de valores de chave das coleções que estão sendo combinadas. A coleção resultante pode conter um membro que referencia uma coleção de elementos da segunda coleção que correspondem ao valor de chave da primeira coleção. Você também pode especificar funções de agregação a ser aplicado aos elementos agrupados da segunda coleção. Para obter informações sobre funções de agregação, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Considere, por exemplo, uma coleção de gerentes e uma coleção de funcionários. Elementos de ambas as coleções possuem uma propriedade de ManagerID que identifica os funcionários subordinados a um gerente específico. Os resultados de uma operação de junção conteria um resultado para cada gerenciador e funcionário com um valor de ManagerID correspondente. Os resultados de uma `Group Join` operação contém a lista completa dos gerentes. Cada gerente no resultado teria um membro que referenciou a lista de funcionários que eram uma correspondência para o gerente específico.  
  
 O conjunto resultante de uma `Group Join` operação pode conter qualquer combinação de valores na coleção identificada na `From` cláusula e as expressões identificadas na `Into` cláusula do `Group Join` cláusula. Para obter mais informações sobre expressões válidas para o `Into` cláusula, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Um `Group Join` operação retornará todos os resultados da coleção identificada no lado esquerdo do `Group Join` operador. Isso é verdadeiro mesmo se não houver nenhuma correspondência na coleção sendo unidas. Isso é como um `LEFT OUTER JOIN` no SQL.  
  
 Você pode usar o `Join` cláusula para combinar coleções em uma única coleção. Isso é equivalente a um `INNER JOIN` no SQL.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir une duas coleções usando o `Group Join` cláusula.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Join](../../../visual-basic/language-reference/queries/join-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
