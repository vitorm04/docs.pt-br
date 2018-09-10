---
title: void (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 223db893dd42181c234d9a07c1a1c00af26f0c30
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213920"
---
# <a name="void-c-reference"></a>void (Referência de C#)
Quando usado como o tipo de retorno para um método, `void` especifica que o método não retorna um valor.

`void` não é permitido na lista de parâmetros de um método. Um método que não usa parâmetros e não retorna nenhum valor é declarado da seguinte maneira:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` também é usado em um contexto desprotegido para declarar um ponteiro para um tipo desconhecido. Para obter mais informações, consulte [Tipos de ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void` é um alias para o tipo <xref:System.Void?displayProperty=nameWithType> do .NET Framework.

## <a name="c-language-specification"></a>Especificação da Linguagem C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)  
- [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)  
- [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
