---
title: Migrando serviços Web de WSE 3.0 para o WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 8f79674350109d111fe263704dee6c40c1a12451
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184579"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrando serviços Web de WSE 3.0 para o WCF
Os benefícios da migração dos serviços da Web WSE 3.0 para o Windows Communication Foundation (WCF) incluem melhor desempenho e suporte a transportes adicionais, cenários adicionais de segurança e especificações WS-*. Um serviço web que é migrado de WSE 3.0 para WCF pode experimentar até uma melhoria de desempenho de 200% a 400%. Para obter mais informações sobre os transportes suportados pelo WCF, consulte [Escolhendo um Transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Para obter uma lista dos cenários suportados pelo WCF, consulte [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Para obter uma lista das especificações suportadas pelo WCF, consulte Guia de [Interoperabilidade de Protocolos de Serviços Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 As seções a seguir fornecem orientações sobre como migrar um recurso específico de um serviço Web WSE 3.0 para O WCF.  
  
## <a name="general"></a>Geral  
 Os aplicativos WSE 3.0 e WCF incluem interoperabilidade de nível de fio e um conjunto comum de terminologia. Os aplicativos WSE 3.0 e WCF são interoperáveis em nível de fio com base no conjunto de especificações WS-* que ambos suportam. Quando um aplicativo WSE 3.0 ou WCF é desenvolvido, há um conjunto comum de terminologia, como os nomes das afirmações de segurança turnkey no WSE e os modos de autenticação.  
  
 Embora existam muitos aspectos semelhantes entre os modelos de programação WCF e ASP.NET ou WSE 3.0, eles são diferentes. Para obter detalhes sobre o modelo de programação wcf, consulte [Ciclo de vida da programação básica](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
> Para migrar um serviço WSE Web para o WCF, a ferramenta [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode ser usada para gerar um cliente. Esse cliente, no entanto, contém interfaces e classes que podem ser usadas como ponto de partida para um serviço WCF também. As interfaces geradas <xref:System.ServiceModel.OperationContractAttribute> têm o atributo aplicado aos <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> membros do `*`contrato com o imóvel definido para . Quando um cliente WSE chama um serviço web com essa configuração, a seguinte exceção é lançada: **Web.Services3.ResponseProcessingException: WSE910: Um erro aconteceu durante o processamento de uma mensagem de resposta, e você pode encontrar o erro na exceção interna**. Para mitigar isso, <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> defina <xref:System.ServiceModel.OperationContractAttribute> a propriedade`null` do atributo `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`como um não-valor, como .  
  
## <a name="security"></a>Segurança  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Serviços Web WSE 3.0 que são protegidos usando um arquivo de diretiva  
 Os serviços WCF podem usar um arquivo de configuração para proteger um serviço e esse mecanismo é semelhante a um arquivo de diretiva WSE 3.0. No WSE 3.0 ao proteger um serviço da Web usando um arquivo de diretiva, você usa uma afirmação de segurança turnkey ou uma afirmação de política personalizada. As afirmações de segurança turnkey mapeiam de perto o modo de autenticação de um elemento de vinculação de segurança WCF. Não só os modos de autenticação WCF e as afirmações de segurança wse 3.0 são nomeados iguais ou similarmente, eles protegem as mensagens usando os mesmos tipos de credenciais. Por exemplo, `usernameForCertificate` a afirmação de segurança turnkey `UsernameForCertificate` em mapas WSE 3.0 para o modo de autenticação no WCF. Os exemplos de código a seguir demonstram `usernameForCertificate` como uma política mínima que usa `UsernameForCertificate` a afirmação de segurança turnkey em mapas WSE 3.0 para um modo de autenticação no WCF em uma vinculação personalizada.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **Wcf**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 Para migrar as configurações de segurança de um serviço Web WSE 3.0 especificado em um arquivo de diretiva para WCF, uma vinculação personalizada deve ser criada em um arquivo de configuração e a afirmação de segurança turnkey deve ser definida para o modo de autenticação equivalente. Além disso, a vinculação personalizada deve ser configurada para usar a especificação WS-Addressing de agosto de 2004 quando os clientes WSE 3.0 se comunicam com o serviço. Quando o serviço WCF migrado não requer comunicação com clientes WSE 3.0 e deve apenas manter a paridade de segurança, considere usar as vinculações definidas pelo sistema WCF com configurações de segurança apropriadas em vez de criar uma vinculação personalizada.  
  
 A tabela a seguir lista o mapeamento entre um arquivo de diretiva WSE 3.0 e a vinculação personalizada equivalente no WCF.  
  
|Afirmação de segurança wse 3.0 turnkey|Configuração de vinculação personalizada wcf|  
|----------------------------------------|--------------------------------------|  
|\<nome de usuárioOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Segurança />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<nome de usuárioForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Segurança />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Para obter mais informações sobre a criação de vinculações personalizadas no WCF, consulte [Vinculações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Serviços Web WSE 3.0 que são protegidos usando código de aplicativo  
 Se o WSE 3.0 ou o WCF forem usados, os requisitos de segurança podem ser especificados no código do aplicativo em vez de na configuração. No WSE 3.0, isso é feito criando uma `Policy` classe que deriva da classe `Add` e, em seguida, adicionando os requisitos chamando o método. Para obter mais detalhes sobre como especificar os requisitos de segurança no código, consulte [Como: Proteger um serviço web sem usar um arquivo de diretiva](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10)). No WCF, para especificar os requisitos <xref:System.ServiceModel.Channels.BindingElementCollection> de segurança no código, crie uma instância da classe e adicione uma instância de a <xref:System.ServiceModel.Channels.SecurityBindingElement> ao <xref:System.ServiceModel.Channels.BindingElementCollection>. Os requisitos de afirmação de segurança são definidos <xref:System.ServiceModel.Channels.SecurityBindingElement> usando os métodos auxiliares do modo de autenticação estática da classe. Para obter mais detalhes sobre a especificação dos requisitos de segurança no código usando o WCF, consulte [Como: Criar uma vinculação personalizada usando o SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md) e [como: Criar um SecurityBindingElement para um modo de autenticação especificado](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Afirmação de política personalizada do WSE 3.0  
 No WSE 3.0 existem dois tipos de afirmações de políticas personalizadas: aquelas que seguram uma mensagem SOAP e aquelas que não seguram uma mensagem SOAP. As afirmações de política que protegem as `SecurityPolicyAssertion` mensagens SOAP derivam da <xref:System.ServiceModel.Channels.SecurityBindingElement> classe WSE 3.0 e o equivalente conceitual no WCF é a classe.  
  
 Um ponto importante a notar é que as afirmações de segurança turnkey wse 3.0 são um subconjunto dos modos de autenticação WCF. Se você criou uma afirmação de política personalizada no WSE 3.0, pode haver um modo de autenticação WCF equivalente. Por exemplo, o WSE 3.0 não fornece uma afirmação `UsernameOverTransport` de segurança CertificateOverTransport que é equivalente à afirmação de segurança turnkey, mas usa um certificado X.509 para fins de autenticação do cliente. Se você definiu sua própria afirmação de política personalizada para este cenário, o WCF torna a migração simples. O WCF define um modo de autenticação para este cenário, para que você possa aproveitar os<xref:System.ServiceModel.Channels.SecurityBindingElement>métodos auxiliares do modo de autenticação estática para configurar um WCF .  
  
 Quando não há um modo de autenticação WCF que seja equivalente a uma afirmação <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>de política personalizada que proteja mensagens SOAP, obtenha uma classe de <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>classes ou WCF e especifique o elemento de vinculação equivalente. Para obter mais detalhes, [consulte Como: Criar uma vinculação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Para converter uma afirmação de diretiva personalizada que não proteja uma mensagem SOAP, consulte [Filtragem](../../../../docs/framework/wcf/feature-details/filtering.md) e o [Interceptor de Mensagens Personalizados](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)de exemplo .  
  
### <a name="wse-30-custom-security-token"></a>Token de segurança personalizado WSE 3.0  
 O modelo de programação WCF para criar um token personalizado é diferente do WSE 3.0. Para obter detalhes sobre a criação de um token personalizado no WSE, consulte [Criando Tokens de segurança personalizados](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10)). Para obter detalhes sobre a criação de um token personalizado no WCF, consulte [Como: Criar um Token Personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 Gerenciador de tokens personalizados  
 O modelo de programação para criar um gerenciador de tokens personalizado é diferente no WCF do que o WSE 3.0. Para obter detalhes sobre como criar um gerenciador de tokens personalizado e os outros componentes necessários para um token de segurança personalizado, consulte [Como: Criar um Token Personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
> Se você criou um `UsernameToken` gerenciador de tokens de segurança personalizado, o WCF fornecerá um mecanismo mais fácil para especificar a lógica de autenticação do que criar um gerenciador de tokens de segurança personalizado. Para obter mais detalhes, [consulte Como: Usar um nome de usuário personalizado e validador de senhas](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Serviços Web WSE 3.0 que usam mensagens SOAP codificadas pelo MTOM  
 Como um aplicativo WSE 3, um aplicativo WCF pode especificar a codificação de mensagem MTOM na configuração. Para migrar essa configuração, adicione o [ \<>mtomMessageEncoding](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) à vinculação do serviço. O exemplo de código a seguir demonstra como a codificação MTOM é especificada no WSE 3.0 para um serviço equivalente em WCF.  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **Wcf**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>Mensagens  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>Aplicativos WSE 3.0 que usam a API de mensagens WSE  

 Quando a API de mensagens WSE é usada para obter acesso direto ao XML que é comunicado entre o cliente e o serviço web, o aplicativo pode ser convertido para usar "Plain Old XML" (POX). Para obter mais detalhes sobre a POX, consulte [Interoperabilidade com aplicações pox](interoperability-with-pox-applications.md). Para obter mais detalhes sobre a API de mensagens WSE, consulte [Enviar e receber mensagens de SABÃO usando a API de mensagens WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10)).  
  
## <a name="transports"></a>Transportes  
  
### <a name="tcp"></a>TCP  
 Por padrão, os clientes WSE 3.0 e os serviços da Web que enviam mensagens SOAP usando o transporte TCP não interoperam com clientes WCF e serviços web. Essa incompatibilidade deve-se a diferenças no enquadramento utilizado no protocolo TCP e por razões de desempenho. No entanto, uma amostra wcf detalha como implementar uma sessão TCP personalizada que interopera com o WSE 3.0. Para obter detalhes sobre esta amostra, consulte [Transporte: Interoperabilidade WSE 3.0 TCP](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Para especificar que um aplicativo WCF usa o transporte TCP, use o [ \<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Transporte personalizado  
 O equivalente a um transporte personalizado WSE 3.0 no WCF é uma extensão de canal. Para obter detalhes sobre a criação de uma extensão de canal, consulte [Estendendo a camada do canal](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Confira também

- [Ciclo de vida de programação básica](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Como criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
