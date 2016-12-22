---
title: "Cl&#225;usula Aggregate (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryAggregateIn"
  - "vb.QueryAggregate"
  - "vb.QueryAggregateInto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "cláusula Aggregate"
  - "instrução Aggregate"
  - "consultas [Visual Basic], Agregado"
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Aggregate (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Aplica uma ou mais funções agregadas a uma coleção.  
  
## Sintaxe  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`element`|Obrigatório.  Variável usada para iterar através dos elementos da coleção.|  
|`type`|Opcional.  O tipo de `element`.  Se nenhum tipo for especificado, o tipo de `element` é inferido de `collection`.|  
|`collection`|Obrigatório.  Refere\-se a coleção sobre a qual operar.|  
|`clause`|Opcional.  Uma ou mais cláusulas de consulta, como uma cláusula `Where`, para refinar o resultado da consulta para aplicar a cláusula ou cláusulas agregadas.|  
|`expressionList`|Obrigatório.  Uma ou mais expressões delimitadas por vírgulas que identifiquem uma função agregada para aplicar à coleção.  Você pode aplicar um alias para uma função agregada para especificar um nome de membro para o resultado da consulta.  Se nenhum alias for fornecido, o nome da função agregada é usado.  Para obter exemplos, consulte a seção sobre funções agregadas mais à frente neste tópico.|  
  
## Comentários  
 A cláusula `Aggregate` pode ser usada para incluir funções agregadas em suas consultas.  Funções agregadas executam verificações e cálculos sobre um conjunto de valores e retornam um único valor.  Você pode acessar o valor calculado usando um membro do tipo do resultado da consulta.  As funções agregadas padrão que você pode usar são as funções `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min` e `Sum`.  Essas funções são familiares para os desenvolvedores que estão familiarizados com agregados em SQL.  Elas são descritas na seção a seguir deste tópico.  
  
 O resultado de uma função agregada é incluído no resultado da consulta como um campo do tipo do resultado da consulta.  Você pode fornecer um alias para o resultado da função agregada para especificar o nome do membro do tipo do resultado da consulta que conterá o valor agregado.  Se nenhum alias for fornecido, o nome da função agregada é usado.  
  
 A cláusula `Aggregate` pode começar uma consulta, ou pode ser incluída como uma cláusula adicional em uma consulta.  Se a cláusula `Aggregate` começar uma consulta, o resultado é um valor único que é o resultado da função agregada especificada na cláusula `Into`.  Se mais de uma função agregada for especificada na cláusula `Into`, a consulta retorna um único tipo com uma propriedade separada para fazer referência ao resultado de cada função agregada na cláusula `Into`.  Se a cláusula `Aggregate` é incluída como uma cláusula adicional em uma consulta, o tipo retornado na coleção de consultas terá uma propriedade separada para referenciar o resultado de cada função agregada na cláusula `Into`.  
  
## Funções Agregadas  
 A lista a seguir descreve as funções agregadas padrão que podem ser usadas com a cláusula `Aggregate`.  
  
|||  
|-|-|  
|Função|Descrição|  
|`All`|Retorna `true` se todos os elementos na coleção satisfazem uma condição especificada; caso contrário, retorna `false`.  A seguir, há um exemplo:<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|Retorna `true` se qualquer elemento da coleção satisfazem uma condição especificada; caso contrário, retorna `false`.  A seguir, há um exemplo:<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|Calcula a média de todos os elementos da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção.  A seguir, há um exemplo:<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|Conta o número de elementos na coleção.  Você pode fornecer uma expressão `Boolean` opcional para contar somente o número de elementos da coleção que satisfazem a uma condição.  A seguir, há um exemplo:<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|Refere\-se aos resultados da consulta que são agrupados como resultado de uma cláusula `Group By` ou `Group Join`.  A função `Group` é válida somente na cláusula `Into` de uma cláusula `Group By` ou `Group Join`.  Para mais informações e um exemplo, consulte [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md) e [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md).|  
|`LongCount`|Conta o número de elementos na coleção.  Você pode fornecer uma expressão `Boolean` opcional para contar somente o número de elementos da coleção que satisfazem a uma condição.  Retorna o resultado como um `Long`.  Para obter um exemplo, consulte a função agregada `Count`.|  
|`Max`|Calcula o valor máximo da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção.  A seguir, há um exemplo:<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|Calcula o valor mínimo da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção.  A seguir, há um exemplo:<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|Calcula a soma de todos os elementos da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção.  A seguir, há um exemplo:<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## Exemplo  
 O exemplo de código a seguir mostra como usar a cláusula `Aggregate` para aplicar uma função agregada a um resultado de consulta.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## Criando funções agregadas definidas pelo usuário  
 Você pode incluir suas próprias funções agregadas personalizadas em uma expressão de consulta adicionando métodos de extensão ao tipo <xref:System.Collections.Generic.IEnumerable%601>.  O método personalizado pode então executar um cálculo ou operação na coleção enumerável que referenciou sua função agregada.  Para obter mais informações sobre estes métodos de extensão, consulte [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Por exemplo, o exemplo de código a seguir mostra uma função agregada personalizada que calcula o valor mediano de uma coleção de números.  Há duas sobrecargas do método de extensão `Median`.  A primeira sobrecarga aceita, como entrada, uma coleção do tipo `IEnumerable(Of Double)`.  Se a função agregada `Median` for chamada para um campo de consulta do tipo `Double`, esse método será chamado.  A segunda sobrecarga do método `Median` pode ser passada a qualquer tipo genérico.  A sobrecarga genérica do método `Median` leva um segundo parâmetro que faz referência a expressão lambda `Func(Of T, Double)` para projetar um valor para um tipo \(de uma coleção\) como o valor correspondente do tipo `Double`.  Ele então delega o cálculo do valor mediano para a outra sobrecarga do método `Median`.  Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 O exemplo de código a seguir mostra exemplos de consultas que chamam a função agregada `Median` em uma coleção do tipo `Integer` e uma coleção do tipo `Double`.  A consulta que chama a função agregada `Median` na coleção do tipo `Double` chama a sobrecarga do método `Median` que aceita, como entrada, uma coleção do tipo `Double`.  A consulta que chama a função agregada `Median` na coleção do tipo `Integer` chama a sobrecarga genérica do método `Median`.  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)