---
title: Cenários sem suporte
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
caps.latest.revision: 43
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cfeca11f7d78e8aa2d201238e3a485576b3e0c82
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="unsupported-scenarios"></a>Cenários sem suporte
Por várias razões, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] não oferece suporte a alguns cenários de segurança específico. Por exemplo, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition não implementa os protocolos de autenticação SSPI ou Kerberos e, portanto, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não oferece suporte à execução de um serviço com a autenticação do Windows nessa plataforma. Outros mecanismos de autenticação, como nome de usuário/senha e a autenticação integrada do HTTP/HTTPS são suportados ao executar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no Windows XP Home Edition.  
  
## <a name="impersonation-scenarios"></a>Cenários de representação  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Identidade representada não pode fluir quando os clientes fazem chamadas assíncronas  
 Quando um cliente WCF faz chamadas assíncronas para um serviço WCF usando a autenticação do Windows em representação, autenticação pode ocorrer com a identidade do processo de cliente em vez da identidade representada.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP e o Cookie de Token de contexto de segurança habilitado  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não dá suporte à representação e um <xref:System.InvalidOperationException> é lançada quando existem as seguintes condições:  
  
-   O sistema operacional é [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   O modo de autenticação resulta em uma identidade do Windows.  
  
-   A propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> do <xref:System.ServiceModel.OperationBehaviorAttribute> é definida como <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
-   Um token de contexto de segurança com base em estado (SCT) é criado (por padrão, a criação está desabilitada).  
  
 O SCT baseadas em estado só pode ser criado usando uma associação personalizada. Para obter mais informações, consulte [como: criar um Token de contexto de segurança para uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).) No código, o token é habilitado por meio da criação de um elemento de associação de segurança (o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) usando o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> ou o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> método e configuração de `requireCancellation` parâmetro para `false`. O parâmetro refere-se ao cache do SCT. Definir o valor como `false` habilita o recurso SCT baseadas em estado.  
  
 Como alternativa, na configuração, o token é habilitado por meio da criação um <`customBinding`>, adicionando um <`security`> elemento e configuração de `authenticationMode` atributo SecureConversation e o `requireSecurityContextCancellation` atributo `true`.  
  
> [!NOTE]
>  Os requisitos acima são específicos. Por exemplo, o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> cria um elemento de associação que resulta em uma identidade do Windows, mas não estabelece um SCT. Portanto, você pode usá-lo com o `Required` opção [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Possíveis conflitos de ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] podem habilitar ou desabilitar a representação. Quando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hosts um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, um conflito pode existir entre o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] definições de configuração. Em caso de conflito, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuração terá precedência, a menos que o <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> está definida como <xref:System.ServiceModel.ImpersonationOption.NotAllowed>, caso em que o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] representação configuração terá precedência.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Cargas de assembly podem falhar em representação  
 Se o contexto representado não tem direitos de acesso para carregar um assembly e se for a primeira vez que o common language runtime (CLR) está tentando carregar o assembly para AppDomain, o <xref:System.AppDomain> armazena em cache a falha. Falha nas tentativas subsequentes de carregar o assembly (ou assemblies), mesmo depois de reverter a representação e até mesmo se o contexto revertido tem direitos de acesso para carregar o assembly. Isso ocorre porque o CLR não tenta novamente a carga depois que o contexto de usuário é alterado. Você deve reiniciar o domínio do aplicativo para se recuperar da falha.  
  
