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
ms.openlocfilehash: 184077f2689eb64e4373d407913eefcc03b795c2
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005727"
---
# <a name="group-join-clause-visual-basic"></a>Cláusula Join Group (Visual Basic)
Combina duas coleções em uma única coleção hierárquica. A operação de junção é baseada em chaves correspondentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`element`|Necessário. A variável de controle para a coleção que está sendo unida.|  
|`type`|Opcional. O tipo de `element`. Se nenhum `type` for especificado, o tipo de `element` será inferido de `collection`.|  
|`collection`|Necessário. A coleção a ser combinada com a coleção que está no lado esquerdo do operador `Group Join`. Uma cláusula `Group Join` pode ser aninhada em uma cláusula `Join` ou em outra cláusula `Group Join`.|  
|`key1` `Equals` `key2`|Necessário. Identifica as chaves para as coleções que estão sendo Unidas. Você deve usar o operador `Equals` para comparar as chaves das coleções que estão sendo Unidas. Você pode combinar condições de junção usando o operador `And` para identificar várias chaves. O parâmetro `key1` deve ser da coleção no lado esquerdo do operador `Join`. O parâmetro `key2` deve ser da coleção no lado direito do operador `Join`.<br /><br /> As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção. No entanto, cada expressão de chave pode conter apenas itens de sua respectiva coleção.|  
|`expressionList`|Necessário. Uma ou mais expressões que identificam como os grupos de elementos da coleção são agregados. Para identificar um nome de membro para os resultados agrupados, use a palavra-chave `Group` (`<alias> = Group`). Você também pode incluir funções de agregação para aplicar ao grupo.|  
  
## <a name="remarks"></a>Comentários  
 A cláusula `Group Join` combina duas coleções com base nos valores de chave correspondentes das coleções que estão sendo Unidas. A coleção resultante pode conter um membro que faz referência a uma coleção de elementos da segunda coleção que corresponde ao valor de chave da primeira coleção. Você também pode especificar funções de agregação para aplicar aos elementos agrupados da segunda coleção. Para obter informações sobre funções de agregação, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Considere, por exemplo, uma coleção de gerentes e uma coleção de funcionários. Os elementos de ambas as coleções têm uma propriedade ManagerID que identifica os funcionários que se reportam a um gerente específico. Os resultados de uma operação de junção contêm um resultado para cada gerente e funcionário com um valor de ManagerID correspondente. Os resultados de uma operação `Group Join` conteriam a lista completa de gerentes. Cada resultado do gerente teria um membro que referenciou a lista de funcionários que eram uma correspondência para o gerente específico.  
  
 A coleção resultante de uma operação `Group Join` pode conter qualquer combinação de valores da coleção identificada na cláusula `From` e as expressões identificadas na cláusula `Into` da cláusula `Group Join`. Para obter mais informações sobre expressões válidas para a cláusula `Into`, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Uma operação `Group Join` retornará todos os resultados da coleção identificada no lado esquerdo do operador `Group Join`. Isso é verdadeiro mesmo se não houver nenhuma correspondência na coleção que está sendo unida. Isso é como um `LEFT OUTER JOIN` no SQL.  
  
 Você pode usar a cláusula `Join` para combinar coleções em uma única coleção. Isso é equivalente a um `INNER JOIN` no SQL.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir une duas coleções usando a cláusula `Group Join`.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Join](../../../visual-basic/language-reference/queries/join-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
