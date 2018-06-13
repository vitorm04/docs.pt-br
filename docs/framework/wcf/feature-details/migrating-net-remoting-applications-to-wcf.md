---
title: Migrando aplicativos remotos .NET para o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 53f63352503a48ee849580e676b5fe98f3dcf2cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492483"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrando aplicativos remotos .NET para o WCF
**Este tópico é específico para uma tecnologia herdada que é mantida para compatibilidade com aplicativos existentes e não é recomendada para novo desenvolvimento. Aplicativos distribuídos agora devem ser desenvolvidos usando o WCF.**  
  
 Há duas maneiras para tirar proveito do WCF com aplicativos existentes de .NET Remoting: migração e integração. A integração permite que o .net 2.0 de comunicação remota e WCF em execução lado a lado, permitindo que você exponha os mesmos objetos de negócios em ambas as tecnologias simultaneamente sem a necessidade de modificar seu .net existente 2.0 de comunicação remota de código. Integração exige que você está executando [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 ou superior. Se você quiser tirar proveito dos recursos do WCF e não é necessário durante a transmissão de compatibilidade com sistemas de comunicação remota 2.0, você pode migrar todo o seu serviço para o WCF. Migração de comunicação remota do .NET 2.0 para WCF requer alterações para a interface do objeto remoto e suas configurações. Ambos esses tópicos são abordados em [de comunicação remota para o Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral conceitual](../../../../docs/framework/wcf/conceptual-overview.md)
