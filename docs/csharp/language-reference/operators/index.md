---
title: Operadores em C#
ms.date: 04/04/2018
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 2b0441dfebb6692cbea0d1ab7909d7b8f04490cb
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="c-operators"></a>Operadores em C#
O C# fornece muitos operadores, que são símbolos que especificam as operações (matemática, indexação, chamada de função, etc.) para executar em uma expressão. Você pode [sobrecarregar](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) muitos operadores para alterar seu significado quando aplicados a um tipo definido pelo usuário.  
  
 As operações em tipos integrais (como `==`, `!=`, `<`, `>`, `&`, `|`) geralmente são permitidas em tipos de enumeração (`enum`).  
  
 As seções abaixo listam os operadores em C# da precedência mais alta para a mais baixa. Os operadores em cada seção compartilham o mesmo nível de precedência.  
 
## <a name="primary-operators"></a>Operadores primários  
 Esses são os operadores de precedência mais alta.
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) – acesso de membro.  
  
 [x?.y](../../../csharp/language-reference/operators/null-conditional-operators.md) – acesso de membro condicional nulo. Retornará `null` se o operando esquerdo for avaliado como `null`.  
 
 [x?[y]](../../../csharp/language-reference/operators/null-conditional-operators.md) – acesso de índice condicional nulo. Retornará `null` se o operando esquerdo for avaliado como `null`.
 
 [f(x)](../../../csharp/language-reference/operators/invocation-operator.md) – invocação de função.  
  
 [a&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md) – indexação de objeto de agregação.  
   
 [x++](../../../csharp/language-reference/operators/increment-operator.md) – incremento de sufixo. Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).  
  
 [x--](../../../csharp/language-reference/operators/decrement-operator.md) – decremento de sufixo. Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).  
  
 [new](../../../csharp/language-reference/keywords/new-operator.md) – instanciação de tipo.  
  
 [typeof](../../../csharp/language-reference/keywords/typeof.md) – retorna o objeto <xref:System.Type> que representa o operando.  
  
 [checked](../../../csharp/language-reference/keywords/checked.md) – habilita a verificação de estouro para operações de inteiros.  
  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) – desabilita a verificação de estouro para operações de inteiros. Este é o comportamento padrão do compilador.  
  
 [default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) – produz o valor padrão do tipo T.  
  
 [delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – declara e retorna uma instância delegada.  
  
 [sizeof](../../../csharp/language-reference/keywords/sizeof.md) – retorna o tamanho em bytes do operando do tipo.  
  
 [->](../../../csharp/language-reference/operators/dereference-operator.md) – desreferência de ponteiro combinada com acesso de membro.  
  
## <a name="unary-operators"></a>Operadores unários  
 Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [+x](../../../csharp/language-reference/operators/addition-operator.md) – retorna o valor de x.  
  
 [-x](../../../csharp/language-reference/operators/subtraction-operator.md) – negação numérica.  
  
 [\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) – negação lógica.  
  
 [~x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – complemento bit a bit.  
  
 [++x](../../../csharp/language-reference/operators/increment-operator.md) – incremento de prefixo. Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).  
  
 [--x](../../../csharp/language-reference/operators/decrement-operator.md) – decremento de prefixo. Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).  
  
 [(T)x](../../../csharp/language-reference/operators/invocation-operator.md) – conversão de tipo.  
  
 [await](../../../csharp/language-reference/keywords/await.md) – aguarda um `Task`.  
  
 [&x](../../../csharp/language-reference/operators/and-operator.md) – endereço.  
  
 [*x](../../../csharp/language-reference/operators/multiplication-operator.md) – desreferenciamento.  
  
## <a name="multiplicative-operators"></a>Operadores de multiplicação  
 Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x * y](../../../csharp/language-reference/operators/multiplication-operator.md) – multiplicação.  
  
 [x / y](../../../csharp/language-reference/operators/division-operator.md) – divisão. Se os operandos forem inteiros, o resultado será um inteiro truncado para zero (por exemplo, `-7 / 2 is -3`).  
  
 [x % y](../../../csharp/language-reference/operators/remainder-operator.md) – restante. Se os operandos forem inteiros, isso retornará o resto da divisão de x por y.  Se `q = x / y` e `r = x % y`, então `x = q * y + r`.  
  
