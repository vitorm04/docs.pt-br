---
title: Gerenciamento de energia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 9ac39df43a08f62e50116c61c4bdeda4cd1c8281
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746857"
---
# <a name="power-management-in-windows-forms"></a>Gerenciamento de energia no Windows Forms
Seus aplicativos Windows Forms podem tirar proveito dos recursos de gerenciamento de energia no sistema operacional Windows. Os aplicativos podem monitorar o status de energia de um computador e agir quando ocorre uma alteração de status. Por exemplo, se o aplicativo é executado em um computador portátil, convém desabilitar determinados recursos do seu aplicativo quando a carga da bateria do computador fica abaixo de um determinado nível.  
  
 O .NET Framework fornece um evento de <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> que ocorre sempre que há uma alteração no status de energia, como quando um usuário suspende ou retoma o sistema operacional, ou quando o status da bateria ou o estado de energia CA é alterado. A propriedade <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> da classe <xref:System.Windows.Forms.SystemInformation> pode ser usada para consultar o status atual, conforme mostrado no exemplo de código a seguir.  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Além das enumerações <xref:System.Windows.Forms.BatteryChargeStatus>, a propriedade <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> também contém enumerações para determinar a capacidade da bateria (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) e a porcentagem de carga da bateria (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Você pode usar o método <xref:System.Windows.Forms.Application.SetSuspendState%2A> da <xref:System.Windows.Forms.Application> para colocar um computador em modo de hibernação ou suspensão. Se o argumento `force` for definido para `false`, o sistema operacional transmitirá um evento para todos os aplicativos solicitando permissão para suspender. Se o argumento `disableWakeEvent` é definido para `true`, o sistema operacional desabilita todos os eventos de ativação.  
  
 O exemplo de código a seguir demonstra como colocar um computador em hibernação.  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Veja também

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
