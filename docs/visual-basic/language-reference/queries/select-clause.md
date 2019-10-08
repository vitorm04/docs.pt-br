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
ms.openlocfilehash: 087472c51d203be083fea0d39ade6f12066cfcb4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004743"
---
# <a name="select-clause-visual-basic"></a>Cláusula Select (Visual Basic)
Define o resultado de uma consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Partes  
 `var1`  
 Opcional. Um alias que pode ser usado para referenciar os resultados da expressão de coluna.  
  
 `fieldName1`  
 Necessário. O nome do campo a ser retornado no resultado da consulta.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a cláusula `Select` para definir os resultados a serem retornados de uma consulta. Isso permite que você defina os membros de um novo tipo anônimo que é criado por uma consulta ou para direcionar os membros de um tipo nomeado que é retornado por uma consulta. A cláusula `Select` não é necessária para uma consulta. Se nenhuma cláusula `Select` for especificada, a consulta retornará um tipo com base em todos os membros das variáveis de intervalo identificadas para o escopo atual. Para obter mais informações, consulte [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Quando uma consulta cria um tipo nomeado, ela retorna um resultado do tipo <xref:System.Collections.Generic.IEnumerable%601> em que `T` é o tipo criado.  
  
 A cláusula `Select` pode fazer referência a qualquer variável no escopo atual. Isso inclui variáveis de intervalo identificadas na cláusula `From` (ou cláusulas `From`). Ele também inclui todas as novas variáveis criadas com um alias pelas cláusulas `Aggregate`, `Let`, `Group By` ou `Group Join`, ou variáveis de uma cláusula `Select` anterior na expressão de consulta. A cláusula `Select` também pode incluir valores estáticos. Por exemplo, o exemplo de código a seguir mostra uma expressão de consulta na qual a cláusula `Select` define o resultado da consulta como um novo tipo anônimo com quatro membros: `ProductName`, `Price`, `Discount` e `DiscountedPrice`. Os valores de membro `ProductName` e `Price` são obtidos da variável de intervalo de produtos que é definida na cláusula `From`. O valor do membro `DiscountedPrice` é calculado na cláusula `Let`. O membro `Discount` é um valor estático.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 A cláusula `Select` apresenta um novo conjunto de variáveis de intervalo para cláusulas de consulta subsequentes, e as variáveis de intervalo anteriores não estão mais no escopo. A última cláusula `Select` em uma expressão de consulta determina o valor de retorno da consulta. Por exemplo, a consulta a seguir retorna o nome da empresa e a ID do pedido para cada pedido de cliente para o qual o total excede 500. A primeira cláusula `Select` identifica as variáveis de intervalo para a cláusula `Where` e a segunda cláusula `Select`. A segunda cláusula `Select` identifica os valores retornados pela consulta como um novo tipo anônimo.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Se a cláusula `Select` identificar um único item a ser retornado, a expressão de consulta retornará uma coleção do tipo desse item único. Se a cláusula `Select` identificar vários itens a serem retornados, a expressão de consulta retornará uma coleção de um novo tipo anônimo, com base nos itens selecionados. Por exemplo, as duas consultas a seguir retornam coleções de dois tipos diferentes com base na cláusula `Select`. A primeira consulta retorna uma coleção de nomes de empresa como cadeias de caracteres. A segunda consulta retorna uma coleção de objetos `Customer` populados com os nomes de empresa e informações de endereço.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir usa uma cláusula `From` para declarar uma variável de intervalo `cust` para a coleção `customers`. A cláusula `Select` seleciona o nome do cliente e o valor da ID e popula as colunas `CompanyName` e `CustomerID` da nova variável de intervalo. A instrução `For Each` faz loop em cada objeto retornado e exibe as colunas `CompanyName` e `CustomerID` para cada registro.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
