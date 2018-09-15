---
title: Migrando serviços Web de WSE 3.0 para o WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 21e36be178bb0dd0c52213d8c4c1387a564a0e5a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649413"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrando serviços Web de WSE 3.0 para o WCF
Os benefícios da migração de serviços Web do WSE 3.0 para o Windows Communication Foundation (WCF) incluem melhor desempenho e o suporte de transportes adicionais, cenários de segurança adicional e WS-* especificações. Um serviço Web que for migrado do WSE 3.0 para o WCF pode apresentar até uma melhoria de desempenho de 200 a 400%. Para obter mais informações sobre os transportes com suporte do WCF, consulte [escolhendo um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Para obter uma lista dos cenários com suporte do WCF, consulte [cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Para obter uma lista das especificações que são compatíveis com o WCF, consulte [guia de interoperabilidade de protocolos de serviços Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 As seções a seguir fornecem orientação sobre como migrar de um recurso específico de um serviço Web do WSE 3.0 para o WCF.  
  
## <a name="general"></a>Geral  
 Aplicativos WCF e do WSE 3.0 incluem a interoperabilidade de nível de transmissão e um conjunto comum de terminologia. Aplicativos WCF e do WSE 3.0 estão no nível de transmissão interoperável com base no conjunto de WS-* especificações que dão suporte a ambos. Quando um aplicativo do WSE 3.0 ou o WCF foi desenvolvido há um conjunto comum de terminologia, como os nomes das asserções de segurança pronta para uso em WSE e os modos de autenticação.  
  
 Embora há muitos aspectos semelhantes entre o WCF e ASP.NET ou modelos de programação do WSE 3.0, eles são diferentes. Para obter detalhes sobre o modelo de programação do WCF, consulte [ciclo de vida de programação básica](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
>  Para migrar um serviço Web de WSE para o WCF a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta pode ser usada para gerar um cliente. No entanto, esse cliente contém interfaces e classes que podem ser usadas como uma partida muito apontam para um serviço WCF. As interfaces que são geradas têm o <xref:System.ServiceModel.OperationContractAttribute> atributo aplicado aos membros do contrato com o <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> propriedade definida como `*`. Quando um cliente do WSE chama um serviço Web com essa configuração, a seguinte exceção é lançada: **Web.Services3.ResponseProcessingException: WSE910: Ocorreu um erro durante o processamento de uma mensagem de resposta, e você encontrará o erro interno exceção**. Para atenuar isso, defina as <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> propriedade do <xref:System.ServiceModel.OperationContractAttribute> atributo para um`null` de valor, tal como `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Segurança  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Serviços Web do WSE 3.0 que são protegidos usando um arquivo de política  
 Serviços WCF podem usar um arquivo de configuração para proteger um serviço e esse mecanismo é semelhante a um arquivo de diretiva do WSE 3.0. O WSE 3.0 ao proteger um serviço Web usando um arquivo de política, você usa uma asserção de segurança pronta para uso ou uma declaração de política personalizada. As asserções de segurança turnkey mapeiam com precisão até o modo de autenticação de um elemento de associação de segurança do WCF. Não só são os modos de autenticação do WCF e WSE 3.0 asserções de segurança pronta para uso com o mesmo nome ou da mesma forma, eles protegem as mensagens usando os mesmos tipos de credencial. Por exemplo, o `usernameForCertificate` asserção de segurança pronta para uso em WSE 3.0 é mapeado para o `UsernameForCertificate` modo de autenticação no WCF. Os exemplos de código a seguir demonstram como uma política mínima que usa o `usernameForCertificate` asserção de segurança pronta para uso em WSE 3.0 é mapeado para um `UsernameForCertificate` modo de autenticação no WCF em uma associação personalizada.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 Para migrar as configurações de segurança de um serviço Web do WSE 3.0 que são especificadas em um arquivo de política para o WCF, uma ligação personalizada deve ser criada em um arquivo de configuração e a declaração de segurança turnkey deve ser definida para o modo de autenticação equivalente. Além disso, a associação personalizada deve ser configurada para usar o agosto de 2004 especificação WS-Addressing quando os clientes do WSE 3.0 se comunicar com o serviço. Quando o serviço WCF migrado não requer comunicação com clientes WSE 3.0 e só deve manter a paridade de segurança, considere usar as ligações do WCF definida pelo sistema com configurações de segurança apropriadas em vez de criar uma ligação personalizada.  
  
 A tabela a seguir lista o mapeamento entre um arquivo de diretiva do WSE 3.0 e a associação personalizada equivalente no WCF.  
  
|Asserção do WSE 3.0 segurança pronta para uso|Configuração de associação personalizada do WCF|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Para obter mais informações sobre como criar associações personalizadas no WCF, consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Serviços Web do WSE 3.0 que são protegidos usando o código do aplicativo  
 Se o WSE 3.0 ou do WCF é usado, os requisitos de segurança podem ser especificados no código do aplicativo em vez de na configuração. WSE 3.0, isso é feito criando uma classe que deriva de `Policy` classe e, em seguida, adicionando os requisitos, chamando o `Add` método. Para obter mais detalhes sobre como especificar os requisitos de segurança no código, consulte [como: proteger um serviço Web sem usando um arquivo de política](https://go.microsoft.com/fwlink/?LinkId=73747). No WCF, para especificar os requisitos de segurança no código, crie uma instância das <xref:System.ServiceModel.Channels.BindingElementCollection> de classe e adicionar uma instância de um <xref:System.ServiceModel.Channels.SecurityBindingElement> para o <xref:System.ServiceModel.Channels.BindingElementCollection>. Os requisitos de asserção de segurança são definidos usando os métodos de auxiliares de modo de autenticação estático do <xref:System.ServiceModel.Channels.SecurityBindingElement> classe. Para obter mais detalhes sobre como especificar os requisitos de segurança no código usando o WCF, consulte [como: criar um personalizado de associação usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) e [como: criar um SecurityBindingElement para um especificado Modo de autenticação](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Asserção do WSE 3.0 política personalizada  
 O WSE 3.0, há dois tipos de asserções de política personalizada: aqueles que proteger uma mensagem SOAP e aqueles que não proteger uma mensagem SOAP. Declarações de política que proteger mensagens SOAP derivam de WSE 3.0 `SecurityPolicyAssertion` classe e o equivalente conceitual no WCF é a <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.  
  
 Um ponto importante a observar é que as declarações de segurança pronta para uso do WSE 3.0 são um subconjunto dos modos de autenticação do WCF. Se você tiver criado uma declaração de política personalizada do WSE 3.0, pode haver um modo de autenticação equivalente do WCF. Por exemplo, o WSE 3.0 não oferece uma asserção de segurança de CertificateOverTransport equivale a `UsernameOverTransport` asserção de segurança de uso imediato, mas usa um certificado x. 509 para fins de autenticação de cliente. Se você tiver definido sua própria declaração de política personalizada para esse cenário, o WCF simplifica a migração. O WCF define um modo de autenticação para esse cenário, portanto, você pode tirar proveito da autenticação estática de métodos de auxiliares de modo a configurar um WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 Quando não há um modo de autenticação do WCF que é equivalente a uma declaração de política personalizada que protege as mensagens SOAP, derive uma classe de <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF classes e especifique o elemento de associação equivalente. Para obter mais detalhes, consulte [como: criar um personalizado de associação usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Para converter uma declaração de política personalizada que não a protege uma mensagem SOAP, consulte [Filtering](../../../../docs/framework/wcf/feature-details/filtering.md) e o exemplo [interceptador de mensagem personalizado](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Token de segurança personalizada 3.0 do WSE  
 O modelo de programação do WCF para a criação de um token personalizado é diferente de WSE 3.0. Para obter detalhes sobre como criar um token personalizado no WSE, consulte [criação de Tokens de segurança personalizados](https://go.microsoft.com/fwlink/?LinkID=73750). Para obter detalhes sobre como criar um token personalizado no WCF, consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>O WSE 3.0 Gerenciador de Token personalizado  
 O modelo de programação para a criação de um Gerenciador de token personalizado é diferente no WCF de WSE 3.0. Para obter detalhes sobre como criar um Gerenciador de token personalizado e outros componentes que são necessários para um token de segurança personalizada, consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
>  Se você tiver criado um personalizado `UsernameToken` Gerenciador de token de segurança, o WCF fornece um mecanismo mais fácil para especificar a lógica de autenticação que a criação de uma segurança personalizada Gerenciador de token. Para obter mais detalhes, consulte [como: usar um nome de usuário personalizada e um validador de senha](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Serviços Web do WSE 3.0 que usam MTOM codificada em mensagens SOAP  
 Como um aplicativo de 3 do WSE, um aplicativo WCF pode especificar a mensagem MTOM na configuração de codificação. Para migrar essa configuração, adicione a [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) para a associação para o serviço. O exemplo de código a seguir demonstra como codificação MTOM é especificado no WSE 3.0 para um serviço que é equivalente no WCF.  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>Mensagens  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>O WSE 3.0 aplicativos que usam a API de mensagens do WSE  
 Quando a API de mensagens do WSE é usado para obter acesso direto ao XML que é comunicado entre o cliente e o serviço Web, o aplicativo pode ser convertido para usar "Plain Old XML" (POX). Para obter mais detalhes sobre POX, consulte [interoperabilidade com aplicativos de POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). Para obter mais detalhes sobre a API de mensagens do WSE, consulte [de envio e recebimento de mensagens usando o WSE mensagens API SOAP](https://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Transportes  
  
### <a name="tcp"></a>TCP  
 Por padrão, os clientes do WSE 3.0 e serviços da Web que enviam mensagens SOAP usando o transporte TCP não interoperam com clientes e serviços Web WCF. Essa incompatibilidade é devido a diferenças no enquadramento usado no protocolo TCP e por motivos de desempenho. No entanto, um exemplo do WCF fornece detalhes sobre como implementar uma sessão TCP personalizada que interopera com o WSE 3.0. Para obter detalhes sobre este exemplo, consulte [transporte: interoperabilidade de TCP do WSE 3.0](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Para especificar que um aplicativo WCF usa o transporte TCP, use o [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Transporte personalizado  
 O equivalente de um transporte personalizado do WSE 3.0 no WCF é uma extensão de canal. Para obter detalhes sobre como criar uma extensão de canal, consulte [estendendo a camada do canal](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Consulte também  
 [Ciclo de vida de programação básica](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Como criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
