---
title: "Cenários de roteamento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: rounting [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ef101a9a5f78e1b85ac7cb983b4766088b83317
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="routing-scenarios"></a>Cenários de roteamento
Enquanto o serviço de roteamento é altamente personalizável, ele pode ser um desafio para criar lógica de roteamento eficiente, ao criar uma nova configuração do zero.  No entanto, há vários cenários comuns que siga a maioria das configurações de serviço de roteamento. Enquanto esses cenários não podem ser aplicadas diretamente em sua configuração específica, Noções básicas sobre como o serviço de roteamento pode ser configurado para tratar desses cenários ajudam a entender o serviço de roteamento.  
  
## <a name="common-scenarios"></a>Cenários comuns  
 O uso mais básico do serviço de roteamento é agregar vários pontos de extremidade de destino para reduzir o número de pontos de extremidade expostos para os aplicativos cliente e, em seguida, usar filtros de mensagem para rotear cada mensagem para o destino correto. As mensagens podem ser roteadas com base nos requisitos de processamento lógico ou físico, como um tipo de mensagem que deve ser processada por um serviço específico ou com base nas necessidades de negócios arbitrário como fornecer processamento de prioridade de mensagens de uma fonte específica. A tabela a seguir lista alguns dos cenários comuns e quando elas são encontradas:  
  
|Cenário|Use quando|  
|--------------|--------------|  
|Controle de versão de serviço|Você precisa oferecer suporte a várias versões de um serviço ou pode implantar um serviço atualizado no futuro|  
|Particionamento de dados de serviço|Você deve particionar um serviço em vários hosts|  
|Atualização dinâmica|É necessário reconfigurar dinamicamente a lógica de roteamento em tempo de execução para lidar com implantações do serviço de alteração|  
|Multicast|Você deve enviar uma mensagem para vários pontos de extremidade|  
|Ponte de protocolo|Mensagens de protocolo de transporte e o ponto de extremidade de destino usa um protocolo diferente|  
|Tratamento de erros|Você precisa fornecer resistência a falhas de comunicação e interrupções de rede|  
  
> [!NOTE]
>  Enquanto muitos dos cenários apresentados são específicos para determinados necessidades de negócios ou requisitos de processamento, planejamento para suporte a atualizações dinâmicas e tratamento de erros que utiliza geralmente podem ser considerados como melhores práticas como eles permitem que você modifique a lógica de roteamento em tempo de execução e recupere de falhas transitórias de comunicação e de rede.  
  
### <a name="service-versioning"></a>Controle de versão de serviço  
 Ao introduzir uma nova versão de um serviço, você geralmente deve manter a versão anterior até que todos os clientes tem mudado para o novo serviço. Isso é especialmente crítico se o serviço é um processo de execução longa que leva dias, semanas ou até mesmo meses para ser concluído. Normalmente, isso requer a implementação de um novo endereço de ponto de extremidade para o novo serviço, mantendo o ponto de extremidade original para a versão anterior.  
  
 Usando o serviço de roteamento, você pode expor um ponto de extremidade para receber mensagens de aplicativos cliente e, em seguida, rotear cada mensagem para a versão de serviço correta com base no conteúdo da mensagem. A implementação mais básica envolve a adição de um cabeçalho personalizado para a mensagem que indica a versão do que a mensagem a ser processado pelo serviço. O serviço de roteamento pode usar o XPathMessageFilter para inspecionar cada mensagem para a presença do cabeçalho personalizado e encaminhar a mensagem para o ponto de extremidade de destino apropriado.  
  
 Para obter as etapas usadas para criar uma configuração de controle de versão de serviço, consulte [como: controle de versão do serviço](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md). Para obter um exemplo de como usar o XPathMessageFilter para rotear mensagens com base em um cabeçalho personalizado, consulte o [filtros avançados](../../../../docs/framework/wcf/samples/advanced-filters.md) exemplo.  
  
### <a name="service-data-partitioning"></a>Particionamento de dados de serviço  
 Ao criar um ambiente distribuído, geralmente é conveniente para distribuir a carga de processamento em vários computadores para fornecer alta disponibilidade, diminua a carga de processamento em computadores individuais ou para fornecer recursos dedicados para um subconjunto específico de mensagens. Enquanto o serviço de roteamento não substitui uma solução de balanceamento de carga dedicada, sua capacidade de executar o roteamento baseado em conteúdo pode ser usado para rotear mensagens caso contrário semelhante para destinos específicos. Por exemplo, você pode ter um requisito para processar mensagens de um cliente específico separadamente de mensagens recebidas de outros clientes.  
  
 Para obter as etapas usadas para criar uma configuração de particionamento de dados de serviço, consulte [como: o particionamento de dados do serviço](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md). Para obter um exemplo de como usar filtros para particionar dados com base na URL e cabeçalhos personalizados, consulte o [filtros avançados](../../../../docs/framework/wcf/samples/advanced-filters.md) exemplo.  
  
