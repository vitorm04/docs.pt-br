---
title: Novidades do Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a275c32caefb54b11cc605c1339526465c8319a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269326"
---
# <a name="what39s-new-in-windows-identity-foundation-45"></a>Novidades do Windows Identity Foundation 4.5
Esta é a primeira versão do Windows Identity Foundation (WIF) fornecido como um download autônomo. Ela também é conhecida como WIF 3.5 porque foi introduzida no período de tempo de distribuição do .NET 3.5 SP1. A partir do .NET 4.5, o WIF faz parte do .NET Framework. Ter as classes do WIF diretamente disponíveis na estrutura permite uma integração muito mais profunda da identidade baseada em declarações no .NET, facilitando o uso de declarações. Os aplicativos escritos para o WIF 3.5 precisam ser modificados para aproveitar o novo modelo; para obter informações, consulte [Diretrizes para migrar um aplicativo criado usando o WIF 3.5 para o WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Abaixo você pode encontrar alguns destaques sobre as alterações principais.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>O WIF agora é parte do .NET Framework  
 As classes WIF agora são distribuídas por meio de vários assemblies, sendo os principais `mscorlib`, `System.IdentityModel`, `System.IdentityModel.Services` e `System.ServiceModel`. Do mesmo modo, as classes do WIF são distribuídas em vários namespaces: <xref:System.Security.Claims?displayProperty=nameWithType>, vários namespaces [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) e <xref:System.ServiceModel.Security?displayProperty=nameWithType>. O namespace <xref:System.Security.Claims?displayProperty=nameWithType> contém as novas classes <xref:System.Security.Claims.ClaimsPrincipal> e <xref:System.Security.Claims.ClaimsIdentity> (consulte abaixo). Todas as entidades de segurança do .NET agora derivam de <xref:System.Security.Claims.ClaimsPrincipal>. Para obter informações mais detalhadas sobre os namespaces do WIF e os tipos de classes que eles contêm, consulte [Referência de API do WIF](../../../docs/framework/security/wif-api-reference.md). Para obter informações sobre como os namespaces são mapeados entre o WIF 3.5 e o WIF 4.5, consulte [Mapeamento de namespaces entre o WIF 3.5 e o WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Novos modelo de declaração e objeto principal  
 As declarações estão no núcleo do .NET Framework 4.5. As classes de declaração de base (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal>, <xref:System.Security.Claims.ClaimTypes> e <xref:System.Security.Claims.ClaimValueTypes>) estão diretamente em `mscorlib` no namespace <xref:System.Security.Claims?displayProperty=nameWithType>. Não é mais necessário usar interfaces para conectar declarações ao sistema de identidade .NET: <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal> e <xref:System.Web.Security.RolePrincipal> agora herdam de <xref:System.Security.Claims.ClaimsPrincipal>; e <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity> e <xref:System.Web.Security.FormsIdentity> agora herdam de <xref:System.Security.Claims.ClaimsIdentity>. Em outras palavras, cada classe principal servirá agora solicitações. As classes de integração do WIF 3.5 e as interfaces (`WindowsClaimsIdentity`, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) foram removidas. Além disso, a classe <xref:System.Security.Claims.ClaimsIdentity> agora expõe métodos que facilitam consultar a coleção de declarações de identidade.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>Alterações na experiência do WIF Visual Studio 4.5  
  
-   A funcionalidade **Adicionar Referência do STS...** do Visual Studio (utilitário de linha de comando FedUtil) não existe mais; em vez disso, use a nova extensão do Visual Studio **Ferramenta de Identidade e Acesso para o Visual Studio 2012**. Isso permite que você realize uma federação com um STS existente ou use um LocalSTS para testar soluções. Depois de instalar a extensão, clique com o botão direito do mouse no projeto e procure **Identidade e Acesso** no menu de contexto.  
  
-   Os modelos ASP.NET e STS não são mais fornecidos como declarações que podem ser usadas diretamente em modelos de projeto existentes do ASP.Net, de sites e do WCF.  
  
-   Os controles no namespace `Microsoft.IdentityModel.Web.Controls` (`SignInControl`, `FederatedPassiveSignInControl` e `FederatedPassiveSignInStatus`) não são transferidos para o WIF 4.5.  
  
## <a name="changes-to-the-wif-45-api"></a>Alterações no WIF 4.5 API  
  
-   Em geral, as classes relacionadas a declarações estão no namespace <xref:System.Security.Claims?displayProperty=nameWithType>; as classes relacionadas ao WCF – contratos de serviço, canais, fábricas de canal e hosts de serviço usados para cenários do WS-Trust – estão no <xref:System.ServiceModel.Security?displayProperty=nameWithType>; e todas as outras classes do WIF são distribuídas entre vários namespaces [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) – que incluem, por exemplo, classes que representam artefatos do WS-* e do SAML, manipuladores de token e classes relacionadas, além das classes usadas em cenários da Web Services Federation. Para obter mais informações, consulte [Mapeamento de namespaces entre o WIF 3.5 e o WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md) e [Referência de API do WIF](../../../docs/framework/security/wif-api-reference.md).  
  
-   A chave do computador foi habilitada para uso em cookies de sessão para cenários de farm Web. Para obter mais informações, consulte [WIF e Web farms](../../../docs/framework/security/wif-and-web-farms.md).  
  
-   Agora, configure o WIF de forma declarativa nos elementos [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) e [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). Para obter mais informações sobre a configuração do WIF, consulte [Referência de configuração do WIF](../../../docs/framework/security/wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>Outras alterações notáveis ou recursos do .NET causados pela integração do WIF no .NET  
  
-   O potencial para executar a autorização baseada em declarações (CBAC) é agora integral na estrutura do .NET Framework. Você pode configurar um objeto <xref:System.Security.Claims.ClaimsAuthorizationManager> e usar as classes <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> e <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> para executar verificações de acesso obrigatórias e declarativas no código. A CBAC oferece mais flexibilidade e granularidade maior do que verificações de acesso com base em funções tradicionais (RBAC). Também permite uma maior separação entre as políticas de autorização e a lógica de negócios, porque a lógica de negócios pode basear a verificação de acesso em uma declaração específica ou em um conjunto de declarações, e a política de autorização dessas declarações pode ser configurada de forma declarativa no elemento [\<claimsAuthorizationManager>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md).  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>O WCF muda como resultado da integração com o WIF:  
  
-   O modelo de identidade baseada em declarações do WCF é substituído pelo do WIF. Isso significa que as classes em <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, em <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, e os namespaces <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> devem ser descartados em favor do uso de classes do WIF.  
  
-   O WIF agora é habilitado em um serviço WCF com a especificação do atributo `useIdentityConfiguration` no elemento `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>` como mostrado no seguinte XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Ao usar a **Ferramenta de Identidade e Acesso para o Visual Studio 2012** (consulte **Alterações na experiência do Visual Studio** acima), a ferramenta adicionará um elemento `<serviceCredentials>` com o atributo `useIdentityConfiguration` definido com o arquivo de configuração para você. Ele também adiciona um elemento [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) correspondente que contém as definições de configuração do WIF e adiciona uma associação e outras configurações necessárias para terceirizar a autenticação para o STS escolhido.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes para migrar um aplicativo criado usando o WIF 3.5 para o WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)  
 [Mapeamento de namespace entre o WIF 3.5 e o WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Referência de API do WIF](../../../docs/framework/security/wif-api-reference.md)  
 [Referência de configuração do WIF](../../../docs/framework/security/wif-configuration-reference.md)
