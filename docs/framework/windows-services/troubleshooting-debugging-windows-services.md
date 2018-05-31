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
manager: douge
ms.openlocfilehash: 77a0c19c2da2d1886beaf396650fa024fc1243a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510131"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="5a384-102">Solucionando problemas: depurando Serviços Windows</span><span class="sxs-lookup"><span data-stu-id="5a384-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="5a384-103">Quando você depurar um aplicativo de serviço Windows, o serviço e o **Windows Service Manager** interagirão.</span><span class="sxs-lookup"><span data-stu-id="5a384-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="5a384-104">O **Service Manager** inicia o serviço chamando o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e, em seguida, espera 30 segundos para que o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retorne.</span><span class="sxs-lookup"><span data-stu-id="5a384-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="5a384-105">Se o método não retornar nesse período, o gerenciador mostra um erro indicando que o serviço não pode ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="5a384-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="5a384-106">Ao depurar o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, conforme é descrito em [Como depurar aplicativos de Serviço Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), você precisará estar ciente desse período de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="5a384-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="5a384-107">Se você colocar um ponto de interrupção no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e não entrar nele em até 30 segundos, o gerente não iniciará o serviço.</span><span class="sxs-lookup"><span data-stu-id="5a384-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a384-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a384-108">See Also</span></span>  
 [<span data-ttu-id="5a384-109">Como depurar aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="5a384-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="5a384-110">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="5a384-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
