---
title: "Visão geral do módulo de autenticação WSFederation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ea17e384ecb4536ed544e3b874631db6fe54e0e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="wsfederation-authentication-module-overview"></a>Visão geral do módulo de autenticação WSFederation
O Windows Identity Foundation (WIF) inclui suporte para autenticação federada em aplicativos do ASP.NET por meio do módulo de autenticação WS-Federated (WS-FAM). Este tópico ajudará você a entender como a autenticação federada funciona e como usá-la.  
  
### <a name="overview-of-federated-authentication"></a>Visão geral da autenticação federada  
 A autenticação federada permite um Serviço de Token de Segurança (STS) em um domínio de confiança para fornecer informações de autenticação para um STS em outro domínio de confiança quando há uma relação de confiança entre os dois domínios. Um exemplo disso é mostrado na ilustração a seguir.  
  
 ![Cenário de autenticação federada](../../../docs/framework/security/media/federatedauthentication.gif "FederatedAuthentication")  
  
1.  Um cliente no domínio de confiança Fabrikam envia uma solicitação para um aplicativo de terceira parte confiável (RP) no domínio de confiança da Contoso.  
  
2.  O RP redireciona o cliente para um STS no domínio de confiança da Contoso. Esse STS não tem conhecimento do cliente.  
  
3.  O STS da Contoso redireciona o cliente para um STS no domínio de confiança da Fabrikam, com a qual o domínio de confiança da Contoso tem uma relação de confiança.  
  
4.  O STS da Fabrikam verifica a identidade do cliente e emite um token de segurança para o STS da Contoso.  
  
5.  O STS da Contoso usa o token da Fabrikam para criar seu próprio token que pode ser usado pelo RP e o envia para o RP.  
  
