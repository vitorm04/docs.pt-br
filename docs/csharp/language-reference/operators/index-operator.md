---
title: Operador [] (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 65908bb3bcd8912ef81fc094e5958ae8dc4ae1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286023"
---
# <a name="-operator-c-reference"></a>Operador [] (Referência de C#)
Os colchetes (`[]`) são usados para matrizes, indexadores e atributos. Eles também podem ser usados com ponteiros.  
  
## <a name="remarks"></a>Comentários  
 Um tipo de matriz é um tipo seguido por `[]`:  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 Para acessar um elemento de uma matriz, o índice do elemento desejado é colocado entre colchetes:  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 Uma exceção será lançada se um índice de matriz estiver fora do intervalo.  
  
 O operador de indexação da matriz não pode ser sobrecarregado. No entanto, os tipos podem definir indexadores e propriedades que recebem um ou mais parâmetros. Os parâmetros do indexador são colocados entre colchetes, assim como os índices de matriz, mas os parâmetros do indexador podem ser declarados para serem de qualquer tipo, ao contrário dos índices de matriz, que devem ser integrais.  
  
 Por exemplo, o .NET Framework define um tipo `Hashtable` que associa chaves e valores de tipo arbitrário:  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 Os colchetes também são usados para especificar [Atributos](../../../csharp/programming-guide/concepts/attributes/index.md):  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 Você pode usar colchetes para desindexar um ponteiro:  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 Nenhuma verificação de limites é executada.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)  
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)
