---
title: Operadores (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: bf453d5770967f26999b8537339f1b690646b97d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150960"
---
# <a name="operators-c-programming-guide"></a>Operadores (Guia de Programação em C#)
Em C#, um *operador* é um elemento de programa aplicado a um ou mais *operandos* em uma expressão ou instrução. Os operadores que usam um operando, como o operador de incremento (`++`) ou `new`, são referidos como operadores *unários*. Os operadores que usam dois operandos, como operadores aritméticos (`+`,`-`,`*`,`/`), são referidos como operadores *binários*. Um operador, o operador condicional (`?:`), usa três operandos e é o único operador ternário em C#.  
  
 A seguinte instrução de C# contém um único operador unário e um operando único. O operador de incremento, `++`, modifica o valor do operando `y`.  
  
 [!code-csharp[csProgGuideStatements#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_1.cs)]  
  
 A seguinte instrução de C# contém dois operadores binários, cada um com dois operandos. O operador de atribuição, `=`, contém a variável inteira `y` e a expressão `2 + 3` como operandos. A expressão `2 + 3` em si consiste no operador de adição e dois operandos, `2` e `3`.  
  
 [!code-csharp[csProgGuideStatements#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_2.cs)]  
  
## <a name="operators-evaluation-and-operator-precedence"></a>Operadores, avaliação e precedência de operadores  
 Um operando pode ser uma expressão válida composta por qualquer comprimento de código e pode incluir qualquer número de subexpressões. Em uma expressão que contém vários operadores, a ordem em que os operadores são aplicados é determinada pela *precedência de operadores*, *associatividade* e parênteses.  
  
 Cada operador possui uma precedência definida. Em uma expressão com vários operadores e diferentes níveis de precedência, a precedência dos operadores determina a ordem em que os operadores são avaliados. Por exemplo, a seguinte instrução atribui 3 a `n1`.  
  
 `n1 = 11 - 2 * 4;`  
  
 A multiplicação é executada primeiro porque ela tem precedência sobre a subtração.  
  
 A tabela a seguir separa os operadores em categorias com base no tipo de operação que eles executam. As categorias são listadas em ordem de precedência.  
  
 **Operadores primários**  
  
|Expressão|Descrição|  
|----------------|-----------------|  
|x[.](../../../csharp/language-reference/operators/member-access-operator.md)y<br /><br /> x?.y|Acesso de membros<br /><br /> Acesso de membro condicional|  
|f[(x)](../../../csharp/language-reference/operators/invocation-operator.md)|Invocação de método e delegado|  
|a[&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md)<br /><br /> a?[x]|Acesso de matriz e indexador<br /><br /> Acesso condicional de matriz e indexador|  
|x[++](../../../csharp/language-reference/operators/increment-operator.md)|Pós-incremento|  
|x[--](../../../csharp/language-reference/operators/decrement-operator.md)|Pós-decremento|  
|[new](../../../csharp/language-reference/keywords/new-operator.md) T(...)|Criação de objeto e delegado|  
|`new` T(...){...}|Criação de objeto com inicializador. Consulte [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).|  
|`new` {...}|Inicializador de objeto anônimo. Consulte [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).|  
|`new` T[...]|Criação de matriz. Consulte [Matrizes](../../../csharp/programming-guide/arrays/index.md).|  
|[typeof](../../../csharp/language-reference/keywords/typeof.md)(T)|Obtém objeto System.Type para T|  
|[checked](../../../csharp/language-reference/keywords/checked.md)(x)|Avalia expressão no contexto selecionado|  
|[unchecked](../../../csharp/language-reference/keywords/unchecked.md)(x)|Avalia expressão no contexto desmarcado|  
|[default](../../../csharp/language-reference/keywords/default.md) (T)|Obtém valor padrão do tipo T|  
|[delegate](../../../csharp/language-reference/keywords/delegate.md) {}|Função anônima (método anônimo)|  
  
 **Operadores unários**  
  
|Expressão|Descrição|  
|----------------|-----------------|  
|[+](../../../csharp/language-reference/operators/addition-operator.md)x|Identidade|  
|[-](../../../csharp/language-reference/operators/subtraction-operator.md)x|Negação|  
|[\!](../../../csharp/language-reference/operators/logical-negation-operator.md)x|Negação lógica|  
|[~](../../../csharp/language-reference/operators/bitwise-complement-operator.md)x|Negação bit a bit|  
|[++](../../../csharp/language-reference/operators/increment-operator.md)x|Pré-incremento|  
|[--](../../../csharp/language-reference/operators/decrement-operator.md)x|Pré-decremento|  
|[(T)](../../../csharp/language-reference/operators/invocation-operator.md)x|Converte explicitamente x no tipo T|  
  
 **Operadores multiplicativos**  
  
|Expressão|Descrição|  
|----------------|-----------------|  
|[*](../../../csharp/language-reference/operators/multiplication-operator.md)|Multiplicação|  
|[/](../../../csharp/language-reference/operators/division-operator.md)|Divisão|  
|[%](../../../csharp/language-reference/operators/modulus-operator.md)|Restante|  
  
 **Operadores aditivos**  
  
|Expressão|Descrição|  
|----------------|-----------------|  
|x [+](../../../csharp/language-reference/operators/addition-operator.md) y|Adição, concatenação de cadeia de caracteres, combinação de delegados|  
|x [-](../../../csharp/language-reference/operators/subtraction-operator.md) y|Subtração, remoção de delegado|  
  
 **Operadores shift**  
  
|Expressão|Descrição|  
|----------------|-----------------|  
|x [<\<](../../../csharp/language-reference/operators/left-shift-operator.md) y|Shift esquerdo|  
|x [>>](../../../csharp/language-reference/operators/right-shift-operator.md) y|Shift direito|  
  
 **Operadores de tipo e relacionais**  
  
|Expressão|Descrição|  
|----------------|-----------------|  
|x [\<](../../../csharp/language-reference/operators/less-than-operator.md) y|Menor que|  
|x [>](../../../csharp/language-reference/operators/greater-than-operator.md) y|Maior que|  
|x [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) y|Menor que ou igual a|  
|x [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) y|Maior que ou igual a|  
|x [is](../../../csharp/language-reference/keywords/is.md) T|Retorna true se x for T, caso contrário, false|  
|x [as](../../../csharp/language-reference/keywords/as.md) T|Retorna x digitado como T ou nulo se x não for T|  
  
 **Operadores de igualdade**  
  
|Expressão|Descrição|  
|----------------|-----------------|  
|x [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) y|Igual|  
|x [!=](../../../csharp/language-reference/operators/not-equal-operator.md) y|Não é igual a|  
  
 **Operadores lógicos, condicionais e nulos**  
  
|Categoria|Expressão|Descrição|  
|--------------|----------------|-----------------|  
|AND lógico|x [&](../../../csharp/language-reference/operators/and-operator.md) y|AND bit a bit inteiro, AND lógico booliano|  
|XOR lógico|x [^](../../../csharp/language-reference/operators/xor-operator.md) y|XOR bit a bit inteiro, XOR lógico booliano|  
|OR lógico|x [&#124;](../../../csharp/language-reference/operators/or-operator.md) y|OR bit a bit inteiro, OR lógico booliano|  
|AND condicional|x [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) y|Avalia y somente se x for true|  
|OR condicional|x [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) y|Avalia y somente se x for false|  
|Coalescência nula|x [??](../../../csharp/language-reference/operators/null-coalescing-operator.md) y|Avalia como y se x for nulo, caso contrário, como x|  
|Condicional|x [?](../../../csharp/language-reference/operators/conditional-operator.md) y : z|Avalia como y se x for true, z se x for false|  
  
 **Operadores de atribuição e anônimos**  
  
|Expressão|Descrição|  
|----------------|-----------------|  
|[=](../../../csharp/language-reference/operators/assignment-operator.md)|Atribuição|  
|x op= y|Atribuição composta. Compatível com estes operadores: [+=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [-=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [*=](../../../csharp/language-reference/operators/multiplication-assignment-operator.md), [/=](../../../csharp/language-reference/operators/division-assignment-operator.md), [%=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md), [^=](../../../csharp/language-reference/operators/xor-assignment-operator.md), [<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|  
|(T x) [=>](../../../csharp/language-reference/operators/lambda-operator.md) y|Função anônima (expressão lambda)|  
  
## <a name="associativity"></a>Associatividade  
 Quando dois ou mais operadores com a mesma precedência estiverem presentes em uma expressão, eles serão avaliados com base em associatividade. Os operadores associativos esquerdos são avaliados em ordem da esquerda para a direita. Por exemplo, `x * y / z` é avaliado como `(x * y) / z`. Os operadores associativos direitos são avaliados em ordem da direita para a esquerda. Por exemplo, o operador de atribuição é associativo direito. Se ele não fosse, o código a seguir resultaria em um erro.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Como outro exemplo, o operador ternário ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) é associativo à direita. A maioria dos operadores binários são associativos à esquerda.  
  
 Se os operadores em uma expressão forem associativos direitos ou esquerdos, os operandos de cada expressão serão avaliados primeiro, da esquerda para a direita. Os exemplos a seguir ilustram a ordem de avaliação de operadores e operandos.  
  
|Instrução|Ordem de avaliação|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>Adicionando parênteses  
 Você pode alterar a ordem imposta pela precedência de operadores e a associatividade ao usar parênteses. Por exemplo, `2 + 3 * 2` resulta normalmente em 8, pois operadores multiplicativos têm precedência sobre operadores aditivos. No entanto, se você escrever a expressão como `(2 + 3) * 2`, a adição será avaliada antes da multiplicação e o resultado será 10. Os exemplos a seguir ilustram a ordem de avaliação em expressões com parênteses. Como nos exemplos anteriores, os operandos são avaliados antes que o operador seja aplicado.  
  
|Instrução|Ordem de avaliação|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>Sobrecarga de operador  
 Você pode alterar o comportamento dos operadores para classes e structs personalizados. Esse processo é chamado *sobrecarga de operador*. Para obter mais informações, consulte [Operadores sobrecarregáveis](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) e o artigo de palavra-chave [operador](../../../csharp/language-reference/keywords/operator.md).  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para obter mais informações, consulte [Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md) e [Operadores do C#](../../../csharp/language-reference/operators/index.md).  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Instruções, expressões e operadores](../../../csharp/programming-guide/statements-expressions-operators/index.md)