6.  O RP extrai declarações do cliente do token de segurança e toma uma decisão de autorização.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>Uso do módulo de autenticação federada com o ASP.NET  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WS-FAM) é um módulo HTTP que permite adicionar a autenticação federada a um aplicativo [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. A autenticação federada permite que a autenticação lógica seja tratada pelo STS e permite que você se concentre em escrever a lógica de negócios.  
  
 Configure o WS-FAM para especificar o STS para o qual as solicitações não autenticadas deverão ser redirecionadas. O WIF permite autenticar um usuário de duas maneiras:  
  
1.  Redirecionamento passivo: quando um usuário não autenticado tenta acessar um recurso protegido e você deseja simplesmente redirecioná-lo para um STS sem a necessidade de uma página de logon, essa é a abordagem correta. O STS verifica a identidade do usuário e emite um token de segurança que contém as declarações apropriadas para esse usuário. Essa opção exige que o WS-FAM seja adicionado ao pipeline dos módulos de HTTP. Você pode usar a Ferramenta de Acesso e Identidade para o Visual Studio 2012 para modificar o arquivo de configuração do seu aplicativo para usar WS-FAM e federar com um STS. Para saber mais, confira [Ferramenta de Identidade e Acesso para o Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2.  Chame o método <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> ou o método <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> por meio do code-behind de uma página de entrada no aplicativo RP.  
  
 No redirecionamento passivo, toda a comunicação é realizada por meio de redirecionamento/resposta do cliente (normalmente um navegador). Você pode adicionar o WS-FAM ao pipeline de HTTP do seu aplicativo, onde ele inspeciona se há solicitações de usuários não autenticados e redireciona os usuários para o STS que você especificar.  
  
 O WS-FAM também gera vários eventos que permitem personalizar sua funcionalidade em um aplicativo do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
### <a name="how-the-ws-fam-works"></a>Como funciona o WS-FAM  
 O WS-FAM é implementado na classe <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>. Normalmente, você adiciona o WS-FAM ao pipeline de HTTP do seu aplicativo de RP [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. Quando um usuário não autenticado tenta acessar um recurso protegido, o RP retorna uma resposta HTTP “401 autorização negada”. O WS-FAM intercepta essa resposta em vez de permitir que o cliente o receba e, em seguida, ele redireciona o usuário para o STS especificado. O STS emite um token de segurança, que o WS-FAM intercepta novamente. O WS-FAM usa o token para criar uma instância de <xref:System.Security.Claims.ClaimsPrincipal> para o usuário autenticado, que permite que os mecanismos de autorização regulares do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] funcionem.  
  
 Como o HTTP é sem monitoração de estado, precisamos de uma maneira de evitar repetir este processo sempre que o usuário tentar acessar outro recurso protegido. É nesse momento que entra o <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Quando o STS emite um token de segurança para o usuário, <xref:System.IdentityModel.Services.SessionAuthenticationModule> também cria um token de segurança de sessão para o usuário e o coloca em um cookie. Em solicitações posteriores, o <xref:System.IdentityModel.Services.SessionAuthenticationModule> intercepta esse cookie e o utiliza para reconstruir a <xref:System.Security.Claims.ClaimsPrincipal> do usuário.  
  
 O diagrama a seguir mostra o fluxo geral de informações no caso de redirecionamento passivo. A solicitação é redirecionada automaticamente por meio do STS para estabelecer credenciais sem uma página de logon:  
  
 ![Diagrama de timing para entrada com redirecionamento passivo](../../../docs/framework/security/media/signinusingpassiveredirect.gif "SignInUsingPassiveRedirect")  
  
 O seguinte diagrama mostra mais detalhes sobre o que acontece quando o usuário se autentica no STS e seus tokens de segurança são processados pelo <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>:  
  
 ![Timing para processamento do token com redirecionamento passivo](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 O seguinte diagrama mostra mais detalhes sobre o que acontece quando os tokens de segurança do usuário foram serializados para cookies e são interceptados pelo <xref:System.IdentityModel.Services.SessionAuthenticationModule>:  
  
 ![Diagrama de timing de SAM que mostra a entrada usando controles](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Eventos  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule> e sua classe pai, <xref:System.IdentityModel.Services.HttpModuleBase>, acionam eventos em vários estágios de processamento de uma solicitação HTTP. Você pode manipular esses eventos no arquivo `global.asax` de seu aplicativo [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
-   A infraestrutura ASP.NET invoca o método <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> do módulo para inicializar o módulo.  
  
-   O evento <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> é acionado quando a infraestrutura ASP.NET invoca o método <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> pela primeira vez em um dos módulos do aplicativo que são derivados de <xref:System.IdentityModel.Services.HttpModuleBase>. Esse método acessa a propriedade <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> estática, que faz com que a configuração seja carregada do arquivo Web.config. Esse evento é gerado apenas na primeira vez em que esta propriedade é acessada. O objeto <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> que é inicializado por meio da configuração pode ser acessado por meio da propriedade <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> em um manipulador de eventos. Você pode usar esse evento para modificar a configuração antes que ela seja aplicada aos módulos. Você pode adicionar um manipulador a este evento no método Application_Start:  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Cada módulo substitui os métodos abstratos <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> e <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType>. O primeiro desses métodos adiciona manipuladores para eventos de pipeline do ASP.NET que são de interesse para o módulo. Na maioria dos casos, a implementação padrão do módulo será suficiente. O segundo desses métodos inicializa as propriedades do módulo por meio de sua propriedade <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType>. (Esta é uma cópia da configuração que foi carregada anteriormente.) Talvez seja necessário substituir esse segundo método se você desejar dar suporte à inicialização de novas propriedades por meio da configuração em classes que são derivadas de <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> ou <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Nesses casos, você também precisará derivar dos objetos de configuração apropriados para dar suporte às propriedades de configuração adicionadas; por exemplo, de <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> ou <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
-   O WS-FAM aciona o evento <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> quando ele intercepta um token de segurança emitido pelo STS.  
  
-   O WS-FAM aciona o evento <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> depois que ele valida o token.  
  
-   O <xref:System.IdentityModel.Services.SessionAuthenticationModule> aciona o evento <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> quando ele cria um token de segurança de sessão para o usuário.  
  
-   O <xref:System.IdentityModel.Services.SessionAuthenticationModule> aciona o evento <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> quando ele intercepta solicitações posteriores com o cookie que contém o token de segurança de sessão.  
  
-   Antes que o WS-FAM redirecione o usuário para o emissor, ele aciona o evento <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>. A solicitação de entrada da Web Services Federation está disponível por meio da propriedade <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> do <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> passado no evento. Você pode optar por modificar a solicitação antes de enviar isso para o emissor.  
  
-   O WS-FAM aciona o evento <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> quando o cookie é gravado com êxito e o usuário é conectado.  
  
-   O WS-FAM aciona o evento <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> uma vez por sessão, pois a sessão é fechada para cada usuário. Ele não será gerado se a sessão for fechada no lado do cliente (por exemplo, excluindo o cookie de sessão). Em um ambiente de SSO, o IP-STS pode solicitar que cada RP saia também. Isso também acionará esse evento, com <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> definido como `true`.  
  
> [!NOTE]
>  Não use a propriedade <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> durante qualquer evento acionado por <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> ou <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Isso ocorre porque <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> é definido após o processo de autenticação, enquanto os eventos são acionados durante o processo de autenticação.  
  
### <a name="configuration-of-federated-authentication"></a>Configuração da autenticação federada  
 O WS-FAM e o SAM são configurados por meio do elemento [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md). O elemento filho [\<wsFederation>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) configura os valores padrão para as propriedades do WS-FAM; por exemplo, a propriedade <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> e a propriedade <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A>. (Esses valores podem ser alterados por solicitação, fornecendo manipuladores para alguns dos eventos do WS-FAM; por exemplo, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) O manipulador de cookie que é usado pelo SAM é configurado por meio do elemento filho [\<cookieHandler>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md). O WIF fornece um manipulador de cookie padrão implementado na classe <xref:System.IdentityModel.Services.ChunkedCookieHandler> que pode ter seu tamanho de parte definido por meio do elemento [\<chunkedCookieHandler>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md). O elemento `<federationConfiguration>` referencia um <xref:System.IdentityModel.Configuration.IdentityConfiguration>, que fornece a configuração de outros componentes do WIF usados no aplicativo, como o <xref:System.Security.Claims.ClaimsAuthenticationManager> e o <xref:System.Security.Claims.ClaimsAuthorizationManager>. A configuração de identidade pode ser referenciada explicitamente especificando um elemento [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) nomeado no atributo `identityConfigurationName` do elemento `<federationConfiguration>`. Se a configuração de identidade não for referenciada explicitamente, a configuração de identidade padrão será usada.  
  
 O XML a seguir mostra uma configuração de um aplicativo de terceira parte confiável (RP) do ASP.NET. As seções de configuração <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> e <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> são adicionadas sob o elemento `<configSections>`. O SAM e o WS-FAM são adicionados aos módulos de HTTP sob o elemento `<system.webServer>`/`<modules>`. Finalmente, os componentes do WIF estão configurados nos elementos `<system.identityModel>`/`<identityConfiguration>` e `<system.identityModel.services>`/`<federationConfiguration>`. Essa configuração especifica o manipulador de cookie em partes, como o manipulador de cookie padrão e não é um tipo de manipulador de cookie especificado no elemento `<cookieHandler>`.  
  
> [!WARNING]
>  No exemplo a seguir, o atributo `requireHttps` do elemento `<wsFederation>` e o atributo `requireSsl` do elemento `<cookieHandler>` são `false`. Isso representa uma ameaça de segurança em potencial. Em produção, esses dois valores devem ser definidos como `true`.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  ...  
  
  <system.webServer>  
    <modules>  
      <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
    </modules>  
  </system.webServer>  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost:50969/" />  
      </audienceUris>  
      <certificateValidation certificateValidationMode="None" />  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
        <trustedIssuers>  
          <add thumbprint="9B74CB2F320F7AAFC156E1252270B1DC01EF40D0" name="LocalSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
    </identityConfiguration>  
  </system.identityModel>  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:15839/wsFederationSTS/Issue" realm="http://localhost:50969/" reply="http://localhost:50969/" requireHttps="false" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
