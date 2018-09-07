---
title: Como acessar um serviço WSE 3.0 com um cliente do WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 2e01d3de6ee7b415c7b3f18a20e840b8ec4ab9b6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098230"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Como acessar um serviço WSE 3.0 com um cliente do WCF
Os clientes do Windows Communication Foundation (WCF) são compatíveis com nível de transmissão com aprimoramentos de WSE (Web Services) 3.0 para serviços do Microsoft .NET quando os clientes do WCF são configurados para usar a versão de agosto de 2004 da especificação WS-Addressing. No entanto, serviços do WSE 3.0 não dão suporte o protocolo do exchange (MEX) de metadados, portanto, quando você usa o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar uma classe de cliente do WCF, as configurações de segurança não são aplicadas para gerado Cliente do WCF. Portanto, você deve especificar as configurações de segurança que o serviço WSE 3.0 requer depois que o cliente do WCF é gerado.  
  
 Você pode aplicar essas configurações de segurança, usando uma ligação personalizada para levar em conta os requisitos do serviço WSE 3.0 e os requisitos interoperáveis entre um serviço WSE 3.0 e um cliente do WCF. Esses requisitos de interoperabilidade incluem o uso mencionados anteriormente de agosto de 2004 especificação WS-Addressing e o WSE 3.0default proteção da mensagem <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. A proteção de mensagem padrão para o WCF é <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Este tópico fornece detalhes sobre como criar uma associação WCF que interopera com um serviço WSE 3.0. O WCF também fornece um exemplo que incorpora essa associação. Para obter mais informações sobre este exemplo, consulte [interoperar com serviços Web ASMX](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Para acessar um serviço Web do WSE 3.0 com um cliente WCF  
  
1.  Execute o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um cliente WCF para o serviço Web do WSE 3.0.  
  
     Para um serviço Web do WSE 3.0, um cliente do WCF é criado. Como o WSE 3.0 não oferece suporte ao protocolo MEX, é possível usar a ferramenta para recuperar os requisitos de segurança para o serviço Web. O desenvolvedor do aplicativo deve adicionar as configurações de segurança para o cliente.  
  
     Para obter mais informações sobre a criação de um cliente do WCF, consulte o [como: criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Crie uma classe que representa uma associação que pode se comunicar com os serviços Web do WSE 3.0.  
  
     A classe a seguir faz parte dos [interoperação com WSE](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) exemplo:  
  
    1.  Crie uma classe que derive da classe <xref:System.ServiceModel.Channels.Binding>.  
  
         O exemplo de código a seguir cria uma classe chamada `WseHttpBinding` que deriva de <xref:System.ServiceModel.Channels.Binding> classe.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Adicione propriedades à classe que especificam a asserção pronta para uso do WSE usada pelo serviço do WSE, se chaves derivadas são necessárias, se sessões seguras são usadas, se as confirmações de assinatura são necessárias e as configurações de proteção de mensagem. O WSE 3.0, uma asserção pronta para uso especifica os requisitos de segurança para um cliente ou serviço da Web — semelhante ao modo de autenticação de uma associação no WCF.  
  
         O exemplo de código a seguir define o `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, e `MessageProtectionOrder` propriedades que especificam a asserção pronta para uso do WSE, se as chaves derivadas são necessárias, se sessões seguras são usadas, se assinatura as confirmações são necessárias e as configurações de proteção de mensagem, respectivamente.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Substituir o <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método para definir as propriedades de associação.  
  
         O exemplo de código a seguir especifica o transporte, codificação de mensagem e as configurações de proteção de mensagem obtendo os valores de `SecurityAssertion` e `MessageProtectionOrder` propriedades.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  No código do aplicativo cliente, adicione código para definir as propriedades de associação.  
  
     O exemplo de código a seguir especifica que o cliente do WCF deve usar autenticação e proteção de mensagem, conforme definido pelo WSE 3.0 `AnonymousForCertificate` asserção de segurança pronta para uso. Além disso, sessões seguras e as chaves derivadas são necessárias.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define uma associação personalizada que expõe propriedades que correspondem às propriedades de uma asserção de segurança pronta para uso do WSE 3.0. Essa associação personalizada, que é chamada `WseHttpBinding`, em seguida, é usado para especificar as propriedades de associação para um cliente WCF que se comunica com o exemplo de início rápido do WSSecurityAnonymous WSE 3.0.  
  
  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.Binding>  
 [Interoperação com WSE](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
