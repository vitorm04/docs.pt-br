---
title: Diretrizes para migrar um aplicativo criado usando o WIF 3.5 para o WIF 4.5
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5db0925900a357134cf0103bbebbf5c9aac9e688
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386859"
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>Diretrizes para migrar um aplicativo criado usando o WIF 3.5 para o WIF 4.5
## <a name="applies-to"></a>Aplica-se a  
  
-   Microsoft® Windows® Identity Foundation (WIF) 3.5 e 4.5.  
  
## <a name="overview"></a>Visão geral  
 O Windows Identity Foundation (WIF) foi originalmente lançado no período de tempo do .NET 3.5 SP1. Essa versão do WIF é conhecida como WIF 3.5. Ele foi lançado como um tempo de execução e SDK separados, o que significa que cada computador no qual um aplicativo habilitado para o WIF estava em execução precisava ter o tempo de execução WIF instalado e os desenvolvedores precisavam baixar e instalar o SDK do WIF para obter os modelos do Visual Studio e as ferramentas que habilitavam o desenvolvimento de aplicativos habilitados para o WIF. A partir do .NET 4.5 o WIF foi totalmente integrado ao .NET Framework. Um tempo de execução separado não é mais necessário e as ferramentas do WIF podem ser instaladas no Visual Studio 2012 usando o Visual Studio Extensions Manager. Esta versão do WIF é conhecida como WIF 4.5.  
  
 A integração do WIF no .NET precisava de várias alterações na superfície da API do WIF. O WIF 4.5 inclui novos namespaces, algumas alterações em elementos de configuração e novas ferramentas para Visual Studio. Este tópico fornece diretrizes que você pode usar para ajudá-lo a migrar aplicativos criados usando o WIF 3.5 para o WIF 4.5. Podem haver situações nas quais você precisa executar aplicativos herdados, criados usando o WIF 3.5 em computadores que executam o Windows 8 ou o Windows Server 2012. Este tópico também fornece orientação sobre como habilitar o WIF 3.5 para esses sistemas operacionais.  
  
## <a name="changes-required-for-wif-45"></a>Alterações necessárias para o WIF 4.5  
 Esta seção descreve as alterações que são necessárias para migrar um aplicativo WIF 3.5 para o WIF 4.5.  
  
