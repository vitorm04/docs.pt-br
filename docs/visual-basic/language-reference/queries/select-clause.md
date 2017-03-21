---
title: "Cláusula Select (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySelect
dev_langs:
- VB
helpviewer_keywords:
- Select statement
- Select clause
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: 21
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
ms.openlocfilehash: ea0243e493831afd58d5cded047a7e6f7b54d8c1
ms.lasthandoff: 03/13/2017

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
 Você pode usar o `Select` cláusula para definir os resultados retornados de uma consulta. Isso permite que você definir os membros de um novo tipo anônimo que é criado por uma consulta, ou direcionar os membros de um tipo nomeado que é retornado por uma consulta. O `Select` cláusula não é necessária para uma consulta. Se nenhum `Select` cláusula for especificada, a consulta retornará um tipo com base em todos os membros das variáveis de intervalo identificadas no escopo atual. Para obter mais informações, consulte [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Quando uma consulta cria um tipo nomeado, ela retornará um resultado de tipo <xref:System.Collections.Generic.IEnumerable%601>onde `T` é do tipo criado.</xref:System.Collections.Generic.IEnumerable%601>  
  
 O `Select` cláusula pode referenciar qualquer variável no escopo atual. Isso inclui variáveis de intervalo identificadas no `From` cláusula (ou `From` cláusulas). Ele também inclui quaisquer variáveis novas criadas com um alias, o `Aggregate`, `Let`, `Group By`, ou `Group Join` cláusulas ou variáveis de anterior `Select` cláusula na expressão de consulta. O `Select` cláusula também pode incluir valores estáticos. Por exemplo, o exemplo de código a seguir mostra uma expressão de consulta no qual o `Select` cláusula define o resultado da consulta como um novo tipo anônimo com quatro membros: `ProductName`, `Price`, `Discount`, e `DiscountedPrice`. O `ProductName` e `Price` os valores de membro são tirados da variável de intervalo do produto que é definido na `From` cláusula. O `DiscountedPrice` valor do membro é calculado no `Let` cláusula. O `Discount` membro é um valor estático.  
  
 [!code-vb[VbSimpleQuerySamples&#27;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 O `Select` cláusula introduz um novo conjunto de variáveis de intervalo para cláusulas de consulta subsequentes, e variáveis intervalo anteriores não estão mais no escopo. A última `Select` cláusula em uma expressão de consulta determina o valor de retorno da consulta. Por exemplo, a consulta a seguir retorna a empresa nome e a ordem de ID para cada pedido de clientes para o qual o total excede 500. A primeira `Select` cláusula identifica as variáveis de intervalo para o `Where` e a segunda cláusula `Select` cláusula. O segundo `Select` cláusula identifica os valores retornados pela consulta como um novo tipo anônimo.  
  
 [!code-vb[VbSimpleQuerySamples&#28;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 Se o `Select` cláusula identifica um único item para retornar, a expressão de consulta retorna uma coleção do tipo daquele item único. Se o `Select` cláusula identifica vários itens para retornar, a expressão de consulta retorna uma coleção de um novo tipo anônimo, com base nos itens selecionados. Por exemplo, as duas consultas a seguir retornam coleções de dois tipos diferentes com base no `Select` cláusula. A primeira consulta retorna uma coleção de nomes de empresa como cadeias de caracteres. A segunda consulta retorna uma coleção de `Customer` objetos preenchidos com os nomes de empresa e informações de endereço.  
  
 [!code-vb[29 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta expressão utiliza um `From` cláusula para declarar uma variável de intervalo `cust` para o `customers` coleção. O `Select` cláusula seleciona o nome do cliente e o valor de ID e preenche o `CompanyName` e `CustomerID` colunas da nova variável de intervalo. O `For Each` instrução faz um loop sobre cada objeto retornado e exibe o `CompanyName` e `CustomerID` colunas para cada registro.  
  
 [!code-vb[30 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Onde cláusula](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
