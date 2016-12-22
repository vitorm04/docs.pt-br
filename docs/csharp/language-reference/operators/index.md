---
title: "Operadores em C# | Microsoft Docs"
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
  - "cs.operators"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "operadores de endereço [C#]"
  - "operadores aritméticos [C#]"
  - "operadores de atribuição [C#]"
  - "operadores bit a bit [C#]"
  - "operadores boolianos [C#]"
  - "expressões [C#], operadores"
  - "operadores de indireção [C#]"
  - "palavras-chave [C#], operadores"
  - "operadores lógicos [C#]"
  - "operadores [C#]"
  - "operadores relacionais [C#]"
  - "operadores shift [C#]"
  - "Visual C#, operadores"
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
caps.latest.revision: 40
caps.handback.revision: 38
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operadores em C# #
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O c\# fornece muitos operadores — símbolos que especificam as operações \(matemática, indexação, chamada de função, etc.\) para executar em uma expressão.  Você pode [sobrecarga](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) muitos operadores para alterar seu significado quando aplicados a um tipo definido pelo usuário.  
  
 Operações em tipos integrais \(como `==`, `!=`, `<`, `>`, `&`,                   `|` \) geralmente são permitidas na enumeração \(`enum`\) tipos.  
  
 As seções lista os operadores c\# começando com a precedência mais alta para o mais baixo.  Os operadores em cada seção compartilham o mesmo nível de precedência.  
  