### <a name="assembly-and-namespace-changes"></a>Alterações de namespace e assembly  
 O WIF 3.5, todas as classes do WIF estavam contidas no assembly `Microsoft.IdentityModel` (microsoft.identitymicrosoft.identitymodel.dll). No WIF 4.5, as classes WIF foram divididas entre os seguintes assemblies: `mscorlib` (mscorlib. dll), `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll) e `System.ServiceModel` (System.ServiceModel.dll).  
  
 As classes do WIF 3.5 estavam contidas em um dos namespaces `Microsoft.IdentityModel`; por exemplo, `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web` e assim por diante. No WIF 4.5, as classes do WIF agora são distribuídas entre o namespaces [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004), o namespace <xref:System.Security.Claims?displayProperty=nameWithType> e o namespace <xref:System.ServiceModel.Security?displayProperty=nameWithType>. Além dessa reorganização, algumas classes do WIF 3.5 foram descartadas no WIF 4.5.  
  
 A tabela a seguir mostra alguns dos mais importantes namespaces do WIF 4.5 e o tipo de classes que eles contêm. Para obter mais informações sobre como os namespaces fazem o mapeamento entre o WIF 3.5 e o WIF 4.5 e sobre namespaces e classes que foram descartados no WIF 4.5, consulte [Mapeamento de namespace entre WIF 3.5 e WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
|Namespace do WIF 4.5|Descrição|  
|-----------------------|-----------------|  
|<xref:System.IdentityModel?displayProperty=nameWithType>|Contém classes que representam as transformações de cookie, serviços de token de segurança e leitores de dicionário XML especializados. Contém classes dos seguintes namespaces do WIF 3.5: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService` e `Microsoft.IdentityModel.Threading`.|  
|<xref:System.Security.Claims?displayProperty=nameWithType>|Contém classes que representam declarações, identidades baseada em declarações, entidades de segurança baseadas em declarações e outros artefatos de modelo de identidade baseado em declarações. Contém classes do namespace `Microsoft.IdentityModel.Claims`.|  
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Contém classes que representam os tokens de segurança, manipuladores de token de segurança e outros artefatos de token de segurança. Contém classes dos seguintes namespaces do WIF 3.5: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11` e `Microsoft.IdentityModel.Tokens.Saml2`.|  
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Contém classes que são usadas nos cenários passivos do (WS-Federation). Contém classes do namespace `Microsoft.IdentityModel.Web`.|  
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|Classes que representam os contratos WCF, canais, hosts de serviço e outros artefatos que são usados em cenários de ativos (WS-Trust) agora estão neste namespace. No WIF 3.5, essas classes estavam no namespace `Microsoft.IdentityModel.Protocols.WSTrust`.|  
  
> [!IMPORTANT]
>  Os seguintes namespaces `System.IdentityModel` contêm classes que implementam o modelo de identidade baseada em declarações do WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> e <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. O modelo de identidade baseada em declarações do WCF é substituído pelo do WIF. Você não deve usar as classes nesses três namespaces ao criar soluções com base no WIF.  
  
### <a name="changes-due-to-net-integration"></a>Alterações devido à integração do .NET  
 O WIF agora está integrado ao .NET Framework. A maioria das classes de identidade e de entidade de segurança do .NET agora é derivada <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> e <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. Isso resultados nas seguintes alterações no WIF 4.5:  
  
-   Agora existem classes do WIF que representam declarações, identidades e entidades de segurança no namespace <xref:System.Security.Claims?displayProperty=nameWithType>.  
  
    > [!IMPORTANT]
    >  O namespace <xref:System.IdentityModel.Claims?displayProperty=nameWithType> contém classes que representam artefatos no modelo de identidade baseada em declarações do WCF. Muitas dessas classes possuem nomes que são os mesmos das classes do WIF; por exemplo, `Claims`. Não use essas classes ao criar soluções com base no WIF.  
  
-   As classes de identidade e de entidade de segurança do .NET agora são derivadas diretamente de <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> e <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, que representam identidades baseadas em declarações e entidades de segurança. Por esse motivo, as interfaces `IClaimsIdentity` e `IClaimsPrincipal` do WIF 3.5 não são mais necessárias e não estão disponíveis no WIF 4.5.  
  
-   Como as classes de identidade e de entidade de segurança do .NET, como <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> e <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> agora são derivadas de <xref:System.Security.Claims.ClaimsIdentity> e <xref:System.Security.Claims.ClaimsPrincipal>, têm funcionalidade interna de declarações. Por este motivo, as classes de entidade de segurança e de identidade específicas de declarações como `WindowsClaimsIdentity` e `WindowsClaimsPrincipal` que estavam presentes no WIF 3.5 não são mais necessárias e não existem no WIF 4.5.  
  
### <a name="other-changes-to-wif-functionality"></a>Outras alterações de funcionalidade do WIF  
 Além das alterações de namespace e as alterações devido à integração com o .NET, ocorrem as seguintes alterações gerais na funcionalidade do WIF no WIF 4.5.  
  
-   A classe `Microsoft.IdentityModel.ExceptionMapper`, que oferecia a funcionalidade que permitia mapear exceções para falhas de SOAP específicas, foi removida.  
  
-   A superfície de exceção foi reduzida consideravelmente.  
  
-   Muitas das classes que definiam constantes específicas de WS-* ou protocolo foram removidas; por exemplo, a classe `Microsoft.IdentityModel.WSAddressing10Constants`, que definia constantes relacionadas ao WS-Addressing 1.0.  
  
-   O Claims to Windows Token Service (c2wts) e suas classes associadas no namespace `Microsoft.IdentityModel.WindowsTokenService` foram removidos.  
  
### <a name="wif-configuration-changes"></a>Alterações de configuração do WIF  
 Muitas das alterações no arquivo de configuração foram causadas por atualizações de namespace no WIF 4.5. Por exemplo, considere a seguinte entrada do WIF 3.5 na seção `<httpModules>` para adicionar o WS-Federation Authentication Manager para um aplicativo:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />  
```  
  
 Esta entrada foi atualizada no WIF 4.5 para incluir os novos namespaces e a versão do assembly:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>  
