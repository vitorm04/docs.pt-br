---
title: Cenários sem suporte
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: 12012f3e0c0c3b0d10c5faebfb2de881f5de3917
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178770"
---
# <a name="unsupported-scenarios"></a>Cenários sem suporte
Por vários motivos, o Windows Communication Foundation (WCF) não oferece suporte a alguns cenários de segurança específicos. Por exemplo, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition não implementa os protocolos de autenticação SSPI ou Kerberos, e, portanto, o WCF não oferece suporte a execução de um serviço com a autenticação do Windows nessa plataforma. Outros mecanismos de autenticação, como nome de usuário/senha e autenticação integrada do HTTP/HTTPS são suportados quando executados WCF em Windows XP Home Edition.  
  
## <a name="impersonation-scenarios"></a>Cenários de representação  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Identidade representada não pode fluir quando os clientes fazem chamadas assíncronas  
 Quando um cliente WCF faz chamadas assíncronas para um serviço WCF usando a autenticação do Windows sob representação, autenticação pode ocorrer com a identidade do processo de cliente em vez da identidade representada.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP e o Cookie de Token de contexto seguro habilitado  
 O WCF não dá suporte à representação e um <xref:System.InvalidOperationException> é lançada quando existem as seguintes condições:  
  
-   O sistema operacional é [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   O modo de autenticação resulta em uma identidade do Windows.  
  
-   A propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> do <xref:System.ServiceModel.OperationBehaviorAttribute> é definida como <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
-   Um token de contexto de segurança com base em estado (SCT) é criado (por padrão, a criação está desabilitada).  
  
 O SCT baseado em estado só pode ser criado usando uma associação personalizada. Para obter mais informações, confira [Como: Criar um contexto de segurança para uma sessão segura Token](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).) No código, o token está habilitado com a criação de um elemento de associação de segurança (tanto <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) usando o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> ou o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> método e a configuração do `requireCancellation` parâmetro para `false`. O parâmetro refere-se para o armazenamento em cache do SCT. Definir o valor como `false` habilita o recurso SCT baseado em estado.  
  
 Como alternativa, na configuração, o token é ativado pela criação de um <`customBinding`>, adicionando um <`security`> elemento e a configuração a `authenticationMode` SecureConversation do atributo e o `requireSecurityContextCancellation` de atributo para `true`.  
  
> [!NOTE]
>  Os requisitos anteriores são específicos. Por exemplo, o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> cria um elemento de associação que resulta em uma identidade do Windows, mas não estabelece um SCT. Portanto, você pode usá-lo com o `Required` opção [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Possível conflito de ASP.NET  
 WCF e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pode ativar ou desativar a representação. Quando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hospeda um aplicativo WCF, um conflito pode existir entre o WCF e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] definições de configuração. No caso de conflito, a configuração do WCF tem precedência, a menos que o <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> estiver definida como <xref:System.ServiceModel.ImpersonationOption.NotAllowed>, caso em que o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] representação configuração terá precedência.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Carregamentos de assembly podem falhar sob representação  
 Se o contexto representado não tem direitos de acesso para carregar um assembly e se ele estiver na primeira vez que o common language runtime (CLR) está tentando carregar o assembly para o AppDomain, o <xref:System.AppDomain> armazena em cache a falha. Tentativas subsequentes para carregar o assembly (ou assemblies) falharem, mesmo após reverter a representação e, mesmo se o contexto revertido tem direitos de acesso para carregar o assembly. Isso ocorre porque o CLR não tente realizar novamente a carga depois que o contexto do usuário for alterado. Você deve reiniciar o domínio do aplicativo para se recuperar da falha.  
  
