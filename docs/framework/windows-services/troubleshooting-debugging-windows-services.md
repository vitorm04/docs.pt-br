---
title: 'Solução de problemas: Depurando serviços Windows'
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
ms.openlocfilehash: 0552fc005a25e83065bb44e425770f9cef84f71b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082575"
---
# <a name="troubleshooting-debugging-windows-services"></a>Solução de problemas: Depurando serviços Windows
Quando você depurar um aplicativo de serviço Windows, o serviço e o **Windows Service Manager** interagirão. O **Service Manager** inicia o serviço chamando o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e, em seguida, espera 30 segundos para que o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retorne. Se o método não retornar nesse período, o gerenciador mostra um erro indicando que o serviço não pode ser iniciado.  
  
 Ao depurar o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, conforme descrito em [Como: Depurar aplicativos de serviço Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), você precisará estar ciente desse período de 30 segundos. Se você colocar um ponto de interrupção no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e não entrar nele em até 30 segundos, o gerente não iniciará o serviço.  
  
## <a name="see-also"></a>Consulte também

- [Como: Depurar aplicativos do serviço Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