```  
  
 A lista a seguir enumera as principais alterações no arquivo de configuração para o WIF 4.5.  
  
-   A seção `<microsoft.identityModel>` agora é a seção [\<System. identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md).  
  
-   O elemento `<service>` agora é o elemento [\<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md).  
  
-   Uma nova seção, [\<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), foi adicionada para especificar as configurações que controlam o comportamento em cenários passivos (WS-Federation).  
  
-   O elemento [\<federationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) e seus elementos filho foram movidos do elemento `<service>` no WIF 3.5 para o novo elemento `<system.identityModel.services>`.  
  
-   Vários elementos que podem ser especificados no nível de serviço-diretamente sob o elemento `<service>` no WIF 3.5 agora estão restritos e devem ser especificados no elemento [\<securityTokenHandlerConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md). (Eles ainda podem ser especificados sob o elemento [\<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) no WIF 4.5 para compatibilidade com versões anteriores.)  
  
 Para obter uma lista completa dos elementos de configuração do WIF 4.5, consulte [Esquema de configuração do WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md).  
  
### <a name="visual-studio-tooling-changes"></a>Alterações de ferramentas do Visual Studio  
 O SDK do WIF 3.5 oferecia um utilitário de federação autônomo, FedUtil.exe (FedUtil), que você podia usar para terceirizar o gerenciamento de identidades em aplicativos habilitados para WIF para um serviço de token de segurança (STS). Essa ferramenta adicionava configurações do WIF ao arquivo de configuração do aplicativo e permitia ao aplicativo obter tokens de segurança de um ou mais STSs e apareceu no Visual Studio por meio do botão **Adicionar referência de serviço do STS**. O FedUtil não é fornecido com o WIF 4.5. Em vez disso, o WIF 4.5 oferece suporte a uma nova extensão do Visual Studio chamada ferramenta de identidade e acesso para o Visual Studio 2012 que você pode usar para modificar o arquivo de configuração do aplicativo com as configurações do WIF necessárias para terceirizar o gerenciamento de identidade para um STS. A ferramenta de acesso e identidade também implementa um STS chamado STS Local que você pode usar para testar seus aplicativos habilitados para o WIF. Em muitos casos, este recurso elimina a necessidade de criar STSs personalizados que geralmente eram necessários no WIF 3.5 para testar soluções em desenvolvimento. Por esse motivo, os modelos de STS não são mais suportados no Visual Studio 2012; no entanto, as classes que oferecem suporte ao desenvolvimento de STSs ainda estão disponíveis no WIF 4.5.  
  
 Você pode instalar a ferramenta de acesso e identidade do gerenciador de atualizações e extensões do Visual Studio ou você pode baixá-lo na seguinte página na Galeria de Código: [Ferramenta de identidade e acesso para o Visual Studio 2012 na Galeria de Código](https://go.microsoft.com/fwlink/?LinkID=245849). As alterações de ferramentas do Visual Studio são resumidas na lista a seguir:  
  
-   A funcionalidade Adicionar referência de serviço do STS foi removida. Essa funcionalidade foi substituída pela ferramenta de acesso e identidade.  
  
-   Os modelos do Visual Studio STS foram removidos. Você pode usar o STS Local disponível por meio da ferramenta de identidade e acesso para testar soluções de identidade que você desenvolve com o WIF. A configuração do STS Local pode ser modificada para personalizar as declarações que ele serve.  
  
-   O utilitário autônomo de Federação (FedUtil) não está disponível no WIF 4.5. Você pode usar a ferramenta de acesso e identidade para modificar os arquivos de configuração para terceirizar o gerenciamento de identidade para um STS.  
  
 Para obter mais informações, consulte [Ferramenta de identidade e acesso para o Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)  
  
<a name="BKMK_ToolingChanges"></a>   
### <a name="passive-ws-federation-scenarios"></a>Cenários passivos (WS-Federation):  
  
-   As classes que dão suporte a cenários passivos foram movidas para o namespace <xref:System.IdentityModel.Services?displayProperty=nameWithType>. No WIF 3.5, essas classes estavam no namespace `Microsoft.IdentityModel.Web`.  
  
-   As classes do namespace `Microsoft.IdentityModel.Web.Configuration` foram movidas para <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Essas classes representam objetos específicos para configuração em cenários passivos.  
  
-   O `FederatedPasssiveSignInControl` não é mais suportado; todas as classes no namespace `Microsoft.IdentityModel.Web.Controls` foram removidos do WIF 4.5.  
  
-   A funcionalidade de saída do módulo de autenticação da Web Services Federation (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) é diferente do WIF 3.5. Para obter mais detalhes sobre como a saída do serviço funciona no WIF 4.5, consulte o tópico sobre a classe <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>.  
  
### <a name="active-wcfws-trust-scenarios"></a>Cenários ativos (WCF/WS-Trust):  
  
-   O namespace `Microsoft.IdentityModel.Protocols.WSTrust` foi dividido principalmente em dois namespaces no WIF 4.5. As classes que representam artefatos que são específicos ao protocolo WS-Trust agora estão na <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. Isso inclui classes como <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. As classes que representam contratos de serviço, canais, hosts de serviço e outros artefatos que estão envolvidos no uso do WS-Trust em aplicativos do WCF foram movidas para a <xref:System.ServiceModel.Security?displayProperty=nameWithType>; por exemplo, a interface <xref:System.ServiceModel.Security.IWSTrust13AsyncContract>.  
  
-   Configurar um aplicativo WCF para usar o WIF foi bastante simplificado. Anteriormente a `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` precisava ser adicionada como uma extensão de comportamento e essa funcionalidade foi usada para incluir WIF no comportamento de serviço especificando um elemento `<federatedServiceHostConfiguration>`. O WIF 4.5 está mais integrado com o WCF. Agora você pode habilitar o WIF em um serviço WCF especificando o atributo `useIdentityConfiguration` no elemento `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>` conforme o XML a seguir:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
-   No WIF 4.5 o serviço de certificado usado por um serviço (WCF) ativo deve ser especificado no host de serviço. Nessa configuração, você pode fazer isso por meio do elemento `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>`/`<serviceCertificate>`, conforme mostrado no exemplo anterior. No WIF 3.5, o certificado de serviço pode ser especificado por meio do elemento filho `<serviceCertificate>` do elemento `<service>` do WIF. Essa funcionalidade não existe no WIF 4.5; em vez disso, especifique o elemento `<serviceCertificate>` sob o elemento `<serviceCredentials>`.  
  
-   As classes usadas para integrar o WIF 3.5 ao WCF não existem mais. Isso inclui as seguintes classes no namespace `Microsoft.IdentityModel.Tokens`: `FederatedSecurityTokenManager`, `FederatedServiceCredentials` e `IdentityModelServiceAuthorizationManager`, bem como a classe `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement`.  
  
## <a name="enabling-wif-35-in-windows-8"></a>Habilitar o WIF 3.5 no Windows 8  
 Como o WIF 4.5 é parte do .NET 4.5, ele é habilitado automaticamente em computadores que executam o Windows 8 e o Windows Server 2012 e aplicativos que são criados usando o WIF 4.5 serão executados no Windows 8 ou no Windows Server 2012 por padrão. No entanto, talvez seja necessário executar aplicativos que foram criados usando o WIF 3.5 em um computador que esteja executando o Windows 8 ou o Windows Server 2012. Nesse caso, você precisa habilitar o WIF 3.5 no computador de destino. Em um computador executando o Windows 8, você pode fazer isso usando a ferramenta de Gerenciamento e Manutenção de Imagens de Implantação (DISM). Em um computador executando o Windows Server 2012, você pode usar a ferramenta DISM ou você pode usar o cmdlet `Add-WindowsFeature` do Windows PowerShell. Em ambos os casos, os comandos apropriados podem ser chamados na linha de comando ou de dentro do ambiente do Windows PowerShell.  
  
 Os comandos a seguir mostram como usar a ferramenta DISM a partir da linha de comando ou de dentro do ambiente do Windows PowerShell. Por padrão, o módulo do PowerShell do DISM está incluído no Windows 8 e no Windows Server 2012 e não precisa ser importado. Para obter mais informações sobre como usar o DISM com o Windows PowerShell, consulte [Como usar o DISM no Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=254419).  
  
 Para habilitar o WIF 3.5 usando o DISM:  
  
```  
dism /online /enable-feature:windows-identity-foundation  
```  
  
 Para desabilitar o WIF 3.5 usando o DISM:  
  
```  
dism /online /disable-feature:windows-identity-foundation  
```  
  
 Para verificar quais recursos estão habilitados ou desabilitados usando o DISM:  
  
```  
dism /online /get-features  
```  
  
 Como alternativa, em computadores que executam o Windows Server 2012, você pode habilitar o WIF 3.5 usando o cmdlet `Add-WindowsFeature` do Windows PowerShell. Para fazer isso a partir da linha de comando, você pode inserir o seguinte comando:  
  
```  
powershell "add-windowsfeature windows-identity-foundation"  
```  
  
 A partir do ambiente do Windows PowerShell, você pode inserir o comando diretamente:  
  
```  
add-windowsfeature windows-identity-foundation  
```  
  
> [!NOTE]
>  Como muitas das classes no WIF 3.5 e WIF 4.5 compartilham os mesmos nomes, quando você estiver usando o WIF 3.5 e o WIF 4.5 juntos, certifique-se de usar nomes de classe totalmente qualificados ou usar um alias de namespace para distinguir entre classes no WIF 3.5 e no WIF 4.5.  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configuração do WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)  
 [Mapeamento de namespace entre o WIF 3.5 e o WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Novidades no Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)  
 [Ferramenta de identidade e acesso para o Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)
