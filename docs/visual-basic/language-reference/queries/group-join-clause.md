---
title: "Cl&#225;usula Join Group (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryGroupJoinIn"
  - "vb.QueryGroupJoinOn"
  - "vb.QueryGroupJoin"
  - "vb.QueryGroupJoinInto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "cláusula Group Join"
  - "instrução Group Join"
  - "consultas [Visual Basic], Group Join"
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Join Group (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Combina duas coleções numa única coleção hierarquizada.  A operação de associação é baseada em chaves correspondentes.  
  
## Sintaxe  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`element`|Obrigatório.  A variável de controle para a coleção sendo juntada.|  
|`type`|Opcional.  O tipo de `element`.  Se nenhum `type` for especificado, o tipo de `element` será inferido de `collection`.|  
|`collection`|Obrigatório.  A coleção a combinar com a coleção identificada no lado esquerdo do operador `Group Join`.  A cláusula `Group Join` pode ser aninhada em uma cláusula `Join` ou outra cláusula `Group Join`.|  
|`key1` `Equals` `key2`|Obrigatório.  Identifica chaves para as coleções que estão sendo combinadas.  Você deve usar o operador `Equals` para comparar chaves das coleções que estão sendo combinadas.  Você pode combinar condições de associação, usando o operador `And` para identificar várias chaves.  O parâmetro `key1` deve ser da coleção no lado esquerdo do operador `Join`.  O parâmetro `key2` deve ser da coleção no lado direito do operador `Join`.<br /><br /> As chavesa usadas na condição de adição podem ser expressões que incluem mais de um item da coleção.  Entretanto, cada expressão chave pode conter somente itens da sua respectiva coleção|  
|`expressionList`|Obrigatório.  Uma ou mais expressões que identificam como os grupos de elementos da coleção são agregados.  Para identificar um nome de membro para os resultados agrupados, use a  palavra\-chave `Group` \(`<alias> = Group`\).  Você também pode incluir funções agregadas para aplicar ao grupo.|  
  
## Comentários  
 A cláusula `Group Join` combina duas coleções baseadas nos valores das chaves que combinam das coleções sendo combinadas.  A coleção resultante pode conter um membro que referencia uma coleção de elementos da segunda coleção  que corresponde ao valor de chave da coleção primeiro.  Você também pode especificar funções agregadas para aplicar aos elementos agrupados da segunda coleção.  Para obter mais informações sobre funções agregadas, consulte [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Considere, por exemplo, uma coleção de gerentes e uma de funcionários.  Elementos de ambos os conjuntos possuem uma propriedade ManagerID que identifica os funcionários que reportam a um gerente específico.  Os resultados de uma operação de assovciação conterá um resultado para cada gerente e funcionário com um valor coincidente ManagerID.  Os resultados de uma operação `Group Join` contém a lista completa dos gerentes.  Cada gerente no resultado teria como membro membro a lista de funcionários que correpondem ao próprio.  
  
 O conjunto resultante de uma operação `Group Join` pode conter qualquer combinação de valores de coleção identificados na cláusula `From` e as expressões identificadas na cláusula `Into` da cláusula `Group Join`.  Para obter mais informações sobre expressões válidas para a cláusula `Into`, consulte [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Uma operação `Group Join` retornará todos os resultados da coleção identificada no lado esquerdo do operador `Group Join`.  Isso é verdadeiro mesmo se não houver nenhuma correspondência na coleção sendo associado.  É como um `LEFT OUTER JOIN` no SQL.  
  
 Você pode usar a cláusula `Join` para combinar coleções em uma única coleção hierárquica.  Isso é equivalente a um `INNER JOIN` no SQL.  
  
## Exemplo  
 O exemplo de código a seguir une duas coleções usando a cláusula `Group Join`.  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Join](../../../visual-basic/language-reference/queries/join-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)