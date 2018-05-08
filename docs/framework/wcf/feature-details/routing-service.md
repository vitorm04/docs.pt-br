---
title: Serviço de roteamento
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: e3170108ae190c08a42cc7d80d66576a7b4f8a8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="routing-service"></a>Serviço de roteamento
O serviço de roteamento é um intermediário SOAP genérico que atua como um roteador de mensagem. A funcionalidade básica do serviço de roteamento é a capacidade para rotear mensagens com base no conteúdo da mensagem, que permite que uma mensagem a serem encaminhados para um ponto de extremidade do cliente com base em um valor dentro da mensagem, no cabeçalho ou no corpo da mensagem.  
  
 O <xref:System.ServiceModel.Routing.RoutingService> é implementado como um serviço do Windows Communication Foundation (WCF) no <xref:System.ServiceModel.Routing> namespace. O serviço de roteamento expõe um ou mais pontos de extremidade que recebem mensagens e, em seguida, rotas de cada mensagem para um ou mais pontos de extremidade de cliente com base no conteúdo da mensagem. O serviço fornece os seguintes recursos:  
  
-   Roteamento baseado em conteúdo  
  
    -   Agregação de serviço  
  
    -   Controle de versão de serviço  
  
    -   Roteamento de prioridade  
  
    -   Configuração dinâmica  
  
-   Ponte de protocolo  
  
-   Processamento de SOAP  
  
-   Tratamento avançado de erros  
  
-   Pontos de extremidade de backup  
  
 Embora seja possível criar um serviço intermediário que realiza um ou mais dessas metas, geralmente essa implementação estiver associada a um cenário específico ou uma solução e não pode ser aplicada prontamente para novos aplicativos.  
  
 O serviço de roteamento fornece um intermediário SOAP genérico, podem ser configurado dinamicamente, conectável que é compatível com os modelos de serviço do WCF e o canal e permite que você execute roteamento baseado em conteúdo de mensagens de baseado em SOAP.  
  