## Operadores primários  
 Esses são os operadores de precedência mais altos.  Observe que você pode clicar em operadores para acessar as páginas detalhadas com exemplos.  
  
 [y](../../../csharp/language-reference/operators/member-access-operator.md) – acesso de membro.  
  
 [x?. y](../../../csharp/language-reference/operators/null-conditional-operators.md) – null acesso de membro condicional.  Retorna null se o operando esquerdo for nulo.  
  
 [f \(x\)](../../../csharp/language-reference/operators/invocation-operator.md) – chamada de função.  
  
 [&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md) – objeto agregado de indexação.  
  
 [a?&#91; x&#93;](../../../csharp/language-reference/operators/null-conditional-operators.md) – indexação condicional nulo.  Retorna null se o operando esquerdo for nulo.  
  
 [x \+ \+](../../../csharp/language-reference/operators/increment-operator.md) – incremento de sufixo.  Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x é um número maior \(normalmente adiciona o inteiro 1\).  
  
 [x\-\-](../../../csharp/language-reference/operators/decrement-operator.md) – decremento de sufixo.  Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x é menos \(normalmente subtrai o inteiro 1\).  
  
 [Novo](../../../visual-basic/language-reference/operators/new-operator.md) – digite instanciação.  
  
 [Typeof](../../../csharp/language-reference/keywords/typeof.md) – retorna o objeto System. Type que representa o operando.  
  
 [Check](../../../csharp/language-reference/keywords/checked.md) – permite a verificação de operações de inteiros de estouro.  
  
 [Desmarcado](../../../csharp/language-reference/keywords/unchecked.md) – desabilita a verificação de operações de inteiros de estouro.  Esse é o comportamento do compilador padrão.  
  
 [Default \(t\)](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md) – retorna o padrão inicializado o valor do tipo T, null para tipos de referência, zero para tipos numéricos, e zero\/nula preenchida em membros de tipos de estrutura.  
  
 [Delegar](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – declara e retorna uma instância delegate.  
  
 [Sizeof](../../../csharp/language-reference/keywords/sizeof.md) – retorna o tamanho em bytes do operando de tipo.  
  
 [\-\>](../../../csharp/language-reference/operators/dereference-operator.md) – desreferência de ponteiro combinado com acesso de membro.  
  
## Operadores unários  
 Esses operadores têm precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar em operadores para acessar as páginas detalhadas com exemplos.  
  
 [\+ x](../../../csharp/language-reference/operators/addition-operator.md) – retorna o valor de x.  
  
 [\- x](../../../csharp/language-reference/operators/subtraction-operator.md) – negação numérica.  
  
 [\! x](../../../csharp/language-reference/operators/logical-negation-operator.md) – negação lógica.  
  
 [~ x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – complemento bit a bit.  
  
 [\+ \+ x](../../../csharp/language-reference/operators/increment-operator.md) – incremento de prefixo.  Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x é um maior \(normalmente adiciona o inteiro 1\).  
  
 [\-\- x](../../../csharp/language-reference/operators/decrement-operator.md) – decremento de prefixo.  Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x é menos \(normalmente adiciona o inteiro 1\).  
  
 [\(T\) x](../../../csharp/language-reference/operators/invocation-operator.md) – tipo de conversão.  
  
 [Await](../../../csharp/language-reference/keywords/await.md) – aguarda um `Task`.  
  
 [&](../../../visual-basic/language-reference/operators/and-operator.md) – endereço do.  
  
 [\* x](../../../csharp/language-reference/operators/multiplication-operator.md) – desreferenciamento.  
  
## Operadores de multiplicação  
 Esses operadores têm precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar em operadores para acessar as páginas detalhadas com exemplos.  
  
 [x \* y](../../../csharp/language-reference/operators/multiplication-operator.md) – multiplicação.  
  
 [x \/ y](../../../csharp/language-reference/operators/division-operator.md) – divisão.  Se os operandos forem números inteiros, o resultado é um inteiro truncado para zero \(por exemplo, `-7 / 2 is -3`\).  
  
 [x % y](../../../csharp/language-reference/operators/modulus-operator.md) – módulo.  Se os operandos forem inteiros, isso retorna o restante da divisão de x, y.  Se `q = x / y` e `r = x % y`, em seguida, `x = q * y + r`.  
  
## Operadores de Addtive  
 Esses operadores têm precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar em operadores para acessar as páginas detalhadas com exemplos.  
  
 [x \+ y](../../../csharp/language-reference/operators/addition-operator.md) – adição.  
  
 [x\-y](../../../csharp/language-reference/operators/subtraction-operator.md) – subtração.  
  
## Operadores Shift  
 Esses operadores têm precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar em operadores para acessar as páginas detalhadas com exemplos.  
  
 [x \<\< y](../../../csharp/language-reference/operators/left-shift-operator.md) – deslocar bits para a esquerda e preencha com zero à direita.  
  
 [x \>\> y](../Topic/%3E%3E%20Operator%20\(C%23%20Reference\).md) – bits de shift direita.  Se o operando esquerdo for `int` ou `long`, e esquerdas bits são preenchidos com o bit de sinal.  Se o operando esquerdo for `uint` ou `ulong`, e esquerdas bits são preenchidos com zero.  
  
## Operadores relacionais e teste de tipo  
 Esses operadores têm precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar em operadores para acessar as páginas detalhadas com exemplos.  
  
 [x \< y](../Topic/%3C%20Operator%20\(C%23%20Reference\).md) – menor que \(true se x for menor que y\).  
  
 [x \> y](../../../csharp/language-reference/operators/greater-than-operator.md) – maior que \(true se x for maior que y\).  
  
 [x \< \= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) – menor ou igual a.  
  
 [x \> \= y](../Topic/%3E=%20Operator%20\(C%23%20Reference\).md) – menor ou igual a.  
  
 [é](../../../csharp/language-reference/keywords/is.md) – a compatibilidade de tipo.  Retorna VERDADEIRO se o operando esquerdo avaliado pode ser convertido no tipo especificado no operando à direita \(um tipo estático\).  
  
 [Como](../../../csharp/language-reference/keywords/as.md) – conversão de tipo.  Retorna o operando esquerdo convertido para o tipo especificado pelo operando à direita \(um tipo estático\), mas `as` retorna `null` onde `(T)x` lançaria uma exceção.  
  
## Operadores de igualdade  
 Esses operadores têm precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar em operadores para acessar as páginas detalhadas com exemplos.  
  
 [x \= \= y](../../../csharp/language-reference/operators/equality-comparison-operator.md) – igualdade.  Por padrão, para referência de tipos diferentes de `string`, esse retorna referência igualdade \(teste de identidade\).  No entanto, podem sobrecarregar os tipos `==`, portanto, se sua intenção for testar a identidade, é melhor usar o `ReferenceEquals` método `object`.  
  
 [x\! \= y](../../../csharp/language-reference/operators/not-equal-operator.md) – não é igual.  Consulte o comentário para `==`.  Se um tipo de sobrecargas `==`, então deve sobrecarga `!=`.  
  
## Operador AND lógico  
 Esse operador tem precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar no operador para ir para a página de detalhes com exemplos.  
  
 [x e y](../../../visual-basic/language-reference/operators/and-operator.md) – e de lógica ou bit a bit.  Use com tipos de inteiros e `enum` tipos geralmente é permitido.  
  
## Operador XOR lógico  
 Esse operador tem precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar no operador para ir para a página de detalhes com exemplos.  
  
 [x ^ y](../../../visual-basic/language-reference/operators/xor-operator.md) – XOR lógico ou bit a bit.  Você pode usar isso em geral com tipos de inteiro e `enum` tipos.  
  
## Lógica ou operador  
 Esse operador tem precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar no operador para ir para a página de detalhes com exemplos.  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – OR lógica ou bit a bit.  Use com tipos de inteiros e `enum` tipos geralmente é permitido.  
  
## Operador AND condicional  
 Esse operador tem precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar no operador para ir para a página de detalhes com exemplos.  
  
 [x & & y](../../../csharp/language-reference/operators/conditional-and-operator.md) – and lógico.  Se o primeiro operando for false, então c\# não avalia o segundo operando.  
  
## Condicional ou operador  
 Esse operador tem precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar no operador para ir para a página de detalhes com exemplos.  
  
 [x &#124; &#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) – OR lógico.  Se o primeiro operando for true, então c\# não avalia o segundo operando.  
  
## Operador de coalescência nula  
 Esse operador tem precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar no operador para ir para a página de detalhes com exemplos.  
  
 [x?? y](../../../csharp/language-reference/operators/null-conditional-operator.md) – retorna `x` se for não \-`null`; caso contrário, retornará `y`.  
  
## Operador condicional  
 Esse operador tem precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar no operador para ir para a página de detalhes com exemplos.  
  
 [t? x: y](../../../csharp/language-reference/operators/conditional-operator.md) – se testar `t` é verdadeiro, em seguida, avaliar e retornar `x`; caso contrário, avaliar e retornar `y`.  
  
## Atribuição e operadores de Lambda  
 Esses operadores têm precedência maior do que a próxima seção e menor precedência que a seção anterior.  Observe que você pode clicar em operadores para acessar as páginas detalhadas com exemplos.  
  
 [x \= y](../../../csharp/language-reference/operators/assignment-operator.md) – atribuição.  
  
 [x \+ \= y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – incremento.  Adicione o valor de `y` como o valor de `x`, armazena o resultado em `x`, e o novo valor de retorno.  Se `x` designa um `event`, em seguida, `y` deve ser uma função adequada c\# adiciona como um manipulador de eventos.  
  
 [\-\= x y](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md) – diminuir.  Subtrai o valor de `y` do valor de `x`, armazena o resultado em `x`, e o novo valor de retorno.  Se `x` designa um `event`, em seguida, `y` deve ser uma função adequada c\# Remove como um manipulador de eventos  
  
 [x \* \= y](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md) – atribuição de multiplicação.  Multiplica o valor de `y` como o valor de `x`, armazena o resultado em `x`, e o novo valor de retorno.  
  
 [x \= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – atribuição de divisão.  Divide o valor do `x` pelo valor de `y`, armazena o resultado em `x`, e o novo valor de retorno.  
  
 [x % \= y](../../../csharp/language-reference/operators/modulus-assignment-operator.md) – atribuição de módulo.  Divide o valor do `x` pelo valor de `y`, armazenar o resto no `x`, e o novo valor de retorno.  
  
 [x & \= y](../../../csharp/language-reference/operators/and-assignment-operator.md) – e atribuição.  E o valor de `y` com o valor de `x`, armazena o resultado em `x`, e o novo valor de retorno.  
  
 [x &#124; \= y](../../../csharp/language-reference/operators/or-assignment-operator.md) – atribuição OR.  OU o valor de `y` com o valor de `x`, armazena o resultado em `x`, e o novo valor de retorno.  
  
 [x ^ \= y](../../../csharp/language-reference/operators/xor-assignment-operator.md) – Atribuição XOR.  XOR o valor de `y` com o valor de `x`, armazena o resultado em `x`, e o novo valor de retorno.  
  
 [x \<\< \= y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – atribuição de shift esquerda.  Alterna o valor de `x` para a esquerda `y` locais, armazena o resultado em `x`, e o novo valor de retorno.  
  
 [x \>\> \= y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – atribuição de deslocamento para a direita.  Alterna o valor do `x` direita `y` locais, armazena o resultado em `x`, e o novo valor de retorno.  
  
 [\= \>](../../../csharp/language-reference/operators/lambda-operator.md) – declaração lambda.  
  
## Estouro aritmético  
 Os operadores aritméticos \([\+](../../../csharp/language-reference/operators/addition-operator.md), [\-](../../../csharp/language-reference/operators/subtraction-operator.md), [\*](../../../csharp/language-reference/operators/multiplication-operator.md), [\/](../../../csharp/language-reference/operators/division-operator.md)\) pode produzir resultados que estão fora do intervalo de valores possíveis para o tipo numérico envolvido.  Consulte a seção sobre um operador específico para obter detalhes, mas em geral:  
  
-   Estouro de aritmética de inteiros qualquer lança um <xref:System.OverflowException> ou descarta os bits mais significativos do resultado.  Divisão por zero sempre lança uma `DivideByZeroException`.  
  
-   Divisão por zero ou estouro aritmético de ponto flutuante nunca lança uma exceção, como tipos de ponto flutuante são baseados em IEEE 754 e então tem provisões para representar o infinito e NaN \(não um número\).  
  
-   [Decimal](../../../csharp/language-reference/keywords/decimal.md) estouro aritmético sempre lança uma <xref:System.OverflowException>.  Decimal divisão por zero sempre lança uma <xref:System.DivideByZeroException>.  
  
 Quando ocorre estouro de inteiros, o que acontece depende do contexto de execução, que pode ser [marcado ou desmarcado](../../../csharp/language-reference/keywords/checked-and-unchecked.md).  Em um contexto verificado, uma <xref:System.OverflowException> é lançada.  Em um contexto desmarcado, os bits mais significativos do resultado são descartados e a execução continua.  Assim, c\# oferece a opção de tratamento ou ignorando o estouro.  
  
 Além dos operadores aritméticos, conversões de tipo integral para integral de tipo podem causar estouro, por exemplo, converter um [longo](../../../csharp/language-reference/keywords/long.md) para um [int](../../../csharp/language-reference/keywords/int.md), e estão sujeitos a execução marcada ou desmarcada.  No entanto, operadores bit a bit e operadores shift nunca causam estouro.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [C\#](../../../csharp/csharp.md)   
 [Operadores sobrecarregáveis](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)