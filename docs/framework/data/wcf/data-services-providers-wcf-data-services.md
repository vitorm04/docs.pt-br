---
title: "Provedores de serviços de dados (WCF Data Services)"
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
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6f25f1f9137206c1adb3ab3f89b7c6a783aeccf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="data-services-providers-wcf-data-services"></a>Provedores de serviços de dados (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]oferece suporte a vários modelos de provedor para expor dados como um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed. Este tópico fornece informações para permitir que você selecione o melhor provedor de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para sua fonte de dados.  
  
## <a name="data-source-providers"></a>Provedores de fontes de dados  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]suporta os seguintes provedores para definir o modelo de dados de um serviço de dados.  
  
|Provider|Descrição|  
|--------------|-----------------|  
|Provedor de Entity Framework|Este provedor usa o ADO.NET Entity Framework para permitir que você use dados relacionais com um serviço de dados definindo um modelo de dados que é mapeado para dados relacionais. Sua fonte de dados pode ser o SQL Server ou qualquer outra fonte de dados com suporte a provedores de terceiros para o Entity Framework. Você deverá usar o provedor de Entity Framework quando tiver uma fonte de dados relacional, como um banco de dados do SQL Server. Para obter mais informações, consulte [provedor do Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).|  
|Provedor de reflexão|Este provedor usa a reflexão para permitir que você defina um modelo de dados com base em classes de dados existentes que podem ser expostas como instâncias da interface <xref:System.Linq.IQueryable%601>. As atualizações são habilitadas com a implementação da interface <xref:System.Data.Services.IUpdatable>. Você deve usar esse provedor quando tem classes de dados estáticas que são definidas em tempo de execução, como aquelas geradas pelo LINQ to SQL ou definidas por um DataSet tipado. Para obter mais informações, consulte [provedor de reflexão](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).|  
|Provedores de serviços de dados personalizados|O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclui um conjunto de provedores que permitem que você defina dinamicamente um modelo de dados baseado em tipos de dados de associação tardia. Você deve implementar essas interfaces quando os dados que estão sendo expostos não são conhecidos quando o aplicativo é criado ou quando os provedores de Entity Framework ou reflexão não são suficientes. Para obter mais informações, consulte [provedores de serviço de dados personalizados](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Outros provedores de serviços de dados  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]tem o seguinte provedor de serviços de dados adicionais que aprimora o desempenho de uma fonte de dados definido usando um dos outros provedores.  
  
|Provider|Descrição|  
|--------------|-----------------|  
|Provedor de streaming|Este provedor permite que você exponha tipos de dados de objetos grandes binários usando o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Um provedor de streaming é criado com a implementação da interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Este provedor pode ser implementado junto com qualquer provedor de fonte de dados. Para obter mais informações, consulte [provedor Streaming](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Consulte também  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)  
 [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)  
 [Hospedagem o serviço de dados](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
