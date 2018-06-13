---
title: Expressões (Guia de Programação em C#)
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 830c68e6857e72fe19099753ba57a7e22491af2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339651"
---
# <a name="expressions-c-programming-guide"></a>Expressões (Guia de Programação em C#)
Uma *expressão* é uma sequência de um ou mais operandos e zero ou mais operadores que podem ser avaliados como um valor, objeto, método ou namespace único. As expressões podem consistir de um valor literal, uma invocação de método, um operador e seus operandos ou um *nome simples*. Os nomes simples podem ser o nome de uma variável, um membro de tipo, um parâmetro de método, um namespace ou um tipo.  
  
 As expressões podem usar operadores que, por sua vez, usam outras expressões como parâmetros ou chamadas de métodos cujos parâmetros são, por sua vez, outras chamadas de métodos. Assim, as expressões podem variar de “simples” a “muito complexas”. Estes são dois exemplos de expressões:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));
   
System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Valores de expressão  
 Na maioria dos contextos em que as expressões são usadas, por exemplo, em instruções ou parâmetros de método, espera-se que a expressão seja avaliada como algum valor. Se x e y são inteiros, a expressão `x + y` será avaliada como um valor numérico. A expressão `new MyClass()` é avaliada como uma referência a uma nova instância de um objeto `MyClass`. A expressão `myClass.ToString()` é avaliada como uma cadeia de caracteres, porque esse é o tipo de retorno do método. No entanto, embora um nome de namespace seja classificado como uma expressão, ele não é avaliado como um valor e, portanto, nunca pode ser o resultado final de qualquer expressão. Não é possível passar um nome de namespace para um parâmetro de método, usá-lo em uma nova expressão ou atribuí-lo a uma variável. Ele poderá ser usado somente como uma subexpressão em uma expressão maior. Isso também se aplica a tipos (diferentes dos objetos <xref:System.Type?displayProperty=nameWithType>), a nomes de grupos de métodos (diferentes de métodos específicos) e aos acessadores de eventos [add](../../../csharp/language-reference/keywords/add.md) e [remove](../../../csharp/language-reference/keywords/remove.md).  
  
 Cada valor tem um tipo associado. Por exemplo, se x e y forem variáveis do tipo `int`, o valor da expressão `x + y` também será tipado como `int`. Se o valor for atribuído a uma variável de um tipo diferente ou se x e y forem tipos diferentes, as regras de conversão de tipo serão aplicadas. Para obter mais informações sobre como essas conversões funcionam, consulte [Conversões e Conversões de Tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Estouros  
 Expressões numéricas podem causar estouros se o valor for maior que o valor máximo do tipo de valor. Para obter mais informações, consulte [Verificado e Não Verificado](../../../csharp/language-reference/keywords/checked-and-unchecked.md) e [Tabela de Conversões Numéricas Explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="operator-precedence-and-associativity"></a>Precedência e associatividade do operador  
 A maneira pela qual uma expressão é avaliada é regida pelas regras de capacidade de associação e de precedência de operador. Para obter mais informações, consulte [Operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md).  
  
 A maioria das expressões, exceto expressões de atribuição e de invocação de método, deve ser inserida em uma instrução. Para obter mais informações, consulte [Instruções](../../../csharp/programming-guide/statements-expressions-operators/statements.md).  
  
## <a name="literals-and-simple-names"></a>Literais e nomes simples  
 Os dois tipos mais simples de expressões são literais e nomes simples. Um literal é um valor constante que não tem nome. Por exemplo, no exemplo de código a seguir, `5` e `"Hello World"` são valores literais:  
  
 [!code-csharp[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_1.cs)]  
  
 Para obter mais informações sobre literais, consulte [Tipos](../../../csharp/language-reference/keywords/types.md).  
  
 No exemplo anterior, `i` e `s` são nomes simples que identificam variáveis locais. Quando essas variáveis são usadas em uma expressão, o nome da variável é avaliado como o valor armazenado atualmente no local da variável na memória. Isso é mostrado no exemplo a seguir:  
  
 [!code-csharp[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_2.cs)]  
## <a name="invocation-expressions"></a>Expressões de invocação  
 No exemplo de código a seguir, a chamada para `DoWork` é uma expressão de invocação.  
  
```csharp
DoWork();  
```  
  
 Uma invocação de método requer o nome do método, como um nome, conforme o exemplo anterior ou como resultado de outra expressão, seguido de parênteses e quaisquer parâmetros de método. Para saber mais, veja [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md). Uma invocação de delegado usa o nome de um delegado e dos parâmetros de método entre parênteses. Para obter mais informações, consulte [Delegados](../../../csharp/programming-guide/delegates/index.md). Invocações de método e de delegados são avaliadas como o valor retornado do método se o método retornar um valor. Métodos que retornam nulo não podem ser usados no lugar de um valor em uma expressão.  

## <a name="query-expressions"></a>Expressões de consulta  
 As mesmas regras para expressões em geral se aplicam a expressões de consulta. Para obter mais informações, consulte [Expressões de Consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="lambda-expressions"></a>Expressões lambda  
 As expressões lambda representam "métodos embutidos" que não têm nome, mas podem ter parâmetros de entrada e várias instruções. Elas são usadas amplamente no LINQ para passar argumentos para métodos. As expressões lambda são compiladas para delegados ou árvores de expressão, dependendo do contexto no qual elas são usadas. Para obter mais informações, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="expression-trees"></a>Árvores de expressão  
 As árvores de expressão habilitam expressões a serem representadas como estruturas de dados. Elas são usadas amplamente por provedores LINQ para mover expressões de consulta para o código significativo em outro contexto, como um banco de dados SQL. Para obter mais informações, consulte [Árvores de Expressão](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
## <a name="expression-body-definitions"></a>Definições de corpo de expressão

O C# dá suporte a *membros aptos para expressão*, o que permite que você forneça uma definição de corpo da expressão concisa para métodos, construtores, finalizadores, propriedades e indexadores. Para obter mais informações, consulte [Membros aptos para expressão](expression-bodied-members.md).

## <a name="remarks"></a>Comentários  
 Sempre que o acesso a uma variável, propriedade de objeto ou indexador de objeto for identificado de uma expressão, o valor desse item será usado como o valor da expressão. Uma expressão pode ser colocada em qualquer lugar no C# em que um valor ou o objeto for necessário, desde que a expressão seja avaliada como o tipo solicitado.  

## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Delegados](../../../csharp/programming-guide/delegates/index.md)  
 [Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
 [Tipos](../../../csharp/programming-guide/types/index.md)  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
