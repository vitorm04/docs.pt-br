---
title: void – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: ce52e4d19335db0e21637b87bbd1589c86c06ae1
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613122"
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

`void` também é usado em um contexto desprotegido para declarar um ponteiro para um tipo desconhecido. Para obter mais informações, consulte [Tipos de ponteiros](../../programming-guide/unsafe-code-pointers/pointer-types.md).

`void` é um alias para o tipo <xref:System.Void?displayProperty=nameWithType> do .NET Framework.

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Tipos de referência](reference-types.md)
- [Tipos de valor](value-types.md)
- [Métodos](../../programming-guide/classes-and-structs/methods.md)
- [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md)