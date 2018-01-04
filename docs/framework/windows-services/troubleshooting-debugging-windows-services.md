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
# <a name="troubleshooting-debugging-windows-services"></a>Solucionando problemas: depurando Serviços Windows
Quando você depurar um aplicativo de serviço do Windows, o serviço e o **Windows Service Manager** interagir. O **do Service Manager** inicia o serviço chamando o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e, em seguida, as esperas de 30 segundos para o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método para retornar. Se o método não retornar nesse período, o Gerenciador mostra um erro se o serviço não pode ser iniciado.  
  
 Quando você depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método conforme descrito em [como: depurar aplicativos de serviço do Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), você deve estar atento esse período de 30 segundos. Se você colocar um ponto de interrupção no <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e não fazer a etapa através dos 30 segundos, o gerente não iniciará o serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Como depurar aplicativos de Serviço Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
