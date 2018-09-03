---
title: delegate (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: 7a5f46d137e22da01b2ab6cd3eee57d66c411e8f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43442727"
---
# <a name="delegate-c-reference"></a>delegate (Referência de C#)

A declaração de um tipo de delegado é semelhante a uma assinatura de método. Ela tem um valor retornado e parâmetros de qualquer tipo:

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

Um `delegate` é um tipo de referência que pode ser usado para encapsular um método nomeado ou anônimo. Representantes são semelhantes a ponteiros de função em C++. No entanto, os representantes são fortemente tipados e seguros. Para aplicativos de representantes, consulte [Representantes](../../../csharp/programming-guide/delegates/index.md) e [Representantes genéricos](../../../csharp/programming-guide/generics/generic-delegates.md).

## <a name="remarks"></a>Comentários

Os representantes são a base dos [Eventos](../../../csharp/programming-guide/events/index.md).

Um delegado pode ser instanciado associando-o a um método nomeado ou anônimo. Para obter mais informações, consulte [Métodos anônimos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) e [Métodos nomeados](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).

O delegado deve ser instanciado com um método ou expressão lambda que tenha um tipo de retorno compatível e parâmetros de entrada. Para obter mais informações sobre o grau de variação permitido na assinatura do método, consulte [Variação em representantes](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Para uso com métodos anônimos, o delegado e o código a ser associado a ele são declarados juntos. As duas formas de instanciar representantes são discutidas nesta seção.

## <a name="example"></a>Exemplo

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)  
- [Delegados](../../../csharp/programming-guide/delegates/index.md)  
- [Eventos](../../../csharp/programming-guide/events/index.md)  
- [Delegados com métodos nomeados vs. métodos anônimos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
- [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
