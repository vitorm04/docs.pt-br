---
title: Provedores de serviços de dados personalizados (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: 9c4b3fa3a706f8dc0ff072520dd91a74bc9d0a2c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871670"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Provedores de serviços de dados personalizados (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclui um conjunto de provedores que permite que você defina um modelo de dados com base nos tipos de dados de associação tardia.  
  
|Provider|Descrição|  
|--------------|-----------------|  
|Provedor de metadados|Isso é o provedor de serviços de dados personalizados de núcleo que lhe permite definir um modelo de dados personalizados em tempo de execução Implementando o <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.|  
|Provedor de consulta|Esse provedor permite que você execute consultas em um modelo de dados personalizado que é definido usando o <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface. O provedor de consulta é criado implementando o <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interface.|  
|Atualizar provedor|Esse provedor permite a você para fazer atualizações em tipos que são expostos em um provedor de serviços de dados personalizados e para gerenciar a simultaneidade. Um provedor de atualização é criado implementando o <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> interface|  
|Provedor de paginação|Esse provedor é usado com o provedor de serviços de dados personalizados para habilitar o suporte de paginação orientado para servidor. Um provedor de paginação para um serviço de dados personalizado é criado implementando o <xref:System.Data.Services.Providers.IDataServicePagingProvider> interface.|  
|Provedor de streaming|Esse provedor permite que você exponha tipos de dados de objeto binário grande como um fluxo. Um provedor de streaming é criado com a implementação da interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. O provedor de streaming também pode ser usado com provedores de fonte de dados do Entity Framework e reflexão. Para obter mais informações, consulte [provedor de Streaming](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
 Para obter mais informações, consulte o artigo [provedores de serviço de dados personalizado](https://go.microsoft.com/fwlink/?LinkID=186850) e o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Kit de ferramentas do provedor no [OData SDK](https://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Consulte também  
 [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)  
 [Provedor de reflexão](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
