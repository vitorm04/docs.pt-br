---
title: is (Referência de C#)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: c01152d016a852c15ffa1d1c82c16d6795965f31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289211"
---
# <a name="is-c-reference"></a>is (Referência de C#) #

Verifica se um objeto é compatível com um determinado tipo ou (começando com o C# 7.0) testa uma expressão em relação a um padrão.

## <a name="testing-for-type-compatibility"></a>Testando a compatibilidade de tipo ##

A palavra-chave `is` avalia a compatibilidade de tipo em tempo de execução. Ela determina se uma instância de objeto ou o resultado de uma expressão pode ser convertido em um tipo especificado. Ela tem a sintaxe

```csharp
   expr is type
```

em que *expr* é uma expressão que é avaliada como uma instância de algum tipo, e *type* é o nome do tipo no qual o resultado de *expr* será convertido. A instrução `is` será `true` se *expr* não for nulo e o objeto resultante da avaliação da expressão puder ser convertido em *type*; caso contrário, ela retornará `false`.

Por exemplo, o código a seguir determina se `obj` pode ser convertido em uma instância do tipo `Person`:

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

A instrução `is` será verdadeira se:

- *expr* for uma instância do mesmo tipo que *type*.

- *expr* for uma instância de um tipo derivado de *type*. Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.

- *expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*. O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração. O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.

- *expr* é uma instância de um tipo que implementa a interface de *type*.

O exemplo a seguir mostra que a expressão `is` é avaliada como `true` para cada uma dessas conversões.

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

A palavra-chave `is` gera um aviso de tempo de compilação caso seja conhecido que a expressão sempre é `true` ou `false`. Ela considera somente conversões de referência, conversões boxing e conversões unboxing, e não considera conversões definidas pelo usuário ou conversões definidas pelos operadores [implicit](implicit.md) e [explicit](explicit.md) de um tipo. O exemplo a seguir gera avisos porque o resultado da conversão é conhecido em tempo de compilação. Observe que a expressão `is` para conversões de `int` para `long` e `double` retorna falso, pois essas conversões são tratadas pelo operador [implicit](implicit.md).

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr` pode ser qualquer expressão que retorna um valor, com exceção de métodos anônimos e expressões lambda. O exemplo a seguir usa `is` para avaliar o valor retornado de uma chamada de método.   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

Começando com o C# 7.0, você pode usar a correspondência de padrões com o [padrão de tipo](#type) para escrever códigos mais concisos que usam a instrução `is`.

## <a name="pattern-matching-with-is"></a>Correspondência de padrões com `is` ##

Começando com o C# 7.0, as instruções `is` e [switch](../../../csharp/language-reference/keywords/switch.md) permitem a correspondência de padrões. A palavra-chave `is` dá suporte aos seguintes padrões:

- [Padrão de tipo](#type), que testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.

- [Padrão constante](#constant), que testa se uma expressão é avaliada como um valor constante especificado.

- [Padrão var](#var), uma correspondência que sempre é bem-sucedida e vincula o valor de uma expressão a uma nova variável local. 

### <a name="type" /> Padrão de tipo </a>

Ao usar o padrão de tipo para realizar a correspondência de padrões, `is` testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo. Trata-se de uma extensão simples da instrução `is` que habilita a conversão e a avaliação de tipo concisas. A forma geral do padrão de tipo `is` é:

```csharp
   expr is type varname 
```

em que *expr* é uma expressão que é avaliada como uma instância de algum tipo, *type* é o nome do tipo no qual o resultado de *expr* será convertido e *varname* é o objeto no qual o resultado de *expr* será convertido se o teste `is` for `true`. 

A expressão `is` será `true` se qualquer uma das condições seguintes for verdadeira:

- *expr* for uma instância do mesmo tipo que *type*.

- *expr* for uma instância de um tipo derivado de *type*. Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.

- *expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*. O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração. O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.

- *expr* é uma instância de um tipo que implementa a interface de *type*.

Se *exp* for `true` e `is` for usado com uma instrução `if`, *varname* será atribuído e terá escopo local somente dentro da instrução `if`.

O exemplo a seguir usa o padrão de tipo `is` para fornecer a implementação do método <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> de um tipo.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira. O uso da correspondência de padrões de tipo produz código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

O padrão de tipo `is` também produz código mais compacto ao determinar o tipo de um tipo de valor. O exemplo a seguir usa o padrão de tipo `is` para determinar se um objeto é uma instância de `Person` ou `Dog` antes de exibir o valor de uma propriedade adequada. 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

O código equivalente sem correspondência de padrões requer uma atribuição separada que inclui uma conversão explícita.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" /> Padrão constante ###

Ao executar a correspondência de padrões com o padrão constante, `is` testa se uma expressão é igual a uma constante especificada. No C# 6 e em versões anteriores, o padrão constante tem suporte da instrução [switch](switch.md). Começando com o C# 7.0, ele também é compatível com a instrução `is`. A sintaxe é:

```csharp
   expr is constant
```

em que *expr* é a expressão a ser avaliada e *constant* é o valor a ser testado. *constant* pode ser qualquer uma das expressões de constante a seguir: 

- Um valor literal.

- O nome de uma variável `const` declarada.

- Uma constante de enumeração.

A expressão de constante é avaliada da seguinte forma:

- Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).

- Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).  

O exemplo a seguir combina os padrões de tipo e constante para testar se um objeto é uma instância de `Dice` e, caso seja, para determinar se o valor de uma distribuição de dados é 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <a name="var" /> Padrão var </a>

Uma correspondência de padrões com o padrão var sempre terá êxito. Sua sintaxe é

```csharp 
   expr is var varname
```

em que o valor de *expr* sempre é atribuído a uma variável local chamada *varname*. *varname* é uma variável estática do mesmo tipo que *expr*. O exemplo a seguir usa o padrão var para atribuir uma expressão a uma variável chamada `obj`. Em seguida, ele exibe o valor e o tipo de `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Observe que, se *expr* for `null`, a expressão `is` ainda será verdadeira e atribuirá `null` a *varname*. 

# <a name="c-language-specification"></a>Especificação da Linguagem C#
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [typeof](../../../csharp/language-reference/keywords/typeof.md)  
 [as](../../../csharp/language-reference/keywords/as.md)  
 [Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)
