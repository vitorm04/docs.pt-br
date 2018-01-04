---
title: Eventos com propriedade alterada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad22d77043f00ab0caaa6d8b08b6b0a9eef1fed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="property-changed-events"></a>Eventos com propriedade alterada
Se você quiser que o controle envie notificações quando uma propriedade chamada *PropertyName* mudar, defina um evento chamado *PropertyName* `Changed` e um método chamado `On` *PropertyName* `Changed` que gera o evento. A convenção de nomenclatura nos Windows Forms é acrescentar a palavra *Changed* ao nome da propriedade. O tipo de delegado do evento associado para eventos de propriedade alterada é <xref:System.EventHandler>, e o tipo de dados de evento é <xref:System.EventArgs>. A classe base <xref:System.Windows.Forms.Control> define vários eventos de propriedade alterada, como <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>e outros. Para obter informações secundárias sobre eventos, consulte [Eventos](../../../../docs/standard/events/index.md) e [Eventos em controles dos Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).  
  
 Eventos de propriedade alterada são úteis porque permitem que os consumidores de um controle anexem manipuladores de eventos que respondem à alteração. Se o seu controle precisa responder a um evento de propriedade alterada que ele emitirá, substitua o método `On` *PropertyName* `Changed` correspondente em vez de associar um delegado ao evento. Um controle normalmente responde a um evento de propriedade alterada atualizando outras propriedades ou redesenhando a superfície de alguns ou todos os desenhos.  
  
 A exemplo a seguir mostra como o `FlashTrackBar` controle personalizado responde a alguns dos eventos de propriedade alterada que ele herda de <xref:System.Windows.Forms.Control>. Para um exemplo completo, consulte [Como criar um controle dos Windows Forms que mostre o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../../docs/standard/events/index.md)  
 [Eventos em controles do Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Propriedades em controles do Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
