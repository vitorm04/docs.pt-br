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
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="2b8d4-102">Gerenciamento de energia no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b8d4-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="2b8d4-103">Seus aplicativos Windows Forms podem tirar proveito dos recursos de gerenciamento de energia no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="2b8d4-104">Os aplicativos podem monitorar o status de energia de um computador e agir quando ocorre uma alteração de status.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="2b8d4-105">Por exemplo, se o aplicativo é executado em um computador portátil, convém desabilitar determinados recursos do seu aplicativo quando a carga da bateria do computador fica abaixo de um determinado nível.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="2b8d4-106">O .NET Framework fornece um evento de <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> que ocorre sempre que há uma alteração no status de energia, como quando um usuário suspende ou retoma o sistema operacional, ou quando o status da bateria ou o estado de energia CA é alterado.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-106">The .NET Framework provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="2b8d4-107">A propriedade <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> da classe <xref:System.Windows.Forms.SystemInformation> pode ser usada para consultar o status atual, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="2b8d4-108">Além das enumerações <xref:System.Windows.Forms.BatteryChargeStatus>, a propriedade <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> também contém enumerações para determinar a capacidade da bateria (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) e a porcentagem de carga da bateria (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span><span class="sxs-lookup"><span data-stu-id="2b8d4-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="2b8d4-109">Você pode usar o método <xref:System.Windows.Forms.Application.SetSuspendState%2A> da <xref:System.Windows.Forms.Application> para colocar um computador em modo de hibernação ou suspensão.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="2b8d4-110">Se o argumento `force` for definido para `false`, o sistema operacional transmitirá um evento para todos os aplicativos solicitando permissão para suspender.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="2b8d4-111">Se o argumento `disableWakeEvent` é definido para `true`, o sistema operacional desabilita todos os eventos de ativação.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="2b8d4-112">O exemplo de código a seguir demonstra como colocar um computador em hibernação.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2b8d4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b8d4-113">See also</span></span>

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
