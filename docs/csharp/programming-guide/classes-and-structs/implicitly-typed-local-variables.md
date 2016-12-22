---
title: "Vari&#225;veis locais de tipo impl&#237;cito (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "variáveis locais tipadas implicitamente [C#]"
  - "var [C#]"
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Vari&#225;veis locais de tipo impl&#237;cito (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Variáveis locais podem ser designadas como um "tipo" inferido do `var` em vez de um tipo explícito.  O `var` palavra\-chave instrui o compilador para inferir o tipo da variável da expressão no lado direito da instrução de inicialização.  O tipo inferido pode ser um tipo interno, um tipo anônimo, um tipo definido pelo usuário ou um tipo definido na.Biblioteca de classes.  Para obter mais informações sobre como inicializar matrizes com `var`, consulte [Matrizes de tipo implícito](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
 Os exemplos a seguir mostram várias maneiras de variáveis locais podem ser declaradas com `var`:  
  
 [!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 É importante entender que o `var` palavra\-chave não significa "variant" e não indica que a variável é vagamente digitado ou ligação tardia.  Ele apenas significa que o compilador determina e atribui o tipo mais apropriado.  
  
 O `var` palavra\-chave pode ser usado nos seguintes contextos:  
  
-   Em variáveis locais \(variáveis declaradas no escopo do método\) conforme mostrado no exemplo anterior.  
  
-   Em um  [para](../../../csharp/language-reference/keywords/for.md) a instrução de inicialização.  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   Em um  [foreach](../../../csharp/language-reference/keywords/foreach-in.md) a instrução de inicialização.  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   Em um  [usando](../../../visual-basic/language-reference/statements/using-statement.md) instrução.  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 Para obter mais informações, consulte [Como usar matrizes e variáveis locais de tipo implícito em uma expressão de consulta](../Topic/How%20to:%20Use%20Implicitly%20Typed%20Local%20Variables%20and%20Arrays%20in%20a%20Query%20Expression%20\(C%23%20Programming%20Guide\).md).  
  
## var e tipos anônimos  
 Em muitos casos, o uso de `var` é opcional e é apenas uma conveniência sintática.  No entanto, quando uma variável é inicializada com um tipo anônimo deve declarar a variável como `var` se você precisar acessar as propriedades do objeto em um momento posterior.  Este é um cenário comum em [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] expressões de consulta.  Para obter mais informações, consulte [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Da perspectiva do seu código\-fonte, um tipo anônimo não tem nome.  Portanto, se uma variável de consulta foi inicializada com `var`, e em seguida, a única maneira de acessar as propriedades na seqüência de objetos retornada é usar `var` como o tipo da variável de iteração na `foreach` instrução.  
  
 [!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## Comentários  
 As seguintes restrições se aplicam a declarações de variável de tipo implícito:  
  
-   `var`só pode ser usado quando uma variável local é declarada e inicializada na mesma instrução; não é possível inicializar a variável como null ou a um grupo de método ou uma função anônima.  
  
-   `var`não pode ser usado em campos no escopo de classe.  
  
-   Variáveis declaradas usando `var` não pode ser usado na expressão de inicialização.  Em outras palavras, essa expressão é legal`: int i = (i = 20);` , mas essa expressão produz um erro em tempo de compilação:`var i = (i = 20);`  
  
-   Múltiplas variáveis de tipo implícito não podem ser inicializadas na mesma instrução  
  
-   Se o nome de um tipo de `var` está no escopo, em seguida, a `var` resolverão ao nome desse tipo de palavra\-chave e não será tratada como parte de uma declaração de variável local digitada implicitamente.  
  
 Talvez você descubra que `var` também pode ser útil com expressões de consulta na qual o tipo exato de construído da variável de consulta é difícil determinar.  Isso pode ocorrer com o agrupamento e classificação de operações.  
  
 O `var` palavra\-chave também pode ser útil quando o tipo específico da variável é entediante digitar no teclado, é óbvio ou não adicionará a legibilidade do código.  Um exemplo onde `var` é útil dessa maneira é com aninhadas tipos genéricos, como aqueles usados com as operações do grupo.  Na consulta a seguir, o tipo da variável de consulta é `IEnumerable<IGrouping<string, Student>>`.  Contanto que você e outras pessoas que deve manter seu código compreendem isso, não há nenhum problema com o uso de digitação implícita para conveniência e questões de brevidade.  
  
 [!CODE [cscsrefQueryKeywords#13](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#13)]  
  
 No entanto, o uso de `var` ter pelo menos o potencial de tornar seu código mais difícil de entender para outros desenvolvedores.  Por esse motivo, a documentação do C\# geralmente usa `var` somente quando for necessário.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Matrizes de tipo implícito](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)   
 [Como usar matrizes e variáveis locais de tipo implícito em uma expressão de consulta](../Topic/How%20to:%20Use%20Implicitly%20Typed%20Local%20Variables%20and%20Arrays%20in%20a%20Query%20Expression%20\(C%23%20Programming%20Guide\).md)   
 [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [for](../../../csharp/language-reference/keywords/for.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Instrução using](../../../visual-basic/language-reference/statements/using-statement.md)