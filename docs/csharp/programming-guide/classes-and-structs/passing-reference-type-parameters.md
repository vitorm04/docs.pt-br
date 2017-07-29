---
title: "Passando parâmetros de tipo de referência (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3f57dc9f0de6fae6da3ec8e6e6cfdc3a21baeaea
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Passando parâmetros de tipo de referência (Guia de Programação em C#)
Uma variável de um [tipo de referência](../../../csharp/language-reference/keywords/reference-types.md) não contém seus dados diretamente; ela contém uma referência a seus dados. Quando você passa um parâmetro de tipo de referência por valor, é possível alterar os dados apontados por referência, como o valor de um membro de classe. No entanto, não é possível alterar o valor de referência em si; ou seja, não é possível usar a mesma referência para alocar memória para uma nova classe e a manter fora do bloco. Para fazer isso, passe o parâmetro usando a palavra-chave [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md). Para simplificar, os exemplos a seguir usam `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Passando tipos de referência por valor  
 O exemplo a seguir demonstra a passagem de um parâmetro de tipo de referência, `arr`, por valor, para um método, `Change`. Como o parâmetro é uma referência a `arr`, é possível alterar os valores dos elementos da matriz. No entanto, a tentativa de reatribuir o parâmetro para um local diferente de memória só funciona dentro do método e não afeta a variável original, `arr`.  
  
 [!code-cs[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 No exemplo anterior, a matriz, `arr`, que é um tipo de referência, é passada para o método sem o parâmetro `ref`. Nesse caso, uma cópia da referência, que aponta para `arr`, é passada para o método. A saída mostra que é possível para o método alterar o conteúdo de um elemento de matriz, nesse caso de `1` para `888`. No entanto, alocar uma nova parte da memória usando o operador [new](../../../csharp/language-reference/keywords/new.md) dentro do método `Change` faz a variável `pArray` referenciar uma nova matriz. Portanto, quaisquer alterações realizadas depois disso não afetarão a matriz original, `arr`, criada dentro de `Main`. Na verdade, duas matrizes são criadas neste exemplo, uma dentro de `Main` e outra dentro do método `Change`.  
  
## <a name="passing-reference-types-by-reference"></a>Passando tipos de referência por referência  
 O exemplo a seguir é o mesmo que o exemplo anterior, exceto que a palavra-chave `ref` é adicionada ao cabeçalho e à chamada do método. Quaisquer alterações que ocorrem no método afetam a variável original no programa de chamada.  
  
 [!code-cs[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 Todas as alterações que ocorrem dentro do método afetam a matriz original em `Main`. Na verdade, a matriz original é realocada usando o operador `new`. Portanto, depois de chamar o método `Change`, qualquer referência a `arr` aponta para a matriz de cinco elementos, criada no método `Change`.  
  
## <a name="swapping-two-strings"></a>Trocando duas cadeias de caracteres  
 Trocar cadeias de caracteres é um bom exemplo de passar parâmetros de tipo de referência por referência. No exemplo, duas cadeias de caracteres, `str1` e `str2`, são inicializadas em `Main` e passadas para o método `SwapStrings` como parâmetros modificado pela palavra-chave `ref`. As duas cadeias de caracteres são trocadas dentro do método e dentro de `Main` também.  
  
 [!code-cs[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 Neste exemplo, os parâmetros precisam ser passados por referência para afetar as variáveis no programa de chamada. Se você remover a palavra-chave `ref` do cabeçalho de método e da chamada de método, nenhuma alteração ocorrerá no programa de chamada.  
  
 Para obter mais informações sobre cadeias de caracteres, consulte [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Passando Parâmetros](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)

