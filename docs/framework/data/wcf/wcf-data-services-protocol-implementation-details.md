---
title: Detalhes de implementação do protocolo do WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 10a330fd6f6f73ffc7e812e0a9012ec20c83861d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975041"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Detalhes de implementação do protocolo do WCF Data Services
## <a name="odata-protocol-implementation-details"></a>Detalhes de implementação do protocolo OData  
 O Protocolo Open Data (OData) requer que um serviço de dados que implementa o protocolo forneça um determinado conjunto mínimo de funcionalidades. Essas funcionalidades são descritas nos documentos de protocolo em termos de "deve" e "devem". Outras funcionalidades opcionais são descritas em termos de "maio". Este tópico descreve essas funcionalidades opcionais que atualmente não são implementadas pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Para obter mais informações, consulte a [documentação do protocolo OData](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Suporte para a opção de consulta $format  
 O protocolo OData dá suporte a JSON (JavaScript Notation) e a feeds Atom, e o OData fornece a opção de consulta do sistema `$format` para permitir que um cliente solicite o formato do feed de resposta. Essa opção de consulta do sistema, se suportada pelo serviço de dados, deve substituir o valor do cabeçalho Accept da solicitação. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dá suporte ao retorno de feeds JSON e Atom. No entanto, a implementação padrão não oferece suporte à opção de consulta `$format` e usa apenas o valor do cabeçalho Accept para determinar o formato da resposta. Há casos em que o serviço de dados pode precisar dar suporte à opção de consulta `$format`, como quando os clientes não podem definir o cabeçalho Accept. Para dar suporte a esses cenários, você deve estender seu serviço de dados para lidar com essa opção no URI. Você pode adicionar essa funcionalidade ao seu serviço de dados baixando o [JSONP e o suporte de formato controlado por URL para](https://go.microsoft.com/fwlink/?LinkId=208228) o projeto de exemplo do ADO.NET Data Services no site da Galeria de códigos do MSDN e adicionando-o ao seu projeto de serviço de dados. Este exemplo remove a opção de consulta `$format` e altera o cabeçalho Accept para `application/json`. Quando você inclui o projeto de exemplo e a adição do `JSONPSupportBehaviorAttribute` à sua classe de serviço de dados permite que o serviço manipule a opção de consulta `$format` `$format=json`. A personalização adicional desse projeto de exemplo também é necessária para lidar com `$format=atom` ou outros formatos personalizados.  
  
## <a name="wcf-data-services-behaviors"></a>Comportamentos de WCF Data Services  
 Os comportamentos de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] a seguir não são definidos explicitamente pelo protocolo OData:  
  
### <a name="default-sorting-behavior"></a>Comportamento de classificação padrão  
 Quando uma solicitação de consulta enviada ao serviço de dados inclui uma opção de consulta de sistema `$top` ou `$skip` e não inclui a opção de consulta de sistema `$orderby`, o feed retornado é classificado pelas propriedades de chave, em ordem crescente. Isso ocorre porque a ordenação é necessária para garantir a paginação correta dos resultados. Para fazer isso, o serviço de dados adiciona uma expressão de ordenação à consulta. Esse comportamento também ocorre quando a paginação controlada por servidor está habilitada no serviço de dados. Para obter mais informações, consulte [Configurando o serviço de dados](configuring-the-data-service-wcf-data-services.md). Para controlar a ordenação do feed retornado, você deve incluir `$orderby` no URI de consulta.  
  
## <a name="see-also"></a>Consulte também

- [Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)
- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
