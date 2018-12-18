---
title: Tipos de ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 5474d179005742c610d29ccd9dac7bf1dc94c9d2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239395"
---
# <a name="pointer-types-c-programming-guide"></a>Tipos de ponteiro (Guia de Programação em C#)

Em um contexto inseguro, um tipo pode ser de ponteiro, valor ou referência. Uma declaração de tipo de ponteiro usa uma das seguintes formas:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

O tipo especificado antes do `*` em um tipo de ponteiro é chamado de **tipo referent**. Qualquer um dos tipos a seguir pode ser do tipo referent:

- Qualquer tipo integral: [sbyte](../../language-reference/keywords/sbyte.md), [byte](../../language-reference/keywords/byte.md), [short](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [long](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).
- Qualquer tipo de ponto flutuante: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).
- [char](../../language-reference/keywords/char.md).
- [bool](../../language-reference/keywords/bool.md).
- [decimal](../../language-reference/keywords/decimal.md).
- Qualquer tipo [enum](../../language-reference/keywords/enum.md).
- Qualquer tipo de ponteiro. Isso permite expressões como `void**`.
- Qualquer struct definido pelo usuário que contenha somente campos de tipos não gerenciados.

Os tipos de ponteiro não são herdados de [objeto](../../language-reference/keywords/object.md) e não há nenhuma conversão entre tipos de ponteiro e `object`. Além disso, as conversões boxing e unboxing não oferecem suporte a ponteiros. No entanto, você pode converter entre diferentes tipos de ponteiro e tipos de ponteiro e tipos integrais.

Quando você designa vários ponteiros na mesma declaração, o asterisco (*) é escrito junto apenas com o tipo subjacente; ele não é usado como um prefixo para cada nome de ponteiro. Por exemplo:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Um ponteiro não pode apontar para uma referência ou um [struct](../../language-reference/keywords/struct.md) que contenha referências, pois uma referência de objeto pode ser coletada como lixo mesmo se um ponteiro estiver apontando para ela. O coletor de lixo não acompanha se um objeto está sendo apontado por qualquer tipo de ponteiro.

O valor da variável de ponteiro do tipo `myType*` é o endereço de uma variável do tipo `myType`. Estes são exemplos de declarações de tipos de ponteiro:

|Exemplo|Descrição|
|-------------|-----------------|
|`int* p`|`p` é um ponteiro para um inteiro.|
|`int** p`|`p` é um ponteiro para um ponteiro para um inteiro.|
|`int*[] p`|`p` é uma matriz unidimensional de ponteiros para inteiros.|
|`char* p`|`p` é um ponteiro para um caractere.|
|`void* p`|`p` é um ponteiro para um tipo desconhecido.|

O operador de indireção de ponteiro * pode ser usado para acessar o conteúdo no local apontado pela variável de ponteiro. Por exemplo, considere a seguinte declaração:

```csharp
int* myVariable;
```

A expressão `*myVariable` denota a variável `int` encontrada no endereço contido em `myVariable`.

Há vários exemplos de ponteiros nos tópicos [Instrução fixed](../../language-reference/keywords/fixed-statement.md) e [Conversões de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-conversions.md). O exemplo a seguir usa a palavra-chave `unsafe` e a instrução `fixed` e mostra como incrementar um ponteiro interior.  Você pode colar esse código na função principal de um aplicativo de console para executá-lo. Estes exemplos precisam ser compilados com o conjunto de opções do compilador [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Você não pode aplicar o operador de indireção para um ponteiro do tipo `void*`. No entanto, você pode usar uma conversão para converter um ponteiro nulo em qualquer outro tipo de ponteiro e vice-versa.

Um ponteiro pode ser `null`. Aplicar o operador de indireção a um ponteiro nulo causa um comportamento definido por implementação.

Passar ponteiros entre métodos pode causar um comportamento indefinido. Considere usar um método que retorne um ponteiro para uma variável local por meio de um parâmetro `in`, `out` ou `ref`, ou como o resultado da função. Se o ponteiro foi definido em um bloco fixo, a variável à qual ele aponta não pode mais ser corrigida.

A tabela a seguir lista os operadores e as instruções que podem operar em ponteiros em um contexto inseguro:

|Operador/Instrução|Use|
|-------------------------|---------|
|*|Executa indireção de ponteiro.|
|->|Acessa um membro de um struct através de um ponteiro.|
|[]|Indexa um ponteiro.|
|`&`|Obtém o endereço de uma variável.|
|++ e --|Incrementa e decrementa ponteiros.|
|+ e -|Executa aritmética de ponteiros.|
|==, !=, \<, >, \<= e >=|Compara ponteiros.|
|`stackalloc`|Aloca memória na pilha.|
|Instrução `fixed`|Corrige temporariamente uma variável para que seu endereço possa ser encontrado.|

## <a name="c-language-specification"></a>Especificação da Linguagem C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)  
- [Código não seguro e ponteiros](index.md)  
- [Conversões de ponteiro](pointer-conversions.md)  
- [Expressões de ponteiro](pointer-expressions.md)  
- [Tipos](../../language-reference/keywords/types.md)  
- [unsafe](../../language-reference/keywords/unsafe.md)  
- [Instrução fixed](../../language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../language-reference/keywords/stackalloc.md)  
- [Conversões boxing e unboxing](../types/boxing-and-unboxing.md)