> [!NOTE]
>  O serviço de roteamento não no momento oferecer suporte ao roteamento de serviços WCF REST.  Para encaminhar chamadas REST, considere o uso de <xref:System.Web.Routing> ou [Application Request Routing](http://go.microsoft.com/fwlink/?LinkId=164589) (http://go.microsoft.com/fwlink/?LinkId=164589).  
  
## <a name="content-based-routing"></a>Roteamento baseado em conteúdo  
 Roteamento baseado em conteúdo é a capacidade de encaminhar uma mensagem com base em um ou mais valores contidos na mensagem. O serviço de roteamento verifica se cada mensagem e a roteia para o ponto de extremidade de destino com base no conteúdo da mensagem e a lógica de roteamento que você criar. Roteamento baseado em conteúdo fornece a base para agregação de serviço, controle de versão de serviço e roteamento de prioridade.  
  
 Para implementar roteamento baseado em conteúdo, o serviço de roteamento depende <xref:System.ServiceModel.Dispatcher.MessageFilter> implementações que são usadas para corresponder valores específicos nas mensagens deve ser roteada. Se um **MessageFilter** corresponde uma mensagem, a mensagem é roteada para o ponto de extremidade de destino associado a **MessageFilter**.  Filtros de mensagem são agrupados em tabelas de filtro (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) para construir a lógica complexa de roteamento. Por exemplo, uma tabela de filtro pode conter cinco filtros de mensagem mutuamente exclusivos que fazer com que as mensagens sejam roteadas para apenas um dos pontos de extremidade de cinco destino.  
  
 O serviço de roteamento permite configurar a lógica que é usada para executar o roteamento baseado em conteúdo, bem como atualizar dinamicamente a lógica de roteamento em tempo de execução.  
  
 Por meio do agrupamento de filtros de mensagem em tabelas de filtro, lógica de roteamento pode ser construída que permite que você manipule vários cenários de roteamentos, como:  
  
-   Agregação de serviço  
  
-   Controle de versão de serviço  
  
-   Roteamento de prioridade  
  
-   Configuração dinâmica  
  
 Para obter mais informações sobre filtros de mensagem e tabelas de filtro, consulte [roteamento Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md) e [filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
### <a name="service-aggregation"></a>Agregação de serviço  
 Usando o roteamento baseado em conteúdo, você pode expor um ponto de extremidade que recebe mensagens do aplicativo cliente externo e, em seguida, encaminha cada mensagem para o ponto de extremidade interno apropriado com base em um valor dentro da mensagem. Isso é útil para oferecer um ponto de extremidade específico para uma variedade de aplicativos back-end e também para apresentar um ponto de extremidade do aplicativo para os clientes durante o cálculo de seu aplicativo em uma variedade de serviços.  
  
### <a name="service-versioning"></a>Controle de versão de serviço  
 Ao migrar para uma nova versão de sua solução, você pode ter que manter a versão antiga em paralelo para atender a clientes existentes. Geralmente, isso requer que clientes conectando-se para a versão mais recente devem usar um endereço diferente ao se comunicar com a solução. O serviço de roteamento permite expor um ponto de extremidade de serviço que serve a ambas as versões de sua solução pelo roteamento de mensagens para a solução apropriada com base nas informações específicas de versão contidas na mensagem. Para obter um exemplo de tal implementação consulte [como: controle de versão do serviço](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
### <a name="priority-routing"></a>Roteamento de prioridade  
 Ao fornecer um serviço para vários clientes, você pode ter um contrato de nível de serviço (SLA) com alguns parceiros que requer que todos os dados desses parceiros para ser processada separadamente a partir de outros clientes. Usando um filtro que procura informações específicas do cliente contidas na mensagem, você pode facilmente rotear mensagens de parceiros específicos para um ponto de extremidade que foi criada para atender aos requisitos de SLA.  
  
## <a name="dynamic-configuration"></a>Configuração dinâmica  
 Para dar suporte a sistemas de missão crítica, onde as mensagens devem ser processadas sem qualquer interrupção no serviço, é essencial que você poderá modificar a configuração dos componentes dentro do sistema em tempo de execução. Para dar suporte a essa necessidade, o serviço de roteamento fornece um <xref:System.ServiceModel.IExtension%601> implementação, o <xref:System.ServiceModel.Routing.RoutingExtension>, que permite que a atualização dinâmica da configuração do serviço de roteamento em tempo de execução.  
  
 Para obter mais informações sobre a configuração dinâmica do serviço de roteamento, consulte [roteamento Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="protocol-bridging"></a>Ponte de protocolo  
 Um dos desafios em cenários intermediários é que os pontos de extremidade internos podem ter diferente transporte ou requisitos de versão do SOAP que o ponto de extremidade que as mensagens são recebidas em. Para dar suporte a esse cenário, o serviço de roteamento pode ligar protocolos, incluindo o processamento da mensagem SOAP para o <xref:System.ServiceModel.Channels.MessageVersion> exigido pela extremidade de destino. Dessa forma, um protocolo pode ser usado para comunicação interna, enquanto outra pode ser usada para comunicações externas.  
  
 Para dar suporte a roteamento de mensagens entre pontos de extremidade com transportes diferentes, o serviço de roteamento usa associações fornecidas pelo sistema que permitem que o serviço acabar com protocolos diferentes. Isso ocorre automaticamente quando o ponto de extremidade do serviço exposto pelo serviço de roteamento usa um protocolo diferente que os pontos de extremidade do cliente que as mensagens são roteadas.  
  
## <a name="soap-processing"></a>Processamento de SOAP  
 Um requisito comum de roteamento é a capacidade para rotear mensagens entre pontos de extremidade com diferentes requisitos de SOAP. Para dar suporte a esse requisito, o serviço de roteamento fornece um <xref:System.ServiceModel.Routing.SoapProcessingBehavior> que cria automaticamente um novo **MessageVersion** que atenda aos requisitos do ponto de extremidade de destino antes da mensagem é roteada para ele. Esse comportamento também cria um novo **MessageVersion** qualquer mensagem de resposta antes de retorná-lo ao aplicativo cliente solicitante, para garantir que o **MessageVersion** da resposta é igual do a solicitação original.  
  
 Para obter mais informações sobre o processamento de SOAP, consulte [roteamento Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="error-handling"></a>Tratamento de erros  
 Em um sistema composto de serviços distribuídos que dependem de comunicações de rede, é importante garantir que as comunicações no sistema são resistente a falhas de rede temporárias.  O serviço de roteamento implementa tratamento de erros que permite que você manipule vários cenários de falha de comunicação que, caso contrário, podem resultar em uma interrupção de serviço.  
  
 Se o serviço de roteamento encontrar um <xref:System.ServiceModel.CommunicationException> ao tentar enviar uma mensagem, tratamento de erro ocorrerá.  Essas exceções geralmente indicam que ocorreu um problema ao tentar se comunicar com o ponto de extremidade do cliente definido como um <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, ou <xref:System.ServiceModel.CommunicationObjectFaultedException>.  O código de tratamento de erros também catch e tentar reenviar quando um **TimeoutException** ocorre, que é outra exceção comum que não é derivada de **CommunicationException**.  
  
 Para obter mais informações sobre tratamento de erros, consulte [roteamento Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="backup-endpoints"></a>Pontos de extremidade de backup  
 Além de destino os pontos de extremidade associados a cada definição de filtro na tabela de filtro, você também pode criar uma lista de pontos de extremidade de backup que a mensagem será roteada para em caso de falha de transmissão. Se ocorrer um erro e uma lista de backup é definida para a entrada de filtro, o serviço de roteamento tentará enviar a mensagem para o primeiro ponto de extremidade definido na lista. Se essa falha de tentativa de transmissão, o serviço tente o próximo ponto de extremidade e continuar este processo até que a tentativa de transmissão for bem-sucedido, retornará que um erro de transmissão não relacionado, ou todos os pontos de extremidade na lista de backup tiveram retornado um erro de transmissão.  
  
 Para obter mais informações sobre pontos de extremidade de backup, consulte [roteamento Introdução](../../../../docs/framework/wcf/feature-details/routing-introduction.md) e [filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
## <a name="streaming"></a>Streaming  
 O serviço de roteamento com êxito pode transmitir mensagens, se você definir a associação para dar suporte a streaming.  No entanto, há algumas condições sob as quais mensagens talvez precise em buffer:  
  
-   Multicast (buffer para criar cópias adicionais)  
  
-   Failover (buffer caso que a mensagem precisa ser enviada a um backup)  
  
-   System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly for false (buffer para apresentar a MessageFilterTable com MessageBuffer para que os filtros podem inspecionar o corpo)  
  
-   Configuração dinâmica  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao roteamento](../../../../docs/framework/wcf/feature-details/routing-introduction.md)  
 [Roteando contratos](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [Filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md)