## <a name="additive-operators"></a>Operadores aditivos  
 Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x + y](../../../csharp/language-reference/operators/addition-operator.md) – adição.  
  
 [x – y](../../../csharp/language-reference/operators/subtraction-operator.md) – subtração.  
  
## <a name="shift-operators"></a>Operadores Shift  
 Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x <\< y](../../../csharp/language-reference/operators/left-shift-operator.md) – bits de deslocamento para a esquerda e preenche com zero à direita.  
  
 [x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) – bits de deslocamento para a direita. Se o operando esquerdo for `int` ou `long`, então, os bits à esquerda serão preenchidos com o bit de sinal. Se o operando esquerdo for `uint` ou `ulong`, então, os bits à esquerda serão preenchidos com zero.  
  
## <a name="relational-and-type-testing-operators"></a>Operadores de teste de tipo e relacional  
 Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) – menor que (verdadeiro se x for menor que y).  
  
 [x > y](../../../csharp/language-reference/operators/greater-than-operator.md) – maior que (verdadeiro se x for maior que y).  
  
 [x \<= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) – menor ou igual a.  
  
 [x > = y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) – maior que ou igual a.  
  
 [is](../../../csharp/language-reference/keywords/is.md) – compatibilidade de tipo. Retornará true se o operando esquerdo avaliado puder ser convertido no tipo especificado no operando à direita (um tipo estático).  
  
 [as](../../../csharp/language-reference/keywords/as.md) – conversão de tipo. Retorna o operando esquerdo convertido para o tipo especificado pelo operando à direita (um tipo estático), mas `as` retorna `null` em que `(T)x` lançaria uma exceção.  
  
## <a name="equality-operators"></a>Operadores de igualdade  
 Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x == y](../../../csharp/language-reference/operators/equality-comparison-operator.md) – igualdade. Por padrão, para tipos de referência diferentes de `string`, isso retorna uma igualdade de referência (teste de identidade). No entanto, os tipos podem sobrecarregar `==`, portanto, se sua intenção for testar a identidade, é melhor usar o método `ReferenceEquals` em `object`.  
  
 [x != y](../../../csharp/language-reference/operators/not-equal-operator.md) – não é igual. Consulte o comentário sobre `==`. Se um tipo sobrecarregar `==`, então, ele deverá sobrecarregar `!=`.  
  
## <a name="logical-and-operator"></a>Operador AND lógico  
 Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x & y](../../../csharp/language-reference/operators/and-operator.md) – AND lógico ou bit a bit. Geralmente, você pode usar isso com tipos de inteiro e tipos `enum`.  
  
## <a name="logical-xor-operator"></a>Operador XOR lógico  
 Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) – XOR lógico ou bit a bit. Geralmente, você pode usar isso com tipos de inteiro e tipos `enum`.  
  
## <a name="logical-or-operator"></a>Operador OR lógico  
 Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – OR lógico ou bit a bit. Geralmente, você pode usar isso com tipos de inteiro e tipos `enum`.  
  
## <a name="conditional-and-operator"></a>Operador AND condicional  
 Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x && y](../../../csharp/language-reference/operators/conditional-and-operator.md) – AND lógico. Se o primeiro operando for avaliado como falso, então o C# não avaliará o segundo operando.  
  
## <a name="conditional-or-operator"></a>Operador OR condicional  
 Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x &#124;&#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) – OR lógico. Se o primeiro operando for avaliado como verdadeiro, então o C# não avaliará o segundo operando.  
  
## <a name="null-coalescing-operator"></a>Operador de coalescência nula  
 Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x ?? y](../../../csharp/language-reference/operators/null-coalescing-operator.md) – retornará `x` se for não `null`; caso contrário, retornará `y`.  
  
## <a name="conditional-operator"></a>Operador condicional  
 Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [t ? x : y](../../../csharp/language-reference/operators/conditional-operator.md) – se o teste `t` for avaliado como verdadeiro, então ele avaliará e retornará `x`; caso contrário, avaliará e retornará `y`.  
  
