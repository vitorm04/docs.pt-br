---
title: "Associações personalizadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 07247573678d81bb45f8b4b7f07a453573326cbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="custom-bindings"></a>Associações personalizadas
Você pode usar o <xref:System.ServiceModel.Channels.CustomBinding> classe quando uma das associações fornecidas pelo sistema não atende aos requisitos de seu serviço. Todas as associações são construídas a partir de um conjunto ordenado de elementos de associação. Associações personalizadas podem ser criadas a partir de um conjunto de elementos de associação fornecida pelo sistema ou podem incluir elementos de associação personalizada definida pelo usuário. Você pode usar elementos de associação personalizada, por exemplo, para habilitar o uso de novos transportes ou codificadores em um ponto de extremidade de serviço. Para obter exemplos de funcionamento, consulte [amostras de associação personalizado](http://msdn.microsoft.com/en-us/657e8143-beb0-472d-9cfe-ed1a19c2ab08). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
## <a name="construction-of-a-custom-binding"></a>Construção de uma associação personalizada  
 Uma associação personalizada é criada usando o <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> construtor de uma coleção de elementos que estão "empilhados" em uma ordem específica de associação:  
  
-   Na parte superior é um recurso opcional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> classe que permite que o fluxo de transações.  
  
-   Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> classe que fornece uma sessão e mecanismos de ordenação, conforme definido na especificação WS-ReliableMessaging. Uma sessão pode cruzar com intermediários SOAP e transporte.  
  
-   Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.SecurityBindingElement> classe que fornece recursos de segurança como autenticação, autorização, proteção e confidencialidade.  
  
-   Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> classe que fornece a capacidade de ter dois comunicação duplex forma com um protocolo de transporte que não oferecem suporte à comunicação duplex nativamente, como HTTP.  
  
-   Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.OneWayBindingElement>) classe que fornece comunicação unidirecional.  
  
-   Em seguida, é um elemento de associação de segurança de fluxo opcional que pode ser um destes procedimentos.  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Em seguida, é um elemento de associação de codificação de mensagem necessário. Você pode usar seu próprio codificador de mensagem ou uma das três associações de codificação de mensagem:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 Na parte inferior é um elemento de transporte necessário. Você pode usar seu próprio transporte ou um dos seguintes elementos de associação de transporte [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fornece:  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 A tabela a seguir resume as opções para cada camada.  
  
|Camada|Opções|Necessária|  
|-----------|-------------|--------------|  
|Transações|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Não|  
|Confiabilidade|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Não|  
|Segurança|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Não|  
|Codificando|Texto, personalizada de binário, mensagem de transmissão de otimização do mecanismo (MTOM)|Sim|  
|Transporte|TCP, HTTP, HTTPS, chamado pipes (também conhecido como IPC), ponto a ponto (P2P), o serviço de enfileiramento de mensagens (também conhecido como MSMQ), personalizado|Sim|  
  
 Além disso, você pode definir seus próprios elementos de associação e inseri-los entre qualquer uma das camadas de definido anteriores.  
  
## <a name="see-also"></a>Consulte também  
 [Endpoint Creation Overview](../../../../docs/framework/wcf/endpoint-creation-overview.md) (Visão geral de criação de ponto de extremidade)  
 [Using Bindings to Configure Services and Clients](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md) (Usando associações para configurar serviços e clientes)  
 [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md) (Associações fornecidas pelo sistema)  
 [Como: personalizar uma associação fornecida pelo sistema](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Associação personalizada](../../../../docs/framework/wcf/samples/custom-binding.md)
