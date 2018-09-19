---
title: Detalhes de implementação de protocolo do WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 1d68e278fbac0137d1a5b2dca2daedba2294a7ee
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323254"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Detalhes de implementação de protocolo do WCF Data Services
## <a name="odata-protocol-implementation-details"></a>Detalhes de implementação do protocolo OData  
 O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] requer que um serviço de dados que implementa o protocolo forneça um determinado conjunto mínimo de funcionalidades. Essas funcionalidades são descritas nos documentos de protocolo em termos de "deve" e "deve". Outra funcionalidade opcional é descrita em termos de "maio". Este tópico descreve essas funcionalidades opcionais que não estejam atualmente implementadas pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Para obter mais informações, consulte [documentação do protocolo OData](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Suporte para a opção de consulta $format  
 O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo oferece suporte à notação JSON (JavaScript) e feeds Atom, e [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fornece o `$format` opção de consulta do sistema para permitir que um cliente para o formato de feed de resposta da solicitação. Essa opção de consulta do sistema, se compatível com o serviço de dados, deve substituir o valor do cabeçalho Accept da solicitação. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dá suporte a retornar JSON e Atom feeds. No entanto, a implementação padrão não oferece suporte a `$format` opção de consulta e usa apenas o valor do cabeçalho Accept para determinar o formato da resposta. Há casos em que o serviço de dados, talvez seja necessário dar suporte a `$format` opção, como quando os clientes não é possível definir o cabeçalho Accept de consulta. Para dar suporte a esses cenários, você deve estender o seu serviço de dados para lidar com essa opção no URI. Você pode adicionar essa funcionalidade ao seu serviço de dados, baixando a [JSONP and URL-controlled format dão suporte para o ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) projeto de exemplo do site da Galeria de códigos do MSDN e adicioná-lo ao seu projeto de serviço de dados. Este exemplo remove os `$format` opção de consulta e altera o cabeçalho Accept para `application/json`. Quando você inclui o exemplo de projeto e adicionando as `JSONPSupportBehaviorAttribute` aos seus dados de classe de serviço permite que o serviço lidar com o `$format` opção de consulta `$format=json`. Personalização adicional deste projeto de exemplo é necessária para tratar também `$format=atom` ou outros formatos personalizados.  
  
## <a name="wcf-data-services-behaviors"></a>Comportamentos do WCF Data Services  
 O seguinte [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] comportamentos não estejam explicitamente definidos pelo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo:  
  
### <a name="default-sorting-behavior"></a>Comportamento de classificação padrão  
 Quando uma solicitação de consulta é enviada para o serviço de dados inclui um `$top` ou `$skip` opção de consulta de sistema e não inclui o `$orderby` opção de consulta do sistema, o feed retornado é classificada pelas propriedades de chave, em ordem crescente. Isso ocorre porque a ordenação é necessária para garantir a correta de paginação de resultados. Para fazer isso, o serviço de dados adiciona uma expressão de classificação na consulta. Esse comportamento também ocorre quando a paginação orientado para servidor está habilitada no serviço de dados. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Para controlar a ordenação de feed retornado, você deve incluir `$orderby` no URI de consulta.  
  
## <a name="see-also"></a>Consulte também  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
