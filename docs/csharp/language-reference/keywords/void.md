---
title: "void (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
dev_langs:
- CSharp
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 15
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
ms.openlocfilehash: d1bd7ece5ce3b558c616a4eb3a4668c3c13eb1cb
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

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

`void` é um alias para o tipo <xref:System.Void?displayProperty=fullName> do .NET Framework.

## <a name="c-language-specification"></a>Especificação da Linguagem C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos de Referência](../../../csharp/language-reference/keywords/reference-types.md)   
 [Tipos de Valor](../../../csharp/language-reference/keywords/value-types.md)   
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)