## <a name="assignment-and-lambda-operators"></a>Atribuição e operadores de Lambda  
 Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.  
  
 [x = y](../../../csharp/language-reference/operators/assignment-operator.md) – atribuição.  
  
 [x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – incremento. Adicione o valor de `y` para o valor de `x`, armazene o resultado em `x` e retorne o novo valor. Se `x` designar um `event`, então, `y` deverá ser uma função adequada que o C# adiciona como um manipulador de eventos.  
  
 [x -= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – diminuir. Subtraia o valor de `y` do valor de `x`, armazene o resultado em `x` e retorne o novo valor. Se `x` designar um `event`, então, `y` deverá ser uma função adequada que o C# remove como um manipulador de eventos  
  
 [x *= y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) – atribuição de multiplicação. Multiplique o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.  
  
 [x /= y](../../../csharp/language-reference/operators/division-assignment-operator.md) – atribuição de divisão. Divida o valor de `x` pelo valor de `y`, armazene o resultado em `x` e retorne o novo valor.  
  
 [x %= y](../../../csharp/language-reference/operators/remainder-assignment-operator.md) – atribuição restante. Divida o valor de `x` pelo valor de `y`, armazene o resto em `x` e retorne o novo valor.  
  
 [x &= y](../../../csharp/language-reference/operators/and-assignment-operator.md) – atribuição AND. AND o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.  
  
 [x &#124;= y](../../../csharp/language-reference/operators/or-assignment-operator.md) – atribuição OR. OR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.  
  
 [x ^= y](../../../csharp/language-reference/operators/xor-assignment-operator.md) – atribuição XOR. XOR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.  
  
 [x <<= y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – atribuição de deslocamento para a esquerda. Desloque o valor de `x` para a esquerda em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.  
  
 [x >>= y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – atribuição de deslocamento para a direita. Desloque o valor de `x` para a direita em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.  
  
 [=>](../../../csharp/language-reference/operators/lambda-operator.md) – declaração de lambda.  
  
## <a name="arithmetic-overflow"></a>Estouro aritmético  
 Os operadores aritméticos ([+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [*](../../../csharp/language-reference/operators/multiplication-operator.md), [/](../../../csharp/language-reference/operators/division-operator.md)) podem produzir resultados que estão fora do intervalo de valores possíveis para o tipo numérico envolvido. Consulte a seção sobre um operador específico para obter detalhes, mas, em geral:  
  
- O estouro aritmético de inteiros lança uma <xref:System.OverflowException> ou descarta os bits mais significativos do resultado. A divisão de inteiro por zero sempre lança um <xref:System.DivideByZeroException>.  

   Quando ocorre um estouro de inteiro, o que acontece depende do contexto de execução, que pode ser [verificação ou não verificado](../../../csharp/language-reference/keywords/checked-and-unchecked.md). Em um contexto marcado, uma <xref:System.OverflowException> é lançada. Em um contexto não verificado, os bits mais significativos do resultado são descartados e a execução continua. Assim, C# oferece a opção para tratar ou ignorar o estouro. Por padrão, as operações aritméticas ocorrem em um contexto *não verificado*. 

   Além das operações aritméticas, as conversões de tipo integral para integral tipo podem causar estouro (como quando você converte um [longo](../../../csharp/language-reference/keywords/long.md) para um [int](../../../csharp/language-reference/keywords/int.md)) e estão sujeitas à execução verificada ou não verificada. No entanto, operadores bit a bit e operadores de deslocamento nunca causam estouro.  
   
-   O estouro aritmético de ponto flutuante ou a divisão por zero nunca gera uma exceção, pois os tipos de ponto flutuante são baseados em IEEE 754 e têm provisões para representar o infinito e NaN (não um número).  
  
-   Um estouro aritmético[Decimal](../../../csharp/language-reference/keywords/decimal.md) sempre lança uma <xref:System.OverflowException>. A divisão decimal por zero sempre lança uma <xref:System.DivideByZeroException>.  
  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md) [Operadores sobrecarregáveis](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)
