---
title: "Provedores de serviços de dados personalizados (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d7db780b97c1a7eadffbfa71f60be4afe590ccb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Provedores de serviços de dados personalizados (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]inclui um conjunto de provedores que permite que você defina um modelo de dados com base nos tipos de dados de associação tardia.  
  
|Provider|Descrição|  
|--------------|-----------------|  
|Provedor de metadados|Este é o provedor de serviços de dados personalizados de núcleo que permite que você defina um modelo de dados personalizado em tempo de execução com a implementação de <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.|  
|Provedor de consulta|Esse provedor permite a execução de consultas em um modelo de dados personalizado que é definido usando o <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface. O provedor de consulta é criado com a implementação de <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interface.|  
|Provedor de atualização|Esse provedor permite a você para fazer atualizações em tipos que são expostos em um provedor de serviços de dados personalizados e gerenciar a simultaneidade. Um provedor de atualização é criado com a implementação de <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> interface|  
|Provedor de paginação|Esse provedor é usado com o provedor de serviços de dados personalizadas para habilitar o suporte de paginação orientado para servidor. Um provedor de paginação para um serviço de dados personalizado é criado com a implementação de <xref:System.Data.Services.Providers.IDataServicePagingProvider> interface.|  
|Provedor de streaming|Esse provedor permite que você exponha os tipos de dados de objeto binário grande como um fluxo. Um provedor de streaming é criado com a implementação da interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. O provedor de streaming também pode ser usado com provedores de fonte de dados do Entity Framework e reflexão. Para obter mais informações, consulte [provedor Streaming](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
 Para obter mais informações, consulte o artigo [provedores de serviço de dados personalizados](http://go.microsoft.com/fwlink/?LinkID=186850) e [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Kit de ferramentas do provedor no [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Consulte também  
 [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)  
 [Provedor de reflexão](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
