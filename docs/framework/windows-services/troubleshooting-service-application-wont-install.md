---
title: 'Solução de problemas: Ganho de aplicativo de serviço&#39;instalação t'
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
manager: douge
ms.openlocfilehash: 1f3e5674f9a52627efdc24d6c70c0ab16dcdbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-service-application-won39t-install"></a>Solução de problemas: Ganho de aplicativo de serviço&#39;instalação t
Se seu aplicativo de serviço não será instalado corretamente, verifique para certificar-se de que o <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> propriedade para a classe de serviço é definida com o mesmo valor, conforme é mostrado no instalador do serviço. O valor deve ser o mesmo em ambas as instâncias para que o serviço seja instalado corretamente.  
  
> [!NOTE]
>  Você também pode examinar os logs de instalação para obter comentários sobre o processo de instalação.  
  
 Você também deve verificar para determinar se você tiver outro serviço com o mesmo nome já está instalado. Nomes de serviço devem ser exclusivos para a instalação tenha êxito.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
