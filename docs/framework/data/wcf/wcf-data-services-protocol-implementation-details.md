---
title: Detalhes de implementação do protocolo do WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 82218f1f8e14c9909d8b617c66b1f18a28e4dcee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363715"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Detalhes de implementação do protocolo do WCF Data Services
## <a name="odata-protocol-implementation-details"></a>Detalhes de implementação do protocolo OData  
 O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] requer que um serviço de dados que implementa o protocolo forneça um determinado conjunto mínimo de recursos. Essas funcionalidades descritas nos documentos de protocolo em termos de "deve" e "deve". Outra funcionalidade opcional é descrita em termos de "maio". Este tópico descreve essas funcionalidades opcionais que não estão atualmente implementadas pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Para obter mais informações, consulte [documentação do protocolo OData](http://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Suporte para a opção de consulta $format  
 O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo dá suporte a JavaScript Notation (JSON) e feeds Atom, e [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fornece o `$format` opção de consulta do sistema para permitir que um cliente solicitar o formato da resposta de feed. Essa opção de consulta do sistema, se houver suporte pelo serviço de dados, deve substituir o valor do cabeçalho de aceitação da solicitação. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dá suporte a retorno de JSON e Atom feeds. No entanto, a implementação padrão não oferece suporte a `$format` opção de consulta e usa apenas o valor do cabeçalho Accept para determinar o formato da resposta. Há casos em que o serviço de dados pode ser necessário dar suporte a `$format` opção, como quando os clientes não é possível definir o cabeçalho Accept de consulta. Para dar suporte a esses cenários, você deve estender o serviço de dados para lidar com essa opção no URI. Você pode adicionar essa funcionalidade ao seu serviço de dados baixando o [JSONP e formato de URL-controlled oferecem suporte para o ADO.NET Data Services](http://go.microsoft.com/fwlink/?LinkId=208228) projeto de exemplo do site da Galeria de códigos do MSDN e adicioná-lo ao seu projeto de serviço de dados. Este exemplo remove o `$format` opção de consulta e altera o cabeçalho Accept para `application/json`. Quando você inclui o exemplo de projeto e adicionar o `JSONPSupportBehaviorAttribute` aos seus dados de classe de serviço permite que o serviço manipular o `$format` opção de consulta `$format=json`. Outra personalização deste projeto de exemplo é necessária para tratar também `$format=atom` ou outros formatos personalizados.  
  
## <a name="wcf-data-services-behaviors"></a>Comportamentos do WCF Data Services  
 O seguinte [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] comportamentos não são explicitamente definidos pelo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo:  
  
### <a name="default-sorting-behavior"></a>Comportamento de classificação padrão  
 Quando uma solicitação de consulta é enviada para o serviço de dados inclui um `$top` ou `$skip` sistema opção de consulta e não inclui o `$orderby` opção de consulta do sistema, o feed retornado é classificada por propriedades de chave, em ordem crescente. Isso ocorre porque a ordenação é necessário para garantir a paginação correta de resultados. Para fazer isso, o serviço de dados adiciona uma expressão de classificação para a consulta. Esse comportamento também ocorre quando a paginação orientado para servidor está habilitada no serviço de dados. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Para controlar a ordem do feed retornado, você deve incluir `$orderby` na consulta URI.  
  
## <a name="see-also"></a>Consulte também  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
