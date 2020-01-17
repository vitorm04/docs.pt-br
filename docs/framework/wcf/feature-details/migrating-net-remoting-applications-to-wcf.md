---
title: Migrando aplicativos remotos .NET para o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 1d7edab8ad89660f3384d0ccf556384175c4d5db
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212159"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrando aplicativos remotos .NET para o WCF
**Este tópico é específico para uma tecnologia herdada que é mantida para compatibilidade com versões anteriores com aplicativos existentes e não é recomendada para desenvolvimento novo. Agora, os aplicativos distribuídos devem ser desenvolvidos usando o WCF.**  
  
 Há duas maneiras de aproveitar o WCF com os aplicativos existentes de comunicação remota do .NET: integração e migração. A integração permite que você tenha o .NET Remoting 2,0 e o WCF em execução lado a lado, permitindo que você exponha os mesmos objetos de negócios em ambas as tecnologias simultaneamente, sem a necessidade de modificar seu código .NET Remoting 2,0 existente. A integração requer que você esteja executando o .NET Framework 2,0 ou superior. Se você quiser aproveitar os recursos do WCF e não precisar de compatibilidade de conexão com os sistemas de comunicação remota 2,0, poderá migrar todo o serviço para o WCF. A migração do .NET Remoting 2,0 para o WCF requer alterações na interface do objeto remoto e em suas definições de configuração. Esses dois tópicos são abordados na [comunicação remota com o Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).  
  
## <a name="see-also"></a>Veja também

- [Visão geral conceitual](../../../../docs/framework/wcf/conceptual-overview.md)
