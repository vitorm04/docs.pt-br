---
title: Associações personalizadas
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 9998daad2d44ff564061a4f73dde4b75648c33d1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587319"
---
# <a name="custom-bindings"></a>Associações personalizadas
Você pode usar o <xref:System.ServiceModel.Channels.CustomBinding> classe quando uma das associações fornecidas pelo sistema não atende aos requisitos do seu serviço. Todas as associações são construídas a partir de um conjunto ordenado de elementos de associação. Associações personalizadas podem ser criadas a partir de um conjunto de elementos de associação fornecida pelo sistema ou podem incluir elementos de associação personalizado definido pelo usuário. Você pode usar elementos de associação personalizado, por exemplo, para habilitar o uso de novos transportes ou codificadores em um ponto de extremidade de serviço. Para obter exemplos de funcionamento, consulte [exemplos de associação personalizado](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)). Para obter mais informações, consulte [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
## <a name="construction-of-a-custom-binding"></a>Construção de uma associação personalizada  
 Uma associação personalizada é criada usando o <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> construtor de uma coleção de elementos de associação que são "empilhados" em uma ordem específica:  
  
- Na parte superior é um recurso opcional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> classe que permite que o fluxo de transações.  
  
- Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> classe que fornece uma sessão e mecanismos de ordenação, conforme definido na especificação WS-ReliableMessaging. Uma sessão pode cruzar intermediários SOAP e transporte.  
  
- Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.SecurityBindingElement> classe que fornece recursos de segurança como autenticação, autorização, proteção e confidencialidade.  
  
- Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> classe que fornece a capacidade de ter dois comunicação duplex forma com um protocolo de transporte que não dão suporte à comunicação duplex nativamente, como HTTP.  
  
- Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.OneWayBindingElement>) classe que fornece comunicação unidirecional.  
  
- Em seguida, é um elemento de associação de segurança de fluxo opcional que pode ser um dos procedimentos a seguir.  
  
    - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
- Em seguida, é um elemento de associação de codificação de mensagem necessário. Você pode usar seu próprio codificador de mensagem ou uma das três associações de codificação de mensagem:  
  
    - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 Na parte inferior é um elemento de transporte obrigatório. Você pode usar seu próprio transporte ou um dos seguintes elementos de associação de transporte fornece Windows Communication Foundation (WCF):  
  
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 A tabela a seguir resume as opções para cada camada.  
  
|Camada|Opções|Necessária|  
|-----------|-------------|--------------|  
|Transações|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Não|  
|Confiabilidade|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Não|  
|Segurança|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Não|  
|Codificando|Texto, personalizada de binário, MTOM Message Transmission Optimization Mechanism (),|Sim|  
|Transporte|TCP, HTTP, HTTPS, chamado pipes (também conhecido como IPC), ponto a ponto (P2P), o serviço de enfileiramento de mensagens (também conhecido como MSMQ), personalizado|Sim|  
  
 Além disso, você pode definir seus próprios elementos de associação e inseri-los entre qualquer uma das camadas anteriores definidas.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de criação de ponto de extremidade](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Usando associações para configurar serviços e clientes](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Como: Personalizar uma associação fornecida pelo sistema](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
- [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Associação personalizada](../../../../docs/framework/wcf/samples/custom-binding.md)