### <a name="dynamic-routing"></a>Roteamento dinâmico  
 Geralmente, é desejável para modificar a configuração de roteamento para atender a necessidades dinâmicas de negócios, como a adição de uma rota para uma versão mais recente do serviço, alterar os critérios de roteamento ou alterando o ponto de extremidade de destino de uma mensagem específica que direciona o filtro para. O serviço de roteamento permite que você faça isso por meio de <xref:System.ServiceModel.Routing.RoutingExtension>, que permite que você forneça uma nova RoutingConfiguration durante o tempo de execução. A nova configuração entra em vigor imediatamente, mas só afeta qualquer sessão nova processada pelo serviço de roteamento.  
  
 Para obter as etapas usadas para implementar roteamento dinâmico, consulte [How To: atualização dinâmica](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md). Para obter um exemplo de como usar o roteamento dinâmico, consulte o [reconfiguração dinâmica](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md) exemplo.  
  
### <a name="multicast"></a>Multicast  
 Quando o roteamento de mensagens, geralmente você roteamento cada mensagem ao ponto de extremidade de destino específico.  No entanto, ocasionalmente, convém rotear uma cópia da mensagem para vários pontos de extremidade de destino. Para executar o roteamento de difusão seletiva, as seguintes condições devem ser verdadeiras:  
  
-   A forma de canal não deve ser solicitação-resposta (embora ele pode ser unidirecionais ou bidirecionais,) porque a solicitação-resposta exige que apenas uma resposta pode ser recebida pelo aplicativo cliente em resposta à solicitação.  
  
-   Vários filtros devem retornar **true** ao avaliar a mensagem.  
  
 Se essas condições forem atendidas, cada ponto de extremidade de destino que está associado com um filtro que retorna true receberá uma cópia da mensagem.  
  
### <a name="protocol-bridging"></a>Ponte de protocolo  
 Quando o roteamento de mensagens entre diferentes protocolos SOAP, o serviço de roteamento usa APIs do WCF para converter a mensagem de um protocolo para o outro. Isso ocorre automaticamente quando a extremidade do serviço exposto pelo uso do serviço de roteamento um protocolo diferente que a extremidade do cliente que as mensagens são roteadas para. É possível desabilitar esse comportamento se os protocolos em uso não são padrão; No entanto, você deve, em seguida, fornecer seu próprio código de ponte.  
  
 . Para obter um exemplo de como usar o serviço de roteamento para traduzir mensagens entre protocolos, consulte o [ponte e o tratamento de erros](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) exemplo.  
  
### <a name="error-handling"></a>Tratamento de erros  
 Em um ambiente distribuído, não é incomum encontrar falhas transitórias de comunicação ou de rede. Sem um serviço intermediário, como o serviço de roteamento, a sobrecarga de lidar com tais falhas se enquadra no aplicativo cliente. Se o aplicativo cliente não incluir lógica específica para tentar novamente em caso de rede ou falhas de comunicação e conhecimento de locais alternativos, o usuário pode encontrar cenários em que uma mensagem deve ser enviada várias vezes antes de ser com êxito processado pelo serviço de destino. Isso pode levar à insatisfação do cliente com o aplicativo, como ele pode ser considerado como não confiável.  
  
 O serviço de roteamento tenta corrigir esse cenário, fornecendo recursos de tratamento de erro robustos para mensagens que encontrar a rede ou falhas de comunicação. Criando uma lista de pontos de extremidade de destino possíveis e associar essa lista cada filtro de mensagem, você deve remover o ponto único de falha devido a ter apenas um destino possível. Em caso de falha, o serviço de roteamento tentará enviar a mensagem para o próximo ponto de extremidade na lista até que a mensagem foi fornecida, ocorre uma falha de comunicação não, ou todos os pontos de extremidade foram esgotados.  
  
 Para obter as etapas usadas para configurar a manipulação de erro, consulte [How To: tratamento de erros](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md). Para obter um exemplo de implementação de tratamento de erros, consulte o [ponte e o tratamento de erros](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) e [avançados de tratamento de erros](../../../../docs/framework/wcf/samples/advanced-error-handling.md) exemplos.  
  
### <a name="in-this-section"></a>Nesta seção  
 [Como controlar a versão do serviço](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Como particionar dados de serviço](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Como atualizar dinamicamente](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Como fazer para tratar erros](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao roteamento](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
