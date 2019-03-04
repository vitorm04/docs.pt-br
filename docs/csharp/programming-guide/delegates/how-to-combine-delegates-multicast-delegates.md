---
title: 'Como: combinar delegados (delegados multicast) – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 426b9f91d3e3328522ec5c7ab043d5074ececc43
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970097"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Como: combinar delegados (delegados multicast) (Guia de Programação em C#)
Este exemplo demonstra como criar delegados multicast. Uma propriedade útil de objetos [delegados](../../../csharp/language-reference/keywords/delegate.md) é que vários objetos podem ser atribuídos a uma instância delegada usando o operador `+`. O delegado multicast contém uma lista dos delegados atribuídos. Quando o delegado multicast é chamado, ele invoca os delegados da lista, em ordem. Apenas os delegados do mesmo tipo podem ser combinados.  
  
 O operador `-` pode ser usado para remover um delegado de componente de um delegado multicast.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.MulticastDelegate>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Eventos](../../../csharp/programming-guide/events/index.md)
