---
title: Elevação de privilégio
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d93a8ae074e4016d7d8ec4b8734f0d14ead938f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="elevation-of-privilege"></a>Elevação de privilégio
*Elevação de privilégio* os resultados de conceder autorização um invasor permissões além desses inicialmente concedida. Por exemplo, um invasor com um conjunto de privilégios de permissões "somente leitura" de alguma forma eleva o conjunto para incluir "leitura e gravação."  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Confiável STS deve assinar as declarações de Token SAML  
 Um token de segurança asserções Markup Language (SAML) é um token XML genérico que é o tipo padrão para tokens emitidos. Um token SAML pode ser criado por um Token de segurança Service (STS) que o final do serviço Web confia em uma troca típica. Tokens SAML contêm declarações em declarações. Um invasor pode copiar as declarações de um token válido, crie um novo token SAML e assiná-lo com um emissor diferente. A intenção é determinar se o servidor está sendo validada emissores e, se não utilizar o ponto fraco para criar tokens SAML que permitem privilégios além desses pretendido por um STS confiáveis.  
  
 O <xref:System.IdentityModel.Tokens.SamlAssertion> classe verifica a assinatura digital contida em um token SAML e o padrão <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> exige que os tokens SAML seja assinado por um certificado x. 509 que é válida quando o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> classe é definida como <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust` modo autônomo é insuficiente para determinar se o emissor do token SAML é confiável. Serviços que exigem um modelo mais granular de confiança pode usam políticas de autorização e imposição para verificar o emissor dos conjuntos de declarações produzido pela autenticação do token emitida ou use as configurações de validação de x. 509 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> para restringir o conjunto de permitido certificados de assinatura. Para obter mais informações, consulte [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) e [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Alternância de identidade sem um contexto de segurança  
 O seguinte se aplica somente ao [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Quando uma conexão é estabelecida entre um cliente e servidor, a identidade do cliente não for alterado, exceto em uma situação: após o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente é aberto, se todas as seguintes condições forem verdadeiras:  
  
-   Os procedimentos para estabelecer um contexto de segurança (usando um segurança de transporte sessão ou a sessão de segurança de mensagem) for desativada (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> está definida como `false` no caso de segurança de mensagem ou não capaz de estabelecer a segurança de transporte sessões é usado em caso de segurança de transporte. HTTPS é um exemplo de tal transporte).  
  
-   Você está usando a autenticação do Windows.  
  
-   Você não definir explicitamente a credencial.  
  
-   Você está chamando o serviço sob o contexto de segurança representado.  
  
 Se essas condições forem verdadeiras, talvez a identidade usada para autenticar o cliente para o serviço de alteração (ele pode não ser a identidade representada, mas a identidade do processo em vez disso) após o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente é aberto. Isso ocorre porque a credencial do Windows usada para autenticar o cliente para o serviço é transmitida com cada mensagem e a credencial usada para autenticação é obtida da identidade do Windows do thread atual. Se a identidade do Windows do thread atual é alterado (por exemplo, representando um chamador diferente), a credencial que é anexada à mensagem e usada para autenticar o cliente para o serviço também pode alterar.  
  
 Se você quiser ter comportamento determinístico ao usar a autenticação do Windows junto com a representação é necessário definir explicitamente a credencial do Windows ou você precisa estabelecer um contexto de segurança com o serviço. Para fazer isso, use uma sessão de segurança de mensagem ou uma sessão de segurança de transporte. Por exemplo, o transporte de NET. TCP pode fornecer uma sessão de segurança de transporte. Além disso, você deve usar apenas uma versão síncrona de operações do cliente ao chamar o serviço. Se você estabelecer um contexto de segurança de mensagem, não mantenha a conexão ao serviço abrir mais tempo do que o período de renovação de sessão configurado, porque a identidade também pode ser alterado durante o processo de renovação de sessão.  
  
### <a name="credentials-capture"></a>Captura de credenciais  
 O seguinte se aplica a [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]e versões posteriores.  
  
 As credenciais usadas pelo cliente ou o serviço se baseiam no thread de contexto atual. As credenciais são obtidas quando a `Open` método (ou `BeginOpen`, para chamadas assíncronas) do cliente ou serviço é chamado. Para ambos o <xref:System.ServiceModel.ServiceHost> e <xref:System.ServiceModel.ClientBase%601> classes, o `Open` e `BeginOpen` métodos herdam o <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> e <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> métodos do <xref:System.ServiceModel.Channels.CommunicationObject> classe.  
  
> [!NOTE]
>  Ao usar o `BeginOpen` método, as credenciais capturadas não podem ser garantidas para ser as credenciais do processo que chama o método.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Token Caches permitem reprodução usando dados obsoletos  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa a autoridade de segurança local (LSA) `LogonUser` função para autenticar usuários por nome de usuário e senha. Porque a função de logon é uma operação dispendiosa, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permite tokens em cache que representam usuários autenticados para aumentar o desempenho. O mecanismo de cache salva os resultados de `LogonUser` para usos subsequentes. Esse mecanismo é desabilitado por padrão. Para habilitá-lo, defina o <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> propriedade `true`, ou use o `cacheLogonTokens` atributo do [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Você pode definir um tempo de vida (TTL) para os tokens em cache, definindo o <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> propriedade para um <xref:System.TimeSpan>, ou use o `cachedLogonTokenLifetime` atributo do `userNameAuthentication` elemento; o padrão é 15 minutos. Observe que, enquanto um token é armazenado em cache, qualquer cliente que apresenta o mesmo nome de usuário e senha pode usar o token, mesmo se a conta de usuário é excluída do Windows ou se a sua senha foi alterada. Até que a TTL expirar e o token é removido do cache, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permite que o usuário (possivelmente mal-intencionados) autenticar.  
  
 Para atenuar esse: diminuir a janela de ataque, definindo o `cachedLogonTokenLifetime` valor para o menor tempo span suas necessidades de usuários.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Autorização de Token emitida: Redefinição de expiração com valor grande  
 Em determinadas condições, o <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> propriedade o <xref:System.IdentityModel.Policy.AuthorizationContext> pode ser definida como um valor maior inesperadamente (o <xref:System.DateTime.MaxValue> campo valor menos um dia ou dia 20 de dezembro, 9999).  
  
 Isso ocorre ao usar o <xref:System.ServiceModel.WSFederationHttpBinding> e qualquer uma das associações fornecidas pelo sistema que têm um token emitido como o cliente do tipo de credencial.  
  
 Isso também ocorre quando você criar associações personalizadas usando um dos seguintes métodos:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Para atenuar isso, a política de autorização deve verificar a ação e o tempo de expiração de cada política de autorização.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>O serviço usa um certificado diferente que o cliente pretendida  
 Sob determinadas condições, um cliente pode assinar uma mensagem com um certificado x. 509 digitalmente e que o serviço de recuperar um certificado diferente daquela pretendida.  
  
 Isso pode ocorrer nas seguintes circunstâncias:  
  
-   O cliente assina digitalmente uma mensagem usando um certificado x. 509 e não anexar o certificado x. 509 para a mensagem, mas referencia apenas o certificado usando seu identificador de chave de entidade.  
  
-   Computador do serviço contém duas ou mais certificados com a mesma chave pública, mas eles contêm informações diferentes.  
  
-   O serviço recupera um certificado que corresponde ao identificador de chave de assunto, mas ele não é o cliente pretende usar. Quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recebe a mensagem e verifica a assinatura, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mapeia as informações no certificado x. 509 não intencional para um conjunto de declarações que são diferentes e potencialmente com privilégios elevados do que o cliente esperava.  
  
 Para atenuar isso, outra maneira, como o uso de certificados de referência a x. 509 <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
