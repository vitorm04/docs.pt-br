---
title: Migrando aplicativos remotos .NET para o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 3f5556eeaf56ac48dd4f1d578ed2e66b90415677
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422939"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrando aplicativos remotos .NET para o WCF
**Este tópico é específico para uma tecnologia herdada que é mantida para compatibilidade com versões anteriores com aplicativos existentes e não é recomendada para novo desenvolvimento. Aplicativos distribuídos agora devem ser desenvolvidos usando o WCF.**  
  
 Há duas maneiras para tirar proveito do WCF com aplicativos existentes do .NET Remoting: migração e integração. Integração permite que você tenha o .net 2.0 de comunicação remota e do WCF em execução lado a lado, permitindo que você exponha os mesmos objetos de negócios sobre ambas as tecnologias simultaneamente sem ter que modificar seu .net existentes 2.0 de comunicação remota de código. A integração requer que você esteja executando no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 ou superior. Se você quiser tirar proveito dos recursos do WCF e não é necessário para compatibilidade com sistemas de comunicação remota 2.0 de transferência, você pode migrar todo o seu serviço para o WCF. Migração do .NET Remoting 2.0 para o WCF requer alterações a interface do objeto remoto e seus parâmetros de configuração. Esses tópicos são abordados [de comunicação remota para o Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral conceitual](../../../../docs/framework/wcf/conceptual-overview.md)
