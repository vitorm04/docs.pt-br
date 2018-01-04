---
title: "Solucionando problemas: depurando Serviços Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: f38e65e93d4e6668795bf254573993d5100e2328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="731cb-102">Solucionando problemas: depurando Serviços Windows</span><span class="sxs-lookup"><span data-stu-id="731cb-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="731cb-103">Quando você depurar um aplicativo de serviço do Windows, o serviço e o **Windows Service Manager** interagir.</span><span class="sxs-lookup"><span data-stu-id="731cb-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="731cb-104">O **do Service Manager** inicia o serviço chamando o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e, em seguida, as esperas de 30 segundos para o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método para retornar.</span><span class="sxs-lookup"><span data-stu-id="731cb-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="731cb-105">Se o método não retornar nesse período, o Gerenciador mostra um erro se o serviço não pode ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="731cb-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="731cb-106">Quando você depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método conforme descrito em [como: depurar aplicativos de serviço do Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), você deve estar atento esse período de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="731cb-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="731cb-107">Se você colocar um ponto de interrupção no <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e não fazer a etapa através dos 30 segundos, o gerente não iniciará o serviço.</span><span class="sxs-lookup"><span data-stu-id="731cb-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="731cb-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="731cb-108">See Also</span></span>  
 [<span data-ttu-id="731cb-109">Como depurar aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="731cb-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="731cb-110">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="731cb-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
