---
title: Delegados com Métodos Nomeados vs. Métodos anônimos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 68428c097b4fc43617834c684ec6dc9705512597
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363936"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Delegados com Métodos Nomeados vs. Métodos anônimos (Guia de Programação em C#)
Um [delegado](../../../csharp/language-reference/keywords/delegate.md) pode ser associado a um método nomeado. Ao instanciar um delegado usando um método nomeado, o método é passado como um parâmetro, por exemplo:  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 Isso é chamado usando um método nomeado. Os delegados construídos com um método nomeado podem encapsular um método [estático](../../../csharp/language-reference/keywords/static.md) ou um método de instância. Métodos nomeados são a única maneira de instanciar um delegado nas versões anteriores do C#. No entanto, em uma situação em que a criação de um novo método for uma sobrecarga indesejada, o C# permite instanciar um delegado e especificar imediatamente um bloco de código que esse delegado processará quando for chamado. O bloco pode conter uma expressão lambda ou um método anônimo. Para obter mais informações, consulte [Funções Anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Comentários  
 O método passado como parâmetro delegado deve ter a mesma assinatura da declaração delegada.  
  
 Uma instância de delegado pode encapsular o método estático ou de instância.  
  
 Embora o delegado possa usar um parâmetro [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), não é recomendável utilizá-lo com delegados de evento multicast, pois não é possível saber qual delegado será chamado.  
  
## <a name="example-1"></a>Exemplo 1  
 Este é um exemplo simples de declaração usando um delegado. Observe que tanto o delegado, `Del` e o método associado, `MultiplyNumbers`, têm a mesma assinatura  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>Exemplo 2  
 No exemplo a seguir, um delegado é mapeado para métodos estáticos e de instância e retorna informações específicas sobre cada um.  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Delegados](../../../csharp/programming-guide/delegates/index.md)
- [Como: combinar delegados (delegados multicast)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
- [Eventos](../../../csharp/programming-guide/events/index.md)
