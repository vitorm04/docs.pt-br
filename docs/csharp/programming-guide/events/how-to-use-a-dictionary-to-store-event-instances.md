---
title: 'Como: usar um dicionário para armazenar instâncias de eventos – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 819c81aed3a6f09a20e51285058dcc77749dd33a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245130"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Como: usar um dicionário para armazenar instâncias de eventos (Guia de Programação em C#)
Um uso de `accessor-declarations` é expor muitos eventos sem alocar um campo para cada evento em vez de usar um dicionário para armazenar as instâncias de eventos. Isso só é útil se você tiver muitos eventos, mas espera que a maioria dos eventos não seja implementada.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Eventos](../../../csharp/programming-guide/events/index.md)  
- [Delegados](../../../csharp/programming-guide/delegates/index.md)
