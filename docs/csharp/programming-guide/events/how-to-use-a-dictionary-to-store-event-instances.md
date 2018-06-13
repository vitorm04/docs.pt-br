---
title: Como usar um dicionário para armazenar instâncias de eventos (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 97a7b0f168e4a1c81ec396f42b731dabb45b3516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327210"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Como usar um dicionário para armazenar instâncias de eventos (Guia de Programação em C#)
Um uso de `accessor-declarations` é expor muitos eventos sem alocar um campo para cada evento em vez de usar um dicionário para armazenar as instâncias de eventos. Isso só é útil se você tiver muitos eventos, mas espera que a maioria dos eventos não seja implementada.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Eventos](../../../csharp/programming-guide/events/index.md)  
 [Delegados](../../../csharp/programming-guide/delegates/index.md)
