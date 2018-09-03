---
title: Palavra-chave checked (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 892b24b0283314f5aded0405df55a93069cf91e2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43404023"
---
# <a name="checked-c-reference"></a>checked (Referência de C#)

A palavra-chave `checked` é usada para habilitar explicitamente a verificação estouro para conversões e operações aritméticas de tipo integral.

Por padrão, uma expressão que contém somente valores constantes causa um erro do compilador se a expressão produzir um valor fora do intervalo do tipo de destino. Se a expressão contiver um ou mais valores não constantes, o compilador não detectará o estouro. Avaliar a expressão atribuída a `i2` no exemplo a seguir não causa um erro do compilador.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Por padrão, essas expressões não constantes não são verificados quanto ao estouro em tempo de execução e não geram exceções de estouro. O exemplo anterior exibe -2,147,483,639 como a soma de dois números inteiros positivos.

A verificação de estouro pode ser habilitada por opções do compilador, configuração do ambiente ou uso da palavra-chave `checked`. Os exemplos a seguir demonstram como usar uma expressão `checked` ou um bloco `checked` para detectar o estouro produzido pela soma anterior no tempo de execução. Os dois exemplos geram uma exceção de estouro.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

A palavra-chave [unchecked](../../../csharp/language-reference/keywords/unchecked.md) pode ser usada para impedir a verificação de estouro.

## <a name="example"></a>Exemplo

Este exemplo mostra como usar `checked` para habilitar a verificação de estouro em tempo de execução.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Checked e Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
