---
title: Provedores de serviço de dados personalizados (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: c5f6bd001a5198f14bf05c0730f3988d54142eae
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569242"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Provedores de serviço de dados personalizados (WCF Data Services)
WCF Data Services inclui um conjunto de provedores que permite que você defina um modelo de dados com base em tipos de dados de associação tardia.  
  
|Provider|Descrição|  
|--------------|-----------------|  
|Provedor de metadados|Este é o principal provedor de serviços de dados personalizados que permite que você defina um modelo de dados personalizado em tempo de execução implementando a interface <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>.|  
|Provedor de consultas|Esse provedor permite que você execute consultas em um modelo de dados personalizado que é definido usando a interface <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>. O provedor de consultas é criado com a implementação da interface <xref:System.Data.Services.Providers.IDataServiceQueryProvider>.|  
|Atualizar provedor|Esse provedor permite que você faça atualizações em tipos expostos em um provedor de serviços de dados personalizado e gerencie a simultaneidade. Um provedor de atualização é criado com a implementação da interface <xref:System.Data.Services.Providers.IDataServiceUpdateProvider>|  
|Provedor de paginação|Esse provedor é usado com o provedor de serviços de dados personalizado para habilitar o suporte de paginação controlado por servidor. Um provedor de paginação para um serviço de dados personalizado é criado com a implementação da interface <xref:System.Data.Services.Providers.IDataServicePagingProvider>.|  
|Provedor de streaming|Esse provedor permite expor tipos de dados de objeto binário grande como um fluxo. Um provedor de streaming é criado com a implementação da interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. O provedor de streaming também pode ser usado com provedores de fonte de dados Entity Framework e Reflection. Para obter mais informações, consulte [streaming Provider](streaming-provider-wcf-data-services.md).|  
  
 Para obter mais informações, consulte o artigo [provedores de serviços de dados personalizados](https://go.microsoft.com/fwlink/?LinkID=186850) e o kit de ferramentas do provedor de protocolo Open Data (OData) no [SDK do OData](https://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Consulte também

- [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md)
- [Entity Framework Provider](entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)
- [Provedor de reflexão](reflection-provider-wcf-data-services.md)
