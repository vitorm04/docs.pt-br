---
title: Passando parâmetros de tipo de valor (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: b64968a89f010f3f904d3a281d346d2ddf999e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Passando parâmetros de tipo de valor (Guia de Programação em C#)
Uma variável de [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) contém seus dados diretamente, o que não acontece com uma variável de [tipo de referência](../../../csharp/language-reference/keywords/reference-types.md), que contém uma referência a seus dados. Passar uma variável de tipo de valor para um método por valor significa passar uma cópia da variável para o método. Quaisquer alterações no parâmetro que ocorrem dentro do método não afetam os dados originais armazenados na variável de argumento. Se desejar que o método chamado altere o valor do parâmetro, é necessário passá-lo por referência, usando a palavra-chave [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md). Você também pode usar a palavra-chave [in](../../../csharp/language-reference/keywords/out-parameter-modifier.md) para passar um parâmetro de valor por referência, para evitar a cópia e ainda garantir que o valor não seja alterado. Para simplificar, os exemplos a seguir usam `ref`.  
  
## <a name="passing-value-types-by-value"></a>Passando tipos de valor por valor  
 O exemplo a seguir demonstra a passagem de parâmetros de tipo de valor por valor. A variável `n` é passada por valor para o método `SquareIt`. Quaisquer alterações que ocorrem dentro do método não afetam o valor original da variável.  
  
 [!code-csharp[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]  
  
 A variável `n` é um tipo de valor. Ela contém seus dados, o valor `5`. Quando `SquareIt` é invocado, o conteúdo de `n` é copiado para o parâmetro `x`, que é elevado ao quadrado dentro do método. No entanto, em `Main`, o valor de `n` é o mesmo depois de chamar o método `SquareIt` como era antes. A alteração que ocorre dentro do método afeta apenas a variável local `x`.  
  
## <a name="passing-value-types-by-reference"></a>Passando tipos de valor por referência  
 O exemplo a seguir é o mesmo que o exemplo anterior, exceto que o argumento é passado como um parâmetro `ref`. O valor do argumento subjacente, `n`, é alterado quando `x` é alterado no método.  
  
 [!code-csharp[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]  
  
 Neste exemplo, não é o valor de `n` que é passado; em vez disso, é passada uma referência a `n`. O parâmetro `x` não é um [int](../../../csharp/language-reference/keywords/int.md); é uma referência a um `int`, nesse caso, uma referência a `n`. Portanto, quando `x` é elevado ao quadrado dentro do método, o que é realmente é elevado ao quadrado é aquilo a que `x` se refere, `n`.  
  
## <a name="swapping-value-types"></a>Trocar valores de tipo  
 Um exemplo comum de alteração dos valores de argumentos é um método de troca, em que você passa duas variáveis para o método e o método troca seu conteúdo. É necessário passar os argumentos para o método de troca por referência. Caso contrário, você troca cópias locais dos parâmetros dentro do método e nenhuma alteração ocorre no método de chamada. O exemplo a seguir troca valores inteiros.  
  
 [!code-csharp[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]  
  
 Quando você chama o método `SwapByRef`, use a palavra-chave `ref` na chamada, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Passando parâmetros](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Passando parâmetros de tipo de referência](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)
