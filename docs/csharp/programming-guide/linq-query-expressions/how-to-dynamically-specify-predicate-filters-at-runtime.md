---
title: "Como especificar filtros predicados dinamicamente em tempo de execu&#231;&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "consultas dinâmicas [LINQ em C#]"
  - "filtros de predicado [C#]"
  - "predicados [C#]"
  - "consultas [LINQ in C#], filtros de predicado"
  - "expressões de consulta [LINQ em C#], filtros de predicado"
ms.assetid: 52f2dc7a-8353-4c6e-98d3-eec99a907a5f
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como especificar filtros predicados dinamicamente em tempo de execu&#231;&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em alguns casos você não souber até o runtime predicados quantas você deve aplicar a elementos de origem na `where` cláusula.  Uma forma de especificar dinamicamente os vários filtros de predicado é usar o <xref:System.Linq.Enumerable.Contains%2A> método, conforme mostrado no exemplo a seguir.  O exemplo é construído de duas maneiras.  Em primeiro lugar, o projeto é executado pela filtragem nos valores que são fornecidos no programa.  Em seguida, o projeto é executado novamente usando a entrada fornecida em tempo de execução.  
  
### Para filtrar usando o método Contains  
  
1.  Abra um novo aplicativo de console em Visual Studio.  Name it `PredicateFilters`.  
  
2.  Cópia do `StudentClass` de classe de [Como consultar uma coleção de objetos](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) e cole\-o no espaço para nome `PredicateFilters` sob a classe `Program`.  `StudentClass`Fornece uma lista de `Student` objetos.  
  
3.  Comente a `Main` método na `StudentClass`.  
  
4.  Substituir a classe `Program` com o código a seguir.  
  
     [!code-cs[csProgGuideLINQ#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  Adicione a seguinte linha para o `Main` método na classe `DynamicPredicates`, sob a declaração de `ids`.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
6.  Pressione F5 para executar o projeto.  
  
7.  A seguinte saída é exibida em uma janela de Prompt de comando:  
  
     Garcia: 114  
  
     O ' Donnell: 112  
  
     Omelchenko: 111  
  
8.  A próxima etapa é executar o projeto novamente, desta vez usando a entrada inserido em tempo de execução em vez de matriz `ids`.  Em  **Solution Explorer**, com o botão direito  **PredicateFilters** e, em seguida, clique em  **Propriedades**.  
  
9. Clique na guia **Debug**.  
  
10. No  **argumentos de linha de comando** janela, tipo 122, 117, 120 e 115, separados por espaços:  `122 117 120 115`.  Quando o projeto é executado, esses valores se tornam elementos de `args`, o parâmetro da `Main` método.  
  
11. Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.  
  
12. Pressione F5 para executar o projeto.  
  
13. A seguinte saída é exibida em uma janela de Prompt de comando:  
  
     Adams: 120  
  
     Feng: 117  
  
     Garcia: 115  
  
     Tucker: 122  
  
### Filtrar usando uma instrução switch  
  
1.  Você pode usar um `switch` predeterminados de instrução para selecionar entre consultas alternativas.  No exemplo a seguir, `studentQuery` usa um diferente `where` cláusula dependendo de qual nível nível ou ano, é especificado em tempo de execução.  
  
2.  O seguinte método de copiar e colá\-lo na classe `DynamicPredicates`.  
  
     [!code-cs[csProgGuideLINQ#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  No  **argumentos de linha de comando** janela, números de substituir a identificação do procedimento anterior com um valor inteiro entre 1 e 4.  
  
4.  No `Main` método, substituir a chamada para `QueryByID` com a seguinte chamada, que envia o primeiro elemento da `args` matriz como seu argumento: `QueryByYear(args[0])`.  
  
5.  Pressione F5 para executar o projeto.  
  
### Para usar esse método em seus próprios aplicativos  
  
-   Quando você adapta este método para seu próprio aplicativo, lembre\-se de que o LINQ requer a versão 3.5 ou 4 da [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], e que o projeto deve conter uma referência a System.Core.dll e um `using` diretriz para `System.Linq`.  LINQ to SQL, LINQ to XML e LINQ to DataSet tipos requerem adicionais `using` diretivas e referências.  Para obter mais informações, consulte [Como criar um projeto LINQ](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Consulte também  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Cláusula where](../../../visual-basic/language-reference/queries/where-clause.md)