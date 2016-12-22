---
title: "Cl&#225;usula join (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "join"
  - "join_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "cláusula join [C#]"
  - "palavra-chave join [C#]"
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cl&#225;usula join (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `join` cláusula é útil para associar elementos de seqüências de origem diferentes que não têm nenhum relacionamento direto no modelo de objeto.  O único requisito é que os elementos em cada fonte compartilham algum valor que pode ser comparado a igualdade.  Por exemplo, um distribuidor de alimentos pode ter uma lista de fornecedores de um determinado produto e uma lista de compradores.  A `join` cláusula pode ser usada, por exemplo, para criar uma lista de fornecedores e compradores desse produto que estejam todos na mesma região de especificado.  
  
 A `join` cláusula utiliza duas seqüências de origem como entrada.  Os elementos em cada seqüência devem ser ou conter uma propriedade que pode ser comparada a uma propriedade correspondente na seqüência de.  O `join` cláusula compara chaves especificadas de igualdade, usando a sintaxe especial `equals` palavra\-chave.  Todas as associações realizadas pelo `join` cláusula são equijoins.  A forma da saída de um `join` cláusula varia de acordo com o tipo específico de associação que você está executando.  Estes são os três tipos mais comuns de associação:  
  
-   Associação interna  
  
-   Associação de grupo  
  
-   Associação externa esquerda  
  
## Associação interna  
 O exemplo a seguir mostra um simple equijoin interna.  Esta consulta produz uma simples seqüência de "nome do produto \/ categoria" pares.  A mesma seqüência de categoria será exibido em vários elementos.  Se um elemento de `categories` não tem correspondente `products`, essa categoria não aparecerão nos resultados.  
  
 [!CODE [cscsrefQueryKeywords#24](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#24)]  
  
 Para obter mais informações, consulte [Como executar junções internas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md).  
  
## Group Join  
 A `join` cláusula com um `into` expressão denomina\-se uma associação de grupo.  
  
 [!CODE [cscsrefQueryKeywords#25](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#25)]  
  
 Uma associação de grupo produz uma seqüência de resultados hierárquicos, que associa elementos na seqüência de origem à esquerda com um ou mais elementos correspondentes a seqüência de origem do lado direito.  Uma associação de grupo não possui nenhum equivalente em termos de relacionais; ele é essencialmente uma seqüência de matrizes de objeto.  
  
 Se nenhum elemento da seqüência de origem direita encontram\-se para corresponder a um elemento na fonte à esquerda, a `join` cláusula produzirá uma matriz vazia para aquele item.  Portanto, a associação de grupo ainda basicamente é uma equijoin de interna, exceto que a seqüência de resultado é organizada em grupos.  
  
 Se você acabou de selecionar os resultados de uma associação de grupo, você pode acessar os itens, mas você não pode identificar a chave que eles coincidem em.  Portanto, é geralmente mais úteis selecionar os resultados da associação de grupo em um novo tipo também tem o nome da chave, conforme mostrado no exemplo anterior.  
  
 Além disso, você pode usar claro, o resultado de uma associação de grupo como gerador de outra subconsulta:  
  
 [!CODE [cscsrefQueryKeywords#26](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#26)]  
  
 Para obter mais informações, consulte [Como executar junções agrupadas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md).  
  
## Junção externa esquerda  
 Em uma junção externa esquerda, todos os elementos na seqüência de origem à esquerda são retornados, mesmo se nenhum elemento correspondente na seqüência correta.  Para executar uma associação externa esquerda na [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)], use o `DefaultIfEmpty` método em combinação com uma associação de grupo para especificar um elemento do lado direito padrão para produzir se um elemento do lado esquerdo não tem nenhuma correspondência.  Você pode usar `null` como o valor padrão para qualquer referência tipo, ou você pode especificar um tipo definido pelo usuário padrão.  No exemplo a seguir, um tipo definido pelo usuário padrão é mostrado:  
  
 [!CODE [cscsrefQueryKeywords#27](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#27)]  
  
 Para obter mais informações, consulte [Como executar junções externas esquerdas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md).  
  
## O operador equals  
 A `join` cláusula realiza uma equijoin.  Em outras palavras, você pode apenas base correspondentes em termos de igualdade de duas chaves.  Não há suporte para outros tipos de comparações, como "maior que" ou "não iguais".  Para tornar claro que todas as associações são equijoins, o `join` cláusula usa a `equals` palavra\-chave em vez da `==` operador.  O `equals` palavra\-chave só pode ser usado em um `join` cláusula e ele difere do `==` operador em um aspecto importante.  Com `equals`, a tecla esquerda consome a seqüência de origem externa e a tecla direita consome a fonte interna.  A fonte externa é somente no escopo no lado esquerdo da `equals` e a seqüência de origem interna é somente no escopo no lado direito.  
  
## Não Equijoins  
 Você pode executar o não\-equijoins, troca de associações e outras operações de associação personalizado, uso de várias `from` cláusulas para introduzir novas seqüências de forma independente em uma consulta.  Para obter mais informações, consulte [Como executar operações de junção personalizadas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## Ingressa no vs de coleções do objeto.tabelas relacionais  
 Em um [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] expressão de consulta, as operações são realizadas em coleções de objeto de associação.  Coleções de objetos não podem ser "associadas" exatamente da mesma forma como duas tabelas relacionais.  Na [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)], explícita `join` cláusulas só são necessários quando duas seqüências de origem não estão ligadas por qualquer relação.  Ao trabalhar com [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)], tabelas de chaves externas são representadas no modelo de objeto como propriedades da tabela primária.  Por exemplo, no banco de dados Northwind, a tabela Customer tem uma relação de chave externa com a tabela Pedidos.  Quando você mapeia as tabelas ao modelo de objeto, a classe Customer tem uma propriedade de pedidos que contém a coleção de ordens associadas a esse cliente.  Na verdade, a associação já foi feita para você.  
  
 Para obter mais informações sobre como fazer consultas em tabelas relacionadas no contexto de [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)], consulte [How to: Map Database Relationships](../Topic/How%20to:%20Map%20Database%20Relationships.md).  
  
## Chaves compostas  
 Você pode testar a igualdade de vários valores usando uma chave composta.  Para obter mais informações, consulte [Como unir usando chaves compostas](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md).  As chaves compostas também podem ser usadas em um `group` cláusula.  
  
## Exemplo  
 O exemplo a seguir compara o resultado de uma associação interna, uma associação de grupo e uma junção externa esquerda mesmo fontes de dados usando as mesmas chaves correspondentes.  Algum código extra é adicionado a esses exemplos para esclarecer os resultados na tela do console.  
  
 [!CODE [cscsrefQueryKeywords#23](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#23)]  
  
## Comentários  
 A `join` cláusula que não é seguida por `into` é traduzido em um <xref:System.Linq.Enumerable.Join%2A> chamada de método.  A `join` cláusula que é seguida por `into` é traduzido como um <xref:System.Linq.Enumerable.GroupJoin%2A> chamada de método.  
  
## Consulte também  
 [Palavras\-chave de consulta \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Operações join](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md)   
 [Como executar junções externas esquerdas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [Como executar junções internas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [Como executar junções agrupadas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [Como ordenar os resultados de uma cláusula join](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)   
 [Como unir usando chaves compostas](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)   
 [Como instalar bancos de dados de exemplo](../Topic/How%20to:%20Install%20Sample%20Databases.md)