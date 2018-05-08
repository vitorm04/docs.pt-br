---
title: Gerenciamento de energia no Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 845cc9c910d63dfc7460bba0d5368b5b1e63efcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="power-management-in-windows-forms"></a>Gerenciamento de energia no Windows Forms
Seus aplicativos Windows Forms podem tirar proveito dos recursos de gerenciamento de energia no sistema operacional Windows. Os aplicativos podem monitorar o status de energia de um computador e agir quando ocorre uma alteração de status. Por exemplo, se o aplicativo é executado em um computador portátil, convém desabilitar determinados recursos do seu aplicativo quando a carga da bateria do computador fica abaixo de um determinado nível.  
  
 O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fornece um <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> evento que ocorre sempre que houver uma alteração no status de energia, como quando um usuário suspende ou reinicia o sistema operacional, ou quando altera o status de energia AC ou o status da bateria. O <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> propriedade o <xref:System.Windows.Forms.SystemInformation> classe pode ser usada para consultar o status atual, conforme mostrado no exemplo de código a seguir.  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Além de <xref:System.Windows.Forms.BatteryChargeStatus> enumerações, o <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> propriedade também contém enumerações para determinar a capacidade da bateria (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) e porcentagem carga da bateria (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Você pode usar o <xref:System.Windows.Forms.Application.SetSuspendState%2A> método o <xref:System.Windows.Forms.Application> para colocar um computador em hibernação ou modo de suspensão. Se o argumento `force` for definido para `false`, o sistema operacional transmitirá um evento para todos os aplicativos solicitando permissão para suspender. Se o argumento `disableWakeEvent` é definido para `true`, o sistema operacional desabilita todos os eventos de ativação.  
  
 O exemplo de código a seguir demonstra como colocar um computador em hibernação.  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
