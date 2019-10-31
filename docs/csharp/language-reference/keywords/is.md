---
title: is – Referência de C#
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: a04105137fad7cd3a25b869c3aa7fcbe91ed20ab
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566313"
---
# <a name="is-c-reference"></a>is (Referência de C#)

O operador `is` verifica se o resultado de uma expressão é compatível com um tipo fornecido ou (a partir do C# 7.0) testa uma expressão em relação a um padrão. Saiba mais sobre o operador `is` de teste de tipo na seção [operador is](../operators/type-testing-and-cast.md#is-operator) do artigo [Operadores cast e teste de tipo](../operators/type-testing-and-cast.md).

## <a name="pattern-matching-with-is"></a>Correspondência de padrões com `is`

Começando com o C# 7.0, as instruções `is` e [switch](switch.md) permitem a correspondência de padrões. A palavra-chave `is` dá suporte aos seguintes padrões:

- [Padrão de tipo](#type-pattern), que testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.

- [Padrão constante](#constant-pattern), que testa se uma expressão é avaliada como um valor constante especificado.

- [Padrão var](#var-pattern), uma correspondência que sempre é bem-sucedida e vincula o valor de uma expressão a uma nova variável local.

### <a name="type-pattern"></a>Padrão de tipo

Ao usar o padrão de tipo para realizar a correspondência de padrões, `is` testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo. Trata-se de uma extensão simples da instrução `is` que habilita a conversão e a avaliação de tipo concisas. A forma geral do padrão de tipo `is` é:

```csharp
   expr is type varname
```

em que *expr* é uma expressão que é avaliada como uma instância de algum tipo, *type* é o nome do tipo no qual o resultado de *expr* será convertido e *varname* é o objeto no qual o resultado de *expr* será convertido se o teste `is` for `true`. 

A expressão `is` será `true` se *expr* não for `null` e qualquer um dos seguintes for verdadeiro:

- *expr* for uma instância do mesmo tipo que *type*.

- *expr* for uma instância de um tipo derivado de *type*. Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.

- *expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*. O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração. O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.

- *expr* é uma instância de um tipo que implementa a interface de *type*.

A partir do C# 7.1, *expr* pode ter um tipo de tempo de compilação definido por um parâmetro de tipo genérico e suas restrições.

Se *expr* for `true` e `is` for usado com uma instrução `if`, *varname* será atribuído somente dentro da instrução `if`. O escopo de *varname* é da expressão `is` até o final do bloco que envolve a instrução `if`. Usar *varname* em qualquer outro local gera um erro em tempo de compilação para o uso de uma variável que não foi atribuída.

O exemplo a seguir usa o padrão de tipo `is` para fornecer a implementação do método <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> de um tipo.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira. O uso da correspondência de padrões de tipo produz código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

O padrão de tipo `is` também produz código mais compacto ao determinar o tipo de um tipo de valor. O exemplo a seguir usa o padrão de tipo `is` para determinar se um objeto é uma instância de `Person` ou `Dog` antes de exibir o valor de uma propriedade adequada.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

O código equivalente sem correspondência de padrões requer uma atribuição separada que inclui uma conversão explícita.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Padrão de constante

Ao executar a correspondência de padrões com o padrão constante, `is` testa se uma expressão é igual a uma constante especificada. No C# 6 e em versões anteriores, o padrão constante tem suporte da instrução [switch](switch.md). A partir do C# 7.0, ele também é compatível com a instrução `is`. A sintaxe é:

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

É possível verificar em busca de `null` usando o padrão de constante. A palavra-chave `null` é compatível com a instrução `is`. A sintaxe é:

```csharp
   expr is null
```

O exemplo a seguir demonstra uma comparação de verificações de `null`:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>Padrão var

O padrão `var` é um catch-all para qualquer tipo ou valor. O valor de *expr* é sempre atribuído a uma variável local do mesmo tipo que o tipo de tempo de compilação de *expr*. O resultado da expressão `is` é sempre `true`. A sintaxe é:

```csharp
   expr is var varname
```

O exemplo a seguir usa o padrão var para atribuir uma expressão a uma variável chamada `obj`. Em seguida, ele exibe o valor e o tipo de `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a>Especificação da linguagem C#
  
Para saber mais, confira a seção [O operador is](~/_csharplang/spec/expressions.md#the-is-operator) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md) e as seguintes propostas da linguagem C#:

- [Correspondência de padrões](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Correspondência de padrões com genéricos](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Palavras-chave do C#](index.md)
- [Operadores cast e teste de tipo](../operators/type-testing-and-cast.md)
