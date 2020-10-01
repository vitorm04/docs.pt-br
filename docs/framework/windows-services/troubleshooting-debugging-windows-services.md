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
ms.openlocfilehash: 5846692fa0d90a62dd569253abbd81aa63b5798d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608888"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="e694a-104">Solucionando problemas: depurando Serviços Windows</span><span class="sxs-lookup"><span data-stu-id="e694a-104">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="e694a-105">Quando você depurar um aplicativo de serviço Windows, o serviço e o **Windows Service Manager** interagirão.</span><span class="sxs-lookup"><span data-stu-id="e694a-105">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="e694a-106">O **Service Manager** inicia o serviço chamando o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e, em seguida, espera 30 segundos para que o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retorne.</span><span class="sxs-lookup"><span data-stu-id="e694a-106">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="e694a-107">Se o método não retornar nesse período, o gerenciador mostra um erro indicando que o serviço não pode ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="e694a-107">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="e694a-108">Ao depurar o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, conforme é descrito em [Como depurar aplicativos de Serviço Windows](how-to-debug-windows-service-applications.md), você precisará estar ciente desse período de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="e694a-108">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="e694a-109">Se você colocar um ponto de interrupção no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e não entrar nele em até 30 segundos, o gerente não iniciará o serviço.</span><span class="sxs-lookup"><span data-stu-id="e694a-109">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e694a-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="e694a-110">See also</span></span>

- [<span data-ttu-id="e694a-111">Como: Depurar aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="e694a-111">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="e694a-112">Introdução a aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="e694a-112">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
