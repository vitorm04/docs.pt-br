---
title: Serviço de roteamento
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 139607614934aedbad9f76172b8e31fb02394d80
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43522164"
---
# <a name="routing-service"></a>Serviço de roteamento
O serviço de roteamento é um intermediário SOAP genérico que atua como um roteador de mensagem. A principal funcionalidade do serviço de roteamento é a capacidade para rotear mensagens com base no conteúdo da mensagem, que permite que uma mensagem a ser encaminhada para um ponto de extremidade do cliente com base em um valor dentro da mensagem em si, no cabeçalho ou no corpo da mensagem.  
  
 O <xref:System.ServiceModel.Routing.RoutingService> é implementado como um serviço do Windows Communication Foundation (WCF) na <xref:System.ServiceModel.Routing> namespace. O serviço de roteamento expõe um ou mais pontos de extremidade que recebem mensagens e, em seguida, roteia cada mensagem para um ou mais pontos de extremidade de cliente com base no conteúdo da mensagem. O serviço oferece os seguintes recursos:  
  
-   Roteamento baseado em conteúdo  
  
    -   Agregação de serviço  
  
    -   Controle de versão do serviço  
  
    -   Roteamento de prioridade  
  
    -   Configuração dinâmica  
  
-   Ponte de protocolo  
  
-   Processamento SOAP  
  
-   Tratamento avançado de erros  
  
-   Pontos de extremidade de backup  
  
 Embora seja possível criar um serviço intermediário que realiza um ou mais dessas metas, muitas vezes tal implementação está vinculada a um cenário específico ou uma solução e não pode ser prontamente aplicada a novos aplicativos.  
  
 O serviço Routing fornece um intermediário SOAP genérico, configurável dinamicamente, conectável que é compatível com os modelos de serviço do WCF e o canal e permite que você execute roteamento baseado em conteúdo de mensagens baseado em SOAP.  
  
