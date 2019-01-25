---
title: Migrando aplicativos remotos .NET para o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 96018b775b858e8ac0d0221135cb5109b0cd81d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509994"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrando aplicativos remotos .NET para o WCF
**Este tópico é específico para uma tecnologia herdada que é mantida para compatibilidade com versões anteriores com aplicativos existentes e não é recomendada para novo desenvolvimento. Aplicativos distribuídos agora devem ser desenvolvidos usando o WCF.**  
  
 Há duas maneiras para tirar proveito do WCF com aplicativos existentes do .NET Remoting: migração e integração. Integração permite que você tenha o .net 2.0 de comunicação remota e do WCF em execução lado a lado, permitindo que você exponha os mesmos objetos de negócios sobre ambas as tecnologias simultaneamente sem ter que modificar seu .net existentes 2.0 de comunicação remota de código. A integração requer que você esteja executando no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 ou superior. Se você quiser tirar proveito dos recursos do WCF e não é necessário para compatibilidade com sistemas de comunicação remota 2.0 de transferência, você pode migrar todo o seu serviço para o WCF. Migração do .NET Remoting 2.0 para o WCF requer alterações a interface do objeto remoto e seus parâmetros de configuração. Esses tópicos são abordados [de comunicação remota para o Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Consulte também
- [Visão geral conceitual](../../../../docs/framework/wcf/conceptual-overview.md)
