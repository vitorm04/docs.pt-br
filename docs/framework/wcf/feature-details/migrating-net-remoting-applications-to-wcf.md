---
title: Migrando aplicativos remotos .NET para o WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 240901f4fa04a2468d5964821680506ea117bf7f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrando aplicativos remotos .NET para o WCF
**Este tópico é específico para uma tecnologia herdada que é mantida para compatibilidade com aplicativos existentes e não é recomendada para novo desenvolvimento. Aplicativos distribuídos agora devem ser desenvolvidos usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**  
  
 Há duas maneiras para tirar proveito dos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com aplicativos existentes de .NET Remoting: migração e integração. A integração permite que o .net 2.0 de comunicação remota e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em execução lado a lado, que ajuda você expõe os mesmos objetos de negócios em ambas as tecnologias simultaneamente sem a necessidade de modificar seu .net existentes 2.0 de comunicação remota de código. Integração exige que você está executando [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 ou superior. Se você quiser tirar proveito de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recursos e não não precisam de transmissão compatibilidade com sistemas de comunicação remota 2.0, você pode migrar o serviço inteiro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Migração de comunicação remota do .NET 2.0 para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requer alterações para a interface do objeto remoto e suas configurações. Ambos esses tópicos são abordados em [de comunicação remota para o Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Consulte também  
 [Conceptual Overview](../../../../docs/framework/wcf/conceptual-overview.md) (Visão geral conceitual)