> [!NOTE]
>  O serviço de roteamento não suporta no momento, o roteamento dos serviços REST do WCF.  Para rotear chamadas REST, considere o uso de <xref:System.Web.Routing> ou [Application Request Routing](https://go.microsoft.com/fwlink/?LinkId=164589).  
  
## <a name="content-based-routing"></a>Roteamento baseado em conteúdo  
 Roteamento baseado em conteúdo é a capacidade para rotear uma mensagem com base em um ou mais valores contidos dentro da mensagem. O serviço de roteamento inspeciona cada mensagem e as rotas para o ponto de extremidade de destino com base no conteúdo da mensagem e a lógica de roteamento que você cria. Roteamento baseado em conteúdo fornece a base para agregação de serviço, controle de versão de serviço e roteamento de prioridade.  
  
 Para implementar o roteamento baseado em conteúdo, o serviço de roteamento depende <xref:System.ServiceModel.Dispatcher.MessageFilter> implementações que são usadas para corresponder a valores específicos nas mensagens a serem roteadas. Se um **MessageFilter** correspondências de uma mensagem, a mensagem é roteada para o ponto de extremidade de destino associado a **MessageFilter**.  Filtros de mensagem são agrupados em tabelas de filtro (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) para construir a lógica de roteamento complexa. Por exemplo, uma tabela de filtros pode conter cinco filtros de mensagem mutuamente exclusivos que fazem com que as mensagens sejam roteadas para apenas um dos pontos de extremidade de cinco destino.  
  
 O serviço de roteamento permite que você configure a lógica que é usada para executar o roteamento baseado em conteúdo, bem como atualizar dinamicamente a lógica de roteamento em tempo de execução.  
  
 O agrupamento de filtros de mensagem em tabelas de filtro, por meio de lógica de roteamento pode ser construída que permite que você manipule vários cenários de roteamento, como:  
  
-   Agregação de serviço  
  
-   Controle de versão do serviço  
  
-   Roteamento de prioridade  
  
-   Configuração dinâmica  
  
 Para obter mais informações sobre tabelas de filtro e filtros de mensagem, consulte [roteamento de Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md) e [filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
### <a name="service-aggregation"></a>Agregação de serviço  
 Usando o roteamento baseado em conteúdo, você pode expor um ponto de extremidade que recebe mensagens de aplicativos de cliente externo e, em seguida, encaminha cada mensagem para o ponto de extremidade interno apropriado com base em um valor dentro da mensagem. Isso é útil para oferecer um ponto de extremidade específico para uma variedade de aplicativos de back-end e também para apresentar um ponto de extremidade do aplicativo para os clientes ao fatorar seu aplicativo em uma variedade de serviços.  
  
### <a name="service-versioning"></a>Controle de versão de serviço  
 Ao migrar para uma nova versão da sua solução, você talvez precise manter a versão antiga em paralelo para servir clientes existentes. Geralmente, isso requer que os clientes conectando-se para a versão mais recente devem usar um endereço diferente ao se comunicar com a solução. O serviço de roteamento permite expor um ponto de extremidade de serviço que serve de ambas as versões de sua solução pelo roteamento de mensagens para a solução apropriada com base nas informações específicas da versão contidas na mensagem. Para obter um exemplo de tal implementação, consulte [How To: controle de versão do serviço](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
### <a name="priority-routing"></a>Roteamento de prioridade  
 Ao fornecer um serviço para vários clientes, você pode ter um contrato de nível de serviço (SLA) com alguns parceiros que requer que todos os dados desses parceiros para ser processada separadamente a partir de outros clientes. Usando um filtro que procura por informações específicas do cliente na mensagem, você pode facilmente rotear mensagens de parceiros específicos para um ponto de extremidade que foi criado para atender aos requisitos de SLA.  
  
## <a name="dynamic-configuration"></a>Configuração dinâmica  
 Para dar suporte a sistemas de missão crítica, onde as mensagens devem ser processadas sem interrupções de serviço, é vital que você poderá modificar a configuração de componentes do sistema em tempo de execução. Para dar suporte a essa necessidade, o serviço Routing fornece um <xref:System.ServiceModel.IExtension%601> implementação, o <xref:System.ServiceModel.Routing.RoutingExtension>, que permite a atualização dinâmica da configuração do serviço de roteamento em tempo de execução.  
  
 Para obter mais informações sobre a configuração dinâmica do serviço de roteamento, consulte [roteamento Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="protocol-bridging"></a>Ponte de protocolo  
 Um dos desafios em cenários intermediários é que os pontos de extremidade internos podem ter requisitos de versão do SOAP que o ponto de extremidade que as mensagens são recebidas em ou de transporte diferentes. Para dar suporte a esse cenário, o serviço de roteamento pode acabar com protocolos, incluindo o processamento da mensagem SOAP para o <xref:System.ServiceModel.Channels.MessageVersion> necessários para os pontos de extremidade de destino. Dessa forma, um protocolo pode ser usado para a comunicação interna, enquanto outra pode ser usada para comunicação externa.  
  
 Para dar suporte a roteamento de mensagens entre pontos de extremidade com diferentes transportes, o serviço de roteamento usa associações fornecidas pelo sistema que permitem que o serviço acabar com protocolos diferentes. Isso ocorre automaticamente quando o ponto de extremidade de serviço exposto pelo serviço de roteamento usa um protocolo diferente que os pontos de extremidade do cliente que as mensagens são roteadas.  
  
## <a name="soap-processing"></a>Processamento SOAP  
 Um requisito comum de roteamento é a capacidade para rotear mensagens entre pontos de extremidade com diferentes requisitos de SOAP. Para dar suporte a esse requisito, o serviço Routing fornece um <xref:System.ServiceModel.Routing.SoapProcessingBehavior> que cria automaticamente um novo **MessageVersion** que atende aos requisitos do ponto de extremidade de destino antes da mensagem é roteada para ele. Esse comportamento também cria um novo **MessageVersion** qualquer mensagem de resposta antes de retorná-lo ao aplicativo solicitante do cliente, para garantir que o **MessageVersion** da resposta corresponde do a solicitação original.  
  
 Para obter mais informações sobre o processamento de SOAP, consulte [roteamento Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="error-handling"></a>Tratamento de erros  
 Em um sistema composto de serviços distribuídos que dependem de comunicações de rede, é importante garantir que as comunicações dentro de seu sistema são resistente a falhas de rede transitórios.  O serviço de roteamento implementa o tratamento de erro que permite que você manipule vários cenários de falha de comunicação que, caso contrário, podem resultar em uma interrupção de serviço.  
  
 Se o serviço de roteamento de encontrar um <xref:System.ServiceModel.CommunicationException> ao tentar enviar uma mensagem, tratamento de erro ocorrerá.  Normalmente, essas exceções indicam que um problema foi encontrado ao tentar se comunicar com o ponto de extremidade do cliente definido como um <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, ou <xref:System.ServiceModel.CommunicationObjectFaultedException>.  O código de tratamento de erros também irá capturar e tentar novamente enviar quando uma **TimeoutException** ocorrer, que é outra exceção comuns que não é derivada de **CommunicationException**.  
  
 Para obter mais informações sobre o tratamento de erro, consulte [roteamento Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="backup-endpoints"></a>Pontos de extremidade de backup  
 Além dos destino os pontos de extremidade associados a cada definição de filtro na tabela de filtros, você também pode criar uma lista de pontos de extremidade de backup que a mensagem será roteada para em caso de falha de transmissão. Se ocorrer um erro e uma lista de backup é definida para a entrada de filtro, o serviço de roteamento tentará enviar a mensagem para o primeiro ponto de extremidade definido na lista. Se essa falha de tentativa de transmissão, o serviço tente o próximo ponto de extremidade e continue esse processo até que a tentativa de transmissão tiver êxito, retorna que um erro de transmissão não relacionado, ou todos os pontos de extremidade na lista de backup tiveram retornado um erro de transmissão.  
  
 Para obter mais informações sobre pontos de extremidade de backup, consulte [roteamento de Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md) e [filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
## <a name="streaming"></a>Streaming  
 O serviço de roteamento com êxito pode transmitir mensagens, se você definir a associação para dar suporte a streaming.  No entanto, há algumas condições sob as quais as mensagens talvez precise em buffer:  
  
-   Multicast (buffer para criar cópias adicionais da mensagem)  
  
-   Failover (buffer caso que a mensagem precisa ser enviada para um backup)  
  
-   System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly for false (buffer para apresentar o MessageFilterTable com MessageBuffer, de modo que os filtros podem inspecionar o corpo)  
  
-   Configuração dinâmica  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao roteamento](../../../../docs/framework/wcf/feature-details/routing-introduction.md)  
 [Roteando contratos](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [Filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md)
