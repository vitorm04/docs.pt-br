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
ms.openlocfilehash: cbedb0051cbb08c2875e145a2bad35ae4d02a74e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053506"
---
# <a name="troubleshooting-debugging-windows-services"></a>Solução de problemas: Depurando serviços Windows
Quando você depurar um aplicativo de serviço Windows, o serviço e o **Windows Service Manager** interagirão. O **Service Manager** inicia o serviço chamando o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e, em seguida, espera 30 segundos para que o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retorne. Se o método não retornar nesse período, o gerenciador mostra um erro indicando que o serviço não pode ser iniciado.  
  
 Ao depurar o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, conforme descrito em [Como: Depurar aplicativos de serviço Windows](how-to-debug-windows-service-applications.md), você precisará estar ciente desse período de 30 segundos. Se você colocar um ponto de interrupção no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e não entrar nele em até 30 segundos, o gerente não iniciará o serviço.  
  
## <a name="see-also"></a>Consulte também

- [Como: Depurar aplicativos do serviço Windows](how-to-debug-windows-service-applications.md)
- [Introdução aos Aplicativos de Serviço Windows](introduction-to-windows-service-applications.md)
