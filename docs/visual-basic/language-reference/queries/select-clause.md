---
title: Cláusula Select (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 55c1e79b9e8e26483c1b7374a755bf977129169b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604400"
---
# <a name="select-clause-visual-basic"></a>Cláusula Select (Visual Basic)
Define o resultado de uma consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Partes  
 `var1`  
 Opcional. Um alias que pode ser usado para referenciar os resultados da expressão de coluna.  
  
 `fieldName1`  
 Necessário. O nome do campo para retornar o resultado da consulta.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Select` cláusula para definir os resultados retornados de uma consulta. Isso permite que você definir os membros de um novo tipo anônimo que é criado por uma consulta, ou os membros de um tipo nomeado que é retornado por uma consulta de destino. O `Select` cláusula não é necessária para uma consulta. Se nenhum `Select` cláusula for especificada, a consulta retornará um tipo com base em todos os membros das variáveis de intervalo identificadas no escopo atual. Para obter mais informações, consulte [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Quando uma consulta cria um tipo nomeado, ela retornará um resultado do tipo <xref:System.Collections.Generic.IEnumerable%601> onde `T` é do tipo criado.  
  
 O `Select` cláusula pode referenciar qualquer variável no escopo atual. Isso inclui variáveis de intervalo identificadas no `From` cláusula (ou `From` cláusulas). Ele também inclui quaisquer variáveis novas criadas com um alias, a `Aggregate`, `Let`, `Group By`, ou `Group Join` cláusulas ou variáveis de anterior `Select` cláusula na expressão de consulta. O `Select` cláusula também pode incluir valores estáticos. Por exemplo, o exemplo de código a seguir mostra uma expressão de consulta no qual o `Select` cláusula define o resultado da consulta como um novo tipo anônimo com quatro membros: `ProductName`, `Price`, `Discount`, e `DiscountedPrice`. O `ProductName` e `Price` os valores de membro são tirados da variável de intervalo do produto que é definido no `From` cláusula. O `DiscountedPrice` valor do membro é calculada de `Let` cláusula. O `Discount` membro é um valor estático.  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 O `Select` cláusula apresenta um novo conjunto de variáveis de intervalo para cláusulas de consulta subsequentes, e variáveis intervalo anteriores não estão no escopo. A última `Select` cláusula em uma expressão de consulta determina o valor de retorno da consulta. Por exemplo, a consulta a seguir retorna a empresa ID de nome e a ordem de cada pedido do cliente para o qual o total exceder 500. A primeira `Select` cláusula identifica as variáveis de intervalo para o `Where` e a segunda cláusula `Select` cláusula. O segundo `Select` cláusula identifica os valores retornados pela consulta como um novo tipo anônimo.  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 Se o `Select` cláusula identifica um único item para retornar, a expressão de consulta retorna uma coleção do tipo de item único. Se o `Select` cláusula identifica vários itens para retornar, a expressão de consulta retorna uma coleção de um novo tipo anônimo, com base nos itens selecionados. Por exemplo, duas consultas a seguir retornam coleções de dois tipos diferentes com base no `Select` cláusula. A primeira consulta retorna uma coleção de nomes de empresa como cadeias de caracteres. A segunda consulta retorna uma coleção de `Customer` objetos preenchidos com os nomes de empresa e informações de endereço.  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## <a name="example"></a>Exemplo  
 A consulta a seguir expressão usa uma `From` cláusula para declarar uma variável de intervalo `cust` para o `customers` coleção. O `Select` cláusula seleciona o nome do cliente e o valor de ID e preenche o `CompanyName` e `CustomerID` colunas da nova variável de intervalo. O `For Each` instrução faz um loop sobre cada objeto retornado e exibe o `CompanyName` e `CustomerID` colunas para cada registro.  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
