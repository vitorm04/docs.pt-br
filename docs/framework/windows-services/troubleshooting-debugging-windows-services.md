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
# <a name="troubleshooting-debugging-windows-services"></a>Solucionando problemas: depurando Serviços Windows
Quando você depurar um aplicativo de serviço do Windows, o serviço e o **Windows Service Manager** interagir. O **do Service Manager** inicia o serviço chamando o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e, em seguida, as esperas de 30 segundos para o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método para retornar. Se o método não retornar nesse período, o Gerenciador mostra um erro se o serviço não pode ser iniciado.  
  
 Quando você depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método conforme descrito em [como: depurar aplicativos de serviço do Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), você deve estar atento esse período de 30 segundos. Se você colocar um ponto de interrupção no <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e não fazer a etapa através dos 30 segundos, o gerente não iniciará o serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Como: depurar aplicativos de serviço do Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Introdução aos aplicativos de serviço do Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
