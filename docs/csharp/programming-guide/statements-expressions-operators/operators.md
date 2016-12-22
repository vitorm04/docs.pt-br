---
title: "Operadores (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "Linguagem C#, operadores"
  - "operadores [C#]"
  - "operadores [C#], sobre operadores"
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
caps.latest.revision: 42
caps.handback.revision: 42
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operadores (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

No c\#, um *operador* é um elemento de programa que é aplicado a um ou mais *operandos* em uma expressão ou instrução. Os operadores que usam um operando, como o operador de incremento \(`++`\) ou `new`, são chamados de *unário* operadores. Os operadores que usam dois operandos, como operadores aritméticos \(`+`,`-`,`*`,`/`\), são conhecidas como *binário* operadores. Um operador, o operador condicional \(`?:`\), usa três operandos e é o único operador ternário em c\#.  
  
 A seguinte instrução c\# contém um único operador unário e um operando único. O operador de incremento, `++`, modifica o valor do operando `y`.  
  
 [!code-cs[csProgGuideStatements#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_1.cs)]  
  
 A seguinte instrução c\# contém dois operadores binários, cada um com dois operandos. O operador de atribuição, `=`, contém a variável inteira `y` e a expressão `2 + 3` como operandos. A expressão `2 + 3` em si consiste o operador de adição e dois operandos, `2` e `3`.  
  
 [!code-cs[csProgGuideStatements#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_2.cs)]  
  
## Operadores, avaliação e precedência de operador  
 Um operando pode ser uma expressão válida que é composta de qualquer tamanho de código e pode incluir qualquer número de subexpressões. Em uma expressão que contém vários operadores, a ordem na qual os operadores são aplicados é determinada pela *precedência do operador*, *associatividade*, e parênteses.  
  
 Cada operador tem uma precedência definida. Em uma expressão que contém vários operadores que têm diferentes níveis de precedência, a precedência dos operadores determina a ordem na qual os operadores são avaliados. Por exemplo, a instrução a seguir atribui 3 a `n1`.  
  
 `n1 = 11 - 2 * 4;`  
  
 A multiplicação é executada primeiro porque ela tem precedência sobre a subtração.  
  
 A tabela a seguir separa os operadores em categorias com base no tipo de operação que eles executam. As categorias são listadas em ordem de precedência.  
  
 **Operadores primários**  
  
|Expressão|Descrição|  
|---------------|---------------|  
|x[.](../../../csharp/language-reference/operators/member-access-operator.md)y<br /><br /> x? y|Acesso de membro<br /><br /> Acesso de membro condicional|  
|f[\(x\)](../../../csharp/language-reference/operators/invocation-operator.md)|Invocação de método e delegado|  
|a[&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md)<br /><br /> um? \[x\]|Acesso de matriz e indexador<br /><br /> Acesso de matriz e indexador condicional|  
|x[\+\+](../../../csharp/language-reference/operators/increment-operator.md)|Pós\-incremento|  
|x[\-\-](../../../csharp/language-reference/operators/decrement-operator.md)|Pós\-decremento|  
|[new](../../../visual-basic/language-reference/operators/new-operator.md) T\(...\)|Criação de objeto e delegado|  
|`new` T\(...\) {...}|Criação de objeto com inicializador. Consulte [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).|  
|`new` {...}|Inicializadores de objeto anônimos. Consulte [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).|  
|`new` T\[...\]|Criação de matriz. Consulte [Matrizes](../../../csharp/programming-guide/arrays/index.md).|  
|[typeof](../../../csharp/language-reference/keywords/typeof.md)\(T\)|Obter o objeto System. Type para T|  
|[check\-](../../../csharp/language-reference/keywords/checked.md)\(x\)|Avaliar expressão no contexto selecionado|  
|[desmarcada](../../../csharp/language-reference/keywords/unchecked.md)\(x\)|Avaliar a expressão no contexto desmarcado|  
|[padrão](../../../csharp/language-reference/keywords/default.md) \(T\)|Obter o valor padrão do tipo T|  
|[Delegar](../../../csharp/language-reference/keywords/delegate.md) {}|Função de anônima \(método anônimo\)|  
  
 **Operadores unários**  
  
|Expressão|Descrição|  
|---------------|---------------|  
|[\+](../../../csharp/language-reference/operators/addition-operator.md)x|Identidade|  
|[\-](../../../csharp/language-reference/operators/subtraction-operator.md)x|Negação|  
|[\!](../../../csharp/language-reference/operators/logical-negation-operator.md)x|Negação lógica|  
|[~](../../../csharp/language-reference/operators/bitwise-complement-operator.md)x|Negação bit a bit|  
|[\+\+](../../../csharp/language-reference/operators/increment-operator.md)x|Pré\-incremento|  
|[\-\-](../../../csharp/language-reference/operators/decrement-operator.md)x|Pré\-decremento|  
|[\(T\)](../../../csharp/language-reference/operators/invocation-operator.md)x|Converter explicitamente x no tipo T|  
  
 **Operadores de multiplicação**  
  
|Expressão|Descrição|  
|---------------|---------------|  
|[\*](../../../csharp/language-reference/operators/multiplication-operator.md)|Multiplicação|  
|[\/](../../../csharp/language-reference/operators/division-operator.md)|Divisão|  
|[%](../../../csharp/language-reference/operators/modulus-operator.md)|Restante|  
  
 **Operadores aditivos**  
  
|Expressão|Descrição|  
|---------------|---------------|  
|x [\+](../../../csharp/language-reference/operators/addition-operator.md) y|Adição, concatenação de cadeia de caracteres, combinação de delegado|  
|x [\-](../../../csharp/language-reference/operators/subtraction-operator.md) y|Subtração, remoção de delegado|  
  
 **Operadores SHIFT**  
  
|Expressão|Descrição|  
|---------------|---------------|  
|x [\<\<](../../../csharp/language-reference/operators/left-shift-operator.md) y|SHIFT esquerda|  
|x [\>\>](../Topic/%3E%3E%20Operator%20\(C%23%20Reference\).md) y|SHIFT direito|  
  
 **Relacionais e operadores de tipo**  
  
|Expressão|Descrição|  
|---------------|---------------|  
|x [\<](../Topic/%3C%20Operator%20\(C%23%20Reference\).md) y|Menor que|  
|x [\>](../../../csharp/language-reference/operators/greater-than-operator.md) y|Maior que|  
|x [\<\=](../../../csharp/language-reference/operators/less-than-equal-operator.md) y|Menor ou igual|  
|x [\>\=](../Topic/%3E=%20Operator%20\(C%23%20Reference\).md) y|Maior que ou igual|  
|x [is](../../../csharp/language-reference/keywords/is.md) T|Retorna true se x for T, FALSO caso contrário|  
|x [as](../../../csharp/language-reference/keywords/as.md) T|Retorna x digitado como T ou nulo se x não for um "T"|  
  
 **Operadores de igualdade**  
  
|Expressão|Descrição|  
|---------------|---------------|  
|x [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) y|Igual a|  
|x [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) y|Não é igual a|  
  
 **Operadores lógicos, condicionais e nulos**  
  
|Categoria|Expressão|Descrição|  
|---------------|---------------|---------------|  
|AND lógico|x [&](../../../visual-basic/language-reference/operators/and-operator.md) y|E de lógica bit a bit e Boolean inteiro|  
|XOR lógico|x [^](../../../visual-basic/language-reference/operators/xor-operator.md) y|XOR bit a bit inteiro, XOR lógico booliano|  
|OR lógico|x [&#124;](../../../csharp/language-reference/operators/or-operator.md) y|OR de lógica bit a bit ou booleano inteiro|  
|AND condicional|x [& &](../../../csharp/language-reference/operators/conditional-and-operator.md) y|Avalia y somente se x for true|  
|OR condicional|x [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) y|Avalia y somente se x for false|  
|Coalescência nula|x [??](../../../csharp/language-reference/operators/null-conditional-operator.md) y|Avalia como y se x for nulo, a x, caso contrário|  
|Condicional|x [?](../../../csharp/language-reference/operators/conditional-operator.md) y : z|Avalia como y se x for true, z se x for false|  
  
 **Atribuição e anônimos operadores**  
  
|Expressão|Descrição|  
|---------------|---------------|  
|[\=](../../../csharp/language-reference/operators/assignment-operator.md)|Atribuição|  
|x op \= y|Atribuição composta. Supports these operators: [\+\=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [\-\=](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md), [\*\=](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md), [\/\=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [%\=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&\=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;\=](../../../csharp/language-reference/operators/or-assignment-operator.md), [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md), [\<\<\=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [\>\>\=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|  
|\(T x\) [\=\>](../../../csharp/language-reference/operators/lambda-operator.md) y|Função anônima \(expressão lambda\)|  
  
## Associatividade  
 Quando dois ou mais operadores que têm a mesma precedência estiverem presentes em uma expressão, eles são avaliados com base em associatividade. Os operadores associativos esquerdos são avaliados na ordem da esquerda para a direita. Por exemplo, `x * y / z` é avaliada como `(x * y) / z`. Operadores associativos direitos são avaliados na ordem da direita para a esquerda. Por exemplo, o operador de atribuição é associativo direito. Se não for, o código a seguir resultaria em um erro.  
  
```c#  
int a, b, c; c = 1; // The following two lines are equivalent. a = b = c; a = (b = c); // The following line, which forces left associativity, causes an error. //(a = b) = c;  
```  
  
 Como outro exemplo do operador ternário \([?:](../../../csharp/language-reference/operators/conditional-operator.md)\) é associativo direito. A maioria dos operadores binários permanecem associativos.  
  
 Se os operadores em uma expressão forem associativos direitos ou esquerdos, os operandos de todas as expressões são avaliados primeiro, da esquerda para a direita. Os exemplos a seguir ilustram a ordem de avaliação de operadores e operandos.  
  
|Instrução|Ordem de avaliação|  
|---------------|------------------------|  
|`a = b`|a, b \=|  
|`a = b + c`|a, b, c, \+, \=|  
|`a = b + c * d`|a, b, c, r, \*, \+, \=|  
|`a = b * c + d`|a, b, c, \*, d, \+, \=|  
|`a = b - c + d`|a, b, c\-, d, \+, \=|  
|`a += b -= c`|a, b, c, \-\=, \+\=|  
  
## Adicionando parênteses  
 Você pode alterar a ordem imposta pela precedência e associatividade usando parênteses. Por exemplo, `2 + 3 * 2` resulta normalmente em 8, pois operadores multiplicativos têm precedência sobre operadores aditivos. No entanto, se você escrever a expressão como `(2 + 3) * 2`, a adição é avaliada antes da multiplicação e o resultado será 10. Os exemplos a seguir ilustram a ordem de avaliação em expressões entre parênteses. Como nos exemplos anteriores, os operandos são avaliados antes que o operador é aplicado.  
  
|Instrução|Ordem de avaliação|  
|---------------|------------------------|  
|`a = (b + c) * d`|a, b, c \+, d, \*, \=|  
|`a = b - (c + d)`|a, b, c, r, \+, \-, \=|  
|`a = (b + c) * (d - e)`|a, b, c, \+, d, e, \-, \*, \=|  
  
## Sobrecarga de operador  
 Você pode alterar o comportamento dos operadores para classes e structs personalizados. Esse processo é conhecido como *sobrecarregamento*. Para obter mais informações, consulte [Operadores sobrecarregáveis](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).  
  
## Seções relacionadas  
 Para obter mais informações, consulte [Palavras\-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md) e [Operadores em C\#](../../../csharp/language-reference/operators/index.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Instruções, expressões e operadores](../../../visual-basic/reference/command-line-compiler/index.md)