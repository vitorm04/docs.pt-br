---
title: "Cl&#225;usula Select (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.QuerySelect"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "consultas [Visual Basic], Selecionar"
  - "cláusula Select"
  - "instrução Select"
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Select (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Define o resultado de uma consulta.  
  
## Sintaxe  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## Partes  
 `var1`  
 Opcional.  Um alias que pode ser usado para referenciar os resultados da expressão de coluna.  
  
 `fieldName1`  
 Obrigatório.  O nome do campo para retornar o resultado da consulta.  
  
## Comentários  
 Você pode usar a cláusula `Select` para definir os resultados retornados de uma consulta.  Isso permite definir os membros de um novo tipo anônimo que é criado por uma consulta, ou direcionar os membros de um tipo nomeado que é retornado por uma consulta.  A cláusula `Select` não é necessária para uma consulta.  Se uma cláusula `Select` for especificada, a consulta retornará um tipo com base em todos os membros das variáveis de intervalo identificadas no escopo atual.  Para obter mais informações, consulte [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  Quando uma consulta cria um tipo nomeado, ela retornará resultado do tipo <xref:System.Collections.Generic.IEnumerable%601> onde `T` é do tipo criado.  
  
 A cláusula `Select` pode referenciar qualquer variável no escopo atual.  Isso inclui variáveis de intervalo identificadas na cláusula `From` \(ou cláusulas `From`\).  Também inclui quaisquer variáveis novas criadas com um alias por cláusulas`Aggregate`, `Let`,`Group By`,ou `Group Join` , ou variáveis de uma cláusula `Select` anterior na expressão de consulta.  A cláusula `Select` também pode incluir valores estáticos.  Por exemplo, o exemplo de código a seguir mostra uma expressão de consulta na qual a cláusula `Select` define o resultado da consulta como um novo tipo anônimo com quatro integrantes: `ProductName`,`Price`,`Discount` e `DiscountedPrice`.  O `ProductName` e os valores membro `Price` são tirados da variável de intervalo do produto que está definida na cláusula `From`.  O valor do membro`DiscountedPrice` é calculado na cláusula `Let`.  O membro `Discount` é um valor estático.  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 A cláusula `Select` apresenta um novo conjunto de variáveis de Intervalo para cláusulas de consulta subsequentes, e variáveis intervalo anteriores não estão mais no escopo.  A última cláusula `Select` em uma expressão de consulta determina o valor de retorno da consulta.  Por exemplo, a seguinte consulta retorna a empresa nome e a ordem de ID para cada pedido do cliente para o qual o total exceder 500.  O primeiro `Select` cláusula identifica as variáveis de intervalo para o `Where` e a segunda cláusula `Select` cláusula.  A segunda cláusula `Select` identifica os valores retornados pela consulta como um novo tipo anônimo.  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 Se a cláusula `Select` identifica um único item para retornar, a expressão de consulta retorna uma coleção do tipo daquele item único.  Se a cláusula `Select` identifica vários itens para retornar, a expressão de consulta retorna uma coleção de um novo tipo anônimo, com base nos itens selecionados.  Por exemplo, as duas consultas a seguir retornam coleções de dois tipos diferentes com base na cláusula `Select`.  A primeira consulta retorna uma coleção de nomes de empresa como sequências de caracteres.  A segunda consulta retorna uma coleção de objetos `Customer` preenchida com os nomes de empresa e informações de endereço.  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## Exemplo  
 A expressão de consulta a seguir usa uma cláusula `From` para declarar uma variável de intervalod `cust` para a coleção `customers`.  A cláusula `Select` seleciona o nome do cliente e valor de identificação e preenche as colunas `CompanyName` e `CustomerID` da nova variável de intervalo.  A instrução `For Each` circula por cada objeto retornado e exibe as colunas `CompanyName` e `CustomerID` para cada registro.  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)