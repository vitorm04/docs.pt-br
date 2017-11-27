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
ms.openlocfilehash: 51c28f6e9b6fa2974fb9861716b2c9fc2a38fe1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="b60a9-102">Solucionando problemas: depurando Serviços Windows</span><span class="sxs-lookup"><span data-stu-id="b60a9-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="b60a9-103">Quando você depurar um aplicativo de serviço do Windows, o serviço e o **Windows Service Manager** interagir.</span><span class="sxs-lookup"><span data-stu-id="b60a9-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="b60a9-104">O **do Service Manager** inicia o serviço chamando o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e, em seguida, as esperas de 30 segundos para o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método para retornar.</span><span class="sxs-lookup"><span data-stu-id="b60a9-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="b60a9-105">Se o método não retornar nesse período, o Gerenciador mostra um erro se o serviço não pode ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="b60a9-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="b60a9-106">Quando você depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método conforme descrito em [como: depurar aplicativos de serviço do Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), você deve estar atento esse período de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="b60a9-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="b60a9-107">Se você colocar um ponto de interrupção no <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e não fazer a etapa através dos 30 segundos, o gerente não iniciará o serviço.</span><span class="sxs-lookup"><span data-stu-id="b60a9-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b60a9-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b60a9-108">See Also</span></span>  
 [<span data-ttu-id="b60a9-109">Como: depurar aplicativos de serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="b60a9-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="b60a9-110">Introdução aos aplicativos de serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="b60a9-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
