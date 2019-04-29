---
title: Eventos com propriedade alterada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: cabfd9e799288a332a0b2f96140f5f1cc328508b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755422"
---
# <a name="property-changed-events"></a>Eventos com propriedade alterada
Se você quiser que o controle envie notificações quando uma propriedade chamada *PropertyName* mudar, defina um evento chamado *PropertyName* `Changed` e um método chamado `On` *PropertyName* `Changed` que gera o evento. A convenção de nomenclatura nos Windows Forms é acrescentar a palavra *Changed* ao nome da propriedade. É o tipo de delegado do evento associado para eventos de propriedade alterada <xref:System.EventHandler>, e o tipo de dados de evento é <xref:System.EventArgs>. A classe base <xref:System.Windows.Forms.Control> define muitos eventos com propriedade alterada, como <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>e outros. Para obter informações secundárias sobre eventos, consulte [Eventos](../../../standard/events/index.md) e [Eventos em controles dos Windows Forms](events-in-windows-forms-controls.md).  
  
 Eventos de propriedade alterada são úteis porque permitem que os consumidores de um controle anexem manipuladores de eventos que respondem à alteração. Se o seu controle precisa responder a um evento de propriedade alterada que ele emitirá, substitua o método `On` *PropertyName* `Changed` correspondente em vez de associar um delegado ao evento. Um controle normalmente responde a um evento de propriedade alterada atualizando outras propriedades ou redesenhando a superfície de alguns ou todos os desenhos.  
  
 A exemplo a seguir mostra como o `FlashTrackBar` controle personalizado responde a alguns dos eventos de propriedade alterada que herda de <xref:System.Windows.Forms.Control>. Para o exemplo completo, consulte [como: Criar um controle de formulários do Windows que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Eventos](../../../standard/events/index.md)
- [Eventos em controles do Windows Forms](events-in-windows-forms-controls.md)
- [Propriedades em controles do Windows Forms](properties-in-windows-forms-controls.md)
