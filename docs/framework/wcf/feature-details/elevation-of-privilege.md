---
title: Elevação de privilégio
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: cf67f3c68acc4cd8838be56d7c814f9e287ce62c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658034"
---
# <a name="elevation-of-privilege"></a>Elevação de privilégio
*Elevação de privilégio* resulta da dando uma autorização invasor permissões além desses inicialmente concedido. Por exemplo, um invasor com um conjunto de privilégios de permissões "somente leitura" de alguma forma eleva o conjunto para incluir a "leitura e gravação."  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Confiável STS devem autenticar as declarações de Token SAML  
 Um token de declarações marcação linguagem SAML (Security) é um token XML genérico que é o tipo padrão para tokens emitidos. Um token SAML pode ser construído por um Security Token Service (STS) que o final do serviço Web confia em uma troca típica. Tokens SAML contêm declarações em declarações. Um invasor pode copiar as declarações de um token válido, crie um novo token SAML e assiná-lo com um emissor diferente. A intenção é determinar se o servidor está sendo validada emissores e, se não, utilize o ponto fraco para criar tokens SAML que permitem que os privilégios além desses pretendido por um STS confiáveis.  
  
 O <xref:System.IdentityModel.Tokens.SamlAssertion> classe verifica a assinatura digital contida dentro de um token SAML e o padrão <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> requer que tokens SAML sejam assinados por um certificado X.509 que é válida quando o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> da <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> classe é definida como <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust` modo sozinho é insuficiente para determinar se o emissor do token SAML é confiável. Serviços que exigem um modelo mais granular de confiança pode usam políticas de autorização e a imposição para verificar o emissor dos conjuntos de declarações produzida pela autenticação de token emitida ou usar as configurações de validação de x. 509 em <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> para restringir o conjunto de permitido certificados de assinatura. Para obter mais informações, consulte [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) e [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Alternância de identidade sem um contexto de segurança  
 O seguinte se aplica apenas ao [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Quando uma conexão é estabelecida entre um cliente e servidor, a identidade do cliente não é alterada, exceto em uma situação: depois que o cliente do WCF é aberto, se todas as seguintes condições forem verdadeiras:  
  
-   Os procedimentos para estabelecer um contexto de segurança (usando uma sessão ou a sessão de segurança de mensagem de segurança do transporte) é desligada (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> estiver definida como `false` no caso de segurança de mensagem ou não capaz de estabelecer a segurança de transporte sessões é usado no caso de segurança de transporte. HTTPS é um exemplo de tal transporte).  
  
-   Você está usando a autenticação do Windows.  
  
-   Você não definir explicitamente a credencial.  
  
-   Você está chamando o serviço sob o contexto de segurança representado.  
  
 Se essas condições forem verdadeiras, a identidade usada para autenticar o cliente para o serviço pode ser alterado (ele pode não ser a identidade representada, mas a identidade do processo em vez disso) depois que o cliente do WCF é aberto. Isso ocorre porque a credencial do Windows usada para autenticar o cliente para o serviço é transmitida com cada mensagem e a credencial usada para a autenticação é obtida da identidade do Windows do thread atual. Se a identidade do Windows do thread atual for alterado (por exemplo, ao representar um chamador diferente), também pode alterar a credencial que é anexada à mensagem e usada para autenticar o cliente para o serviço.  
  
 Se você quiser ter um comportamento determinístico ao usar a autenticação do Windows junto com a representação é necessário definir explicitamente a credencial do Windows ou você precisa estabelecer um contexto de segurança com o serviço. Para fazer isso, use uma sessão de segurança de mensagem ou uma sessão de segurança de transporte. Por exemplo, o transporte NET. TCP pode fornecer uma sessão de segurança de transporte. Além disso, você deve usar somente uma versão síncrona de operações do cliente ao chamar o serviço. Se você estabelecer um contexto de segurança de mensagem, você deve não manter a conexão ao serviço aberto mais tempo do que o período de renovação de sessão configurado, como a identidade também pode ser alterado durante o processo de renovação de sessão.  
  
### <a name="credentials-capture"></a>Captura de credenciais  
 O seguinte se aplica a [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]e as versões subsequentes.  
  
 As credenciais usadas pelo cliente ou o serviço são baseados no thread atual do contexto. As credenciais são obtidas quando o `Open` método (ou `BeginOpen`, para chamadas assíncronas) de cliente ou do serviço é chamado. Para ambos o <xref:System.ServiceModel.ServiceHost> e <xref:System.ServiceModel.ClientBase%601> classes, o `Open` e `BeginOpen` métodos herdam o <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> e <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> métodos do <xref:System.ServiceModel.Channels.CommunicationObject> classe.  
  
> [!NOTE]
>  Ao usar o `BeginOpen` método, as credenciais capturadas não podem ser garantidas para ser as credenciais do processo que chama o método.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Token Caches permitem que a reprodução usando dados obsoletos  
 O WCF usa a autoridade de segurança local (LSA) `LogonUser` função para autenticar usuários por nome de usuário e senha. Como a função de logon é uma operação cara, o WCF permite que você armazenar tokens em cache que representam usuários autenticados ao aumentar o desempenho. O mecanismo de cache salva os resultados de `LogonUser` para usos subsequentes. Esse mecanismo é desabilitado por padrão. Para habilitá-lo, defina as <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> propriedade para `true`, ou usar o `cacheLogonTokens` atributo do [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Você pode definir um tempo de vida (TTL) para os tokens em cache, definindo a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> propriedade para um <xref:System.TimeSpan>, ou usar o `cachedLogonTokenLifetime` atributo do `userNameAuthentication` elemento; o padrão é 15 minutos. Observe que, enquanto um token é armazenado em cache, qualquer cliente que apresenta o mesmo nome de usuário e senha pode usar o token, mesmo se a conta de usuário é excluída do Windows ou se a sua senha foi alterada. Até que o TTL expire e o token é removido do cache, o WCF permite que o usuário (possivelmente mal-intencionado) autenticar.  
  
 Para atenuar esse problema: Diminuir a janela de ataque, definindo o `cachedLogonTokenLifetime` valor para o menor tempo abranger suas necessidades de usuários.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Emitido autorização de Token: Redefinição de expiração com valor grande  
 Sob certas condições, o <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> propriedade do <xref:System.IdentityModel.Policy.AuthorizationContext> pode ser definido como um valor maior inesperadamente (o <xref:System.DateTime.MaxValue> campo valor menos um dia ou dia 20 de dezembro, 9999).  
  
 Isso ocorre ao usar o <xref:System.ServiceModel.WSFederationHttpBinding> e qualquer uma das associações fornecidas pelo sistema que tem um token emitido como o cliente o tipo de credencial.  
  
 Isso também ocorre quando você cria ligações personalizadas, usando um dos seguintes métodos:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Para atenuar isso, a política de autorização deve verificar a ação e o tempo de expiração de cada política de autorização.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>O serviço usa um certificado diferente do pretendido do cliente  
 Sob certas condições, um cliente pode assinar uma mensagem com um certificado x. 509 digitalmente e ter o serviço a recuperar um certificado diferente daquele pretendido.  
  
 Isso pode ocorrer nas seguintes circunstâncias:  
  
-   O cliente assina digitalmente uma mensagem usando um certificado X.509 e não anexar o certificado X.509 para a mensagem, mas em vez disso, simplesmente referencia o certificado usando seu identificador de chave de assunto.  
  
-   Computador do serviço contém dois ou mais certificados com a mesma chave pública, mas eles contêm informações diferentes.  
  
-   O serviço recupera um certificado que corresponde ao identificador de chave da entidade, mas ele não é o cliente pretende usar. Quando o WCF recebe a mensagem e verifica a assinatura, o WCF mapeia as informações no certificado x. 509 não intencional a um conjunto de declarações que são diferentes e potencialmente com privilégios elevados do que o cliente esperava.  
  
 Para atenuar isso, outra maneira, como o uso de certificado de referência a x. 509 <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Consulte também
- [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
