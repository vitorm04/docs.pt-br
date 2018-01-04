---
title: "Solução de problemas: Ganho de aplicativo de serviço &#39; instalar t"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 43c973d83d2d1b614cf0ce49ba8d4af24123b47e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-service-application-won39t-install"></a>Solução de problemas: Ganho de aplicativo de serviço &#39; instalar t
Se seu aplicativo de serviço não será instalado corretamente, verifique para certificar-se de que o <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> propriedade para a classe de serviço é definida com o mesmo valor, conforme é mostrado no instalador do serviço. O valor deve ser o mesmo em ambas as instâncias para que o serviço seja instalado corretamente.  
  
> [!NOTE]
>  Você também pode examinar os logs de instalação para obter comentários sobre o processo de instalação.  
  
 Você também deve verificar para determinar se você tiver outro serviço com o mesmo nome já está instalado. Nomes de serviço devem ser exclusivos para a instalação tenha êxito.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
