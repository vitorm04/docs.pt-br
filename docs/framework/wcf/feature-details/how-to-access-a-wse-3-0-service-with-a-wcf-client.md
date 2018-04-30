---
title: Como acessar um serviço WSE 3.0 com um cliente do WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 382762917e790d54dca31158f2b7ffde560c1427
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Como acessar um serviço WSE 3.0 com um cliente do WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] os clientes são compatíveis com o nível de transmissão com aprimoramentos WSE (Web Services) 3.0 para Microsoft .NET de serviços quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] os clientes são configurados para usar a versão de agosto de 2004 da especificação WS-Addressing. No entanto, serviços WSE 3.0 não dão suporte o protocolo de intercâmbio (MEX) de metadados, então quando você usa o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe de cliente, as configurações de segurança não são aplicadas para gerado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente. Portanto, você deve especificar as configurações de segurança que o serviço WSE 3.0 requer após o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente é gerado.  
  
 Você pode aplicar essas configurações de segurança usando uma associação personalizada para levar em conta os requisitos do serviço WSE 3.0 e os requisitos de interoperabilidade entre um serviço WSE 3.0 e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente. Esses requisitos de interoperabilidade incluem o uso mencionados acima de agosto de 2004 especificação WS-Addressing e o WSE 3.0default mensagem proteção de <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. A proteção de mensagem padrão para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Este tópico fornece detalhes sobre como criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de associação que interage com um serviço WSE 3.0. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também fornece um exemplo que incorpora essa associação. Para obter mais informações sobre esse exemplo, consulte [interoperar com serviços Web ASMX](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Para acessar um serviço WSE 3.0 Web com um cliente do WCF  
  
1.  Execute o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente para o serviço Web do WSE 3.0.  
  
     Para um serviço WSE 3.0 Web, um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente é criado. Como WSE 3.0 não dá suporte ao protocolo MEX, você não pode usar a ferramenta para recuperar os requisitos de segurança para o serviço Web. O desenvolvedor do aplicativo deve adicionar as configurações de segurança para o cliente.  
  
     Para obter mais informações sobre como criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, consulte o [como: criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Crie uma classe que representa uma associação que pode se comunicar com serviços WSE 3.0 Web.  
  
     A seguinte classe faz parte do [interoperar com WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) exemplo:  
  
    1.  Crie uma classe que derive da classe <xref:System.ServiceModel.Channels.Binding>.  
  
         O exemplo de código a seguir cria uma classe denominada `WseHttpBinding` que deriva de <xref:System.ServiceModel.Channels.Binding> classe.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Adicione propriedades à classe que especificam a declaração completa de WSE usada pelo serviço de WSE, se as chaves derivadas são necessárias, se sessões seguras são usadas, se as confirmações de assinatura são necessárias e as configurações de proteção de mensagem. WSE 3.0, uma declaração completa Especifica os requisitos de segurança para um cliente ou serviço da Web — semelhante ao modo de autenticação de uma associação em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
         O exemplo de código a seguir define o `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, e `MessageProtectionOrder` propriedades que especificam a declaração completa de WSE, se as chaves derivadas são necessárias, se sessões seguras são usadas, se assinatura confirmações são necessárias e as configurações de proteção de mensagem, respectivamente.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Substituir o <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método para definir as propriedades de associação.  
  
         O exemplo de código a seguir especifica o transporte, a codificação de mensagem e as configurações de proteção de mensagem, fazendo com que os valores da `SecurityAssertion` e `MessageProtectionOrder` propriedades.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  No código do aplicativo cliente, adicione código para definir as propriedades de associação.  
  
     O exemplo de código a seguir especifica que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente deve usar a autenticação e proteção de mensagem conforme definido pelo WSE 3.0 `AnonymousForCertificate` asserção de segurança completa. Além disso, sessões seguras e chaves derivadas são necessárias.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define uma associação personalizada que expõe propriedades que correspondem às propriedades de uma asserção de segurança completa de WSE 3.0. Essa associação personalizada, que é chamada de `WseHttpBinding`, é usado para especificar as propriedades de associação para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente que se comunica com o exemplo de início rápido do WSSecurityAnonymous WSE 3.0.  
  
  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.Binding>  
 [Interoperando com WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
