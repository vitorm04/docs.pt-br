---
title: Utilizando o ServiceThrottlingBehavior para controlar o desempenho de serviço do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: 77fe2d3bb7f0e9c9d2e2defd4aa8c0053799406b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609493"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>Utilizando o ServiceThrottlingBehavior para controlar o desempenho de serviço do WCF
O <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> classe expõe propriedades que você pode usar para limitar quantas instâncias ou as sessões são criadas no nível do aplicativo. Usando esse comportamento, você pode ajustar o desempenho do seu aplicativo do Windows Communication Foundation (WCF).  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Controlando a instâncias de serviço e de chamadas simultâneas  
 Use o <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> propriedade para especificar o número máximo de mensagens processando ativamente em um <xref:System.ServiceModel.ServiceHost> classe e o <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> propriedade para especificar o número máximo de <xref:System.ServiceModel.InstanceContext> objetos no serviço.  
  
 Como determinar as configurações para essas propriedades geralmente acontece depois de experiências do mundo real que executa o aplicativo contra carrega, as configurações para o <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> propriedades geralmente é especificado em um arquivo de configuração de aplicativo usando o [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) elemento.  
  
 O exemplo de código a seguir mostra o uso do <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> classe a partir de um arquivo de configuração de aplicativo que define o <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, e <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> propriedades como 1 como um exemplo trivial. Experiência do mundo real determina as definições ideais para qualquer aplicativo em particular.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 O comportamento de tempo de execução exato depende dos valores da <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> e <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedades que controlam quantas mensagens podem executar dentro de uma operação uma vez e os tempos de vida do serviço <xref:System.ServiceModel.InstanceContext> em relação a sessões de canal de entrada , respectivamente.  
  
 Para obter detalhes, consulte <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, e <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
