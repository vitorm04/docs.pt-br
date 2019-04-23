---
title: Cenários de roteamento
ms.date: 03/30/2017
helpviewer_keywords:
- rounting [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: fa5d588211cfe40cde9e9db3161a931e3287cd39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223821"
---
# <a name="routing-scenarios"></a>Cenários de roteamento
Enquanto o serviço de roteamento é altamente personalizável, ele pode ser um desafio para a lógica de roteamento eficiente de design ao criar uma nova configuração do zero.  No entanto, há vários cenários comuns que seguem a maioria das configurações de serviço de roteamento. Enquanto esses cenários não podem ser aplicadas diretamente em sua configuração específica, Noções básicas sobre como o serviço de roteamento pode ser configurado para tratar desses cenários ajudam a entender o serviço de roteamento.  
  
## <a name="common-scenarios"></a>Cenários comuns  
 O uso mais básico do serviço de roteamento é agregar vários pontos de extremidade de destino para reduzir o número de pontos de extremidade expostos aos aplicativos cliente e, em seguida, usar filtros de mensagem para rotear cada mensagem para o destino correto. As mensagens podem ser roteadas com base nos requisitos de processamento lógico ou físico, como um tipo de mensagem que deve ser processado por um serviço específico ou com base nas necessidades de negócios arbitrário, como fornecer processamento de prioridade de mensagens de uma fonte específica. A tabela a seguir lista alguns dos cenários comuns e quando eles forem encontrados:  
  
|Cenário|Use quando|  
|--------------|--------------|  
|Controle de versão do serviço|Você precisa dar suporte a várias versões de um serviço ou pode implantar um serviço atualizado no futuro|  
|Particionamento de dados de serviço|Você deve particionar um serviço em vários hosts|  
|Atualização dinâmica|Você deve reconfigurar dinamicamente lógica de roteamento em tempo de execução para lidar com implantações do serviço de alteração|  
|Multicast|Você deve enviar uma mensagem para vários pontos de extremidade|  
|Ponte de protocolo|Receber mensagens através do protocolo de transporte e o ponto de extremidade de destino usa um protocolo diferente|  
|Tratamento de erros|Você precisa fornecer resiliência a interrupções de rede e falhas de comunicação|  
  
> [!NOTE]
>  Embora muitos dos cenários apresentados são específicos a determinadas necessidades de negócios ou requisitos de processamento, Planejando dar suporte a atualizações dinâmicas e utilizando o tratamento de erro geralmente podem ser considerado como melhores práticas, pois permitem que você modifique a lógica de roteamento em tempo de execução e se recuperar de falhas transitórias de rede e comunicação.  
  
### <a name="service-versioning"></a>Controle de versão de serviço  
 Ao introduzir uma nova versão de um serviço, você geralmente deve manter a versão anterior até que todos os clientes têm feito a transição para o novo serviço. Isso é especialmente crítico se o serviço é um processo de longa execução que leva os dias, semanas ou até meses para ser concluído. Normalmente, isso requer a implementação de um novo endereço de ponto de extremidade para o novo serviço, mantendo o ponto de extremidade original para a versão anterior.  
  
 Ao usar o serviço de roteamento, você pode expor um ponto de extremidade para receber mensagens de aplicativos cliente e, em seguida, rotear cada mensagem para a versão de serviço correto com base no conteúdo da mensagem. A implementação mais básica envolve a adição de um cabeçalho personalizado para a mensagem que indica a versão do que a mensagem deve ser processado pelo serviço. O serviço de roteamento pode usar o XPathMessageFilter para inspecionar cada mensagem para a presença do cabeçalho personalizado e rotear a mensagem para o ponto de extremidade de destino apropriado.  
  
 Para obter as etapas usadas para criar uma configuração de controle de versão de serviço, consulte [How To: Controle de versão de serviço](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).
  
### <a name="service-data-partitioning"></a>fornecer particionamento de dados  
 Ao criar um ambiente distribuído, geralmente é desejável para distribuir a carga de processamento entre vários computadores para fornecer alta disponibilidade, diminuir a carga de processamento em computadores individuais ou para fornecer recursos dedicados para um subconjunto específico de mensagens. Enquanto o serviço de roteamento não substitui uma solução de balanceamento de carga dedicada, sua capacidade de executar o roteamento com base em conteúdo pode ser usado para rotear mensagens de outra forma semelhante para destinos específicos. Por exemplo, você pode ter um requisito para processar as mensagens de um cliente específico separadamente de mensagens recebidas de outros clientes.  
  
 Para obter as etapas usadas para criar uma configuração de particionamento de dados de serviço, consulte [How To: Particionamento de dados de serviço](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md).  
  
### <a name="dynamic-routing"></a>Roteamento dinâmico  
 Muitas vezes é desejável para modificar a configuração de roteamento para atender às crescentes necessidades do negócio, como a adição de uma rota para uma versão mais recente de um serviço, a alteração dos critérios de roteamentos ou alterando o ponto de extremidade de destino uma mensagem específica que o filtro faça o roteamento. O serviço de roteamento permite que você faça isso por meio de <xref:System.ServiceModel.Routing.RoutingExtension>, que permite que você forneça um novo RoutingConfiguration durante o tempo de execução. A nova configuração entrará em vigor imediatamente, mas só afeta qualquer sessão nova processada pelo serviço de roteamento.  
  
 Para obter as etapas usadas para implementar o roteamento dinâmico, consulte [How To: Atualização dinâmica](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md).
  
### <a name="multicast"></a>Multicast  
 Quando o roteamento de mensagens, geralmente você roteamento cada mensagem ao ponto de extremidade de um destino específico.  No entanto, ocasionalmente, talvez precise rotear uma cópia da mensagem para vários pontos de extremidade de destino. Para executar o roteamento de difusão seletiva, as seguintes condições devem ser verdadeiras:  
  
-   A forma de canal não deve ser de solicitação-resposta (embora ele possa ser unidirecionais ou bidirecionais,) porque a solicitação-resposta exige que apenas uma resposta pode ser recebida pelo aplicativo cliente em resposta à solicitação.  
  
-   Vários filtros devem retornar **verdadeira** ao avaliar a mensagem.  
  
 Se essas condições forem atendidas, a cada ponto de extremidade de destino que está associado com um filtro que retorna true receberá uma cópia da mensagem.  
  
### <a name="protocol-bridging"></a>Ponte de protocolo  
 Ao rotear mensagens entre diferentes protocolos SOAP, o serviço de roteamento usa APIs do WCF para converter a mensagem de um protocolo para o outro. Isso ocorre automaticamente quando os pontos de extremidade de serviço expostos pelo uso do serviço de roteamento de um protocolo diferente que os pontos de extremidade do cliente que as mensagens são roteadas para. É possível desabilitar esse comportamento se os protocolos em uso não são padrão; No entanto, em seguida, forneça seu próprio código de ponte.
  
### <a name="error-handling"></a>Tratamento de erros  
 Em um ambiente distribuído, não é incomum encontrar falhas de rede ou de comunicação transitórias. Sem um serviço intermediário como o serviço de roteamento, a sobrecarga de lidar com tais falhas se enquadra no aplicativo cliente. Se o aplicativo cliente não inclui a lógica específica para tentar novamente em caso de rede ou falhas de comunicação e conhecimento sobre locais alternativos, o usuário pode encontrar situações em que uma mensagem deve ser enviada várias vezes antes que ele seja com êxito processado pelo serviço de destino. Isso pode levar a insatisfação do cliente com o aplicativo, pois podem ser considerado como não confiável.  
  
 O serviço de roteamento tenta corrigir esse cenário, fornecendo recursos de tratamento de erros robusto para mensagens que encontrar a rede ou falhas relacionadas à comunicação. Ao criar uma lista de pontos de extremidade de destino possíveis e associar essa lista com cada filtro de mensagem, você remove o ponto único de falha incorrido por ter apenas um destino possível. Em caso de falha, o serviço de roteamento tentará entregar a mensagem para o próximo ponto de extremidade na lista até que a mensagem foi entregue, ocorre uma falha de comunicação não, ou todos os pontos de extremidade foram esgotados.  
  
 Para obter as etapas usadas para configurar o tratamento de erros, consulte [How To: Tratamento de erro](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md).
  
### <a name="in-this-section"></a>Nesta seção  
 [Como: Controle de versão do serviço](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Como: Particionamento de dados de serviço](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Como: Atualização dinâmica](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Como: Tratamento de erros](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao roteamento](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
