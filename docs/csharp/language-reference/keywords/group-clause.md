---
title: "Cl&#225;usula group (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "group"
  - "group_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "cláusula group [C#]"
  - "palavra-chave group [C#]"
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cl&#225;usula group (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `group` cláusula retorna uma seqüência de <xref:System.Linq.IGrouping%602> objetos que contêm zero ou mais itens que coincidem com o valor da chave para o grupo.  Por exemplo, você pode agrupar uma seqüência de cadeias de caracteres de acordo com a primeira letra de cada seqüência de caracteres.  Nesse caso, a primeira letra é a chave e tem um tipo de  [char](../../../csharp/language-reference/keywords/char.md)e é armazenado na `Key` propriedade de cada <xref:System.Linq.IGrouping%602> objeto.  O compilador infere o tipo da chave.  
  
 Você pode finalizar uma expressão de consulta com um `group` cláusula, conforme mostrado no exemplo a seguir:  
  
 [!CODE [cscsrefQueryKeywords#10](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#10)]  
  
 Se você quiser executar operações de consulta adicionais em cada grupo, você pode especificar um identificador temporário usando o  [em](../../../csharp/language-reference/keywords/into.md) palavra\-chave contextual.  Quando você usa `into`, você deve continuar com a consulta e eventualmente encerrá\-lo com um um `select` instrução ou outro `group` cláusula, conforme mostrado no trecho a seguir:  
  
 [!CODE [cscsrefQueryKeywords#11](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#11)]  
  
 Mais completas de exemplos do uso de `group` com e sem `into` são fornecidos na seção exemplo deste tópico.  
  
## Enumerando os resultados de uma consulta de grupo  
 Porque o <xref:System.Linq.IGrouping%602> objetos produzidos por um `group` consulta são essencialmente uma lista de listas, você deve usar um aninhadas  [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loop para acessar os itens em cada grupo.  O loop externo itere sobre as chaves de grupo e o loop interno é iterado em cada item do grupo propriamente dito.  Um grupo pode ter uma chave, mas nenhum elemento.  A seguir está o `foreach` loop que executa a consulta nos exemplos de código anterior:  
  
 [!CODE [cscsrefQueryKeywords#12](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#12)]  
  
## Tipos de chaves  
 Chaves de grupo podem ser qualquer tipo, como uma seqüência de caracteres, um tipo numérico interno ou definido um usuário chamado tipo ou tipo anônimo.  
  
### Agrupando por string  
 Os exemplos de código anterior usados um `char`.  Uma string key poderia facilmente foram especificada em vez disso, por exemplo, o sobrenome completo:  
  
 [!CODE [cscsrefQueryKeywords#13](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#13)]  
  
### Agrupando por bool  
 O exemplo a seguir mostra o uso de um valor booleano para uma chave dividir os resultados em dois grupos.  Observe que o valor produzido por uma subexpressão na `group` cláusula.  
  
 [!CODE [cscsrefQueryKeywords#14](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#14)]  
  
### Agrupando por intervalo numérico  
 O próximo exemplo utiliza uma expressão para criar chaves de grupo numérico que representam uma faixa percentil.  Observe o uso de  [permitem que](../../../csharp/language-reference/keywords/let-clause.md) como um local conveniente para armazenar um método de chamada como resultado, para que você não precisará chamar o método duas vezes na `group` cláusula.  Observe também na `group` cláusula que para evitar uma exceção de "divisão por zero", o código verifica para certificar\-se de que o aluno não possui uma média de zero.  Para obter mais informações sobre como usar com segurança os métodos em expressões de consulta, consulte [Como manipular exceções em expressões de consulta](../Topic/How%20to:%20Handle%20Exceptions%20in%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md).  
  
 [!CODE [cscsrefQueryKeywords#15](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#15)]  
  
### Agrupando pelas chaves compostas  
 Quando você deseja agrupar elementos de acordo com a mais de uma chave, use uma chave composta.  Você pode criar uma chave composta por meio de um tipo anônimo ou um tipo nomeado para conter um elemento\-chave.  O exemplo a seguir, suponha que uma classe `Person` ter sido declarado com membros chamados `surname` e `city`.  O `group` cláusula faz com que um grupo separado seja criado para cada conjunto de pessoas com o mesmo sobrenome e da mesma cidade.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Se você deve passar a variável de consulta para outro método, use um tipo nomeado.  Crie uma classe especial usando propriedades de auto\-implementado para as chaves e, em seguida, substituir o <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A> métodos.  Você também pode usar uma struct, caso em que você não estritamente precisará substituir esses métodos.  Para obter mais informações, consulte [Como implementar uma classe leve com propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) e [Como consultar arquivos duplicados em uma árvore de diretório \(LINQ\)](../Topic/How%20to:%20Query%20for%20Duplicate%20Files%20in%20a%20Directory%20Tree%20\(LINQ\).md).  O último tópico tem um exemplo de código que demonstra como usar uma chave composta com um tipo nomeado.  
  
## Exemplo  
 O exemplo a seguir mostra o padrão para ordenação de dados de origem em grupos quando nenhuma lógica de consulta adicional é aplicada aos grupos.  Isso é chamado um agrupamento sem uma continuação.  Os elementos em uma matriz de seqüências de caracteres são agrupados de acordo com sua primeira letra.  O resultado da consulta é um <xref:System.Linq.IGrouping%602> tipo que contém um relatório público `Key` propriedade do tipo `char` e um <xref:System.Collections.Generic.IEnumerable%601> coleção que contém a cada item no agrupamento.  
  
 O resultado de uma `group` cláusula é uma seqüência de seqüências.  Portanto, para acessar os elementos individuais dentro de cada grupo retornado, use um aninhadas `foreach` loop dentro do loop que itera as chaves de grupo, conforme mostrado no exemplo a seguir.  
  
 [!CODE [cscsrefQueryKeywords#16](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#16)]  
  
## Exemplo  
 Este exemplo mostra como executar lógica adicional nos grupos, após você ter criado\-los, usando um  *continuação* com `into`.  Para obter mais informações, consulte [into](../../../csharp/language-reference/keywords/into.md).  O exemplo a seguir consulta cada grupo para selecionar somente aqueles cujo valor da chave é uma vogal.  
  
 [!CODE [cscsrefQueryKeywords#17](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#17)]  
  
## Comentários  
 Em tempo de compilação, `group` cláusulas são traduzidas em chamadas para o <xref:System.Linq.Enumerable.GroupBy%2A> método.  
  
## Consulte também  
 <xref:System.Linq.IGrouping%602>   
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.Enumerable.ThenBy%2A>   
 <xref:System.Linq.Enumerable.ThenByDescending%2A>   
 [Palavras\-chave de consulta \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Como criar um grupo aninhado](../Topic/How%20to:%20Create%20a%20Nested%20Group%20\(C%23%20Programming%20Guide\).md)   
 [Como agrupar resultados de consultas](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)   
 [Como executar uma subconsulta em uma operação de agrupamento](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)