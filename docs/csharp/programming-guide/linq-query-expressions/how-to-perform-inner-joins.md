---
title: "Como executar jun&#231;&#245;es internas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "junções internas [LINQ em C#]"
  - "junções [C#], internas"
  - "consultas [LINQ in C#], junções"
  - "expressões de consulta [LINQ em C#], junções"
ms.assetid: d9edb404-8314-413e-ae51-83bb86c7a4b5
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como executar jun&#231;&#245;es internas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em termos de banco de dados relacional, uma  *associação interna* produz um conjunto de resultados no qual cada elemento da coleção primeiro aparece uma vez para cada elemento correspondente na segunda coleção.  Se um elemento na primeira coleção não tiver nenhum elemento correspondente, ele não aparecerá no conjunto de resultados.  O <xref:System.Linq.Enumerable.Join%2A> método, que é chamado pelo `join` cláusula C\# implementa uma associação interna.  
  
 Este tópico mostra como executar quatro variações de uma associação interna:  
  
-   Uma associação interna simple que correlaciona os elementos de duas fontes de dados com base em uma chave simple.  
  
-   Uma associação interna que correlaciona os elementos de dados de duas origens com base em um  *composto*  chave.  Uma chave composta, o que é uma chave que consiste em mais de um valor, permite que você correlacione os elementos com base em mais de uma propriedade.  
  
-   A  *associação múltipla* em qual associação sucessiva operações são acrescentadas uns aos outros.  
  
-   Uma associação interna que é implementada usando uma associação de grupo.  
  
## Exemplo  
  
## Exemplo de associação de chave simples  
 O exemplo a seguir cria duas coleções que contêm objetos dos dois tipos definidos pelo usuário, `Person` e `Pet`.  A consulta usa a `join` cláusula em C\# para corresponder à `Person` objetos com `Pet` objetos cuja `Owner` é que `Person`.  O `select` cláusula C\# define qual serão a aparência de objetos resultantes.  Neste exemplo, os objetos resultantes são tipos anônimos que consistem em nome do proprietário e o nome do bicho de estimação.  
  
 [!CODE [CsLINQProgJoining#1](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#1)]  
  
 Observe que o `Person` de objeto cuja `LastName` é "Huff" não aparece no resultado definido porque não há nenhum `Pet` objeto que tem `Pet.Owner` igual a `Person`.  
  
## Exemplo  
  
## Exemplo de associação de chave composta  
 Em vez de correlacionar os elementos com base em apenas uma propriedade, você pode usar uma chave composta para comparar os elementos com base em várias propriedades.  Para fazer isso, especifique a função de seletor de chave de cada coleção para retornar um tipo anônimo que consiste nas propriedades que você deseja comparar.  Se você rotular as propriedades, eles devem ter o mesmo rótulo em um tipo anônimo do cada chave.  As propriedades também devem aparecer na mesma ordem.  
  
 O exemplo a seguir usa uma lista de `Employee` objetos e uma lista de `Student` objetos para determinar quais funcionários estão também os alunos.  Esses dois tipos de tem um `FirstName` e um `LastName` propriedade do tipo <xref:System.String>.  As funções que cria as chaves de associação a partir de elementos de cada lista retornam um tipo anônimo que consiste o `FirstName` e `LastName` propriedades de cada elemento.  A operação de ingresso compara essas chaves compostas de igualdade e retorna pares de objetos de cada lista onde coincidir com o nome e o sobrenome.  
  
 [!CODE [CsLINQProgJoining#2](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#2)]  
  
## Exemplo  
  
## Exemplo de associação de múltiplos  
 Qualquer número de operações de associação pode ser anexado a si para realizar uma associação múltipla.  Cada `join` cláusula C\# correlaciona uma fonte de dados especificada com os resultados da associação anterior.  
  
 O exemplo a seguir cria três coleções: uma lista de `Person` objetos, uma lista de `Cat` objetos e uma lista de `Dog` objetos.  
  
 O primeiro `join` cláusula C\# corresponde a pessoas e gatos com base em um `Person` correspondentes do objeto `Cat.Owner`.  Ele retorna uma seqüência de tipos anônimos que contêm o `Person` objeto e `Cat.Name`.  
  
 A segunda `join` cláusula C\# correlaciona os tipos anônimos retornados pela primeira associação com `Dog` objetos na lista fornecida de cães, com base em uma chave composta que consiste o `Owner` propriedade do tipo `Person`e a primeira letra do nome do animal.  Ele retorna uma seqüência de tipos anônimos que contêm o `Cat.Name` e `Dog.Name` propriedades de cada par correspondente.  Como esta é uma associação interna, apenas os objetos da primeira fonte de dados que têm uma correspondência na segunda fonte de dados são retornados.  
  
 [!CODE [CsLINQProgJoining#3](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#3)]  
  
## Exemplo  
  
## Associação interna usando agrupados exemplo ingressar  
 O exemplo a seguir mostra como implementar uma associação interna por meio de uma associação de grupo.  
  
 Na `query1`, a lista de `Person` objetos é o grupo associado à lista de `Pet` objetos com base na `Person` correspondentes a `Pet.Owner` propriedade.  A associação de grupo cria uma coleção dos grupos de intermediários, onde cada grupo consiste em um `Person` objeto e uma seqüência de correspondência `Pet` objetos.  
  
 Adicionando um segundo `from` cláusula à consulta, essa seqüência de seqüências é combinada \(ou achatada\) em uma seqüência mais longa.  O tipo dos elementos da seqüência final é especificado pelo `select` cláusula.  Neste exemplo, se o tipo é um tipo anônimo que consiste o `Person.FirstName` e `Pet.Name` propriedades para cada par correspondente.  
  
 O resultado de `query1` é equivalente ao conjunto de resultados que teria sido obtido usando o `join` cláusula sem a `into` cláusula para realizar uma junção interna.  O `query2` variável demonstra essa consulta equivalente.  
  
 [!CODE [CsLINQProgJoining#4](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#4)]  
  
## Compilando o código  
  
-   Crie um novo projeto de aplicativo de Console em [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  
  
-   Adicione uma referência a System.Core.dll se já não é referenciado.  
  
-   Incluir o <xref:System.Linq> espaço para nome.  
  
-   Copie e cole o código do exemplo no arquivo Program. cs, abaixo do `Main` método.  Adicionar uma linha de código para o `Main` método para chamar o método que você colou no.  
  
-   Execute o programa.  
  
## Consulte também  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Operações join](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [Como executar junções agrupadas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [Como executar junções externas esquerdas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [How to: Join Two Collections](../Topic/How%20to:%20Join%20Two%20Collections%20\(C%23\)%20\(LINQ%20to%20XML\).md)   
 [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)