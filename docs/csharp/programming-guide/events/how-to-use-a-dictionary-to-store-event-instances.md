---
title: 'Como: usar um dicionário para armazenar instâncias de eventos – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 8f0284c5637890f35642346880d035619bc0e1e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560055"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Como: usar um dicionário para armazenar instâncias de eventos (Guia de Programação em C#)
Um uso de `accessor-declarations` é expor muitos eventos sem alocar um campo para cada evento em vez de usar um dicionário para armazenar as instâncias de eventos. Isso só é útil se você tiver muitos eventos, mas espera que a maioria dos eventos não seja implementada.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Eventos](../../../csharp/programming-guide/events/index.md)
- [Delegados](../../../csharp/programming-guide/delegates/index.md)
