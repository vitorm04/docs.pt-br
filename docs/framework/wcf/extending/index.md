---
title: Estendendo o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 4990f14178551d9dccaca0f2899d8dbc4416cdc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="extending-wcf"></a>Estendendo o WCF
Windows Communication Foundation (WCF) permite que você modifique e estender os componentes de tempo de execução para controlar com precisão e estender aplicativos baseados em serviço. Os tópicos nesta seção vá em detalhes sobre a arquitetura de extensibilidade. Para obter mais informações sobre programação básica, consulte [básicas de programação WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estendendo ServiceHost e a camada de modelo de serviço](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 A camada de modelo de serviço é responsável por recebendo mensagens de entrada fora dos canais subjacentes, convertendo-os em invocações do método no código do aplicativo e enviar os resultados de volta para o chamador.  Extensões do modelo de serviço modificam ou implementam a execução ou o comportamento de comunicação e recursos que envolvem a funcionalidade de dispatcher, comportamentos personalizados, mensagem e interceptação de parâmetro e outras funcionalidades de extensibilidade.  
  
 [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 Associações são objetos que descrevem os detalhes de comunicação necessários para conectar a um ponto de extremidade. Extensões de associação ou associações personalizadas implementam a funcionalidade de comunicação personalizados necessária para dar suporte a recursos do aplicativo.  
  
 [Estendendo a camada do canal](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 A camada do canal fica abaixo da camada de modelo de serviço e é responsável pela troca de mensagens entre clientes e serviços. Extensões de canal podem implementar a nova funcionalidade de protocolo, como a segurança. Extensões de canal de transporte também funcionalidades, como implementar um novo transporte de rede para transportar mensagens SOAP.  
  
 [Estendendo a segurança](../../../../docs/framework/wcf/extending/extending-security.md)  
 Segurança em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consiste em segurança de transferência (integridade, confidencialidade e autenticação), o controle de acesso (autorização) e auditoria. As classes encontradas no `IdentityModel` namespace são usados por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para controle de acesso. Noções básicas sobre a arquitetura de segurança permite que você crie tipos de declaração personalizada para acomodar sistemas de controle de acesso personalizados.  
  
 [Estendendo o sistema de metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistema de metadados é um grupo de interfaces e classes que representam os metadados necessários para implementar aplicativos baseados em serviço. Modificar ou estender as classes de ou implementar e configurar as interfaces para exportar e importar metadados personalizados, como extensões WSDL Web Services Description Language () ou asserções de WS-PolicyAttachments personalizadas.  
  
 [Estendendo codificadores e serializadores](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 Serializadores e codificadores convertem dados de um formulário para outro. Os tópicos nesta seção abordam como estender as classes fornecidas para atender aos requisitos especiais.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [Detalhes de recursos do WCF](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [Diretrizes e práticas recomendadas](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