> [!NOTE]
>  O valor padrão para o <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> propriedade o <xref:System.ServiceModel.Security.WindowsClientCredential> classe é <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. Na maioria dos casos, um contexto de representação de nível de identificação não tem direitos para carregar todos os assemblies adicionais. Este é o valor padrão, portanto, esta é uma condição muito comuns a serem consideradas. Representação de nível de identificação também ocorre quando o processo de representação não tiver o `SeImpersonate` privilégio. Para obter mais informações, consulte [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>A delegação exige a negociação de credencial  
 Para usar o protocolo de autenticação Kerberos com delegação, você deve implementar o protocolo Kerberos com a negociação de credencial (às vezes chamada de Kerberos vários trecho ou várias etapas). Se você implementar a autenticação Kerberos sem negociação de credencial (às vezes chamada de Kerberos única ou segmento único), uma exceção será lançada. Para obter mais informações sobre como implementar a negociação de credencial, consulte [depurando erros de autenticação do Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Criptografia  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256 tem suportada apenas para os usos de chave simétricos  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte a uma variedade de criptografia e assinatura de criação de algoritmos de compilação que você pode especificar usando o conjunto de algoritmos nas associações fornecidas pelo sistema. Para maior segurança, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dá suporte a algoritmos de Secure Hash Algorithm (SHA) 2, especificamente SHA-256, para criar hashes de resumo da assinatura. Esta versão dá suporte a SHA-256 somente para usos de chave simétricos, tais como chaves de Kerberos, e onde um certificado x. 509 não é usado para assinar a mensagem. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não oferece suporte a assinaturas RSA (usadas em certificados x. 509) usando o hash SHA-256 devido à falta de suporte atual para RSA-SHA256 no [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>Compatível com FIPS hash SHA-256 não tem suportada  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não suporta compatível com FIPS SHA-256 hashes, portanto não há suporte para pacotes de algoritmo que usam o SHA-256 por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em sistemas em que é necessário o uso de algoritmos compatíveis com FIPS.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Algoritmos compatíveis com FIPS podem falhar se o registro está sendo editado  
 Você pode habilitar e desabilitar FIPS Federal Information Processing Standards () - algoritmos compatíveis com usando o snap Local segurança configurações Microsoft Management Console (MMC) - no. Você também pode acessar a configuração no registro. No entanto, observe que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não dá suporte ao uso do registro para redefinir a configuração. Se o valor é definido como qualquer coisa diferente de 1 ou 0, podem ocorrer resultados inconsistentes entre o CLR e o sistema operacional.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>Limitação de criptografia AES compatível com FIPS  
 Criptografia de AES compatível com FIPS não funciona em retornos de chamada duplex na representação de nível de identificação.  
  
### <a name="cngksp-certificates"></a>Certificados CNG/KSP  
 *: API geração CNG (Cryptography Next)* é a substituição de longo prazo para o CryptoAPI. Esta API está disponível em código não gerenciado em [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] e versões posteriores do Windows.  
  
 .NET framework 4.6.1 e versões anteriores não dão suporte a esses certificados porque eles usam o CryptoAPI herdado para lidar com certificados CNG/KSP. O uso desses certificados com o .NET Framework 4.6.1 e versões anteriores fará com que uma exceção.  
  
 Há duas maneiras de saber se um certificado usa o KSP:  
  
-   Fazer um `p/invoke` de `CertGetCertificateContextProperty`e inspecionar `dwProvType` no `CertGetCertificateContextProperty`.  
  
-   Use o `certutil` comando da linha de comando de consulta de certificados. Para obter mais informações, consulte [tarefas do Certutil para solucionar problemas de certificados](http://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>Falha de segurança de mensagem se é necessário usar a representação do ASP.NET e compatibilidade com ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não oferece suporte a seguinte combinação de configurações, porque eles podem impedir que a autenticação do cliente ocorra:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Representação está habilitada. Isso é feito no arquivo Web. config, definindo o `impersonate` atributo do <`identity`> elemento `true`.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade é habilitado definindo o `aspNetCompatibilityEnabled` atributo do [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) para `true`.  
  
-   Segurança de modo de mensagem é usada.  
  
 A solução é desativar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade. Ou, se o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade é necessário, desative o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso de representação e use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-fornecida a representação em vez disso. Para obter mais informações, consulte [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>Falha de Literal de endereço IPv6  
 Solicitações de segurança falharem quando o cliente e o serviço estiverem no mesmo computador, e os endereços IPv6 literais são usados para o serviço.  
  
 Literal IPv6 endereços trabalho se o cliente e serviço estão em computadores diferentes.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Falhas de recuperação de WSDL com confiança federada  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requer exatamente um documento WSDL para cada nó da cadeia de confiança federada. Tenha cuidado para não configurar um loop ao especificar pontos de extremidade. Uma maneira em que podem surgir loops está usando um download WSDL cadeias de relação de confiança federada com dois ou mais links no mesmo documento WSDL. Um cenário comum que pode produzir esse problema é um serviço federado em que o servidor de Token de segurança e o serviço estão contidos dentro do mesmo ServiceHost.  
  
 Um exemplo dessa situação é um serviço com três endereços de ponto de extremidade a seguir:  
  
-   http://localhost/CalculatorService/service (o serviço)  
  
-   http://localhost/CalculatorService/issue_ticket (STS)  
  
-   http://localhost/CalculatorService/mex (o ponto de extremidade de metadados)  
  
 Isso gera uma exceção.  
  
 Você pode fazer neste cenário de trabalho colocando o `issue_ticket` ponto de extremidade em outro lugar.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>Atributos de importação WSDL pode ser perdido  
 WCF perde o controle dos atributos em uma `<wst:Claims>` elemento em um `RST` modelo ao executar uma importação WSDL. Isso ocorre durante uma importação WSDL, se você especificar `<Claims>` diretamente no `WSFederationHttpBinding.Security.Message.TokenRequestParameters` ou `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` em vez de usar as coleções de tipo de declaração diretamente.  Desde que a importação perde os atributos, a associação não ida e volta corretamente através de WSDL e, portanto, está incorreta no lado do cliente.  
  
 A correção é modificar a associação diretamente no cliente depois de fazer a importação.  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
