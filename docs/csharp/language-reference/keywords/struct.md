---
title: struct (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 7931da2e5f5c493b54eb1f33a1d6f57b38592f6e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399012"
---
# <a name="struct-c-reference"></a>struct (Referência de C#)
O tipo `struct` é um tipo de valor normalmente usado para encapsular pequenos grupos de variáveis relacionadas, tais como coordenadas de um retângulo ou as características de um item em um inventário. O seguinte exemplo mostra uma declaração simples de struct:  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a>Comentários  
 Os structs também podem conter [construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constantes](../../../csharp/programming-guide/classes-and-structs/constants.md), [campos](../../../csharp/programming-guide/classes-and-structs/fields.md), [métodos](../../../csharp/programming-guide/classes-and-structs/methods.md), [propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexadores](../../../csharp/programming-guide/indexers/index.md), [operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [eventos](../../../csharp/programming-guide/events/index.md) e [tipos aninhados](../../../csharp/programming-guide/classes-and-structs/nested-types.md), embora, se vários desses membros forem necessários, você deva considerar tonar seu tipo uma classe.  
  
 Para obter exemplos, consulte [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
 Os structs podem implantar uma interface, mas não podem herdá-la de outra struct. Por esse motivo, os membros de struct não podem ser declarados como `protected`.  
  
 Para obter mais informações, consulte [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="examples"></a>Exemplos  
 Para obter exemplos e mais informações, consulte [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 Para obter exemplos, consulte [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md)  
- [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tipos](../../../csharp/language-reference/keywords/types.md)  
- [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)  
- [class](../../../csharp/language-reference/keywords/class.md)  
- [interface](../../../csharp/language-reference/keywords/interface.md)  
- [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)
