---
title: 'Solucionando problemas: depurando Serviços Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
author: ghogen
ms.openlocfilehash: 0dbbebd14ce0ff5f69a12c256238c7e0a02494cb
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199938"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="45efb-102">Solucionando problemas: depurando Serviços Windows</span><span class="sxs-lookup"><span data-stu-id="45efb-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="45efb-103">Quando você depurar um aplicativo de serviço Windows, o serviço e o **Windows Service Manager** interagirão.</span><span class="sxs-lookup"><span data-stu-id="45efb-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="45efb-104">O **Service Manager** inicia o serviço chamando o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e, em seguida, espera 30 segundos para que o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retorne.</span><span class="sxs-lookup"><span data-stu-id="45efb-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="45efb-105">Se o método não retornar nesse período, o gerenciador mostra um erro indicando que o serviço não pode ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="45efb-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="45efb-106">Ao depurar o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, conforme é descrito em [Como depurar aplicativos de Serviço Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), você precisará estar ciente desse período de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="45efb-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="45efb-107">Se você colocar um ponto de interrupção no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e não entrar nele em até 30 segundos, o gerente não iniciará o serviço.</span><span class="sxs-lookup"><span data-stu-id="45efb-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45efb-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45efb-108">See Also</span></span>  
 [<span data-ttu-id="45efb-109">Como depurar aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="45efb-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="45efb-110">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="45efb-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