> [!NOTE]
>  O valor padrão para o <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> propriedade do <xref:System.ServiceModel.Security.WindowsClientCredential> classe é <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. Na maioria dos casos, um contexto de representação de nível de identificação não tem direitos para carregar todos os assemblies adicionais. Isso é o valor padrão, portanto, essa é uma condição muito comuns a serem consideradas. Representação de nível de identificação também ocorre quando o processo de representação não tiver o `SeImpersonate` privilégio. Para obter mais informações, consulte [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegação exige a negociação de credencial  
 Para usar o protocolo de autenticação Kerberos com delegação, você deve implementar o protocolo Kerberos com negociação de credencial (às vezes chamada de Kerberos multi-segmentos ou de várias etapas). Se você implementar a autenticação Kerberos sem negociação de credencial (às vezes chamada de propagandas ou segmento único de Kerberos), uma exceção é lançada. Para obter mais informações sobre como implementar a negociação de credencial, consulte [depurando erros de autenticação do Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Criptografia  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256 tem suportada apenas para usos de chave simétricos  
 O WCF oferece suporte a uma variedade de criptografia e algoritmos de criação de resumo de assinatura que você pode especificar usando o pacote de algoritmos nas associações fornecidas pelo sistema. Para maior segurança, o WCF dá suporte a algoritmos de Secure Hash Algorithm (SHA) 2, especificamente SHA-256, para criar hashes de resumo da assinatura. Esta versão dá suporte a SHA-256 somente para usos de chave simétricos, tais como chaves de Kerberos, e em que um certificado X.509 não é usado para assinar a mensagem. O WCF não oferece suporte para assinaturas RSA (usadas em certificados x. 509) usando o hash SHA-256 devido à falta de suporte atual para RSA-SHA256 no [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>Compatível com FIPS Hashes SHA-256 não tem suportados  
 WCF não oferece suporte a hashes SHA-256-compatível com FIPS, portanto, os conjuntos de algoritmo que usem o SHA-256 não têm suporte pelo WCF em sistemas em que o uso de algoritmos compatíveis com FIPS é necessário.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Algoritmos compatíveis com FIPS podem falhar se o registro é editado  
 Você pode habilitar e desabilitar FIPS Federal Information Processing Standards () - algoritmos em conformidade usando o snap Local segurança configurações Microsoft Management Console (MMC) - no. Você também pode acessar a configuração no registro. No entanto, observe que o WCF não oferece suporte usando o registro para redefinir a configuração. Se o valor for definido como algo diferente de 1 ou 0, resultados inconsistentes podem ocorrer entre CLR e o sistema operacional.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>Limitação de criptografia AES compatíveis com FIPS  
 A criptografia AES em conformidade com FIPS não funciona nos retornos de chamada duplex em representação de nível de identificação.  
  
### <a name="cngksp-certificates"></a>Certificados CNG/KSP  
 *API de criptografia: Próxima geração (CNG)* é o substituto de longo prazo a CryptoAPI. Esta API está disponível no código não gerenciado em [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] e versões posteriores do Windows.  
  
 .NET framework 4.6.1 e versões anteriores não suportam esses certificados porque eles usam a CryptoAPI herdada para lidar com certificados CNG/KSP. O uso desses certificados com o .NET Framework 4.6.1 e versões anteriores fará com que uma exceção.  
  
 Há duas maneiras possíveis de saber se um certificado usa o KSP:  
  
-   Fazer uma `p/invoke` dos `CertGetCertificateContextProperty`e inspecionar `dwProvType` em retornado `CertGetCertificateContextProperty`.  
  
-   Use o `certutil` comando da linha de comando para consultar os certificados. Para obter mais informações, consulte [tarefas do Certutil para solucionar problemas de certificados](https://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>Falha de segurança de mensagem se é necessário usar a representação do ASP.NET e compatibilidade do ASP.NET  
 O WCF não oferece suporte a seguinte combinação de configurações porque eles podem impedir que a autenticação do cliente ocorra:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Representação está habilitada. Isso é feito no arquivo Web. config, definindo a `impersonate` atributo da <`identity`> elemento `true`.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade é habilitado definindo o `aspNetCompatibilityEnabled` atributo o [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) para `true`.  
  
-   Segurança de modo de mensagem é usada.  
  
 A solução é desativar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade. Ou, se o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade for necessário, desabilite o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] representação de recursos e usar em vez disso, a representação de fornecido pelo WCF. Para obter mais informações, consulte [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>Falha de Literal de endereço IPv6  
 Solicitações de segurança falharem quando o cliente e o serviço estão no mesmo computador e endereços literais IPv6 são usados para o serviço.  
  
 Literal IPv6 aborda o trabalho se o serviço e cliente estão em computadores diferentes.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Falhas de recuperação de WSDL com confiança federada  
 WCF requer exatamente um documento WSDL para cada nó na cadeia de confiança federada. Tenha cuidado para não configurar um loop ao especificar pontos de extremidade. Em que os loops podem surgir de uma maneira é usar um download WSDL de cadeias de confiança federada com dois ou mais links no mesmo documento WSDL. Um cenário comum que pode produzir esse problema é um serviço federado onde o servidor de Token de segurança e o serviço estão contidos dentro do mesmo ServiceHost.  
  
 Um exemplo dessa situação é um serviço com três endereços de ponto de extremidade a seguir:  
  
- `http://localhost/CalculatorService/service` (o serviço)  
  
- `http://localhost/CalculatorService/issue_ticket` (STS)  
  
- `http://localhost/CalculatorService/mex` (o ponto de extremidade de metadados)  
  
 Isso gera uma exceção.  
  
 Você pode fazer com que esse cenário funcione, colocando o `issue_ticket` ponto de extremidade em outro lugar.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>Atributos de importação WSDL pode ser perdida  
 WCF perde o controle dos atributos em uma `<wst:Claims>` elemento em um `RST` modelo ao fazer uma importação WSDL. Isso ocorre durante uma importação WSDL, se você especificar `<Claims>` diretamente na `WSFederationHttpBinding.Security.Message.TokenRequestParameters` ou `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` em vez de usar as coleções de tipo de declaração diretamente.  Uma vez que a importação perde os atributos, a associação não ida e volta corretamente por meio de WSDL e, portanto, está incorreta no lado do cliente.  
  
 A correção é modificar a associação diretamente no cliente depois de fazer a importação.  
  
## <a name="see-also"></a>Consulte também

- [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Ataques por repetição](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
