---
title: 'Solucionando problemas: depurando Serviços Windows'
description: Introdução à depuração de serviços do Windows. Quando você depurar um aplicativo de serviço Windows, o serviço e o Windows Service Manager interagirão.
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
ms.openlocfilehash: 935f5dcbd369ba5d723cc0e947ba708afdd590ea
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925534"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="d2f2c-104">Solucionando problemas: depurando Serviços Windows</span><span class="sxs-lookup"><span data-stu-id="d2f2c-104">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="d2f2c-105">Quando você depurar um aplicativo de serviço Windows, o serviço e o **Windows Service Manager** interagirão.</span><span class="sxs-lookup"><span data-stu-id="d2f2c-105">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="d2f2c-106">O **Service Manager** inicia o serviço chamando o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e, em seguida, espera 30 segundos para que o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retorne.</span><span class="sxs-lookup"><span data-stu-id="d2f2c-106">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="d2f2c-107">Se o método não retornar nesse período, o gerenciador mostra um erro indicando que o serviço não pode ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="d2f2c-107">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="d2f2c-108">Ao depurar o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, conforme é descrito em [Como depurar aplicativos de Serviço Windows](how-to-debug-windows-service-applications.md), você precisará estar ciente desse período de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="d2f2c-108">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="d2f2c-109">Se você colocar um ponto de interrupção no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e não entrar nele em até 30 segundos, o gerente não iniciará o serviço.</span><span class="sxs-lookup"><span data-stu-id="d2f2c-109">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f2c-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="d2f2c-110">See also</span></span>

- [<span data-ttu-id="d2f2c-111">Como: Depurar aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="d2f2c-111">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="d2f2c-112">Introdução a aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="d2f2c-112">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
