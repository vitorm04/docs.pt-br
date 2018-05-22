---
title: Variáveis locais de tipo implícito (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: c6c2bae39764e78fad2510bbc8937b0ac790bef5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Variáveis locais de tipo implícito (Guia de Programação em C#)
Variáveis locais podem ser declaradas sem fornecer um tipo explícito. A palavra-chave `var` instrui o compilador a inferir o tipo da variável da expressão no lado direito da instrução de inicialização. O tipo inferido pode ser um tipo interno, um tipo anônimo, um tipo definido pelo usuário ou um tipo definido na biblioteca de classes .NET Framework. Para obter mais informações sobre como inicializar matrizes com `var`, consulte [Matrizes de tipo implícito](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
 Os exemplos a seguir mostram várias maneiras em que as variáveis locais podem ser declaradas com `var`:  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 É importante entender que a palavra-chave `var` não significa "variante" e não indica que a variável é vagamente tipada ou de associação tardia. Isso apenas significa que o compilador determina e atribui o tipo mais apropriado.  
  
 A palavra-chave `var` pode ser usada nos seguintes contextos:  
  
-   Em variáveis locais (variáveis declaradas no escopo do método) conforme mostrado no exemplo anterior.  
  
-   Em uma instrução de inicialização [for](../../../csharp/language-reference/keywords/for.md).  
  
    ```csharp  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   Em uma instrução de inicialização [foreach](../../../csharp/language-reference/keywords/foreach-in.md).  
  
    ```csharp  
    foreach(var item in list){...}  
    ```  
  
-   Em uma instrução [using](../../../csharp/language-reference/keywords/using-statement.md).  
  
    ```csharp  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 Para obter mais informações, consulte [Como usar matrizes e variáveis locais de tipo implícito em uma expressão de consulta](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).  
  
## <a name="var-and-anonymous-types"></a>var e tipos anônimos  
 Em muitos casos, o uso de `var` é opcional e é apenas uma conveniência sintática. No entanto, quando uma variável é inicializada com um tipo anônimo você deve declarar a variável como `var` se precisar acessar as propriedades do objeto em um momento posterior. Esse é um cenário comum em expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Para obter mais informações, consulte [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Da perspectiva do código-fonte, um tipo anônimo não tem nome. Portanto, se uma variável de consulta tiver sido inicializada com `var`, a única maneira de acessar as propriedades na sequência retornada será usar `var` como o tipo da variável de iteração na instrução `foreach`.  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a>Comentários  
 As seguintes restrições se aplicam às declarações de variável de tipo implícito:  
  
-   `var` pode ser usado apenas quando uma variável local é declarada e inicializada na mesma instrução, a variável não pode ser inicializada como nula, um grupo de métodos ou uma função anônima.  
  
-   `var` não pode ser usado em campos no escopo da classe.  
  
-   Variáveis declaradas usando `var` não podem ser usadas na expressão de inicialização. Em outras palavras, essa expressão é válida `: int i = (i = 20);`, mas essa expressão gera um erro em tempo de compilação: `var i = (i = 20);`  
  
-   Diversas variáveis de tipo implícito não podem ser inicializadas na mesma instrução.  
  
-   Se um tipo nomeado `var` estiver no escopo, a palavra-chave `var` será resolvida para esse nome de tipo e não será tratada como parte de uma declaração de variável local de tipo implícito.  
  
 Você pode descobrir que `var` também pode ser útil com expressões de consulta em que o tipo construído exato da variável de consulta é difícil de ser determinado. Isso pode ocorrer com operações de agrupamento e classificação.  
  
 A palavra-chave `var` também pode ser útil quando o tipo específico da variável é enfadonho de digitar no teclado, é óbvio ou não acrescenta à legibilidade do código. Um exemplo em que `var` é útil dessa maneira é com os tipos genéricos aninhados, como os usados com operações de grupo. Na consulta a seguir, o tipo da variável de consulta é `IEnumerable<IGrouping<string, Student>>`. Contanto que você e as outras pessoas que devem manter o código entendam isso, não há problema em usar a tipagem implícita por questões de conveniência e brevidade.  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 No entanto, o uso de `var` tem pelo menos o potencial de tornar seu código mais difícil de entender para outros desenvolvedores. Por esse motivo, a documentação do C# geralmente usa `var` somente quando é necessário.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Matrizes de tipo implícito](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [Como usar matrizes e variáveis locais de tipo implícito em uma expressão de consulta](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [for](../../../csharp/language-reference/keywords/for.md)  
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Instrução using](../../../csharp/language-reference/keywords/using-statement.md)
