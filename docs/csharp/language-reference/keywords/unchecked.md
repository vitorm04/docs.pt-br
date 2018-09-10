---
title: unchecked (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: daccd7916a9f81f26f468ab0f64833d9537cff8e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44206004"
---
# <a name="unchecked-c-reference"></a>unchecked (Referência de C#)
A palavra-chave `unchecked` é usada para suprimir a verificação estouro para conversões e operações aritméticas de tipo integral.  
  
 Em um contexto não verificado, se uma expressão produzir um valor que está fora do intervalo do tipo de destino, o estouro não será sinalizado. Por exemplo, como o cálculo no exemplo a seguir é realizado em uma expressão ou bloco `unchecked`, o fato de o resultado ser muito grande para um inteiro é ignorado e `int1` recebe a atribuição do valor -2.147.483.639.  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 Se o ambiente `unchecked` for removido, ocorrerá um erro de compilação. O estouro pode ser detectado em tempo de compilação porque todos os termos da expressão são constantes.  
  
 Expressões que contêm termos não constantes não são verificadas por padrão em tempo de compilação e tempo de execução. Consulte [checked](../../../csharp/language-reference/keywords/checked.md) para obter informações sobre como habilitar um ambiente verificado.  
  
 Como a verificação de estouro leva tempo, o uso de código não verificado em situações em que não há nenhum risco de estouro pode melhorar o desempenho. No entanto, se o estouro for uma possibilidade, um ambiente verificado deverá ser usado.  
  
## <a name="example"></a>Exemplo  
 Esse exemplo mostra como usar a palavra-chave `unchecked`.  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Checked e Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [checked](../../../csharp/language-reference/keywords/checked.md)
